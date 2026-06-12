---
title: "Default Window Title Font"
date: 2007-05-25
forum: Art &amp; Design
---

### Post by ankursethi on 2007-05-25
I was tweaking my fonts but forgot to note the default ones. Can somebody please tell me the name and size of the default window title font?

Thanks.

---

### Post by sebbouckaert on 2007-05-25
Isn't that Sans by default?

---

### Post by ankursethi on 2007-05-25
Can someone just check and tell me?

---

### Post by kiddo on 2007-05-25
Window titles are **Sans Bold 10**
Fixed width is **Monospace 10**

All the rest is **Sans 10** :)

also, you could always use this bunch of commands to reset the fonts:

```
gconftool-2 --unset /desktop/gnome/interface/document_font_name
gconftool-2 --unset /desktop/gnome/interface/font_name
gconftool-2 --unset /desktop/gnome/interface/monospace_font_name
```

---

### Post by ankursethi on 2007-05-26
Whew, thanks.

And thanks for the neat commands, too.

---

### Post by JohanSwe on 2007-06-02
But Sans isn't the name of the font right? In the dialog it says font family, and I can't find a font named sans in my fonts:///

Anyone knows the name of the standard font?

---

### Post by JohanSwe on 2007-06-05
oh, there is a font called Sans, it is visible in Gimp, but not in fonts:// in Nautilus or in the font menu in OOo Writer, I can use it in OOo if typing the name of the font, this is strange

anyone that knows anything about this.. :/

---

### Post by Wise Ferret on 2007-06-05
Sans was once a pointer to Bitstream Vera Sans. Now it is a pointer to DejaVu Sans.

---

