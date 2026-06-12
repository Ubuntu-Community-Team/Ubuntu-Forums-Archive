---
title: "Ubuntu on my Sony Vaio VGN-FE790P"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Deten on 2008-02-23
I know that using a laptop is slightly more complicated than a desktop... so where should I start? 

Heres some questions:

My laptop has a built in camera, how do I get that activated?

Is there a way to find the components detected by UBUNTU which are not supported?


Thanks.

---

### Post by Deten on 2008-02-23
Just to let you know, most features were detected and work great, though my built in microphone does have some issues :(

I was suprised how easily it did work... much easier than my windows install (dont even get me started)

---

### Post by Joeb454 on 2008-02-23
First check in System>Administration>Restricted Drivers Manager

Any closed-source driver (Nvidia etc.) will be listed in there if Ubuntu knows it's there.

---

### Post by Deten on 2008-02-23
> **Joeb454 said:**
> First check in System>Administration>Restricted Drivers Manager

Any closed-source driver (Nvidia etc.) will be listed in there if Ubuntu knows it's there.

Done, it only had my wireless/bluetooth and my nvidia card... still missing a few things.  And my internal camera was not detected there.

---

### Post by warbird on 2008-02-23
my camera for my vgn-fe90ps works perfect, out of the box. did you test it, with something like cheese or whatever?

---

### Post by Deten on 2008-02-23
> **warbird said:**
> my camera for my vgn-fe90ps works perfect, out of the box. did you test it, with something like cheese or whatever?
When I used windows, my camera appeared in the "My Compuer" Folder and I could access it there... where would I go to "find" the camera?  Or what would you suggest I use to test it.

---

### Post by warbird on 2008-02-23
> **Deten said:**
> When I used windows, my camera appeared in the "My Compuer" Folder and I could access it there... where would I go to "find" the camera?  Or what would you suggest I use to test it.

dont quite remember where in /dev/ its located, but an easy way to try it is
sudo aptitude install cheese

---

