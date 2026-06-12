---
title: "Windows XP and Ubuntu Dual Boot Problems"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by n5bail on 2008-01-09
I've installed Ubuntu with a windows xp install a few months ago. I'm pretty impressed so I used kept using it. Around that time I had a huge problem with XP and decided to just use Ubuntu. Now, I need to do some things on windows so I decided to format the partition with acronis and reinstall windows. Now, I cannot boot ubuntu. Acronis can't find it in the OS search and when acronis was not installed it would only boot windows. I was wondering if there is anything I can do that doesn't require me to reinstall Ubuntu.

---

### Post by john_spiral on 2008-01-09
try re-installing grub.

---

### Post by Ryadt on 2008-01-09
Windows does not really like sharing:mad:...what I would do would be to install windows first then re-install ubuntu...

---

### Post by n5bail on 2008-01-09
I just installed windows. As of now I have no way of getting into Ubuntu so I cannot install reinstall grub. I don't want to reinstall either. When I try to boot my install on the hard drive with the live cd it just runs the live cd.

---

### Post by john_spiral on 2008-01-09
I re-installed grub via the live-cd the other day.

anyone recommend a good howto on the forums?

---

### Post by n5bail on 2008-01-09
I got it working. Thanks. I should have done a little bit more searching around.

---

### Post by john_spiral on 2008-01-10
what thread/howto did you use?

---

### Post by DoctorColossus on 2008-01-12
I actually was having the same issue and reinstalled grub from the live cd using this post
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
the problem is that once i've done that, the grub menu won't give me an option to boot xp, it's just 3 different options to boot ubuntu and that's it.
now, this thread 
[http://ubuntuforums.org/showthread.php?t=659625&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=659625&highlight=dual+boot)
mentions something about adding a windows entry to the grub reinstallation, but i don't know how to do that:confused:
can anyone tell me how to?

---

### Post by dstew on 2008-01-12
You need to add the option to boot XP to the /boot/grub/menu.lst file. You will need to know which partition your XP is on. So first, open a terminal and enter the command **sudo fdisk -l**. This will list your partitions. If Windows is on the first partition, which might have the name hda1, then grub will use the corresponding name (hd0,0)  You then add statements to the menu.lst file to chainload from the (hd0,0) partition.

To edit the file with a graphical text editor, do ```
gksudo gedit /boot/grub/menu.lst
```At the end of the file, after the ### END DEBIAN AUTOMAGIC KERNELS LIST , add these lines:```
title Windows XP
     root        (hd0,0)
     makeactive
     chainloader +1
```Save the file and exit the editor. Then reboot and see if it works.

---

### Post by jivabill on 2008-01-12
I have a similar problem.  I have a nicely running Ubuntu 7.10 all tweaked up to my desires, networked with my Win98SE machine, cool.  I do not want to re install Ubuntu.  Too much work would go down the drain.

But, I do need to have XP running on here also so I can run some Quicken programs.  I can't use VMware.  I would like someone to advise me how to go about installing XP in a dual boot along with the already existing Ubuntu 7.10.

If that is possible of course.
Thanks
Bill

---

### Post by dstew on 2008-01-13
Installing Windows after installing Ubuntu can be done, but you will have problems. First, you need to prepare a partition to install it to, You can use gparted to create a partition. Windows will want to wipe out your Ubuntu installation if it is on the first partition, so you have to make sure to direct windows to the proper place. After windows is installed, it will replace the grub boot loader on the MBR with its own. You will have to re-install grub. Then, you will have to configure grub to boot Windows. This might be tricky, because you will have to use the map statement to fool windows into thinking it is on the first partition, if in fact it is not. [Here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") is a How-To on recovering your Ubuntu system after installing WIndows. It is not trivial.

---

### Post by Aurora@FleetBuzz on 2008-01-13
Bill, do you have a desktop?  If so, you might want to consider a separate HD.

---

### Post by DoctorColossus on 2008-01-13
Thanks dstew!!! 
it worked \\:D/

---

### Post by jivabill on 2008-01-13
Thank you all for your good answers to my problem of needing to install XP alongside an existing Ubuntu.  And Dstew especially, thank you.  I also posed a similar question on another thread yesterday and subsequently found a detailed tutorial for doing this very thing at
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

I think I can follow it alright.  The only problem for me is that if one of the steps were to fail I would be stuck as I am not a Linux Expert by any means.  

All of this just goes to show you, if you are planning on running Dual Boot you should start by installing XP first and then install Ubuntu in Dual Boot.  I wish I had done that in the beginning but I had some hardware problem with this machine that trashed the XP install.  At that point I lost patience and installed Ubuntu which has been running happily every since.  It was even able to fix the problems when the hardware troubles (loose connection on the HD) tried to come back.

And Aurora, thank you for your suggestion the second HD.  Actually at this point that would be the cleanest easiest approach.

I think before I do anything I am going to figure out how to make a complete system backup of my machine.  Then if I screw up I will have a way back.

Again, thanks for the good helpful informations.
bill

---

### Post by Aurora@FleetBuzz on 2008-01-14
Bill, if you decide to go with a separate hard drive, check out this thread.  It helped me enormously and actually made it easy--especially referring to the links contained in the first post.

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

My drives are IDE as I have an old Dell Dimension 8200, but I suspect the directions will work equally well with SATA.

Don't forget to set your windows drive as slave and the ubuntu drive as master!  During install, just select the new hard drive (the master) and let Gutsy do the work.

---

