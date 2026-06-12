---
title: "VGA 815em Installation Problem"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by mayol1 on 2007-10-28
I  have a dell inspiron 2500 which has an intel 815em vga card. But Kubuntu install vesa driver's what should i do to install the intel driver's.I have download intel driver's in rpm format but i can not install them.  thanks in advance

---

### Post by overdrank on 2007-10-28
> **mayol1 said:**
> I  have a dell inspiron 2500 which has an intel 815em vga card. But Kubuntu install vesa driver's what should i do to install the intel driver's.I have download intel driver's in rpm format but i can not install them.  thanks in advance

Hi and welcome, if you are using Feisty 7.04 or Gutsy 7.10 you can use the restricted drivers to install. KMenu &#8594; System Settings, go to the Advanced tab and click Restricted Drivers. Then click the Administrator Mode button and check the box marked Enable to install the driver. This should install the right package for your card and set it up for you.

---

### Post by mayol1 on 2007-10-28
I have done this but nothing a message tells me that my hardware does not need close code drivers

---

### Post by overdrank on 2007-10-28
> **mayol1 said:**
> I have done this but nothing a message tells me that my hardware does not need close code drivers

Ok then you may search in adept package manager for intel and you should find the i810 driver that may help.

---

