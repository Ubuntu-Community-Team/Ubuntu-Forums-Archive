---
title: "Resolution Prob"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2006-12-23
I installed ubuntu and everything is all big. So I go to change the resolution and it only has one size and my Video Card is a ATI VisonTech Radeon 7K

---

### Post by peterj on 2006-12-23
Essentialy you should install the optimum ATI drivers, more info here:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

---

### Post by RED WIND on 2006-12-23
I followed the steps exactly and now I get a message at startup saying it failed to start X server and I need to know how to fix it

---

### Post by peterj on 2006-12-23
Did you use the right drivers there are two on that page?
Is GDM starting up?as in can you see any graphics? if not
this command will reconfigure the old drivers and then you should try again.

```

sudo dpkg-reconfigure xserver-xorg

```
Then you need to troubleshoot why the drivers didn't work.

---

### Post by KenSentMe on 2006-12-23
I think you should have a look at this page: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) . It tells you how to change the resolution when there seems to be one option.

---

