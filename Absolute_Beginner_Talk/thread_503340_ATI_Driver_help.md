---
title: "ATI Driver help"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by lilbugleboy09 on 2007-07-17
I have an ATI 9250 video card, and I've been trying for weeks to get it set up.

I tried following this guide: [http://www.clipmarks.com/clipmark/28280FB2-D4CE-4204-8F7D-45D3988622CD/]("http://www.clipmarks.com/clipmark/28280FB2-D4CE-4204-8F7D-45D3988622CD/")

After I type in the first code I get an error.
Here's the full code (sorry can't do the code thing)

jd@jd-desktop:~$ sudo chmod 777 ati-driver-installer-8.28.8.run
Password:
jd@jd-desktop:~$ sudo sh ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
jd@jd-desktop:~$  sudo chmod 777 ati-driver-installer-8.28.8.run 
jd@jd-desktop:~$  sudo sh ati-driver-installer-8.28.8.run 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
jd@jd-desktop:~$ bitchass
bash: bitchass: command not found

---

### Post by crispy_420 on 2007-07-17
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by lilbugleboy09 on 2007-07-17
Radeon 9500+
So my 9250 is screwed?

---

### Post by mrlarouc on 2007-07-20
> **crispy_420 said:**
> [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

I am also having trouble installing my 9250 on Ubuntu Feisty Fawn! :( By referring to this link do you mean that the 9250 will not work?

ie it says on that page "The latest fglrx driver supports Radeon 9500+ and the X-series cards up to X1900" in other words not 9250s! is there any other advice?

---

### Post by kittyhawk63 on 2007-07-20
Have you tried going to:

 [http://www.ati.com](http://www.ati.com).

Select at top where it gives "Drivers and Software."
You can try using the fglrx install procedure given there.

---

### Post by SPQQKY on 2007-07-20
I would think, since the 9250 was actually released AFTER the 9500, you should have support. But don't quote me as I have had my own driver nightmare and I have an nVidia card which I understand is easier in Linux. But I am 100% sure the 9250 was released after the 9500. Perhaps the 9250 just doesn't have enough "strength" to run the OS...? which is why the state 9500+

---

### Post by Githlar on 2007-07-22
Haha! I, too, am having problems with my 9250 under Feisty. I tried to run the proprietary installer, but I got a weird error:
./ati-installer.sh: 165: Syntax error: Bad substitution

I simply don't know what's going wrong. Keep in mind that I'm a COMPLETE Linux n00b...

---

### Post by w4ett on 2007-07-22
I'm afraid you are stuck with the open source xorg-driver-ati.   I have a 9200SE (same GPU/RV280 as you)  The ATI driver does not support our cards.

---

