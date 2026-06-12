---
title: "web devs - border-radius in webkit-gtk"
date: 2010-06-10
forum: Art &amp; Design
---

### Post by ajy0852 on 2010-06-10
Does anyone besides me have this problem with webkit-gtk browsers (epiphany, midori, uzbl)?

Elements with border-radius have rounded corners like normal, but if they have a border, the border is not drawn on 3 of the 4 corners of the element (see attachment).

I'm wondering if this is just me or if everyone's experiencing this with this version of WebKitGtk+ (I'm using WebKitGTK+ 1.2.1 from the webkit-team ppa, the latest version). Any ideas?

Test page:
[http://dl.dropbox.com/u/6605310/border-radius.html]("http://dl.dropbox.com/u/6605310/border-radius.html")

The attachment shows what I get in Epiphany on this test page. Other browsers are just fine.

---

### Post by Mathieu147 on 2010-06-20
It seems to work fine in Midori and Chromium...

(Midori 0.2.2 with WebKitGTK+ 1.1.21, Chromium 5.0.375.38 (46659) Ubuntu)

---

### Post by ajy0852 on 2010-06-20
Thanks. Since this post, I've found that it's just something happening to me, and I don't really know why... or how to fix it. Are there any webkit configuration files anywhere? I don't want to remove & reinstall webkit since that would require removing and reinstalling LOTS of programs that are dependent on it...

It's kind of ugly, but I can deal with it until the next Ubuntu release. I'm not going to bother reinstalling before then.

---

