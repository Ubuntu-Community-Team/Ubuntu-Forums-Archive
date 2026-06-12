---
title: "First Install - No GUI"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by nchaleys on 2005-12-04
Took many tries to get a good install, but finally was able to run through entire install with no errors.  Have a dual-boot configuration (XP on primary harddrive, Ubuntu on secondary).  When the boot completes, I'm prompted for my password and username with a commandline interface.  Afterwards, I'm left with a command line that looks like UsernameComputerName:~$

I thought it would boot directly to a GUI and I don't yet know linux commands to get there.  Can't find what I'm looking for with searches; can someone direct me?  Thanks!

---

### Post by Evil Whisper on 2005-12-04
*Deleted*

---

### Post by Turtle.net on 2005-12-04
That's weird...on your first install and no graphic...
What's your video card ?
You may try to tape after the prompt 
```
sudo dpkg-reconfigure xorg-common
```
it will ask for your user password and try to reconfigure the graphic server.
After that try 
```
startx
```
That should launch the graphical interface...

Good luck ;)

---

### Post by nchaleys on 2005-12-04
Didn't seem to work:

When I tried the sudo command, I received some lines telling me that links already exist and it was setting up xserver socket directory - ok

When I tried startx, I received:

x: cannot stat /etc/x11/x no such file or directory, aborting, giving up
xinit: Connection refused
No such process server error.

I'm willing to reinstall, if this is the best path.  Is there some command for a reinstall, or do I just do another full install?

Thanks

---

### Post by astoltz on 2005-12-04
Sounds like it's possible that X didn't even get installed.  What happens when you do ```
sudo apt-get install ubuntu-desktop
```

---

### Post by nchaleys on 2005-12-04
I'm attempting to reinstall ( again ).  I'll report back when it's finished.  Thanks!

---

### Post by corkee on 2005-12-04
Similar problem with no GUI, tried your suggestions, but get message 'dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem.

When I do, I then get requested operation requires a superuser privilege!  Whatever that is?

This is now my fourth attempt at installing Ubuntu and I'm not impressed, it seems most unfriendly so far, but no doubt if I can get it to load properly, I'll be able to see what everone is raving about.

Would appreciate any help

---

### Post by IdolizingStewie on 2005-12-04
[QUOTE=corkee]Similar problem with no GUI, tried your suggestions, but get message 'dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem.

When I do, I then get requested operation requires a superuser privilege!  Whatever that is?

This is now my fourth attempt at installing Ubuntu and I'm not impressed, it seems most unfriendly so far, but no doubt if I can get it to load properly, I'll be able to see what everone is raving about.

Would appreciate any help[/QUOTE]

Superuser privilege means you need to be root to do that because it will make important changes to the computer. This is done by prefacing your command with "sudo". It will ask your password afterwards. The password won't show up on the screen as you type it, but it is registering. That's just a security precaution.

---

### Post by nchaleys on 2005-12-04
I ended up booting with a Win98 floppy, fdisking my slave drive to remove any trace of Ubuntu, then reinstalling.

This time there were zero errors, and it works.

Thanks to all who gave their time to help!

---

### Post by nchaleys on 2005-12-04
I neglected to mention that I also booted to my XP CD and fixed the MBR.  I put everything back to a "clean" state and re-installed.

I was a little shaken by the number of installs I had to try and errors that I'd seen over the past 20 hours, but now that it's running, it seems very nice. 

In retrospect, I was trying to install over a drive that was previously used as an XP boot drive; maybe this was a bad idea.  Unfortunately, the Ubuntu install program leads one to believe that the drive is partitioned and "erased", so I thought I was ok.  I wouldn't do it again unless I was bored and had a day to waste.  Anyone else able to do this WITHOUT all of the problems I incurred?

---

### Post by Terry of Astoria on 2005-12-04
I've installed Ubuntu dozens of times on dozens of machines. Most times it's a breeze. Even Hoary was breezy. Heh. Heh. But I hear you. Anyway, yes. Usually it's really easy. I think I had one once where my installation routine got interrupted somehow and I ended up at the prompt, w/no x. That time I found that someone here had advised that I install ubuntu-desktop so I did and it was fixed. One time I found a computer that wanted to be a real pain. I believe I replaced the video card in that one. No, All I had to do was choose the correct x-server and properly configure my xorg I seem to remember.  Took a while to figger out, but it was worth it. I learned a bunch. One I have right here had a Riva TNT in it, and I switched that out for an ati card, since the regular Nvidia driver doesn't cover TNT's anymore and the nv driver provided no better than 60 Hz headache display refresh rate. I guess I just felt like taking a short cut. Nice thing about desktop computers- they're modular. Replaceable parts!
    Glad you got it to work.

---

### Post by i4ni on 2005-12-06
I had a similar problem to nchaleys. Got an error halfway through the install (the base install phase) and ended up with a command prompt. Followed turtle.net's advice and now have the Ubuntu gui up and running (good advice!). 

One problem remains. When I boot from the Grub menu (I dual boot w/ Win2k), the gui will only load if my ethernet cable is plugged in (I used it, rather than my wireless card, during the install; I don't have a working CD drive, so did it via Windows and over the network). Now, Ubuntu stops loading until the cable is plugged, even though I disable it (in favor of the wireless card) when the gui is up. 

Can I somehow change my setup process to either look for the wireless card instead; or, since it doesn't need an Internet connection during boot up, change it so that it skips this step entirely? 

Thanks all for your advice and assistance.

---

### Post by rivergater on 2005-12-09
I'm newb.  Installing on vmware.  
Few issues- 
I get warnings that not all packages are able to be installed but I skip ahead and proceed until it needs to reboot.  

Then it looks like stuff loads up, i see the ubuntu picture and then it gets to base install. sometimes it never gets past 0%, other times it gets stuck at 48%.  Last night I left it running for hours and then rebooted.  At that point, I was able to get to a login and then to command prompt.  

I just used the apt-get install ubuntu-desktop and it looks like a lot of (good) things are happening.  

I'm waiting for it to finish running but is there anything else I should do afterwards since my base install went awry?  Also, if anyone has ideas about whats going on with my base install, I'd appreciate.

Thanks.

---

