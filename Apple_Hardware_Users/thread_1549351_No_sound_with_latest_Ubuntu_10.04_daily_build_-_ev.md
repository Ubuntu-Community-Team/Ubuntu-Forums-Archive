---
title: "No sound with latest Ubuntu 10.04 daily build - even after editing alsa-base.conf"
date: 2010-08-09
forum: Apple Hardware Users
---

### Post by bastones on 2010-08-09
Hi,

I've downloaded the latest daily build Ubuntu 10.04 ISO today and I added the following to the bottom of the alsa-base.conf file:

options snd-hda-intel model=mbp55

According to this user's post just a few days back ([http://ubuntuforums.org/showpost.php?p=9682392&postcount=156](http://ubuntuforums.org/showpost.php?p=9682392&postcount=156)) state there has been a kernel header update that has made sound break again, and still, the same alsa-base.conf line is still there as usual, so I'm posting whether someone can help me (and others, when it comes round to them updating their system which will break their sound) get sound working.

Thanks!

(I have MacBook Pro 7,1)

**EDIT: Nevermind. It was just me not configuring gnome-alsamixer correctly. I did a clean install of Ubuntu 10.04 with the daily build I downloaded yesterday, installed the 2 updates that were available (just incase it was anything sound related), then I installed and activated the proprietary WiFi and NVIDIA graphics driver via Hardware Drivers. Then I followed the instructions [on this MacBook Pro 7,1 Community Page](https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Sound) as others have (which states the following):**

[list]
[*]Execute *gksudo gedit /etc/modprobe.d/alsa-base.conf* via Terminal
[*]Add the following to the **end of the file**: *options snd-hda-intel model=mbp55*
[*]Then, execute: *sudo apt-get install gnome-alsamixer*.
[*]Then execute *gnome-alsamixer* via Terminal to bring up the GNOME ALSA Mixer. I made sure every option (master, Headphone, PCM, Front Sp, Surround, Capture was on at full volume (it's actually the reverse - make sure the volume icons are at the top - I initially dragged the volume icons downwards so they went orange but that actually is for quieter volume/mute). Once you've done this, ensure the 'Front Sp' mute checkbox is unchecked. Close the window and restart. You'll hear the startup Ubuntu sound as your computer logs in. All works for me fine! :)
[*]By the way, when you restart it won't complete the restarting process - it'll freeze as it's about to restart. On the Community Page I linked to there's a fix for that, type: [u]sudo gedit /etc/default/grub[/i] and find the line: *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"* and add *reboot=pci* to the end so it's like this: *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"*. Then execute *sudo update-grub* then restart Ubuntu twice (as documented in the Community Page).
[*]By the way: The first time I rebooted Ubuntu sound didn't work. I clicked "Restart" and it just went into the login window. I had to force shut down with the power button. Turned it back on and sound worked fine. I restarted again and same thing occurred. I did the same hard shut down and started again, sound worked fine. Then I restarted and sound worked fine this time. Basically I just continue the process until sound finally worked on a restart. That's when the sound fix has done its job. I think it was two proper restarts until it worked :).
[/list]

---

### Post by rchille on 2010-08-09
Hey there, I think I'm having the same issue. Anyone out there have a fix?

I do note that alsamixer only shows 2 columns (PCM and S/PDIF) whe before I had several columns

Thanks in advance.

---

### Post by bastones on 2010-08-10
Anyone have any ideas on how to get sound working again?

---

