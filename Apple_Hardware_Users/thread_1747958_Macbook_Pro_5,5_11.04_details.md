---
title: "Macbook Pro 5,5 11.04 details"
date: 2011-05-03
forum: Apple Hardware Users
---

### Post by Evasen on 2011-05-03
Good day Ubuntu community! After three or so months ago I upgraded from my awesome four year old white Macbook to this mid-2009 13 inch unibody Macbook Pro model. What forced me to upgrade was that Final Cut Pro 7 required a graphics card with more ram. So I managed to sell my Macbook and make the leap to this model that has a graphics card compatible with Final Cut Pro 7. Along the way I have been running Windows 7 Ultimate Edition (for the Adobe Creative Suite since it runs a lot faster than on Apple's operating system) along with the latest Snow Leopard 10.6.7. Needless to say the inevitable happened and my install was beginning to slow down. After all I have been running the same Snow Leopard install for a year or so now; I all I had to do was boot off of an external drive and copy my operating system image onto the new Macbook Pro when I sold off my previous Macbook. I came to the conclusion that I was using my Apple and Microsoft operating systems for regular tasks that were pretty much unnecessary in order to maintain a clean operating system for video and graphics, and web work. So I came to the conclusion that I will have to try my luck with a triple boot system with Ubuntu, Snow Leopard and Windows 7 so that I may be able to use it for e-mail and media consumption.

    I found this great thread here in this forum: 
          [http://ubuntuforums.org/showthread.php?t=1387861](http://ubuntuforums.org/showthread.php?t=1387861)
It helped ever so much. I don't think I have ever experienced such an easy partitioning scheme. I honestly thought it was bound to be such a headache. I'm glad I was wrong.

    To my surprise things have changed a lot since my Lucid and Maverick days on an old Pentium 4. I am completely amazed by the new look of Unity over Gnome. However I do miss the Compiz Fusion element that really made me enjoy Ubuntu over Snow Leopard and Windows 7. (Well you know, above the whole not having to worry about viruses and mal-ware. :D) So here is my report on what works and what nearly works.

**Model**: Macbook Pro 5,5
**Keyboard**: The keyboard works great, I selected the Apple keyboard and everything is a-ok! Even the keyboard light works!
**Trackpad**: The trackpad works like a charm. The right click with two fingers, scrolling, and holding work better than the Windows 7 drivers in my Bootcamp  Ver. 3.1 Windows 7 drivers.
**Sound**: The sound is a little bit tricky, it doesn't work as well as it should. Granted there is sound, but the problem lies in how faint it is.
**Display**: The display is sharp and bright as ever. The issue that I have found with it is that the brightness setting is not at all adjustable. Which is bearable, but nevertheless a problem. Also I have noticed that when I go the Power Management Preferences in Screensaver and manipulate the brightness setting for the display it only changes the brightness setting for the keyboard lights. So I'm not so sure what is happening there. Maybe the Nvidia drivers are to blame? I thought this so I went to the recommended drivers and the issue was still present.

Other than that it's a delight to use. I'll continue trying out 11.04 and report anything else that might arise.

---

### Post by Silmathoron on 2011-05-03
> **Evasen said:**
> for the Adobe Creative Suite since it runs a lot faster than on Apple's operating system

Very surprising, since it's originally designed to work with apple ^^

> **Evasen said:**
> The issue that I have found with it is that the brightness setting is not at all adjustable...

Did you try the Mactel PPA ? And this help page (may be helpful, though it was written for maverick) ?

[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)
[https://help.ubuntu.com/community/MacBookPro5-5/Maverick](https://help.ubuntu.com/community/MacBookPro5-5/Maverick)

---

### Post by Evasen on 2011-05-04
> **Silmathoron said:**
> Very surprising, since it's originally designed to work with apple ^^



Did you try the Mactel PPA ? And this help page (may be helpful, though it was written for maverick) ?

[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)
[https://help.ubuntu.com/community/MacBookPro5-5/Maverick](https://help.ubuntu.com/community/MacBookPro5-5/Maverick)

Yeah tell me about it, I think that Windows reads Nvidia graphics cards more efficiently. However it might be more stable in Snow Leopard, considering that it is a more stable operating system.

Thank you for linking me to the Maverick Macbook Pro 5,5 details page it really did help a lot. I cannot believe I managed to overlook that small detail. I ended up installing the GNOME ALSA Mixer and I checked the surround sound box and voila! Sound problem solved.

The inability to manipulate the brightness of my display still persists. However I hope there will be a way around it soon. The keyboard keys do not work even though it shows on the screen that it is lessing or increasing brightness. I have already added the MACTEL PPA and updated so let's see where that takes me.

On another note, I have found a new problem. It turns out that the display does not return from sleep after I either close the laptop or allow it to go into sleep from it being inactive. Have you had any experience with this issue?

Right now I am going to try to install Rosetta Stone, that way I may be able to continue my language learning. I really don't want to boot into Snow Leopard or Windows 7 for this. Wish me luck.

---

### Post by Silmathoron on 2011-05-04
Good luck with Rosetta

By the way, this thread may help you deal with your sleep problems... [http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928)

---

### Post by Arrqh on 2011-05-04
> **Evasen said:**
> The inability to manipulate the brightness of my display still persists. However I hope there will be a way around it soon. The keyboard keys do not work even though it shows on the screen that it is lessing or increasing brightness. I have already added the MACTEL PPA and updated so let's see where that takes me.

I did a clean install of 11.04 on my Macbook Pro 5,5 last night and I had the same problem with display brightness. I installed the nvidia-bl-dkms package like the documentation page for 10.10 said and now I have full control over the brightness.

---

### Post by Evasen on 2011-05-11
Sorry for the wait on my updated results. I ended up installing a daily build of a 64-bit version of Natty Narwhal made specifically for Macs. It can be found here:

[http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-amd64+mac.iso)

Which ended up working out pretty great! I'm even running the free experimental 3D support driver for NVIDIA cards, and it works really, really well (For some reason I was not able to get two monitors working with NVIDIA's version 173 and current drivers. I have no idea why, but it's okay). I was not able to use Unity with my dual monitor set-up so I find myself going into Classic Mode whenever I am in need of two monitors. Other than that Unity works fine most of the time. I had my first crash today but I have a feeling it was a video I was checking out on YouTube. You know how Flash rocks it on any operating system, for shame.

The sound worked out of the box with this version of 11.04 and did the display brightness levels as well as the keyboard lights (I was super stoked about that!).

What did not work out of the box was the Airport Extreme wireless card or the iSight (Which I will soon figure out as soon as I have time!). For the wireless to work all you have to do is install the Broadcom STA wireless driver in the Additional Drivers panel.

Apart from this I have been having a pretty good experience thus far. I managed to get Rosetta Stone to work under an XP VirtualBox machine I made originally to run Final Draft (I had no problems using the on-board microphone as well!).

---

### Post by Jaxilian on 2011-05-11
I have a Macbook pro 5,5 and wants to know how to make a clean install with 11.04 (meaning no OSX). From what I understand there is a lot of work needed to be done with partitioning n' stuff.

Any have a good post on that?

---

### Post by Evasen on 2011-05-11
> **flodis said:**
> I have a Macbook pro 5,5 and wants to know how to make a clean install with 11.04 (meaning no OSX). From what I understand there is a lot of work needed to be done with partitioning n' stuff.

Any have a good post on that?

Are you you planning to dual boot? Or solely run 11.04 on your machine? If so I would just slide the 11.04 install CD and just do an erase install.

---

### Post by tmette on 2011-05-14
> **flodis said:**
> I have a Macbook pro 5,5 and wants to know how to make a clean install with 11.04 (meaning no OSX). From what I understand there is a lot of work needed to be done with partitioning n' stuff.

Any have a good post on that?

Just go ahead and run the installer.  It will ask you if you want to do complete erase of OSX.  I just did this and am typing right now from 11.04.  There are a few minor issues with it so far.

Everything pretty much worked right out of the box once I switched over to the Broadcom drivers.  Then I switched to the recommended Nvidia drivers which killed the ability to adjust the brightness controls.  I've tried a couple suggestions on fixing it but still haven't got it to work.  Also, the sound was a little low so I just ran Alsamixer and had to turn up the front speaker..it was only set at like 40-50.

I'm pretty impressed on how well it's running.  I also installed the Mactel PPA and that got the trackpad working fairly decently.  The weird thing is in OSX, if I wanted to move a window around I would be able to click and hold with one finger, and use another finger to move the window around.  With the Mactel PPA drivers, it's actually easier because all you have to do is a 3 finger drag and it will move the selected window.  :)

---

