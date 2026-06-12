---
title: "I cannot change the window title font size"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2007-07-05
hi there,
The size of the window title font it got (I do not know why) too small, and also the "username" when I log on in Ubuntu.  
I went to System->Preferences->Font, and the only options that do not work are "window title font" and "Fixed width font", then I wonder how can I fix this problem?
Also, the font size of the menu (and window title) of Emacs is too small, I have re-installed Emacs and still is the same. Mean while for this problem, at least I am able to set the font size of the text within Emacs in the .emacs file.

Can anybody help me, please?

thanks in advance

Ps: I am using ubuntu 7.04 in an IBM lenovo T60

---

### Post by moore.bryan on 2007-07-06
> **cseljatib said:**
> I went to System->Preferences->Font, and the only options that do not work are "window title font" and "Fixed width font", then I wonder how can I fix this problem?
*i don't think i understand... what do you mean by "the only options that do not work?"*
> Also, the font size of the menu (and window title) of Emacs is too small, I have re-installed Emacs and still is the same. Mean while for this problem, at least I am able to set the font size of the text within Emacs in the .emacs file.
[i]did that solve your problem?  you can try editing/making your ~/.gtkrc-2.0 file...
```

style "user-font"
     {
     font_name="name_of_the _font_you_want_to_use"
     }
widget_class "*" style "user-font"

gtk-font-name="name_of_the _font_you_want_to_use"

```
this will make system-wide changes...
[/i]

---

### Post by mcduck on 2007-07-06
Are you using Compiz or Beryl? In that case you need to configure the window title in Beryl Theme Manager (or whatever tool Compiz has for themes).

---

### Post by ela04cz on 2007-08-18
solved! Adding ¨-dpi 96¨ in the end of >login window>security>configure Xserver>command line

---

