---
title: "GIMP: How do I save font?"
date: 2005-11-23
forum: Art &amp; Design
---

### Post by bashhelp on 2005-11-23
Whenever I start Gimp, it resets back to the default font, Ariel or whatever it is.

Anyways, how do I save my favourite font into Gimp settings?  So when I start Gimp, my favourite font is loaded initially when I click on the Font tool.

Thanks in advance for the help.

---

### Post by 2notch on 2005-11-24
By default, the font config is read from /usr/share/gimp/2.0/themes/Default/gtkrc. At about line 63 you'll find this code: ```
style "gimp-tiny-font-style"
{
  font_name = "sans 8"
}  
```
If you have root access, you can change it there.

If not, then you need to add the above code to the gtkrc file in the .gimp-2.x directory in your home folder and change the font and size to your preference.

---

### Post by bashhelp on 2005-11-28
Not working.

I tried:

font_name = "Smooth 9"
font_name = "Artwiz Smooth 9"
font_name = "Artwiz Smooth Semi-Condensed 9"

None of them worked.

---

