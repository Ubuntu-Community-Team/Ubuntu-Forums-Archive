---
title: "[SOLVED] My Experiences Upgrading from Fiesty to Gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by rmockler on 2007-10-23
I thought I would share the results of my recent efforts at upgrading two computers at home from Feisty to Gutsy. My first upgrade was on my Compaq desktop.  First, I made sure that all updates had been installed to Feisty, then I booted from the System Rescue CD.  I saved the entire partition to my external drive using partimage, so I could restore in case of any disasters.  I rebooted into Feisty and did the upgrade to Gutsy.  Everything went smoothly, and I was optimistic when I rebooted.  After some testing, I only discovered a couple of minor problems (font rendering and extremely slow web access), but I resolved them quickly after following suggestions I found on our forum.  My network functioned perfectly, and local and remote printing worked great.  Firefox and Epiphany never skipped a beat.  There were some features in Gutsy that I really liked such as the improved VNC interface and CUPS performance,  so I decided to upgrade Feisty to Gutsy on my Toshiba R100 laptop.  I followed the same procedure as with the Compaq by completely updating Feisty, then did a partition backup using partimage on the System Rescue CD.  I rebooted into Feisty and did the upgrade to Gutsy. When I rebooted after completion of the upgrade, I noticed immediately  that the resolution was not  1024x768 as it had been in Feisty.  It looked like it was about 400x300.  My workaround for that was to log off and log back in again, and the resolution was back to 1024x768.  However, when I rebooted, the resolution was bad again.  I worked on this problem for a few days, searched the forums for an answer, but was unable to fix it.  It seemed  pretty poor to have to log off after a fresh boot and log back in again to get the proper screen resolution,  especially in a room full of Windows users, so I decided to go back to Feisty on the laptop and sit this one out for a while.  Fortunately, I had a good backup and it went smoothly, again using partimage on the System Rescue CD.  So, now I have a Compaq desktop running Gusty and a Toshiba laptop running Feisty.  I toyed with the idea of doing a clean install on the laptop, but I figured it probably wouldn't make any difference.  If anyone has any ideas on what may be causing this screen resolution problem on the laptop, I would appreciate a response.  I will gladly provide any specific details you may want.  I didn't provide these details in this post,  the only item that may have value is the video card.  It is a Trident CyberBlade XP4m32.

---

### Post by Dr Small on 2007-10-23
Have you tried ?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Find the screen resolution and see if you can select the screensize you want.

Dr Small

---

### Post by rmockler on 2007-10-24
Thanks Dr Small, I tried that command early in my efforts to get the laptop to boot up at 1024x768.  I set the resolution to the only choice available, which was 1024x768.  After I rebooted and it opened at about 400x300, I did a Ctl-Alt-Backspace and it came back at the proper resolution, and I had a look at the xorg.conf file.  I was surprised to see that only resolution for ALL depths was 1024x768.  Therefore, why doesn't the machine use that at bootup?  Huge mystery to me, I'm just going to continue with Feisty on the laptop for a while and see what develops later.  I appreciate your suggestion, I hardly expected any responses to my post, about the only hope would be if someone else with a Toshiba R100 had happened to solve the problem and passed it along to me.  Another strange thing is that it works just fine in Feisty, boots right up with the display at 1024x768.  
~Richard

---

### Post by RedPillMode on 2007-11-04
Hello, I too have R100 and have the same problem. It seems to me it is a acpi problem. Or what do I know, Booting with "acpi=off" kernel parameter does solve this, anyway, but... then acpi is off. Not nice. So I have not been able to solve this. Will keep you posted if I find something, if it takes too long its time to give Sidux or Zenwalk a try. I am so spoiled.

---

### Post by rmockler on 2007-11-04
Thanks RedPillMode.  I tried your suggestion and booted the R100 with acpi=off and it came up fine.  My understanding is that I have now limited the function of power management for things like suspend and hibernate.  I seldom use those functions, so maybe it's not all bad.  Plus, how do I make that boot parameter permanent so I won't forget to do it?  At least I'm satisfied with running the laptop with Feisty, so maybe I should just leave it alone.

---

### Post by Cool Surfer on 2007-11-04
I am back to fiesty after guty failed to update :(

---

### Post by RedPillMode on 2007-11-05
Well following wrestles with this exact same problem, only with 7.04: 
[http://ubuntuforums.org/showthread.php?t=533793&highlight=r100](http://ubuntuforums.org/showthread.php?t=533793&highlight=r100)

Sadly those instructions seem to do nothing with 7.10. I have used my limited resources :). 

Anyways, there was an interesting thing. You can get good resolution back by switching to virtual console (Ctrl+alt+F1) and then back (Ctrl+alt+F7). I hadn't noticed that. I can live with this, for some time. Until someone better skilled solves this. 

I dont much use sleep/hibernate/resume, but this laptop (at least mine) does not have too good screen, and I seem to need those light up/down buttons. I find acpi=off thingy very restrictive.

---

### Post by RedPillMode on 2007-11-09
I also have openSuse on this laptop, and there seems to be no problem at all. One needs to start TOSHIBA_ACPI, but suse has something called sysconfig editor for that. There were some peculiarities, but everything was easy to fix. Funny thing is, suse uses standard vesa driver instead on trident, and acpi-related things work great. If I remember correctly, i needed to install toshutils package. 

One solution for this  problem could be to use vesa driver. Trident seems not to be any better. I am not sure about this, and I am not going to find out, because ubuntus performance does not make me happy. Suse is much faster. I also tried xubuntu, but that was pretty useless. NOT faster than suse with KDE. If I want XFCE, I will try Zenwalk.

Seems to me, openSuse 10.3 works better than Ubuntu 7.10 on R100.

---

