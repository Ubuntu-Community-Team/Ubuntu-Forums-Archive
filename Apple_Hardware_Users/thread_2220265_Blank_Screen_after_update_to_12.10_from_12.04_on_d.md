---
title: "Blank Screen after update to 12.10 from 12.04 on dual boot MacbookPro 8,2(Early 2011)"
date: 2014-04-27
forum: Apple Hardware Users
---

### Post by ege2 on 2014-04-27
[FONT=trebuchet ms][COLOR=#333333]I decided to setup Ubuntu on my MacbookPro 8,2(Early 2011, Graphics Cards:Radeon HD 6750M and Intel HD 3000) within a 40gb partition to setup the framework ROS to work on robotics projects(I didn't downloaded yet).[/COLOR]
[COLOR=#333333]
First of all, I downloaded the 12.04 Precise Pangolin on my Macbook pro using dual boot via rEFIt. It worked well, then I saw on [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) that for MacbookPro 8,2's 12.10 or 13.04 is suggested.[/COLOR]
[COLOR=#333333]
So (I still don't know why) I decided to update 12.10 instead of 13.04 via 12.04's system update. After installation was successful, I restarted my computer, pick the tux from rEFIt interface, choose the 'Ubuntu' from GRUB v.2 and then blank purple screen for 3 secs THEN several lines of error manifestations(I think they are not related to Switching Graphic Card problem) THEN ubuntu dot illustrations and then black with backlight AND unresponsive till shutting down.[/COLOR]
[COLOR=#333333]
After several trials and same errors, I've decided to download rEFInd replacing with rEFIt, restarted, picking the tux from interface and the same error again.[/COLOR]
[COLOR=#333333]I tried removing fglrx, though they were not even installed AND I tried switching 'quiet splash' with 'radeon.modeset = 0' in the GRUB v.2 interface and THEN same as usual BUT now no more dot illustrations, only blank screen with a lone dash symbol on upperleft corner.[/COLOR]
[COLOR=#333333]
I'm really confused, thinking downloading the supported 13.04 but don't know how since I have a 12.10, unable to boot on my partition.[/COLOR]
[COLOR=#333333]
Could you help me?[/COLOR][/FONT]

---

### Post by neoanderthal on 2014-05-02
Hi there,
Have you tried disabling your AMD card from the grub boot to see if that is the problem?
edit the grub boot options, and add the following information just below the line that reads 'insmod ext2':
obset 0x728 1
obset 0x710 2
obset 0x740 2
obset 0x750 0

find the line that has your kernel, and on the same line after 'quiet splash' add (on the same line):
i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0

This should get you to the Ubuntu startup screen and login. Let me know what happens.

---

