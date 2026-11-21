<div align="center">

[English](../../README.md) · [简体中文](README_zh.md) · [繁體中文](README_zh-TW.md) · [日本語](README_ja.md) · [한국어](README_ko.md) · [Türkçe](README_tr.md) · [Русский](README_ru.md) · [Tiếng Việt](README_vi.md) · [ไทย](README_th.md) · [Deutsch](README_de.md) · [Español](README_es.md) · [Français](README_fr.md) · [Українська](README_uk.md) · [Polski](README_pl.md) · [Português (Brasil)](README_pt-BR.md) · [العربية](README_ar.md) · [فارسی](README_fa.md) · [Bahasa Indonesia](README_id.md) · [Italiano](README_it.md)
· [Ελληνικά](README_el.md) · [മലയാളം](README_ml.md) · **हिन्दी** · [Roman Urdu](README_ur-Latn.md) · [Română](README_ro.md) · [Български](README_bg.md)

# REA: किसी भी चीज़ को Reverse Engineer करें

### Binaries, ऐप्लिकेशन्स और रनटाइम बिहेवियर के रिवर्स इंजीनियरिंग के लिए एक संपूर्ण MCP।

**कोई ऐसा फ़ीचर देखा जो आपको पसंद आया? जानिए कि वह बाइनरी स्तर तक कैसे काम करता है।**

[![GitHub stars](https://img.shields.io/github/stars/morluto/rea?style=flat-square&logo=github)](https://github.com/morluto/rea/stargazers)
[![Monthly npm downloads](https://img.shields.io/npm/dm/rea-agents?style=flat-square&label=npm%20downloads)](https://www.npmjs.com/package/rea-agents)
[![MIT license](https://img.shields.io/badge/license-MIT-f4c430?style=flat-square)](../../LICENSE)
[![Join the REA Discord](https://img.shields.io/badge/Discord-5865F2?style=flat-square&logo=discord&logoColor=white)](https://discord.gg/GkcryMnJDM)
[![Follow REA on X](https://img.shields.io/badge/X-000000?style=flat-square&logo=x&logoColor=white)](https://x.com/reatools)
[![Supported platforms: macOS, Windows, and Linux](https://img.shields.io/badge/macOS%20%7C%20Windows%20%7C%20Linux-4493F8?style=flat-square)](../getting-started/installation.md)
[![skills.sh](https://skills.sh/b/morluto/rea?style=flat-square)](https://skills.sh/morluto/rea/reverse-engineer-anything)

**[वेबसाइट](https://rea.tools/) · [गाइड्स](https://rea.tools/guides/) · [शोकेस](https://rea.tools/showcase/)**

<a href="https://discord.com/invite/GkcryMnJDM"><img alt="Discord पर REA कम्युनिटी से जुड़ें" src="https://img.shields.io/badge/Join%20us%20on%20Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" height="40"></a>

[त्वरित शुरुआत](#त्वरित-शुरुआत) · [शोकेस](#शोकेस) · [REA कैसे काम करता है](#rea-कैसे-काम-करता-है) · [आप क्या विश्लेषण कर सकते हैं](#आप-क्या-विश्लेषण-कर-सकते-हैं) · [RL वातावरण बनाएं](#rl-वातावरण-बनाएं) · [अक्सर पूछे जाने वाले प्रश्न](#अक्सर-पूछे-जाने-वाले-प्रश्न) · [दस्तावेज़](#दस्तावेज़)

<code>npx rea-agents setup</code>

</div>

> [!IMPORTANT]
> REA केवल [morluto/rea](https://github.com/morluto/rea),
> [rea.tools](https://rea.tools/), या [rea-agents npm package](https://www.npmjs.com/package/rea-agents) से ही प्राप्त करें।
> इन आधिकारिक स्रोतों से ही इंस्टॉलेशन और रिलीज़ लिंक का पालन करें। केवल मिलता-जुलता नाम या कॉपी किया गया README किसी डाउनलोड को आधिकारिक नहीं बनाता।

<div align="center">

<br />

<img src="../assets/rea-hopper-analysis.png" alt="एक native binary का निरीक्षण करते समय Hopper के अंदर REA अपना विश्लेषण ब्रिज शुरू कर रहा है" width="1200" />

<br /><br />

<table aria-label="REA community">
<tr>
<td align="center" width="360">
  <a href="https://discord.gg/GkcryMnJDM">
    <img src="../assets/discord.svg" height="42" alt="Discord" /><br />
    <strong>रिवर्स इंजीनियरिंग कम्युनिटी से जुड़ें</strong>
  </a><br />
  <sub>Discord · प्रश्नोत्तर · शो और टेल</sub>
</td>
</tr>
</table>

<br />

</div>

---

किसी ऐप में कोई ऐसा फ़ीचर देखा जो आपको अपने प्रोडक्ट में चाहिए? अपने AI एजेंट से कहें कि वह REA के साथ उसकी जांच करे। यह बिना सोर्स कोड के ऐप का निरीक्षण कर सकता है, समझा सकता है कि फ़ीचर कैसे काम करता है, साक्ष्य (evidence) दिखा सकता है, और आपके प्रोजेक्ट के लिए एक नया संस्करण तैयार कर सकता है।

REA आपके एजेंट को नेटिव बाइनरीज़, जावास्क्रिप्ट और इलेक्ट्रॉन ऐप्स, .NET असेंबली और वेबसाइटों का निरीक्षण करने वाले टूल्स से जोड़ता है। आप इन्हीं टूल्स का उपयोग अपने टर्मिनल से भी कर सकते हैं। विश्लेषण स्थानीय रूप से चलता है, और परिणामों में प्रत्येक निष्कर्ष के पीछे का साक्ष्य शामिल होता है।

सेटअप आपके एजेंट के साथ REA को पंजीकृत करता है और संबंधित वर्कफ़्लो निर्देश इंस्टॉल करता है। नेटिव विश्लेषण मौजूदा Hopper, Ghidra, IDA या Kuna इंस्टॉलेशन का उपयोग कर सकता है। स्टेटिक जावास्क्रिप्ट विश्लेषण के लिए किसी नेटिव इंजन की आवश्यकता नहीं होती है।

## त्वरित शुरुआत

प्रत्येक ऑपरेटिंग सिस्टम, एजेंट और विश्लेषण प्रदाता के लिए चरण-दर-चरण निर्देशों के लिए **[rea.tools पर शुरुआत करें](https://rea.tools/get-started/)** देखें।

### अपने एजेंट को कनेक्ट करें (MCP)

[Node.js और npm](#आप-क्या-विश्लेषण-कर-सकते-हैं) इंस्टॉल होने के बाद, इसे अपने प्रोजेक्ट से बाहर किसी विश्वसनीय डायरेक्टरी में चलाएं:

```bash
npx rea-agents setup
```

अपना एजेंट चुनें, सेटअप योजना की समीक्षा करके उसे स्वीकृत करें, और फिर अपने एजेंट को पुनः आरंभ करें। सेटअप मौजूदा कॉन्फ़िगरेशन का बैकअप लेता है और REA का MCP कनेक्शन जोड़ता है। समर्थित क्लाइंट, प्लगइन्स और समस्या निवारण के लिए [स्थापना गाइड](../getting-started/installation.md) देखें।

अपने एजेंट से इस प्रकार पूछें:

```text
Understand how search works in the Notes app, show me the evidence, and build a
similar feature for my project.
```

### टर्मिनल से REA का उपयोग करें (CLI)

निकाली गई जावास्क्रिप्ट/इलेक्ट्रॉन ऐप डायरेक्टरी या ASAR का निरीक्षण करें:

```bash
npx -y rea-agents@latest analyze-javascript-application /absolute/path/to/app --json
```

परिणाम में मॉड्यूल, आयात, इलेक्ट्रॉन सीमाएं और उनके साक्ष्य शामिल होते हैं। पथ को अपने लक्ष्य से बदलें, जैसे Windows पर `"D:/apps/example"`।

नियमित उपयोग के लिए `rea` कमांड इंस्टॉल करें:

```bash
npm install --global rea-agents
rea --help
```

नेटिव विश्लेषण के लिए, पहले एक प्रदाता कॉन्फ़िगर करें। [CLI और साक्ष्य गाइड](../getting-started/cli.md) प्रदाता चयन, नेटिव कमांड और स्क्रिप्टिंग को कवर करता है।

### REA को अपडेट करें

ग्लोबल npm या Bun इंस्टॉलेशन के लिए, अपडेटर चलाएं:

```bash
rea update
```

यदि आप `npx` का उपयोग करते हैं, तो अपने एजेंट सेटअप को इसके साथ रीफ़्रेश करें:

```bash
npx rea-agents@latest setup
```

## शोकेस

<a href="https://rea.tools/showcase/">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/rea-showcases-dark.svg" />
    <img alt="DX-Ball साउंड-पैन, Notion क्लिपबोर्ड-ब्रिज और TH04 बुलेट-रिंग शोकेस के चित्र" src="../assets/rea-showcases.svg" />
  </picture>
</a>

<table>
<tbody>
<tr>
<td>
<h3>DX-Ball: साउंड-पैन गणना का पुनर्निर्माण</h3>
<p>x86 निर्देशों से स्थिति-से-पैन हेल्पर को पुनर्प्राप्त करें और मूल-x86 मामलों और सभी 63 संकलित फ़ंक्शन बाइट्स के विरुद्ध C पुनर्निर्माण को सत्यापित करें।</p>
<a href="https://rea.tools/showcase/dx-ball/">केस स्टडी पढ़ें</a> ·
<a href="https://github.com/N0zoM1z0/dx-ball">पुनर्निर्माण रिपॉजिटरी</a>
</td>
</tr>
<tr>
<td>
<h3>Notion: इलेक्ट्रॉन क्लिपबोर्ड ब्रिज को ट्रेस करें</h3>
<p>रेंडरर के क्लिपबोर्ड API को प्रीलोड और IPC के माध्यम से मुख्य प्रक्रिया में ट्रैक करें ताकि यह देखा जा सके कि Notion रिच क्लिपबोर्ड डेटा को कैसे संभालता है।</p>
<a href="https://rea.tools/showcase/notion/">केस स्टडी पढ़ें</a>
</td>
</tr>
<tr>
<td>
<h3>TH04: एक डॉस बुलेट-रिंग गणना पुनर्प्राप्त करें</h3>
<p>PC-98 गेम के 16-बिट निर्देशों से कोण गणना पुनर्प्राप्त करें और ऐतिहासिक कंपाइलर आउटपुट के साथ पुनर्निर्मित C++ की तुलना करें।</p>
<a href="https://rea.tools/showcase/th04/">केस स्टडी पढ़ें</a> ·
<a href="https://github.com/N0zoM1z0/th04">पुनर्निर्माण रिपॉजिटरी</a>
</td>
</tr>
</tbody>
</table>

## REA कैसे काम करता है

आपका एजेंट किसी लक्ष्य का निरीक्षण करने और प्रासंगिक कोड को ट्रेस करने के लिए MCP के माध्यम से REA का उपयोग करता है। यह अनुवर्ती प्रश्न पूछने, व्यवहार समझाने या कार्यान्वयन बनाने और परीक्षण करने के लिए REA द्वारा लौटाए गए साक्ष्य का उपयोग कर सकता है।

<img src="../../website/public/assets/figures/rea-investigation-flow.svg" alt="REA जांच प्रवाह" width="1200" />

## आप क्या विश्लेषण कर सकते हैं

REA नेटिव बाइनरीज़, जावास्क्रिप्ट और इलेक्ट्रॉन ऐप्स, वेबसाइटों, .NET असेंबली, एंड्रॉइड ऐप्स, फर्मवेयर, और रिकॉर्ड की गई रनटाइम और नेटवर्क गतिविधि को कवर करता है।

REA के लिए Node.js 22.x (>=22.23.4), 24.x (>=24.22.1), या 26.12.1+, और npm आवश्यक है।

नेटिव डीकंपाइलेशन के लिए, ऐसा प्रदाता चुनें जो आपके लक्ष्य प्रारूप और होस्ट OS का समर्थन करता हो।

## RL वातावरण बनाएं

किसी AI एजेंट को किसी वास्तविक ऐप को चलाए बिना किसी कार्य का अभ्यास करने के लिए एक स्थानीय वातावरण प्रदान करें। इसका उपयोग रीइन्फोर्समेंट लर्निंग (RL) के लिए या यह जांचने के लिए करें कि एजेंट कार्यों को कितनी अच्छी तरह पूरा करता है।

REA रिकॉर्ड किए गए API अनुरोधों और प्रतिक्रियाओं को ऐसे टूल्स में बदल देता है जिन्हें एजेंट कॉल कर सकता है।

```text
Use REA to build an RL environment from my test web app at
http://127.0.0.1:3000.
Cover listing, creating, renaming, and deleting folders. You may create and
remove test folders. Leave existing data unchanged.
Save it in a folder named my-env. Check which operations work and tell me
how to run it.
```

## अक्सर पूछे जाने वाले प्रश्न

<details>
<summary><strong>कौन से एजेंट REA का उपयोग कर सकते हैं?</strong></summary>

कोई भी एजेंट जो स्थानीय MCP सर्वर का समर्थन करता है। सेटअप समर्थित एजेंटों को कॉन्फ़िगर करता है; अन्य क्लाइंट मैन्युअल MCP पंजीकरण का उपयोग कर सकते हैं।

</details>

<details>
<summary><strong>क्या मुझे नेटिव विश्लेषण इंजन की आवश्यकता है?</strong></summary>

डीप नेटिव विश्लेषण लक्ष्य और ऑपरेशन के आधार पर Hopper, Ghidra, IDA या Kuna का उपयोग करता है। स्टेटिक जावास्क्रिप्ट और .NET निरीक्षण बिना नेटिव इंजन के काम करते हैं।

</details>

<details>
<summary><strong>क्या REA मेरा ऐप अपलोड करता है?</strong></summary>

REA स्थानीय रूप से लक्ष्यों का विश्लेषण करता है। आपका कोड किसी बाहरी सर्वर पर अपलोड नहीं किया जाता।

</details>

<details>
<summary><strong>यदि कोई बग मिले तो मुझे क्या करना चाहिए?</strong></summary>

पहले REA को अपडेट करें। यदि समस्या बनी रहती है, तो अपने REA संस्करण, लक्ष्य प्रकार और त्रुटि विवरण के साथ एक [GitHub Issue](https://github.com/morluto/rea/issues) खोलें।

</details>

## दस्तावेज़

विस्तृत विकल्पों, पूर्वापेक्षित आवश्यकताओं और अनुबंधों के लिए:

- [स्थापना और सेटअप](../getting-started/installation.md)
- [CLI और साक्ष्य](../getting-started/cli.md)
- [MCP अनुबंध और एजेंट प्रॉम्प्ट](../getting-started/mcp-prompts.md)
- [समर्थित लक्ष्य](../reference/supported-targets.md)

कमज़ोरियों की रिपोर्ट [SECURITY.md](../../SECURITY.md) के माध्यम से करें।

## लाइसेंस

[MIT](../../LICENSE)

REA द्वारा लिखित कोड MIT के तहत लाइसेंस प्राप्त है। अधिक जानकारी के लिए [थर्ड पार्टी नोटिस](../../THIRD_PARTY_NOTICES.md) देखें।
