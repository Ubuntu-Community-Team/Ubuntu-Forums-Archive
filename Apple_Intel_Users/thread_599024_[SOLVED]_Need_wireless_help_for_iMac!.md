---
title: "[SOLVED] Need wireless help for iMac!"
date: 2007-10-31
forum: Apple Intel Users
---

### Post by God of the Meeps on 2007-10-31
Hi, I also downloaded Ubuntu Feisty Fawn (7.04) on my iMac a few days ago. (So I'm a total newbie!)  It's the second newest desktop that Apple has released. The wireless networks don't show up when I check the network settings. Any help would be appreciated! :)

---

### Post by cyberdork33 on 2007-11-01
> **God of the Meeps said:**
> Hi, I also downloaded Ubuntu Feisty Fawn (7.04) on my iMac a few days ago. (So I'm a total newbie!)  It's the second newest desktop that Apple has released. The wireless networks don't show up when I check the network settings. Any help would be appreciated! :)

1. Should be using Gutsy (newest version)

2. Broadcom does not produce linux drivers. Try ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by God of the Meeps on 2007-11-01
If I download Gutsy, will my files be deleted?

---

### Post by cyberdork33 on 2007-11-01
> **God of the Meeps said:**
> If I download Gutsy, will my files be deleted?

you can upgrade. In fact, it should offer to do an upgrade. 

You do not have to upgrade though. Ndiswrapper will work on feisty.

---

### Post by Levo75 on 2007-11-02
Does anyone know if i can get this working on my 17" iMac with a built in broadcom BCM4328 wireless network adapter? I've tried several toturails and it still isn't working.

---

### Post by cyberdork33 on 2007-11-02
> **Levo75 said:**
> Does anyone know if i can get this working on my 17" iMac with a built in broadcom BCM4328 wireless network adapter? I've tried several toturails and it still isn't working.

Will work with ndiswrapper. Same card I have in mine.

---

### Post by Scimu on 2007-11-03
I thought it was hard that ndiswrapper as I was a newbie at the time.. So I just upgraded to gutsy, enabled the broadcom restricted driver, downloaded this other file what I selected to get it off the internet, then it worked perfect. I reccomend upgrading if you dont know how to do that ndiswrapper stuff.

---

### Post by cyberdork33 on 2007-11-03
> **Scimu said:**
> I thought it was hard that ndiswrapper as I was a newbie at the time.. So I just upgraded to gutsy, enabled the broadcom restricted driver, downloaded this other file what I selected to get it off the internet, then it worked perfect. I reccomend upgrading if you dont know how to do that ndiswrapper stuff.

There is no 802.11n support in bcm43xx, but it will work. Too flaky for me still.

---

### Post by tashmooclam on 2007-11-03
The Broadcom wireless works with mac and windows, but very poorly in Ubuntu 7.1 in my experience. 
I used synaptic to get "bcm43xx-fwcutter" and the restricted drivers manager to get my wireless working. I also changed from the default Network manager to  Wicd ="wicked",
My wireless was very sporadic, speeds went from 0kbs to 347kbs, and everything in between.
My solution is replacing the Broadcom wireless card with an Intel card, which is an upgrade, costs $24, and Intel has drivers for linux.
The Broadcom solutions are all work-arounds. 
I would not put Ubuntu Linux in a perfectly functioning mac.

---

### Post by God of the Meeps on 2007-11-03
Cyberdork33:
Thanks for the help! I see that you are running OSX as well as Gutsy... so that means you have dual-boot exp... right? I want to run OSX (10.4) as well, because my ipod shuffle seems not to be able to work on Feisty. Could you give me a link to a useful thread?

---

### Post by God of the Meeps on 2007-11-03
I tried Ndiswrapper, but it only shows directions for Windows...

---

### Post by cyberdork33 on 2007-11-04
> **God of the Meeps said:**
> I tried Ndiswrapper, but it only shows directions for Windows...
I think you are confused on what ndiswrapper does. It is a linux module (or driver) that "wraps" around a windows driver for your device. This makes it possible to use Wi-Fi cards from companies that release Windows Drivers but do not support linux. (Like broadcom). So you are using a windows driver, but you install it in linux. If what you are using works, no need to change.

There is really no tutorial needed anymore. The most difficult part is resizing your OSX partition to make room for Ubuntu. Just use bootcamp (the beta will work if you set your clock back ;) ), or resize [via the commandline]("http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes"), or even use the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"). After you do that, you just install to that empty partition. and installing [rEFIt]("http://refit.sourceforge.net/") may be useful.

---

### Post by God of the Meeps on 2007-11-04
Ah... I see. I think I'll just use safari (with dual boot) to use wireless. Thanks for all your help!

---

