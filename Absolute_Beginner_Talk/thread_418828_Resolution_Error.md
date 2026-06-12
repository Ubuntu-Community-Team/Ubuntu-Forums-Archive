---
title: "Resolution Error"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by yad39 on 2007-04-22
Have had Ubuntu 6.06 now for 2 weeks

On occasion this fault would occur, but after re-booting it would clear

The fault now appears at every boot-up and won't clear

The fault in question is my screen resolution is set at 640 * 480 at 60hz

When going to screen resolution preference's there is no option to change up

Can anyone help....

---

### Post by heimo on 2007-04-22
Start here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by bobplano on 2007-04-22
change your xorg.conf by

```
sudo dpkg-reconfigure xserver-xorg
```
then answer the questions to the best of your knowledge

or manual 
```
sudo gedit /etc/X11/xorg.conf
```
look for your bitdepth and add your resolution

---

### Post by yad39 on 2007-04-23
After a couple attempts of answering config question's, all is good.

I have my 1280*1024 res back.

Thanks for your help.

---

