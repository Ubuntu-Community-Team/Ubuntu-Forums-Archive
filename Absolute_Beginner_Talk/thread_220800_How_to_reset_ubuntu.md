---
title: "How to reset ubuntu"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by goodfren on 2006-07-22
My system is slightly unstable due to downloading / removing / install wrong file.

1. currently, sometimes can boot sometimes cannot and need to off power plug then on again to works.

2. Always not able to remember my adsl login password.

I need advice on how to reinstall but keep existing inportant setup and data save uneffected by reinstalling process or any way to remove unseen file inside ubuntu, 

i believed when i remove program using sypnatic package are not totally remove all file and folder of the program remove like firewall and guarddog but i do not know to clean the remaining.

thks

---

### Post by Jussi Kukkonen on 2006-07-22
Goodfren, more information would help here... E.g. What did you download/install/remove?

> **goodfren said:**
> 
1. currently, sometimes can boot sometimes cannot and need to off power plug then on again to works.

Again, details of what happens would help us help you... Actual error messages, info on where the booting fails, etc.

> I need advice on how to reinstall but keep existing inportant setup and data save uneffected by reinstalling process or any way to remove unseen file inside ubuntu, 


Not 100% what you mean, but here's some info for you, hope it helps:
[LIST]
[*]reinstalling the whole operating system is usually not needed. Still, if you decide to do that, your data will be safe *as long as it's on another partition than Ubuntu*
[*]removing applications so that nothing (like configuration files) are left on your machine is possible but, as you semed to suspect, is not the default action: right-click on a package in Synaptic and select *Mark for complete removal*
[/LIST]
Again, knowing what you want to remove would help...

---

### Post by goodfren on 2006-07-22
I don really remember what software i download for some as I even cannot find it's installed program folder as i don no where the system keep the program, i think the file from tar.gz (something like this) and it cannot appears in the system but shown already installed. This software are normally from the net and not from sypnatic package area.

About rebooting, there are no error message, it is at on / off system area, it will not boot, then i unplug and plug back to on, then it works. Is like the drive and processor not connected but after the above mention it works. Most of the time, it succeed at second time.

About firestarter, i did install using terminal following the net guide then again install from sypnatic package as i see non functional at first attempt,  after that i remove and install guarddog (did not know is for KDE platform) again cannot find the software after install to do the setup, then i remove it, 

now i install using terminal for iptable firewall as recommend by someone in this forum. Everything goes smoothly but one instalation error as the system cannot detect the file i create for iptable firewall, that file is for init.d script, so now i cannot set script executable for init.d/firewall

If i mark complete removal, will the whole thing gone and unseen in the sypnatic package? Because I do not know if i will need it in future. If it is still exist in the sypnatic package area, then i would like to try it as i don want to google it out in the net when i needed in the future.

Thks

---

### Post by Jussi Kukkonen on 2006-07-23
Yes, you can reinstall software after a "complete removal" -- they'll still be visible in Synaptic.

If you have installed software by compiling from source (as it seems since you mentioned .tar.gz format), it won't automatically appear in synaptic -- you'll have to read the INSTALL or README files of that software to find out how to uninstall it.

---

### Post by goodfren on 2006-07-24
> **Jussi Kukkonen said:**
> Yes, you can reinstall software after a "complete removal" -- they'll still be visible in Synaptic.

If you have installed software by compiling from source (as it seems since you mentioned .tar.gz format), it won't automatically appear in synaptic -- you'll have to read the INSTALL or README files of that software to find out how to uninstall it.
Thks for your time to guide me.

One thing, where do this file tar.gz is normally place in our computer? Where is the archived manager? I think i normally extract into archived manager but cannot find the archived manager.

---

### Post by aysiu on 2006-07-24
Two links you may be interested in:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by goodfren on 2006-07-24
> **aysiu said:**
> Two links you may be interested in:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)
Thks for the link, it is quite useful to read. Will go through it.

---

