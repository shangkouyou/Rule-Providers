# Rule-Providers

个人使用的 **Mihomo / Clash Meta** 域名规则集仓库。

所有规则文件位于 [`Mihomo/`](./Mihomo) 目录，可通过 `raw.githubusercontent.com` 直接引用。

## 目录结构

```
Rule-Providers/
├── README.md
├── ICO/
│   └── favicon.ico
└── Mihomo/
    ├── 21Proxy.list
    ├── 21LAN.list
    ├── UK-WI-FICalling.list
    └── ...（ACL4SSR 快照）
```

## 文件说明

| 文件 | 规则数 | 说明 | 来源 |
|---|---:|---|---|
| `21LAN.list` | 154 | 强制直连白名单（银行 / 支付 / 政务 / 国内常用） | 自维护 |
| `21Proxy.list` | 85 | 独立出口分组（交易所 / AI / 流媒体 / Meta 等） | 自维护 |
| `Apple.list` | 29 |  | ACL4SSR 快照 |
| `Bahamut.list` | 5 |  | ACL4SSR 快照 |
| `BanAD.list` | 588 |  | ACL4SSR 快照 |
| `BanProgramAD.list` | 1016 |  | ACL4SSR 快照 |
| `Bilibili.list` | 20 |  | ACL4SSR 快照 |
| `BilibiliHMT.list` | 21 |  | ACL4SSR 快照 |
| `Bing.list` | 3 |  | ACL4SSR 快照 |
| `ChinaCompanyIp.list` | 208 |  | ACL4SSR 快照 |
| `ChinaDomain.list` | 635 |  | ACL4SSR 快照 |
| `ChinaMedia.list` | 38 |  | ACL4SSR 快照 |
| `Download.list` | 22 |  | ACL4SSR 快照 |
| `Epic.list` | 6 |  | ACL4SSR 快照 |
| `GoogleCN.list` | 29 |  | ACL4SSR 快照 |
| `GoogleFCM.list` | 44 |  | ACL4SSR 快照 |
| `LSProxy.list` | 2 |  | ACL4SSR 快照 |
| `LocalAreaNetwork.list` | 37 |  | ACL4SSR 快照 |
| `Microsoft.list` | 79 |  | ACL4SSR 快照 |
| `NetEaseMusic.list` | 37 |  | ACL4SSR 快照 |
| `Netflix.list` | 40 |  | ACL4SSR 快照 |
| `Nintendo.list` | 15 |  | ACL4SSR 快照 |
| `OneDrive.list` | 17 |  | ACL4SSR 快照 |
| `OpenAi.list` | 17 |  | ACL4SSR 快照 |
| `Origin.list` | 7 |  | ACL4SSR 快照 |
| `ProxyGFWlist.list` | 6986 |  | ACL4SSR 快照 |
| `ProxyMedia.list` | 372 |  | ACL4SSR 快照 |
| `Sony.list` | 5 |  | ACL4SSR 快照 |
| `Steam.list` | 18 |  | ACL4SSR 快照 |
| `SteamCN.list` | 16 |  | ACL4SSR 快照 |
| `Telegram.list` | 13 |  | ACL4SSR 快照 |
| `UK-WI-FICalling.list` | 12 | 英国 EE WiFi Calling（ePDG） | 自维护 |
| `UnBan.list` | 31 |  | ACL4SSR 快照 |
| `YouTube.list` | 14 |  | ACL4SSR 快照 |

## 在 Mihomo 中引用

```yaml
rule-providers:
  21Proxy:
    type: http
    behavior: classical
    format: text
    url: "https://raw.githubusercontent.com/shangkouyou/Rule-Providers/main/Mihomo/21Proxy.list"
    path: ./ruleset/21Proxy.list
    interval: 86400
  21LAN:
    type: http
    behavior: classical
    format: text
    url: "https://raw.githubusercontent.com/shangkouyou/Rule-Providers/main/Mihomo/21LAN.list"
    path: ./ruleset/21LAN.list
    interval: 86400
```

## 图标

`ICO/favicon.ico` 为 Mihomo 面板中策略组使用的图标：

```yaml
icon: "https://raw.githubusercontent.com/shangkouyou/Rule-Providers/main/ICO/favicon.ico"
```

## 维护约定

- **注释必须独立成行。** Mihomo 的 `format: text` 解析器只跳过以 `#` 开头的整行，
  不会剥离行尾注释；`DOMAIN-SUFFIX,x.com  # 说明` 会把注释当成域名的一部分，导致该条规则**静默失效**。
- 本仓库所有文件均为 **classical** 文本格式，引用时 `behavior` 请设为 `classical`。
- 支持的写法：`DOMAIN`、`DOMAIN-SUFFIX`、`DOMAIN-KEYWORD`、`IP-CIDR`、`IP-CIDR6` 等。
- `IP-CIDR` / `IP-CIDR6` 规则建议带 `no-resolve`。
- ACL4SSR 相关文件为某一时点的快照，**不会随上游自动更新**；需要刷新时重新拉取覆盖即可。

## 变更记录

- **2026-10-25**
  - 新建仓库，规则文件统一归入 `Mihomo/` 目录。
  - 新增 `ICO/favicon.ico` 图标。
  - `21Proxy.list` 新增 OKX / 欧易（OE）域名：`okx.com`、`okex.com`、`oklink.com`、`okx.cab`。
  - `21LAN.list` 修正 53 条带行尾注释的规则（原写法在 Mihomo 中不生效）。
  - 去除重复规则（`DOMAIN-KEYWORD,lovart`）。
