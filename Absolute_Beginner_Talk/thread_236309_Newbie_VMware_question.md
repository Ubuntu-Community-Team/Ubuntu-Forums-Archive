---
title: "Newbie VMware question"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Aggienator on 2006-08-14
Is VMware what I need? 

I have a dual boot (Ubuntu/winXP) system. The reasons it is dual boot are:

Quicken 98 - 8 years worth of accounts that I can't seem to transfer sensibly to either KMyMoney or GnuCash.

Forte Agent - 8 years worth of emails

Canon Canoscan3200F Scanner that won't work with linux.

If I install VMware will I be able to use any (all) of these without rebooting the system? Will it run the apps already installed on my windows partition, or will I need to reinstall? Does VMware run just like another program on the desktop, eg can I alt-tab between an app running in VMware and another app running in ubuntu?

Does the fact I can't answer these questions myself after reading the website mean I'm out of my depth!

Thanks Aggie

---

### Post by siacs on 2006-08-14
The answer to the last question is yes ;) you need to read up a little. but you're on the right track, keep going. You can also use Xen.

Some links to help you on your way

[http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)

[http://en.wikipedia.org/wiki/VMware](http://en.wikipedia.org/wiki/VMware)

[http://en.wikipedia.org/wiki/Xen](http://en.wikipedia.org/wiki/Xen)

---

### Post by siacs on 2006-08-14
Then when you are all read up and ready to go

[HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://www.ubuntuforums.org/showthread.php?t=183209")

---

### Post by Aggienator on 2006-08-14
Thanks siacs, I've got my homework now:D

---

### Post by djsroknrol on 2006-08-14
> **Aggienator said:**
> Is VMware what I need? 

I have a dual boot (Ubuntu/winXP) system. The reasons it is dual boot are:

Quicken 98 - 8 years worth of accounts that I can't seem to transfer sensibly to either KMyMoney or GnuCash.

Forte Agent - 8 years worth of emails

Canon Canoscan3200F Scanner that won't work with linux.

If I install VMware will I be able to use any (all) of these without rebooting the system? Will it run the apps already installed on my windows partition, or will I need to reinstall? Does VMware run just like another program on the desktop, eg can I alt-tab between an app running in VMware and another app running in ubuntu?

Does the fact I can't answer these questions myself after reading the website mean I'm out of my depth!

Thanks Aggie

I've found that with my VMware server install, if the hardware doesn't work in Ubuntu (i.e. serial port, LPT1, etc), it won't work in VMware, as the hardware is dependant on Linux to function at all...

Just something to keep in mind. I mention this because you talk of needing the scanner...

---

### Post by shoot2kill on 2006-08-14
yes, just use windows as your main OS, with vmware installed on it, then run ubuntu on the VM...

note, i have used VM and disguarded it straight away, performance iss not too good.... unless u got a great PC

---

### Post by rbmorse on 2006-08-14
> **djsroknrol said:**
> I've found that with my VMware server install, if the hardware doesn't work in Ubuntu (i.e. serial port, LPT1, etc), it won't work in VMware, as the hardware is dependant on Linux to function at all...

Just something to keep in mind. I mention this because you talk of needing the scanner...

Well, it depends. I have an HP 4570c scanner. Uses USB inteface and is detected by Kubuntu, but there is no Linux software driver support for this particular scanner. In this case, I can use VMware to set up a Win2K VM that runs on top of Linux, install the Windows HP driver software into the Win2K VM and everything works fine. 

Now clearly, if the host machine does not even detect the hardware there is no way the VM can use it.

---

### Post by djsroknrol on 2006-08-14
> **rbmorse said:**
> Well, it depends. I have an HP 4570c scanner. Uses USB inteface and is detected by Kubuntu, but there is no Linux software driver support for this particular scanner. In this case, I can use VMware to set up a Win2K VM that runs on top of Linux, install the Windows HP driver software into the Win2K VM and everything works fine. 

Now clearly, if the host machine does not even detect the hardware there is no way the VM can use it.

Not really...if there **is** USB support, then you can load the drivers in VMware and it should be good to go...

---

### Post by JerMe on 2006-08-15
> **djsroknrol said:**
> Not really...if there **is** USB support, then you can load the drivers in VMware and it should be good to go...

Wouldn't that mean that iTunes could be run under a virtualized Windows XP?  I haven't read much in this regard, so I'm a bit skeptical about this.

---

