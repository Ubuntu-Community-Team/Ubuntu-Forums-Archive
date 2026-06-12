---
title: "Fonts not selectable in Inkscape since upgrade to 14.04"
date: 2014-09-15
forum: Art &amp; Design
---

### Post by cov on 2014-09-15
Inkscape loads and displays fonts on existing documents correctly, but the fonts are not present in the dropdown if I want to enter new text.

My document has text which is rendered as ARIAL.

However, ARIAL does not appear in the dropdown when I want to enter new text.

This appears to be since an upgraded from 12.04 to 14.04.

---

### Post by ian-weisser on 2014-09-15
Do you have an arial font installed in /usr/share/fonts/truetype/msttcorefonts/ ?

---

### Post by cov on 2014-09-16
Hi Ian,

Thanks for the response.

No, I don't:
```
dave@Threepwood:~$ ls /usr/share/fonts/truetype/
dejavu                     kacst       openoffice            ubuntu-font-family
droid                      kacst-one   takao-gothic          unfonts-core
fonts-japanese-gothic.ttf  lao         tlwg                  unifont
freefont                   liberation  ttf-dejavu            wqy
gentium                    lyx         ttf-indic-fonts-core
gentium-basic              McCrystal   ttf-khmeros-core
horai-umefont              nanum       ttf-punjabi-fonts

```

Just to be clear, the document displays without error. If I double-click the text the font appears in a dropdown (with an exclamation icon). If I select 'Text and Font', the dialog box appears but the font (in this case Verdana font) is not present in the font selector. The preview panel is also corrupted.

[ATTACH=CONFIG]256475[/ATTACH]

---

### Post by ian-weisser on 2014-09-16
Install the package: ttf-mscorefonts-installer .

---

### Post by cov on 2014-09-16
Thank you: that sorted it.

:)

---

