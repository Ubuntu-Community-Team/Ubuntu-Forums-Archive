---
title: "Slow boot time due to removed OSX partition"
date: 2017-02-23
forum: Apple Hardware Users
---

### Post by seninha on 2017-02-23
Here a new Ubuntu user.
Reason for installing ubuntu on my white 2006 iMac (Core Duo) was that lack of bowser support. I was not able to install the latest Firefox.

I managed to install Ubuntu 15.04 on my OSX 10.6.8 using rEFInd.
Everything went well. Ubuntu is now running as single OS on my iMac.

Along the way there where some issues I had to tackle , on of them was no Wifi. That problem is solved.
Next issues I need to give attention to are: 
[LIST]
[*]No iSight cam
[*]BT keyboard connecting using a USB BT dongle, but keys do not work
[/LIST]

But first thing I really wan to solve is booting times.
At this moment when I start up the iMac, i get next image on my screen:

[IMG]http://cdn.onemorething.nl/uploads/community/2dfe27af1fdc276ee3a2379c91838f7235c52b64_0.jpg[/IMG]

This image blinks three times before Ubuntu boots up.

I know that this image appears because there i no OSX partition available. 
Does anybody know how I can make it possible to start Ubuntu right away without system looking for OSX partition?

I already checked my boot folder and there is no EFI folder init.
And as far as I can see rEFInd i no longer available (as it was installed on the OSX partition)

---

### Post by luciano.x on 2017-03-12
> **seninha said:**
> I already checked my boot folder and there is no EFI folder init.

It looks like you installed Ubuntu in BIOS mode. This is known as longer boot times. 
Open terminal and type 
ls /sys/firmware/efi

If "no such file or directory" then you installed Ubuntu in BIOS mode.

---

### Post by Bashing-om on 2017-03-12
seninha; Hello; Welcome to the forum .

I know nothing of Macs .. but the root of the problems here maybe that you have installed an End_Of_Life (15.04 ) release. The software repository no longer exists.
verify the release you have installed:
```

lsb_release -a

```
If it is indeed 15.04 you will have to install a current release ( say 16.04 LTS - Long Term Support )

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-03-12
Welcome. 

> **Bashing-om said:**
> 
If it is indeed 15.04 you will have to install a current release ( say 16.04 LTS - Long Term Support )

^^^
This. Try 16.04 LTS and post back if you have an issue.

PS: Try 

sudo update-grub

... in a terminal and reboot. Aside from that, you won't get much support if you have any issues with such an old (in technology terms) release. 15.04 died over a year ago, hasn't had updates/upgrades since, including security updates so going online probably best avoided. Long gone. :)

On an old machine like that, you've probably gone for such an old release because new ones won't run. Give Xubuntu or Lubuntu a shot. Both of them will give you a better ride and are lighter than Ubuntu. Usually work well on older machines. Good luck.

---

