---
title: "Dual Boot"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by maineman2 on 2007-12-26
Hi I need to install windows xp on my dell 1505n. I want to get one of these robot kits to build with my children and these have windows software. How do i know what kind of graphics card I have? I read the ati card needs to be tweeked to work with windows. I have read how to install ubuntu on a windows machines but how do I install windows on an ubuntu machine? since I bought my computer from dell could I get a good deal on xp from them? thanks Dan

---

### Post by Cypher on 2007-12-26
Install XP on a machine that is already running Ubuntu is only slightly tricky. You'd first have to make space for XP on the HD. So a LiveCD with GParted will help you make that space. Then you'd install XP into that newly created space, but XP is going to blow GRUB away and install it's own boot manager.

You'd then have to use the LiveCD and re-install GRUB and add XP to the boot options.

By default XP will install in just VGA mode on your machine, once fully installed, you can grab the latest ATI drivers for your video card and you will have no problems at all..

To determine what video card you have, you can type "lspci" in your Ubuntu command prompt and look for ATI in the output..

---

### Post by shafin on 2007-12-26
For finding your graphics Card,go to system>administration>Screens And Graphics and see the graphics card section. In windows,normally,your ATI card should work fine once you download and install the needed driver.

To install windows:

1. If you dont have a ubuntu live CD download and burn one.

2. Boot from Live CD

3. run system>administration>GpartED

4.In GpartED,You'll have your Drives listed in a way like this:
Partition ||||||||Filesystem ||||||Size ||||||||||Used |||||||Unused ||||Flags
/dev/sds1 ____ext3 __________71.45gb____7.73gb____63.71gb___boot
~/dev/sda2 __extended ______3.08gb
  /dev/sda5 __linux-swap _____3.08gb
Here the ext3 drive is your linux drive and the linux-swap drive is your swap drive.

5.Select the linux drive, select resize and take out spaces for your vista drive.

6.If you already have a seperate drive for vista,you'll just need to move any data from that to the linux partition.

7.Then boot from xp installation CD,you'll have some unpartitioned space , create and format a drive from the unpartitioned space.

8.After booting,you'll see only xp,but no ubuntu. This is where the burned LiveCD comes in.

9.To fix it,Boot form Linux live CD.mount your primary partition in the terminal type [B]sudo grub-install /dev/hda
[/B] a better guide on this step can be found [here]("http://www.daniweb.com/blogs/entry708.html").Or you can simply re install ubuntu from the Live CD,if you have not customized your installation.If you reinstall,you'll lose all data in your linux drive.

---

