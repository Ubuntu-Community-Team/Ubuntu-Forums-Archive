---
title: "black screen on log out after new ati driver install"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by ljpm on 2007-02-26
Hi all,

I just installed a new ati driver for my video card

driver:   ati-driver-installer-8.34.8-x86.x86_64

I see the log in screen after a reboot but if I log out the screen goes black and I am forced to hit the reset button.

Video card is ati xpress200 on board.

---

### Post by ljpm on 2007-02-26
Anyone??

Bump

---

### Post by ed-j on 2007-02-26
Caution: Reply from Novice!

Hi !
What version of Linux are you using?

---

### Post by ljpm on 2007-02-26
Using Edgy. 
amd chip but i386 version

Everything was fine before the upgrade.
So far the only problem seems to be screen to black when log off.

---

### Post by ed-j on 2007-02-26
> **ljpm said:**
> Using Edgy. 
amd chip but i386 version

Everything was fine before the upgrade.
So far the only problem seems to be screen to black when log off.

Hi !

Apologies, but, I Don't understand the problem?

---

### Post by krrh on 2007-03-10
I have the same problem after the ATI driver uprade.  I also have a 200m.

Unfortunatly, I have no remedial advice -- only commiseration to offer.

---

### Post by mobio on 2008-03-06
Hi,
If you are using ubuntu try editing file /etc/X11/gdm/gdm.conf. Set the value AlwaysRestartServer=true. 
If you are using kubuntu you might try editing  /etc/kde3/kdm/kdmrc set value TerminateServer=true.

For some people this fix it. For me it did fix this morning, I also had to clean up xorg.conf file from custom code, but sadly this afternoon all of a sudden stopped working again. It is not clear to me why I didn't edit any configuration file. Only thing was that I was connecting my PC to projector and I was also running compiz. Than it stopped working, than started working again (only once) and now is dead again.  

It is strange problem, and since I am not expert in linux I don't know in which log file I should look to figure out where the problem exactly is.

---

