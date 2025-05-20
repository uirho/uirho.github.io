---
title: KaTeXのテスト
description: 'Please enter a description of your post here, between 50-160 chars!'
publishDate: 21 May 2025
tags: [blog]
draft: false
---

暗号技術関連の記事を書くときに必ず数式を記述するため、TeX形式で書けるKaTeXを導入することにした。

## 導入方法
まず、<u>rehype-katex</u>と<u>remark-math</u>をインストールする。

``` shell
npm install rehype-katex remark-math
```

次に、<u>astro.config.ts</u>を開き、rehype-katexとremark-mathを追加する。

``` typescript
import { defineConfig } from "astro/config";

// KaTeX plugins
import rehypeKatex from 'rehype-katex';
import remarkMath from 'remark-math';

export default defineConfig({
  markdown: {
    rehypePlugins: [rehypeKatex],
    remarkPlugins: [remarkMath],
  },
})
```

最後に、KaTeXのCSSを適当なところに追加する。
``` html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.22/dist/katex.css" integrity="sha384-o3WH+1yEhq+grOgz1BVYTZPyTlMXrDxnjN1By9/ba94JqJhva6wFm2Hb+URQX53v" crossorigin="anonymous">
```

## 動作テスト
- インライン数式（\$\.\.\.\$で囲む）
$ e^{\pi i}+1=0$

- ブロック数式（\$\$\.\.\.\$\$で囲む）

$$
\varphi(n) = \prod_{p|m}(p-1)p^{e_p-1}
           = n\prod_{p|m}(1-\frac{1}{p})
$$
