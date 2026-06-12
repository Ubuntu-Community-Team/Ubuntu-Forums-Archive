---
title: "BSOD/No bootable device"
date: 2011-05-23
forum: Apple Hardware Users
---

### Post by mattakafred on 2011-05-23
^and so much more.

I recently bought a new [750 GB Seagate Momentus]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148599") for my mid 2009 unibody MBP to replace the stock 500 GB HD. Before the upgrade I had been running, with great success, Snow Leopard (SL), Windows 7(W7), and Ubuntu (UB) 10.04. They were triple-booted using 3 partitions and rEFIt to manage startup. This time around I wanted to do essentially the same thing, only with Ubuntu 11.04 and a 4th FAT32 partition to use as universal storage between OSs for things like my iTunes library.

Having done all of this before, I thought it would be really straightforward. I followed the same steps I did last time, using the ["Easiest Triple Boot Ever"]("http://ubuntuforums.org/showthread.php?t=594298") instructions from Ubuntu Forums.

Here are the steps I took:

[LIST=1]
[*]I decided to start completely fresh so I formatted the HD and did a clean SL install. I then installed all of the extra programs from the "Applications Install DVD" that came with my laptop, and I gave everything time to update/reboot/update/reboot etc until the system was where it should be.


[*]Once everything SL related was happy, I used Boot Camp to set up a 200 GB partition for W7. I used the W7 install DVD to format that partition and install the OS normally. From there I updated the system and installed the Boot Camp drivers from the Leopard DVD that came with my laptop, and updated them with the SL DVD. I continued to allow the system to update and reboot until everything ducky.


[*]Once the first two OSs worked, I moved on. I went back to SL, where I used the Disk Utility to partition the Macintosh HD. I reduced SL to 200 GB, gave 300 to the FAT32 partition called STORAGE, and made the remaining 50 GB partition Ubuntu formated HFS+ (OSX can't format ext4, that has to be done through the Ubuntu live CD). At this time I also installed rEFIt and ran the enable.sh command.


When I rebooted, I found that rEFIt was working and could easily boot into either of the currently installed operating systems. This was a good sign.


[*]Next I realized I needed to format the Ubuntu partition, so I tried the Partition Utility on rEFIt. **I believe this was my big mistake**. After doing that booting into anything other than SL was no longer an option (not a worst-case scenario, but not good either). If I held down option during boot, only the OSX partition showed up, Windows was nowhere to be found.

I figured my partitions were still intact somewhere, so I decided what the hell and tried to go on with the Ubuntu install. I created both a CD and a flash drive to install Ubuntu because I had nothing but time on my hands while my laptop updated itself repeatedly for the first two OS. 


[*]I inserted the Ubuntu CD, held down option while booting to load it (my internal CD drive is busted, so I'm using an external one). When the CD loaded I was met with a fairly normal looking install screen for Ubuntu. From there I selected "Install Ubuntu" and was promptly met with a "Non system disk or disk error." Yuck. This was at about 5am. I fiddled with everything trying to get SOMETHING to work, reinstalled rEFIt to try to get it running, etc. No luck. Read somewhere that I should use the OSX install DVD to verify and repair my disk. Sure enough when verifying I received several red error messages and repaired them, though this only sped up the LS load, it did nothing for the other problems. At about 630 am I gave up and went to bed. This afternoon when I woke up I decided to just start fresh since nothing was working the way it was supposed to.


[*]I repeated the first couple steps until I had rEFIt loading W7 and LS with the two extra partitions (for UB and Storage). At this point all is well.


[*]Next step: I put in the UB install flash drive. It hangs with some form of nouveau error. (Nouveau I believe being related to NVIDIA drivers, concerning in my book.)
```
[drm] nouveau 0000:02:00.0: PRAMIN flush timeout
```

I found a post suggesting:
[quote=[keybuk]("http://ubuntuforums.org/showpost.php?p=8996142&postcount=2")]Add "nomodeset" to the kernel command-line.

If you're coming from the installer, press a key at the initial logo, F6 for options, and it's the first one.

If you're on an installed system, hold down shift as the BIOS finishes, press "e" to edit the boot line, cursor down to the line with "quiet splash" etc. and add it to the end of that line - Ctrl-X to boot[/quote]
[/LIST]
I did this and it worked. Ubuntu installer loaded. From there I followed the instructions provided by fossapps.com [here.]("http://www.fossapps.com/how-to-install-ubuntu-11-04/") Here I think I made another mistake. I changed the "Device Boot Loader Installation" to the UB partition. Once the install finished UB asked to reboot, so I let it. It seemed to be going okay, but then UB decided to hang on some sort of a screen telling me it was powering down. After 30 minutes of being stuck on that screen I finally just forced it to power down. 


I turned my system back on to be greeted by the **black screen of death** and a very loud, omnious, beep. I waited 10 minutes, when nothing changed I forced a shutdown, and booted up holding down option. Nothing happened. Blank screen, no beep, but a flashing white sleep-light. Held down power again to kill it, turned it back on again, holding option down. This time I had success!!! A single drive popped up, it was rEFIt to the rescue! It showed OSX, Windows and Linux I loaded SL through rEFIt, and it worked! Naturally, next I decided to push my luck. I powered down and turned it back on, holding down option. Instead of going back to rEFIt, I got that damned loud beep and bsod. I turned it off, and back on, no luck, off, back on, no luck, off, back on, and finally I got back into the rEFIt menu. It appears I have a ~30% chance of getting into there... Once in I attempted Windows. This is where I get "No bootable device" error. Yuck. Next I reboot a few times and try UB. It does absolutely nothing except send me to another blank screen. My final attempt thus far was just before writing this. I managed to get back into rEFIt, told it to boot to OSX, and since I started writing this until I posted it (this took me about an hour to write) OSX was stuck on the grey Apple logo with the spinning wheel.


My next step is to use the SL DVD to reformat the partitions not linked to OSX and repair anything it can. I was hoping there was someone out there with more experience, or different insight, than me that could help me with this problem.

---

