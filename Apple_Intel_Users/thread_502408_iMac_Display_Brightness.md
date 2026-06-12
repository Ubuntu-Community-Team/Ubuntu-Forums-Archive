---
title: "iMac Display Brightness"
date: 2007-07-16
forum: Apple Intel Users
---

### Post by rami1983 on 2007-07-16
My iMac display is too bright ... is there is a way to lower the brightness in Ubuntu?

---

### Post by cyberdork33 on 2007-07-16
I have never actually tried to adjust mine, but have you tried the tools that the macbook users have?

---

### Post by rami1983 on 2007-07-16
Thanks it's working ... problems solved :)
 there is tool called brightness from MacBook tools ... I compiled brightness.c  and use it "**sudo brightness 200**"


**[COLOR="Red"]Not brightness --> backlight[/COLOR]**

---

### Post by zm887 on 2007-07-17
Hi.  I'm having the same problem with a new 20" imac.  Can someone please post a link to the "brightness.c" code?  I've been googling to try to find it, but no luck ...

Thanks!

---

### Post by rami1983 on 2007-07-18
Sorry .. the tool is not **brightness** ... it's called **backlight** ... I've changed the name so I can remmber

the backlight.c is from  **Nicolas Boichat** **"Apple Macbook Pro LCD backlight control"**

see the attachment .. I have compiled the backlight.c also 

chmod +x backlight    (just check if you need it)
sudo ./backlight 120

---

