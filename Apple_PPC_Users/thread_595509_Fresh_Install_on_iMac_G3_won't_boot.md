---
title: "Fresh Install on iMac G3 won't boot"
date: 2007-10-28
forum: Apple PPC Users
---

### Post by siriusfox on 2007-10-28
I've been running Ubuntu all the way back to Dapper Drake on x86 machines with no problems. Recently I began considering turning an old Rev A iMac G3 into a general machine just to have out in the front room. Running Mac OS 9 wasn't really a practical OS for this type of thing, so I turned to Linux.

I've looked about at things like Debian, YDL, and Slackware, but in the end none of them would boot after an install with no errors. Every time I try to install ANY linux distro on the machine, all of the data goes on the hard drive no errors, but then the system won't startup. I get the Open Firmware blinking question mark!

There are a few things I'm wondering. Could anyone who has an iMac G3 running Linux type printenv in the open firmware (Boot up while holding O+P+Cmd+Option), or could anyone get me a listing of the partitions on their hard drive (from mac-disk or pdisk). I'd like to start by eliminating the possibility that the problem lies within those two areas.

ANYONE who has this information, your help would me very much appreciated.
-Siriusfox

---

### Post by pxwpxw on 2007-10-29
[B]siriusfox
[/B]
You should also be able to get some clues from Open firmware or by using the rescue mode and mac-fdisk from the install cd, but the alternate install CD is best for this.
Open firmware 3 should let you do this for example:
```

0> devalias
0> ls
0> dev hd pwd
0> dir hd:,\
0> dir hd:2,\
0> boot hd:,\\:tbxi
0> boot hd:2,yaboot

```
But note that Open Firmware  will only open Apple partitions (hfs,hfs+) such as macosx and the yaboot bootstrap. 
You can also run nvsetenv from the rescue disk I think. 

You might be able to use the rescue disk to mount your installed system and run it
```
 
chroot /target /bin/bash 

```
As I dont have an imac g3 to check it out, I cant be sure what will work.

---

### Post by siriusfox on 2007-11-02
No luck. I get an error about not being able to open the device whenever I try those commands.

---

### Post by humble.life on 2007-12-03
i've got the same problem on my Ibook g3 and various hardware issues on the PC.

not impressed...

---

### Post by humble.life on 2007-12-03
As for the G3, wait for it to drop to console (or tap/hold down escape to try and force it) then try

modprobe ide_core
exit


you will need to do this each and every time you start ubuntu.

also, you will probably have gnome-applets crashing on each successful boot,,,,  and quite possible no sound too....

---

### Post by GrayWizardLinux on 2007-12-05
i installed ubuntu about 5 months back on a flat panel original pumpkin iMac.... it 3workede no issues for ubuntu but the mac mouse with the ctlr click woulod not work.   sound worked and adjusted. no wireless and no playback of various stuff due to codec issues but it started everytime..  I reinstalled panther on it so I can't help other that.

---

### Post by jtappin on 2007-12-11
> **humble.life said:**
> As for the G3, wait for it to drop to console (or tap/hold down escape to try and force it) then try

modprobe ide_core
exit


you will need to do this each and every time you start ubuntu.



You can make it permanent by building a new initramfs:
1) add the line ide_core to /etc/initramfs-tool/modules
2) run "sudo update-initramfs"
3) reboot and (with a bit of luck) you'll be in business again 

The change to  /etc/initramfs-tool/modules will work for any new kernel packages (including custom builds using make-kpkg) until you remove the line.

---

### Post by humble.life on 2007-12-12
> **jtappin said:**
> You can make it permanent by building a new initramfs:
1) add the line ide_core to /etc/initramfs-tool/modules
2) run "sudo update-initramfs"
3) reboot and (with a bit of luck) you'll be in business again 

The change to  /etc/initramfs-tool/modules will work for any new kernel packages (including custom builds using make-kpkg) until you remove the line.

i tried this on my G3 but still the same issue i'm afraid, i've ditched ubuntu and put panther back on there.

sorry.

---

