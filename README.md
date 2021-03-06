# Aragog
Aragog is a crawler used to fetch list of a repository's issues.

# Development
```
npm run build & npm run dev
```

# Usage

```javascript
import fs from 'fs';
import path from 'path';
import Aragog from 'aragog';
const aragog = new Aragog({
  username: 'zz1211',
  repository: 'Doraemon',
  selector: `div[id^=issue_] a[href*="/zz1211/Doraemon/issues/"][id^=issue-id-]` // optional parameters
});

(async () => {
  await aragog.openPage();
  let issueList = [];
  let list = []
  let page = 1;
  do {
    list = await aragog.fetchIssueList({
      queryConditions: {
        'utf8': true,
        page: page++,
        q: ['is:issue', 'is:open', 'label:blog', '-label:TBD ']
      }
    });
    issueList = issueList.concat(list)
  } while (list.length > 0)
  fs.writeFileSync(path.resolve(process.cwd(), './issues.json'), JSON.stringify(issueList, null, 4), 'utf8');
  await aragog.closeBrowser();
})();
```

# Result

```json
[
  {
    "title": "ES6 -> Javascript的类与继承在Babel的实现",
    "href": "https://github.com/zz1211/Doraemon/issues/26",
    "labels": [
      "blog",
      "javascript",
      "zon"
    ]
  },
  {
    "title": "Javascript的模块机制s",
    "href": "https://github.com/zz1211/Doraemon/issues/25",
    "labels": [
      "blog",
      "browser",
      "javascript",
      "nodejs"
    ]
  },
  {
    "title": "前端基础性攻防对象 XSS & CSRF 的介绍",
    "href": "https://github.com/zz1211/Doraemon/issues/24",
    "labels": [
      "blog",
      "browser",
      "javascript",
      "security"
    ]
  },
  {
    "title": "梳理一下 Event Loop 这个东西",
    "href": "https://github.com/zz1211/Doraemon/issues/23",
    "labels": [
      "blog",
      "browser",
      "javascript",
      "nodejs"
    ]
  },
  {
    "title": "看看webpack都打出了些什么",
    "href": "https://github.com/zz1211/Doraemon/issues/22",
    "labels": [
      "blog",
      "tool",
      "zon"
    ]
  },
  {
    "title": "简单说一下 [清除 & 闭合]浮动",
    "href": "https://github.com/zz1211/Doraemon/issues/21",
    "labels": [
      "blog",
      "css",
      "html"
    ]
  },
  {
    "title": "Git 中那些容易混淆和忽略的指令都做了些神马",
    "href": "https://github.com/zz1211/Doraemon/issues/19",
    "labels": [
      "blog",
      "tool"
    ]
  },
  {
    "title": "浅谈前端的动画",
    "href": "https://github.com/zz1211/Doraemon/issues/13",
    "labels": [
      "blog",
      "browser",
      "css"
    ]
  },
  {
    "title": "Javascript 部分重点整理",
    "href": "https://github.com/zz1211/Doraemon/issues/12",
    "labels": [
      "blog",
      "javascript"
    ]
  },
  {
    "title": "React源码分析 - Diff算法",
    "href": "https://github.com/zz1211/Doraemon/issues/11",
    "labels": [
      "blog",
      "source code",
      "zon"
    ]
  },
  {
    "title": "React源码分析 - 生命周期",
    "href": "https://github.com/zz1211/Doraemon/issues/10",
    "labels": [
      "blog",
      "source code",
      "zon"
    ]
  },
  {
    "title": "React源码分析 - 组件更新与事务",
    "href": "https://github.com/zz1211/Doraemon/issues/9",
    "labels": [
      "blog",
      "source code",
      "zon"
    ]
  },
  {
    "title": "<深入浅出Nodejs> --- 内存管理",
    "href": "https://github.com/zz1211/Doraemon/issues/8",
    "labels": [
      "blog",
      "book"
    ]
  },
  {
    "title": "React源码分析 - 事件机制",
    "href": "https://github.com/zz1211/Doraemon/issues/7",
    "labels": [
      "blog",
      "source code",
      "stick",
      "zon"
    ]
  },
  {
    "title": "React源码分析 - 组件初次渲染",
    "href": "https://github.com/zz1211/Doraemon/issues/6",
    "labels": [
      "blog",
      "source code",
      "zon"
    ]
  },
  {
    "title": "函数式编程",
    "href": "https://github.com/zz1211/Doraemon/issues/5",
    "labels": [
      "blog",
      "javascript"
    ]
  },
  {
    "title": "常规CSS元素垂直居中",
    "href": "https://github.com/zz1211/Doraemon/issues/4",
    "labels": [
      "blog",
      "css"
    ]
  },
  {
    "title": "像素和viewport",
    "href": "https://github.com/zz1211/Doraemon/issues/3",
    "labels": [
      "blog",
      "browser",
      "css",
      "html"
    ]
  },
  {
    "title": "Koa源码分析",
    "href": "https://github.com/zz1211/Doraemon/issues/2",
    "labels": [
      "blog",
      "source code",
      "zon"
    ]
  },
  {
    "title": "Javascript中装饰器的实现原理",
    "href": "https://github.com/zz1211/Doraemon/issues/1",
    "labels": [
      "blog",
      "javascript",
      "zon"
    ]
  }
]
```