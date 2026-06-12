---
title: "Desktop effects could not be enabled"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by sinterklaars on 2007-11-20
Hi

I m pretty new to ubuntu (this is actualy my first post), but after I bought my notebook I was getting pretty sick of Vista in a couple of weeks so I started on Ubuntu Gutsy. After 2 moths of mostly using Vista, but triing to get Ubuntu up and ready I think I might just complete switch one of these days. But  I still want some more fancy desktop stuff so I can show to all of my friends that this is also possible on Linux. But I always get the same error while using advanced desctop settings, and even the standard normal or extra visual effects give these errors ... can anyone help?

---

### Post by Inxsible on 2007-11-20
Have you installed the restricted drivers for your video card?

---

### Post by sinterklaars on 2007-11-20
nope, really I m seriously new ... any manuals or tips?

---

### Post by Inxsible on 2007-11-20
> **sinterklaars said:**
> nope, really I m seriously new ... any manuals or tips?System>>Administration>>Restricted Driver Manager.

Enable the video card drivers. and then reboot. Since you have an ATI card, you may also have to install xgl, but thats for later.

---

### Post by sinterklaars on 2007-11-20
thanks, but still having some problems: new error: The Composite extension is not available, is this because of the xgl? But actually I normally installed that one because of tips in other posts ...

---

### Post by Inxsible on 2007-11-20
> **sinterklaars said:**
> thanks, but still having some problems: new error: The Composite extension is not available, is this because of the xgl? But actually I normally installed that one because of tips in other posts ...
try this one more time```
sudo aptitude install xserver-xgl
```the other thing to check would be whether or not your card is blacklisted. I do not remember the name of the file ( I am currently on a windows machine @ work ) But  a search thru the forums should get you the name.

---

### Post by sinterklaars on 2007-11-20
really thanks worked as a charm

---

### Post by Inxsible on 2007-11-20
> **sinterklaars said:**
> really thanks worked as a charm
you are quite welcome :)

also mark your thread as solved. Thread Tools>>Mark Thread As Solved.

---

### Post by thevictor390 on 2007-11-20
Wow, same problem, same graphics card... worked for me too.  Gutsy is turning out the be a HUGE improvement over Fiesty.

---

