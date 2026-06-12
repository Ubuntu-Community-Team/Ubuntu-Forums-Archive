---
title: "Hooray! And thank you!"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by squiggs on 2007-12-01
Guys I have eventually got Ubuntu installed after tinkering all week. My machine is a Dell Dimension 8300 with SATA drives and an Audigy 2 sound card, and a Radeon 9600 graphics card.

The process.

Dell Bios can be a pain in the ***, you'll need to start from fresh disks (i.e. both blank formatted). I managed to lose my Windows Partition, but I'm prepared to work with it. Turn SATA array off - (second Array). Start Ubuntu installer. 

[Initial problem was a 640x480 graphics problem]("http://ubuntuforums.org/showthread.php?t=625901"). Couldn't see the install button on the installer. So Terminal

sudo dpkg-reconfigure xserver-xorg - use the defaults and it picked up my Radeon 8600. Save, reboot and restart the boot disk


Let it install on HDA (I used 100% of the partition). Due to some weird problem Linux wouldn't install with both Array's installed. Correction it installed ok, but I got an[ Error 2 with Grub]("http://ubuntuforums.org/showthread.php?t=625123"). So anyway, boot up with Array 2 disabled, run the live CD, reboot, Now you will get a Grub Error 15. I reenabled my secondary Array - and BINGO linux boots. 

Now we have a working Ubuntu install. But without Sound. You could try all of that ALSA Mixer stuff, Manage to uninstall your [Ubuntu desktop completely]("http://ubuntuforums.org/showthread.php?t=627906") - have to start all over again, scratch your head then realise that you forgot to plug in the speakers to the sound card....

My next task is to make sure that the second SATA drive is operational. I have yet to decide whether to attempt to get Windows onto the machine or not. I'm assuming that I now have a second disk free ready for action...I'll report how it goes. 

Thanks to everyone who replied to posts and helped me out. For any newbies reading this dont give up ! I had to run the Installer at least 15 - 20 times trying different things, learning all the time before I got things working proper.

Paul.

---

