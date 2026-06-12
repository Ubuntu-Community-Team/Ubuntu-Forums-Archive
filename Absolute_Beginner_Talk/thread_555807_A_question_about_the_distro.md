---
title: "A question about the distro"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by welshboy on 2007-09-20
Hi folks,

Wasn't really sure where to post this so I thought this would be as good a place as any, also this may have all ready been answered elsewhere, if so, the please accept my apologies.

Is there a specific reason why Ndiswrapper is not included in the distro of Ubuntu?  My ethernet ports on my router don't work for some reason, as a result of a serious hard disk failure, I had to re-install Ubuntu on a new drive, and there was no ndiswrapper for my wireless card.  

Or is it possible to download it in windows and install it manually?  If so, any help would be great.

Since the crash, I've been running XP and Vista (on seperate HD's) and was looking to do some linux work going again.

Many thanks

Welshboy

---

### Post by Pumalite on 2007-09-20
Ndiswrapper is proprietary and cannot be included in the Ubuntu disk.

---

### Post by Bothered on 2007-09-20
Direct link to the appropriate repository folder: [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

For Feisty you need:

ndiswrapper-utils-1.9_1.38-1ubuntu1_[architecture].deb
ndiswrapper-common_1.38-1ubuntu1_all.deb 

You can download these in Windows and then install them in ubuntu.

---

### Post by welshboy on 2007-09-20
I trust I use apt-install to install them yeah?? 

Not used Linux for some four months so I'm a bit rust :)

Welshboy

---

### Post by Maestro23 on 2007-09-20
> **welshboy said:**
> I trust I use apt-install to install them yeah?? 

Not used Linux for some four months so I'm a bit rust :)

Welshboy

Those .deb

> sudo dpkg -i package.deb

---

### Post by Bothered on 2007-09-20
> **welshboy said:**
> I trust I use apt-install to install them yeah?? 

If you double click on the files in nautilus it'll launch an installer.

---

### Post by welshboy on 2007-09-20
Thanks chaps, hopefully see you when I get back in to Linux :D

Welshboy

---

