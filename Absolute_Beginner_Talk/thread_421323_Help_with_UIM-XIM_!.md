---
title: "Help with UIM-XIM !"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-24
I was trying to setup UIM-XIM to use along with the browser. Found an article : [http://uim.freedesktop.org/wiki/UIM_2dXIM](http://uim.freedesktop.org/wiki/UIM_2dXIM) and followed the instructions. Unfortunately, I haven't used any such applications before and I am new to linux also..so basically I am stuck .

For an overview, this is what I did :

$ apt-get install uim uim-utils uim-gtk2.0 uim-xim uim-fep  -- 

and then later :

$ uim-xim --engine=tutcode
 UIM-XIM bridge. Now supporting multiple locales.
 Using full-synchronous XIM event flow
 Supported conversion engines:
  tutcode (ja)
  tcode (ja)
  hangul2 (ko)
  hangul3 (ko)
  romaja (ko)
  viqr (vi)
  ipa-x-sampa ()
  latin ()
  byeoru (ko)
  py (zh_CN)
  pyunihan (zh)
  pinyin-big5 (zh_TW:zh_HK)
  direct (*)
XMODIFIERS=@im=uim registered, selecting tutcode (ja) as default conversion engine

Frankly I have no Idea how to proceed from here. It would be great if anyone with any experience could shed some light on it.  What else should I do here ? Hope I am not making any big blunder.. 

Any sort of help is much appreciated.

---

### Post by Najand on 2007-04-24
You want to install uim for using inputing Japanese on gnome or other desktop managers?

---

### Post by Joseaa on 2007-04-24
In a way yes. Apart from that I want to test how UIM-XIM works in a browser.

---

### Post by Najand on 2007-04-24
Add the following to any of "~/.xsession", "~/.xinitrc", "~/.gnomerc", "~/.xprofile" files.
```

GTK_IM_MODULE=uim ; export GTK_IM_MODULE
QT_IM_MODULE=uim ; export QT_IM_MODULE
uim-xim &
XMODIFIERS=@im=uim ; export XMODIFIERS

```
Restart X. (CTRL+ALT+BACKSPACE)
Use SHIFT+SPACE to change your INPUT METHOD ENGINE.

---

### Post by Joseaa on 2007-04-24
As per your instructions I edited the file ~/.xinitrc"( Note that this file didn't exist in the home directory before so I created a new one and appended the code) restarted X. Then I again ran  uim-xim in the terminal to start the server. 

Nothing seems to be having any effect ( with shift + space ). Am I doing it wrong ? or is there any other way to do it ?

---

