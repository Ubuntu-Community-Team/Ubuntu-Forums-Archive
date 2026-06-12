---
title: "Can Ubuntu be uninstalled?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Eugene Carvalho on 2006-10-04
Just installed Ubuntu and I have two hard drives.  Windows is on one drive and I wanted to install Ubunto on the other drive.    When I did that the drive that Windows is on now wants to start Ubuntu, even though its not installed on that drive.    I would like to uninstall unbuntu so it is removed from its present partition and it's presence on the Windows drive MBR is also removed.  I don't see an "uninstall" anywhere.](*,)

---

### Post by tronica on 2006-10-04
well theres no "uninstall". in order to get rid of it you just format the drive. as for the mbr i'm not sure. theres a command to remove i think.

---

### Post by Old Pink on 2006-10-04
Simply run your live CD, open the partition editor, delete the Ubuntu partition, click shut down.

Replace your live CD with your XP disk, reboot, wait until the XP disc takes you to recovery console then type```
fixmbr
fixboot
```

Remove XP disk and reboot. You're back to just windows. :( (Sorry I had to provide that information)

---

### Post by tonyr1988 on 2006-10-04
If you have the slightest urge to reconsider, you could try this:

I'm assuming the WinXP hard drive is your master (hda) drive. My knowledge about booting is really limited, but if it's the master drive, it'll look towards that MBR to boot. On the other hand, I'm sure Ubuntu only threw GRUB into the MBR of your second hard drive.

If you want (it won't take long, and it shouldn't have any damaging effects at all to anything), open your computer and switch your hard drives. Make the master the slave and vice versa. You should be able to just switch the cords and change the pin-things (I completely forgot what those are called . . . anyone have a tutorial to show how to do that?)

I dual-boot off of two hard drives just like you, and that's my set up. Afterwards, when you boot up, you should get a choice between Ubuntu and WinXP.

If you decide you don't like it (or if it doesn't work correctly), just put everythink back the way it was and do what Matt said.

EDIT: Oops - I read the original post wrong. I was getting my MBRs mixed up. :)

---

### Post by Drakkor on 2006-10-04
Or, you could change the boot/grub/menu.list to make XP the default and Ubuntu the second choice. I also dual boot with Ubuntu/XP on different drives,no problems,you should be presented with options from the gurb boot menu when it boots,though the default setup is to boot to Ubuntu.

---

### Post by Eugene Carvalho on 2006-10-04
When the Boot process starts I get a screen (GNU GRUB) that gives me choices of Ubuntu Kernel, Ubuntu recovery mode, Windows, etc.    and instructions that say use Up key, Down key to select entry, then 'e" to edit before booting.   If I select 'e'  I have choices "Root (hd0,0), savedefault, makeactive, chainloader +1.   What do these choices offer?  Can I use these to select which OS boots preferentially?

What I want to do is be able to select which drive (in the BIOS) boots and have Windows on one drive and Ubuntu on the other, but dont know how to get there from here.:-?

---

### Post by confused57 on 2006-10-04
Here's how to change the default OS grub boots into:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

I believe Ubuntu installed grub onto your Windows drive mbr, if you want to uninstall Ubuntu(restore Windows mbr):

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Here's a guide for installing Ubuntu onto a 2nd hard drive without installing grub to the Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

To use bios to select which drive (OS) you want to boot, you'd need to install grub to the Ubuntu drive mbr...you'd need to use the alternate cd(where you can select where to install grub) or use the live cd(automatically installs grub to the mbr of Windows), but you'd probably need to disconnect the Windows drive before installing.  You'd also need to restore the Windows mbr.

You can use the live cd to install grub on an already installed Ubuntu, without having to reinstall Ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
This is the better choice for installing grub to the Ubuntu drive.

Hope this helps...

---

### Post by Eugene Carvalho on 2006-10-05
Thanks  - this is  very helpful.

---

### Post by deadw8 on 2008-07-22
my friend (moved away) installed Ubuntu for me, praising its worth and ive always been fascinated by Linux. 
Anyhow, there are some errors in my feisty fawn and paradoxically im not able to go online because of these errors to download an automatic update which would fix them. 
So i want to uninstall and use XP to write my scripts. I have an XP cd rom but thats all. No floppy and dont want to burn any CDs. is there a while, all i know how to do is press ESC before the GRUB (???) counts down. I dont even know if anyone can help someone as hopeless as me...

---

