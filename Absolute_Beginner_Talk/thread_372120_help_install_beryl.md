---
title: "help install beryl"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-02-27
I have now tried to inst beryl at least 6 times and end up with the same result. (CRASH & RELOAD)
i would very much like to see it run on on my AMD Athlon  3200+ computer with  geforce fx 5700le graphics card any help and guidance would be greatly appreicated

---

### Post by Quillz on 2007-02-27
Do you have the most recent nVidia drivers installed? Did you install either XGL or AIGLX, and reflect these changes in /etc/X11/xorg.conf?

---

### Post by fongs on 2007-02-27
> **Quillz said:**
> Do you have the most recent nVidia drivers installed? Did you install either XGL or AIGLX, and reflect these changes in /etc/X11/xorg.conf?

no but how do i do this. thanks for quick reponse

---

### Post by Maestro23 on 2007-02-27
Are you flying blind or following any of these guides?
[http://www.ubuntuforums.org/showthread.php?t=272104](http://www.ubuntuforums.org/showthread.php?t=272104)

---

### Post by igknighted on 2007-02-27
[http://www.ubuntuforums.org/showthread.php?t=349732](http://www.ubuntuforums.org/showthread.php?t=349732)

---

### Post by fongs on 2007-02-27
> **Maestro23 said:**
> Are you flying blind or following any of these guides?
[http://www.ubuntuforums.org/showthread.php?t=272104](http://www.ubuntuforums.org/showthread.php?t=272104)

thanks for the links Maestro But which one would you recommend for my set up and should i update nvdia driver on xp  as i'm running Ubuntu 6.10 0n vmware workstation

---

### Post by igknighted on 2007-02-27
> **fongs said:**
> thanks for the links Maestro But which one would you recommend for my set up and should i update nvdia driver on xp  as i'm running Ubuntu 6.10 0n vmware workstation

VMware doesn't support 3d... I don't think it is possible to run beryl.

---

### Post by Maestro23 on 2007-02-27
> **fongs said:**
> thanks for the links Maestro But which one would you recommend for my set up and should i update nvdia driver on xp  as i'm running Ubuntu 6.10 0n vmware workstation

I have not and will not mess with Beryl until its final release.:guitar:   Reason being at the link the other person posted.  Some have success, other's have hosed their systems. Take your pick on the guides.  As for your driver, you need the linux driver for your card while you are in Ubuntu.

Have you used the Evny script to install your driver or did you follow a  How-To?

Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

Good luck.

---

### Post by fongs on 2007-02-27
> **Maestro23 said:**
> I have not and will not mess with Beryl until its final release.:guitar:   Reason being at the link the other person posted.  Some have success, other's have hosed their systems. Take your pick on the guides.  As for your driver, you need the linux driver for your card while you are in Ubuntu.

Have you used the Evny script to install your driver or did you follow a  How-To?

Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

Good luck.

i tried lunapark  and it starts : then i get ERROR Nvidia card not found.

---

### Post by Quillz on 2007-02-27
> **Maestro23 said:**
> I have not and will not mess with Beryl until its final release.:guitar:   Reason being at the link the other person posted.  Some have success, other's have hosed their systems. Take your pick on the guides.  As for your driver, you need the linux driver for your card while you are in Ubuntu.

Have you used the Evny script to install your driver or did you follow a  How-To?

Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

Good luck.
Beryl is just now reaching 0.2. It's going to be a while before the 1.0 release.

---

### Post by Maestro23 on 2007-02-27
> **Quillz said:**
> Beryl is just now reaching 0.2. It's going to be a while before the 1.0 release.

I know.  That's why I'm not even worried about it.:)   Just hate seeing the new people come in and see the pretty eye-candy and hose their systems before they even know how to install anything.

---

### Post by fongs on 2007-02-27
> **Maestro23 said:**
> I know.  That's why I'm not even worried about it.:)   Just hate seeing the new people come in and see the pretty eye-candy and hose their systems before they even know how to install anything.

I've managed to clone a copy of ubuntu  6.10 in vmware workstation that i can sacrifice in order to install beryl on this. is there anywhere else to install nvidia drivers. Thanks

---

### Post by fongs on 2007-02-27
> **Maestro23 said:**
> I know.  That's why I'm not even worried about it.:)   Just hate seeing the new people come in and see the pretty eye-candy and hose their systems before they even know how to install anything.

So in summmary i would like to ask is it possible to install Beryl on Ubuntu on vmware workstation on xp

---

### Post by igknighted on 2007-02-27
No.  VMware creates "virtual hardware" that the VM runs on.  Even tho your physical box has an nvidia card, the VM does not.  You cannot get 3d on the vmware "virtual" vid card, ergo, no beryl.

---

### Post by kittyhawk63 on 2007-02-27
Fongs,
I would wait for the official release like Maestro23 suggested. Accorging to the web pages I've been reading on Beryl, there are just too many unresolved issues at this time. Many of them will be worked out by 1.0. I would wait. In my opinion, and especially from what I've been reading on this forum and on other web sites, Dapper is the choice today if you want Ubuntu. Very stable. Well supported. Lots of great packages. Lots of support. A great Linux version to learn on. Right Maestro23? :)
KH

---

### Post by fongs on 2007-02-27
> **igknighted said:**
> No.  VMware creates "virtual hardware" that the VM runs on.  Even tho your physical box has an nvidia card, the VM does not.  You cannot get 3d on the vmware "virtual" vid card, ergo, no beryl.

is there anthing that can do this as i need to have xp for autodesk

---

