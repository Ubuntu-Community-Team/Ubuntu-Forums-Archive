---
title: "XML declarations not well-formed"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Ink-Jet on 2007-06-03
Inputting the command:
```
gedit ~/.fonts.conf
```gives the result
```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
```The text in "~/.fonts.conf" is:
```
<?xml version=”1.0”?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font”>
<edit name=”autohint” mode=”assign”>
<bool>true</bool>
</edit>
</match>
</fontconfig>
```Anyone know how to stop this message appearing? It happens very often, after I was playing around wtih something. Can't remember what, it was a while ago, but i just didn't get around to addressing it.

---

### Post by Ink-Jet on 2007-06-03
Swapping all the speech marks with colons fixed it.
Don't worry.

---

