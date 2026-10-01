# 一、 文件说明
## 1. 规则集文件类型
① 重构上游项目 [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip)，生成供下游项目 [panyichen48737/ruleset_geodata](https://github.com/panyichen48737/ruleset_geodata) 使用的 IP 数据源文件  
② 数据源文件为 [mihomo 内核](https://github.com/MetaCubeX/mihomo) rule-set 规则集文件（.list 格式），包含：`IP-ASN`、`IP-CIDR` 和 `IP-CIDR6` 规则类型，配置 `behavior: classical` 和 `format: text` 后可直接使用  
③ mihomo 内核 geodata 规则集文件，包括：geoip.dat、Country.mmdb、geoip.metadb 和 ASN.mmdb 等  
④ [sing-box 内核](https://github.com/SagerNet/sing-box) geodata 规则集文件，包括：geoip.db 等  
⑤ [ShellCrash](https://github.com/juewuy/ShellCrash) 中 CN_IP 绕过内核所需文件，包括：cn_ipv4.txt 和 cn_ipv6.txt，适用于开启“CN_IP 绕过内核”或“CNV6 绕过内核”的使用场景，分别用于替换 *\$CRASHDIR/cn_ip.txt* 和 *\$CRASHDIR/cn_ipv6.txt* 文件
## 2. 数据源
① 每天凌晨 2 点（北京时间 UTC+8）自动构建，根据 [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip) 进行深度定制，可点击查看包含的 [IP 段列表](https://github.com/panyichen48737/geoip/tree/ips)  
② `geoip,private,🔒 私有网络` & `privateip.list` 源采用 [config.json](https://github.com/panyichen48737/geoip/blob/master/config.json) 中的 `input.type:private`  
③ `geoip,cn,🀄️ 国内 IP` & `cnip.list` & `cn-asn.list` 源组合如下，`cn_ipv4.txt` 和 `cn_ipv6.txt` 由合并后的完整 CN 列表（即 `cnip.list`）拆分而来，而非只取其中某一个源：
  - [GeoLite2-Country-CSV/CN](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data) 和 [APNIC/CN](http://ftp.apnic.net/stats/apnic/delegated-apnic-latest)
  - [misakaio/chnroutes2](https://github.com/misakaio/chnroutes2)、[blackmatrix7/ios_rule_script/ChinaIPs](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash/ChinaIPs)（含 ChinaIPs 和 ChinaIPsTest 两份）、[ChanthMiao/China-IPv4-List](https://github.com/ChanthMiao/China-IPv4-List) 和 [ChanthMiao/China-IPv6-List](https://github.com/ChanthMiao/China-IPv6-List)
  - [zhufengme/block_cn_files](https://github.com/zhufengme/block_cn_files)、[17mon/china_ip_list](https://github.com/17mon/china_ip_list)、[metowolf/iplist](https://github.com/metowolf/iplist)、[gaoyifan/china-operator-ip](https://github.com/gaoyifan/china-operator-ip)（china.txt 和 china6.txt）和 [苍狼山庄/IPNetDB](https://ispip.clang.cn)（all_cn.txt 和 all_cn_ipv6.txt）
  - `cn-asn.list` 源采用 [blackmatrix7/ios_rule_script/ChinaASN](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Surge/ChinaASN) 和 [VirgilClyne/GetSomeFries/ASN.China](https://github.com/VirgilClyne/GetSomeFries) 合并去重
④ `geoip,netflix,🎥 奈飞视频` & `netflixip.list` & `netflix-asn.list` 源采用 [GeoLite2-ASN-CSV/Netflix](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data)（AS55095、AS40027、AS394406 和 AS2906）和 [blackmatrix7/ios_rule_script/Netflix](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash/Netflix)（Netflix_IP.txt）组合  
⑤ `geoip,media,🌍 国外媒体` & `mediaip.list` 源采用 [blackmatrix7/ios_rule_script/GlobalMedia](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash/GlobalMedia)（仅 IP）  
⑥ `geoip,games,🎮 国外游戏` & `gamesip.list` 源采用 [blackmatrix7/ios_rule_script/Game](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Clash/Game)（仅 IP）  
⑦ `geoip,telegram,📲 电报消息` & `telegramip.list` & `telegram-asn.list` 源采用 [GeoLite2-ASN-CSV/Telegram](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data)（AS62041、AS62014、AS59930、AS44907 和 AS211157）和 [Telegram IP 段](https://core.telegram.org/resources/cidr.txt)组合
# 二、 文件下载
**规则集文件包含的规则和下载地址对应关系如下表：**
<table>
  <tr>
    <td><b>规则集文件名称</b></td>
    <td align="center"><b>包含规则</b></td>
    <td><b>GitHub 源</b></td>
    <td><b>jsDelivr 源</b></td>
    <td><b>GitHub Proxy 源</b></td>
  </tr>
  <tr>
    <td>geoip-all.dat</td>
    <td rowspan="4" align="center"><a href="https://github.com/Loyalsoldier/geoip/tree/release/text">点此查看</a></td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-all.dat">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip-all.dat">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-all.dat">点此下载</a></td>
  </tr>
  <tr>
    <td>Country-all.mmdb</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-all.mmdb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country-all.mmdb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-all.mmdb">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip-all.metadb</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-all.metadb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip-all.metadb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-all.metadb">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip-all.db</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/sing-box-geodata/geoip-all.db">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@sing-box-geodata/geoip-all.db">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/sing-box-geodata/geoip-all.db">点此下载</a></td>
  </tr>
  <tr>
    <td>Country-ASN-all.mmdb</td>
    <td><code>cloudflare</code>、<code>cloudfront</code>、<code>facebook</code>、<code>fastly</code>、<code>google</code>、<code>netflix</code>、<code>telegram</code> 和 <code>twitter</code>，即上游 <a href="https://github.com/Loyalsoldier/geoip/tree/release/text">release 分支</a>的 Country-asn.mmdb 原样文件</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-ASN-all.mmdb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country-ASN-all.mmdb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-ASN-all.mmdb">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip.dat</td>
    <td rowspan="4"><code>private</code>、<code>cn</code>、<code>netflix</code>、<code>media</code>、<code>games</code> 和 <code>telegram</code></td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip.dat">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip.dat">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip.dat">点此下载</a></td>
  </tr>
  <tr>
    <td>Country.mmdb</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country.mmdb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country.mmdb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country.mmdb">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip.metadb</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip.metadb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip.metadb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip.metadb">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip.db</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/sing-box-geodata/geoip.db">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@sing-box-geodata/geoip.db">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/sing-box-geodata/geoip.db">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip-lite.dat</td>
    <td rowspan="4"><code>private</code>、<code>cn</code> 和 <code>telegram</code></td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-lite.dat">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip-lite.dat">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-lite.dat">点此下载</a></td>
  </tr>
  <tr>
    <td>Country-lite.mmdb</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-lite.mmdb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country-lite.mmdb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-lite.mmdb">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip-lite.metadb</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-lite.metadb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip-lite.metadb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/geoip-lite.metadb">点此下载</a></td>
  </tr>
  <tr>
    <td>geoip-lite.db</td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/sing-box-geodata/geoip-lite.db">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@sing-box-geodata/geoip-lite.db">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/sing-box-geodata/geoip-lite.db">点此下载</a></td>
  </tr>
  <tr>
    <td>Country-ASN.mmdb</td>
    <td><code>netflix</code>（AS55095、AS40027、AS394406 和 AS2906）和 <code>telegram</code>（AS62041、AS62014、AS59930、AS44907 和 AS211157），具体可<a href="https://github.com/panyichen48737/geoip/blob/master/config.json">点此查看</a></td>
    <td><a href="https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-ASN.mmdb">点此下载</a></td>
    <td><a href="https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country-ASN.mmdb">点此下载</a></td>
    <td><a href="https://ghfast.top/https://github.com/panyichen48737/geoip/releases/download/mihomo-geodata/Country-ASN.mmdb">点此下载</a></td>
  </tr>
</table>

# 三、 文件导入
## 1. 导入 Linux 端（以 ShellCrash 导入 geoip.dat、Country.mmdb、geoip.metadb、ASN.mmdb 和 geoip.db 为例）
连接 SSH 后执行如下命令：
```shell
# mihomo 内核
curl -fo "${CRASHDIR}/GeoIP.dat" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip.dat
curl -fo "${CRASHDIR}/Country.mmdb" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country.mmdb
curl -fo "${CRASHDIR}/geoip.metadb" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip.metadb
curl -fo "${CRASHDIR}/ASN.mmdb" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country-ASN.mmdb
# sing-box 内核
curl -fo "${CRASHDIR}/geoip.db" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@sing-box-geodata/geoip.db
"${CRASHDIR}/start.sh" restart
```
## 2. 导入 Windows 端（以 [Clash Verge](https://github.com/clash-verge-rev/clash-verge-rev) 导入 geoip.dat、Country.mmdb、geoip.metadb 和 ASN.mmdb 为例）
以管理员身份运行 CMD，执行如下命令：
```shell
taskkill /f /t /im "Clash Verge*"
taskkill /f /t /im Clash-Verge*
taskkill /f /t /im clash-meta*
curl -fo "%APPDATA%\io.github.clash-verge-rev.clash-verge-rev\geoip.dat" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip.dat
curl -fo "%APPDATA%\io.github.clash-verge-rev.clash-verge-rev\Country.mmdb" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country.mmdb
curl -fo "%APPDATA%\io.github.clash-verge-rev.clash-verge-rev\geoip.metadb" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/geoip.metadb
curl -fo "%APPDATA%\io.github.clash-verge-rev.clash-verge-rev\ASN.mmdb" -L https://cdn.jsdelivr.net/gh/panyichen48737/geoip@mihomo-geodata/Country-ASN.mmdb
pause
```

# 四、 开发说明
① 本仓库实际使用的 geoip 程序库来自 go.mod 中的 [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip) 模块（即 `github.com/Loyalsoldier/geoip/lib` 和 `github.com/Loyalsoldier/geoip/plugin/*`），根目录的 `main.go`、`init.go`、`list.go`、`convert.go`、`merge.go` 和 `lookup.go` 引用的都是该模块  
② 仓库根目录下的 `lib/` 和 `plugin/` 是 fork 上游时一并带入的副本，**不参与构建**：没有任何代码 import 它们，CI 执行的是 `go build ./`（只编译根包），因此改动它们不会影响任何产物，且会随 go.mod 中模块版本的升级逐渐过时  
③ 需要改变产物内容时，改根目录的 `*.go` 和 `config.json` 即可；无需本地编译，[GitHub Actions](https://github.com/panyichen48737/geoip/actions) 会自动完成构建
