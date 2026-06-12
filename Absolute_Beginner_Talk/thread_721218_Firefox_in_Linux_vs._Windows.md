---
title: "Firefox in Linux vs. Windows?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-11
the same page in the same browser(firefox 2.0.0.12), the page looks different in window than linux(linux looks worse), it is also like the css is being rendered differently, anyone know what would case this?

---

### Post by kellemes on 2008-03-11
Could be a font-issue..
Have you tried different fonts? Maybe even the MS ones?
[https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts]("https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts")

---

### Post by kesman on 2008-03-11
Maybe there's a different configuration in the firefox in ubuntu repository. If you want, you could try to download the firefox linux version from their site directly, it comes in a tar.bz -package. Extract in your /home somewhere and run with
```

/home/user/path/to/firefox

```
also, if you wan't to force it to use ABSOLUTELY default settings, move your /home/user/.mozilla -directory somewhere else, and put it back after you have tested to get your bookmarks and other settings back.

---

### Post by hyper_ch on 2008-03-11
The Windoze fonts are proprietary and not by default installed on Ubuntu

---

### Post by vishzilla on 2008-03-11
Its a font issue, you could install the fonts from the repo. Follow the link mentioned above

---

### Post by RyanZec on 2008-03-11
it was the fonts, most other site looked fine tho.  Is that an issue that could be fixed with proper css?

---

### Post by Jabz.biz on 2008-03-11
I agree, it`s mostely a question of how well the website was scripted. Clean CSS and XHTML should look the same in all browsers (exept Internet Explorer). Another thing could be the font size wich you can adjust in firefox`s settings > content.

---

### Post by Sukarn on 2008-03-11
I honestly find the windows fonts to be worse than the ones Ubuntu defaults to, but its just personal taste.

People don't realize Ubuntu's fonts are better because they've gotten too used to looking at the fonts in Windows.

I used to be a windows only user, and now I'm a Linux only user, but even when I dual booted, I found Ubuntu's fonts to be better, although this was not the case initially.

---

