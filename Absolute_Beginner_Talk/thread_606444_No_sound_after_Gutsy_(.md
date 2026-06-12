---
title: "No sound after Gutsy :("
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-11-07
Hi all,

like the title says, I have no sound anymore since I updated to Gutsy. First of all, after putting the title I checked the 5 links that the forum showed me, some people have the same problem as me, but apparently nobody fixed it.

I have a Toshiba A135 s4656 laptop (hda intel sound card) and I recently updated my ubuntu to Gutsy. But my sound stopped working. When I click the icon in the top it says> 
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I tried to reinstall all alsa drivers but it didn`t work (like a how-to hda-intel sound link told me). I "./configure" using version.h file from linux-lastkernelversion-generic. And then I make, and make install (twice actually) but it didn`t work as well.

I put here all that I tried and my computer system to, hopefully, get some help because I don`t want to go back to Feisty. In my last attempts I will try to install a fresh Gutsy and then if no success I will put feisty again.

so please, if anyone could help me I would be really grateful. This problem took me a lot of time to resolve, or may I say to still not resolve.

Thanks,
Bruno

---

### Post by bharris25 on 2007-11-08
You can try this, not sure If it will work but I had some sound problems with my toshiba satellite A105 and adding this line to gedit worked after reboot.

Originally Posted by jekylczar View Post
i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

---

### Post by brunoskrebs on 2007-11-08
Yeah this worked for me as well on Feisty, but not now :(

I think I have no choice, I will have to install a fresh installation of Gutsy, unbelievable. And if does not work, and probably it won`t because it stopped working when I updated to Gutsy, I will have to use my old Feisty...

](*,):cry:

---

### Post by bjstabio on 2007-11-08
I'm not in Ubuntu now so I'm doing this from memory.  I had the same problem.  This worked for me.  Right click on the speaker icon in the upper right hand corner.  There's a tab on the far right of the popup that appears; says switch or something like that.  Click on that.  Uncheck the box that appears.  Like I said, this worked for me.

---

### Post by brunoskrebs on 2007-11-08
Hmmm, I right clicked on the icon but no panel to click, only "open volume control" "preferences" and "mute". If I click the first or the second it gives me an error. The third one, well checked or not my sound is not working :P

So if you login in Ubuntu later, then please see if you remembered well.
Thanks

Bruno

---

### Post by DutyDuty on 2007-11-08
I had a similar  problem, this thread helped: [http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

---

