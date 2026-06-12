---
title: "Ubuntu not booting"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-09-27
hello,
i installed ubuntu 6.06 and it ws running well except for the screen resolution so i used some advice from here and did something with the xorg.conf file it generated a file called xorg.conf(succeded by numbers!)so it stopped booting i tried to reinstall it but the setup wouldnt run for the same reason( the screen turns off) i then installed Ubuntu 5 DVD version and the installation went well but still it doesnt boot and gives the black screen again and the resolution is set to 1280x800 because i have a widescreen on my laptop.
and is there any major difference between Ubuntu 5 and 6.06?
again i'm really really new to this...so any help would be really apreciated.
thanks 
Mazen

---

### Post by enopepsoo on 2006-09-27
when it boots you into the terminal type this:
```
cp /etc/X11/xorg.conf_43209812340987123409872134 /etc/X11/xorg.conf
```

where the one with the numbers is the one you mentioned.  It might help to do ls /etc/X11/xorg* first, and/or use tab to autocomplete the filename.

This will restore your old configuration! ;)

---

### Post by Mazen on 2006-09-28
well 10x buddy but the file with #s isnt there anymore since i reinstalled Ubuntu 5...so i don't know what the problem mayb it's the resolution still....is there any way to uninstall linux along with grub?and restart the whole procedure from the very begining because i havea dual boot with WinXP

---

### Post by jordanmthomas on 2006-09-28
If you want to restart, you can boot off the CD and go to System --> Administration --> Gnome Partition Editor
From there, you can delete you Linux partitions and tell Ubuntu to install in the largest free space afterwards.

Also, when you say it doesn't boot do you mean it gets stuck at a terminal / login prompt or that it just...doesn't boot?

---

### Post by ian.l on 2006-09-28
Try re-installing with 6.06 and tell the installer to wipe the linux paritions. Just don't delete your windows partition and grub will configure itself again during installation. You'll still be able to dual boot. If after re-installing Ubuntu still boots to a black screen, try switching to tty3 with CTRL-ALT-F3 and log in with your user name and pass. 

Run the command 'sudo dexconf'
Then type startx and see if it will go to the desktop. If not, try restarting the computer.

If this still fails, from the tty3 prompt type:

sudo vim/etc/X11/xorg.conf

Look for the entries under Screen that look like this:

       EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"

These are the settings for the 16 bit and 24 bit color depth display modes.
To get to a desktop you can erase the higher resolutions (i.e. 1280x1024 and/or 1024x768 ) from these lines and let 800x600 be the highest (remove the quotation marks around each one as well).

If that doesn't work, under 'Device' change the 'driver' entry to 'vesa' for generic drivers. You can always try to install the manufacturer's binaries later or update them with apt-get.

Note to toggle text insert in vim, use the 'i' key. Use the arrow keys to navigate the file. Type ':' to enter a vim command. you'll want to enter 'x' from the : prompt to save and exit. If you want to quit without saving, enter 'q!' from the : prompt.

---

