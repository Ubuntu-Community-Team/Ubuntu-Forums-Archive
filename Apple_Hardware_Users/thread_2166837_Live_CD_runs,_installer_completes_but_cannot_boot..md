---
title: "Live CD runs, installer completes but cannot boot. G5"
date: 2013-08-11
forum: Apple Hardware Users
---

### Post by pauljwells-m on 2013-08-11
I can boot the Lubuntu liveCD following these instructions [http://ubuntuforums.org/showthread.php?t=2141774&p=12632814#post12632814](http://ubuntuforums.org/showthread.php?t=2141774&p=12632814#post12632814) and I get to the desktop ok. Everything works. I can run the installer and it completes without errors. The problem comes when I try to reboot the machine and run from the HD: I get the stage1 yaboot menu, type 'l' for Linux and the screen flashes briefly and then drops back to the stage1 menu. Then it says 'starting stage2 boot' and stops. After a few seconds the fans fire up and I have to hard shutdown.

I've tried a 'vanilla' install, I've tried adding the extras in the 'modules' files to fix the video and running ybin, both from the liveCD and from a chroot into the hard disk. Always the same result.

10.04 installed faultlessly and boots. I can't install anything from 11.10 to 12.10 because the early 3.x kernels had a bug specific to the G5 dual core, which I have.

I'm stumped now. :-(

Update: Tried this: booted to openfirmware, got to yaboot prompt giving the options Linux, old. Now booting gives of/path/to/boot/vmlinux: Unknown or corrupt filesystem.
Update2: I found on a Gentoo thread that it might be because of installing onto second HD (sdb). So, backing up all my files and preparing to nuke OSX finally...

---

### Post by pauljwells-m on 2013-08-12
Sorted it, so I'll record everything here in case it helps others.

 Installing on the second hard disk didn't work (couldn't get yaboot to boot it) so install on the first disk (sda). I wiped OSX completely.

 Start with Lubuntu 13.04 live cd, boot with options:

```
live video=offb:off nouveau.modeset=0 single
```

 Wait until the white open firmware screen appears and then 60 seconds after the cd drive stops whirring type:

```
modprobe nvidiafb mode_option=1440x900-32 
```(use your own monitor resolution and colour depth)

 You should then get a single user black shell, if you don't you'll have to reboot and try a different wait time than 60 seconds.

 In the shell type: ```
start lightdm
```

This will get you to the Lubuntu desktop!

 Open a terminal and sudo gparted to erase all the partitions on sda except the first one, (which is a partition map I think)

 Run the installer using 'erase disk and install'

 Once it's finished drop back to the single user shell (ctrl-option-cmd-f1)

 First chroot into the hard disk file system

 ```
# mkdir /mnt/hd
 # mount /dev/sda3 /mnt/hd
 # mount --bind /dev /mnt/hd/dev
 # mount --bind /proc /mnt/hd/proc
 # mount --bind /sys /mnt/hd/sys
 # chroot /mnt/hd

```
 Then make the necessary mods to the boot files as follows, since you're in a root shell you don't need sudo:

 ```
nano /etc/modules
```

 add this to the file

 ```
nvidiafb mode_option=1440x900-32
```

 (ctrl-o to save, ctrl-x to exit)

 then ```
nano /etc/initramfs-tools/modules
```

 again add:

 ```
nvidiafb mode_option=1440x900-32
```

 nano /etc/yaboot.conf

 edit the lines starting with 'append' to read:

```
 append="nosplash video=offb:off nouveau.modeset=0"
```

 Then ```
ybin -v -C /etc/yaboot.conf
```

 You should see output including the line about penguin pee (yes, really)

 then reboot:

 ```
shutdown -r now
```

 You may have to hold in the power button to fully shut down.

 It should now boot into Lubuntu!

 If your sound doesn't work, edit /etc/modprobe.d/blacklist.local.conf to comment out (add a # at the beginning) all the lines that have a 'snd' in them. (on my system it was all the lines) and reboot. You can also install kubuntu with sudo apt-get install kubuntu-desktop.

 Sweet. A few more years use out of a nice old machine!

---

### Post by Boab1993 on 2013-08-12
Very nice job sir, remember to mark your thread as solved so others can see your page for referencing nd fixing their problems.

---

### Post by jared_marshall on 2013-08-15
I got a message saying theyaboot conf file doeswnt exist and when I did the reboot it thru me into a error about firmware

---

### Post by jared_marshall on 2013-08-15
Nvm I love u tnx so much

---

### Post by pauljwells-m on 2013-08-15
Either you entered the command wrongly or your installation went badly wrong! If you didn't do the ybin step properly then the system will be unbootable, that's clear.
What you need to do is fire up the live CD again. You probably don't need to reinstall, just go back to the part about chroot immediately after the install and repeat those steps. Check the typing in every file you edit because any error will screw it all up. As a tip, do you know that you can start to type the first few letters of a filename in any of these commands and press the Tab key - the shell will automatically fill in the letters for you if it can guess what you want. Saves a lot of typing and errors.

Good luck, you're nearly there! I know how difficult it can seem.

---

### Post by frank18 on 2013-10-17
> **pauljwells-m said:**
> Either you entered the command wrongly or your installation went badly wrong! If you didn't do the ybin step properly then the system will be unbootable, that's clear.
What you need to do is fire up the live CD again. You probably don't need to reinstall, just go back to the part about chroot immediately after the install and repeat those steps. Check the typing in every file you edit because any error will screw it all up. As a tip, do you know that you can start to type the first few letters of a filename in any of these commands and press the Tab key - the shell will automatically fill in the letters for you if it can guess what you want. Saves a lot of typing and errors.

Good luck, you're nearly there! I know how difficult it can seem.

Thanks Paul; i'm trying to install Lubuntu on PPC G5 with ATI card  and i hung at log in and password,
if i have to do what you did,what are the codes for ATI card thanks.apreciate.

---

