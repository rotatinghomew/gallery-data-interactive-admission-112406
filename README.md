# 云岫数字展厅预约资料

以下台账为合成数据，不涉及真实访客、供应商或展馆。CSV 采用 UTF-8，首行为字段名，空字段代表源资料未给出。标识仅在字段明示的实体范围内使用。`data/agreements.json` 是当期业务方提供的运营资料，`data/formats.json` 记录文件列顺序和确定的外键引用。

- `data/days.csv` 记录同一馆日的开售资料截点、实际上线政策和观察截止。行序为历史先后。列为 `day`、`venue`、`shift`、`policy`、`plan_received`、`close`。
- `data/groups.csv` 记录预约与散客组级机会，档开始分钟用于确认预约范围。散客档列为观测分箱。列为 `group`、`day`、`source`、`size`、`route`、`request_min`、`slot_start`、`arrival_min`、`receipt`。
- `data/device_use.csv` 记录前台排队、短离或设备真实占用，分钟以同一馆日为参照。列为 `group`、`stage`、`device`、`joined`、`started`、`end`、`state`、`source`。
- `data/interruptions.csv` 记录停用及降级的有效分钟和获知分钟。降级表示可容纳人数减半。列为 `day`、`device`、`start`、`end`、`received`、`status`、`reason`。
- `data/observation.csv` 记录观察员实际覆盖的时间和区域。列为 `day`、`scope`、`first`、`last`、`status`。
- `data/bookings.csv` 记录已确认和候选选择。窗口以竖线分隔，窗口内任一连续可完成组合即可。改约对原范围的释放取决于确认。列为 `booking`、`day`、`route`、`size`、`windows`、`status`、`fallback_ack`、`received`。

使用 Python 3.11，无第三方依赖。用 `python3 -m unittest discover -s tests -v` 核对文件的可读性、列结构和确定引用，源文件保持只读。
