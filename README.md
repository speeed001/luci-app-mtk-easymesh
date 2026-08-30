# luci-app-mtk-easymesh

> 不确定稳定性，连能不能跑都不知道。暂时无暇更新，慎用！

LuCI 界面，用于在 OpenWrt / ImmortalWrt（MediaTek MT7981 / MT7986 + mtwifi 闭源驱动）上控制 MTK EasyMesh（MAP / wapp / bs20）。

## 功能

- Basic：开关 EasyMesh、设置 Device Mode / Role、PBC / DPP 入网、恢复默认
- Advanced：漫游调优、回程（Backhaul）优先级、信道/扫描阈值、1905d 参数等
- MAP QoS：Channel Planning、Network Optimization、信道利用率阈值
- Status：wapp / bs20 运行状态、AL MAC、MAP 版本、角色、ALID、无线列表
- Topology：运行时拓扑与在线客户端展示

## 依赖

- `mtwifi-cfg`（含 wapp / 1905d 闭源驱动配置）
- `mtwifi-wapp`
- `lua-cjson`

## 编译

放到 `package/` 下，然后在固件根目录：

```sh
make package/luci-app-mtk-easymesh/compile
```

或直接在 menuconfig 中启用 `luci-app-mtk-easymesh` 后整体编译。

## 使用方法

编译进固件后，LuCI → 网络 → EasyMesh 即可配置。保存并应用后，插件会把配置写入
`/etc/map/mapd_cfg`、`/etc/map/1905d.cfg` 并重启 wapp / bs20。
