---
title: "Ubuntu Freezes 10 minutes after reaching Desktop"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by SimonBor on 2006-08-19
Hi - I wonder if anyone can help me. This is my first go at Linux and apart from a weird glitch it has all gone really well. I really want to be able to see if I can make the switch properly from Windows, but at the moment can't get this sorted out.

I've set up a dual boot system between Windows XP Pro and Ubuntu 6.06 using Grub and between two master IDE HDs. Installation was incredibly easy and I managed to sort out mounting hard drives etc. However, once logged in, within 5 to 15 minutes the mouse freezes and I get no keyboard response at all and I have to restart. This obviously is a little annoying and I am not proficient enough with Linux to be able to work much out in those 5 minutes.

Something similar happened with XP when I think I installed a new driver for my Soundblaster Audigy 2 soundcard, but I just reverted to an older driver. Could this be the problem? All help greatly appreciated.

Thanks,

Simon

PS System configuration:
1024mb 3200 RAM
Gigaybyte motherboard GA-8IPE1000
P4 2.53
120gb IDE HD - Windows on one partition
13gb IDE HD - Linux
160gb SATA HD
250gb SATA HD
Ati Radeon 9500 Pro
Soundblaster Audigy 2 with front panel
Bluetooth USB adaptor
Winfast 2000 TV card (not used at the moment)
A CDR drive, DVD-Rom Drive and DVD-R drive (All LG)

---

### Post by encompass on 2006-08-19
It sounds like a problem with your graphics card... the ATI driver can be buggy for some...  Search the forums for that one... but for the time being try this at a terminal...
sudo dpkg-reconfigure xserver-xorg
select everything as the default by just pressing enter  EXCEPT for the graphics driver... select the vesa graphics driver.  Reboot... does that fix your problem?  If so... I can help you search for a good howto if someone else doesn't have one... that can help you step by step to get it running the right way.  Congrats on your switch to linux and I hope that we can help you ghet over this bump in the road.

---

### Post by sailor2001 on 2006-08-19
> **SimonBor said:**
> Hi - I wonder if anyone can help me. This is my first go at Linux and apart from a weird glitch it has all gone really well. I really want to be able to see if I can make the switch properly from Windows, but at the moment can't get this sorted out.

I've set up a dual boot system between Windows XP Pro and Ubuntu 6.06 using Grub and between two master IDE HDs. Installation was incredibly easy and I managed to sort out mounting hard drives etc. However, once logged in, within 5 to 15 minutes the mouse freezes and I get no keyboard response at all and I have to restart. This obviously is a little annoying and I am not proficient enough with Linux to be able to work much out in those 5 minutes.

Something similar happened with XP when I think I installed a new driver for my Soundblaster Audigy 2 soundcard, but I just reverted to an older driver. Could this be the problem? All help greatly appreciated.

Thanks,

Simon

PS System configuration:
1024mb 3200 RAM
Gigaybyte motherboard GA-8IPE1000
P4 2.53
120gb IDE HD - Windows on one partition
13gb IDE HD - Linux
160gb SATA HD
250gb SATA HD
Ati Radeon 9500 Pro
Soundblaster Audigy 2 with front panel
Bluetooth USB adaptor
Winfast 2000 TV card (not used at the moment)
A CDR drive, DVD-Rom Drive and DVD-R drive (All LG)

there are a lot of posts on this forum regard the freeze up as you have..It all has something to do with memory leak...In my case, I found GAIM was causing the memory leak, so I use that program on a different computer as I can't install additional RAM on this computer (E machine). If your mobo can handle additional RAM, that is probably the direction you have to go

---

### Post by SimonBor on 2006-08-19
Encompass

Thanks a lot for the tip - I have made the change and after 20 minutes or so everything seems to be fine. You mentioned that I needed to now properly fix the problem - I have searched the forums with terms like "ATI driver bug fix" and not found anything that goes beyond your suggestion.

Is there something specific I should do next? Will I encounter problems with video for instance without the proper driver?

Many thanks again,

Simon

---

### Post by sailor2001 on 2006-08-19
since there are so many posts on freeze ups and so many different solutions, I wonder if there is a bug in Dapper that stops the swap file from being used...I have 512 mb ram and 1 1/2 gig swap...I didn't have a freeze-up problem in Breezy..  something to think about...

---

