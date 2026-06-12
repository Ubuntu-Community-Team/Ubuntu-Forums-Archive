---
title: "NTFS Drive"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by flubmasterq on 2007-04-01
How do I copy Windows files to an NTFS drive?
I don't know how to access the drive, how do I get to it? 
I'm using Windows XP x64.

---

### Post by bruenig on 2007-04-01
NTFS is not able to be written to natively by linux. You can use drivers such as ntfs-3g to do it which is available in the repositories. Also you need to specify a bit more, are you able to mount the drive and just not write to it or can you not mount to it at all?

---

### Post by land0 on 2007-04-01
Just some clarification...
You are booted int Ubuntu and you want to copy some files onto a NTFS drive or partition?

---

### Post by flubmasterq on 2007-04-01
Right now I'm just trying to find the drive.
I don't know where it is.

---

### Post by flubmasterq on 2007-04-01
> **land0 said:**
> Just some clarification...
You are booted int Ubuntu and you want to copy some files onto a NTFS drive or partition?

I'm running a dual-boot and I want to copy some of my Windows files to Ubuntu, and I was told I need to copy it through the NTFS drive, and I don't know where that is.

---

### Post by land0 on 2007-04-01
Well in short you will not be able to find or access the Linux drive/partition while in M$. M$ will never ever support this ever! Just one more lock in ploy that you can thank M$ for ;) You will however be able to access the M$ partition from Linux then copy the data over to Linux. The M$ drive should appear in the top left menu under Places. You should be able to copy the information you need by default. If you would like to save files on the M$ side then you need to install a helper app for that. You can use Synaptic to install ntfs-3 like bruenig suggested. 
Or while in Ubuntu go to [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) click on the version that matches your Ubuntu version number. When the save dialog pops up choose Open with GDebi. Once Automatix is installed go to **Applications-->System Tools-->Automatix** once you provide your password and it starts up. Go to **Miscellaneous** and check the top entry **Automatix read/write NTFS and FAT32 mounter.** Then click the apply button.

---

### Post by bruenig on 2007-04-01
Automatix is kind of a stupid solution imo but whatever. While in windows, if you use the driver from
fs-driver.org you can save files to the ubuntu partition.

Do
```
sudo fdisk -l
```
to figure out what the name of your windows ntfs partition is.

---

### Post by compiledkernel on 2007-04-01
Automatix is unsupported software by the community. These forums do not support it either. 

If you are not aware of what automatix is -- "automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu."

I would invite you to read -- 

[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)
[https://wiki.ubuntu.com/WriteSupportForNTFS](https://wiki.ubuntu.com/WriteSupportForNTFS)
[http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

These links should provide you with adequate knowledge on getting NTFS drive to communicate properly. Be warned that NTFS writing may cause damage to your NTFS partition, so just be careful.

---

### Post by land0 on 2007-04-01
Wow sorry to have offered such a controversial/stupid solution. Automatix has always just worked for me. I'll take your word for it though, and I apologize I will never suggest it on this forum again. :)

---

### Post by flubmasterq on 2007-04-01
> **land0 said:**
> Well in short you will not be able to find or access the Linux drive/partition while in M$. M$ will never ever support this ever! Just one more lock in ploy that you can thank M$ for ;) You will however be able to access the M$ partition from Linux then copy the data over to Linux. The M$ drive should appear in the top left menu under Places. You should be able to copy the information you need by default. If you would like to save files on the M$ side then you need to install a helper app for that. You can use Synaptic to install ntfs-3 like bruenig suggested. 
Or while in Ubuntu go to [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation) click on the version that matches your Ubuntu version number. When the save dialog pops up choose Open with GDebi. Once Automatix is installed go to **Applications-->System Tools-->Automatix** once you provide your password and it starts up. Go to **Miscellaneous** and check the top entry **Automatix read/write NTFS and FAT32 mounter.** Then click the apply button.

Are the Windows files supposed to be under Network Servers?
'Cause that's the only one under Places I can find that has to do with Windows, and I can't log onto the Windows Server because it's asking for a password and mine isn't working.

---

### Post by Dual Cortex on 2007-04-01
> **compiledkernel said:**
> Automatix is unsupported software by the community. These forums do not support it either. 

If you are not aware of what automatix is -- "automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu."

I would invite you to read -- 

[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)
[https://wiki.ubuntu.com/WriteSupportForNTFS](https://wiki.ubuntu.com/WriteSupportForNTFS)
[http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

These links should provide you with adequate knowledge on getting NTFS drive to communicate properly. Be warned that NTFS writing may cause damage to your NTFS partition, so just be careful.

:lolflag: it almost seems like CK searches the forums every minute for 'automatix' and if he sees it he copies and pastes that.
... but I also don't really recommend Automatix since you learn a great deal by doing such tasks manually.

---

### Post by flubmasterq on 2007-04-01
Also, when I try the NTFS read/write program installion through Automatix, I get an error that says "An apt-based error occurred and installation was unsuccessful."

---

### Post by Perfect Storm on 2007-04-01
> **Dual Cortex said:**
> :lolflag: it almost seems like CK searches the forums every minute for 'automatix' and if he sees it he copies and pastes that.
... but I also don't really recommend Automatix since you learn a great deal by doing such tasks manually.

Well, also with the upcomming Feisty, Automatix will become obsolite in the sense that it's much more easier with Feisty.

---

### Post by land0 on 2007-04-01
So the files you need are on a remote windows server/workstation? Not a partition on the hard drive of the ubuntu system? If that is the case you need to install Samba. Once that is setup and configured you should be able to browse the files by going to Places-->Network Servers in the top menu. When the "Network-File Browser" opens up there will be an icon named Windows Network. Clicking on that should provide you the access you need. Samba is outside the scope of my experience so if you run into problems you will need to search the forum for Samba solutions. Good luck. Please post back here if you are successful.

---

### Post by land0 on 2007-04-01
> **flubmasterq said:**
> Also, when I try the NTFS read/write program installion through Automatix, I get an error that says "An apt-based error occurred and installation was unsuccessful."

FYI: there are solutions for that issue in the Auto****x forum. You may want to go there to resolve this. I would post a link but I do not wish to anger the Ubuntu Forum gods. ;P ;)

---

### Post by flubmasterq on 2007-04-01
> **land0 said:**
> So the files you need are on a remote windows server/workstation? Not a partition on the hard drive of the ubuntu system? If that is the case you need to install Samba. Once that is setup and configured you should be able to browse the files by going to Places-->Network Servers in the top menu. When the "Network-File Browser" opens up there will be an icon named Windows Network. Clicking on that should provide you the access you need. Samba is outside the scope of my experience so if you run into problems you will need to search the forum for Samba solutions. Good luck. Please post back here if you are successful.

I can't find any versions of Samba for Ubuntu, but I think I'm doing this wrong.
Can you find me a link?

---

### Post by Dual Cortex on 2007-04-01
> **land0 said:**
>  Auto****x 

:lolflag: :lolflag:

---

### Post by flubmasterq on 2007-04-01
Now it's not even loading the servers page...

---

### Post by richbarna on 2007-04-01
> **Dual Cortex said:**
> :lolflag: it almost seems like CK searches the forums every minute for 'automatix' and if he sees it he copies and pastes that.
... but I also don't really recommend Automatix since you learn a great deal by doing such tasks manually.

Lol! A few of us have noticed that too ;)

---

### Post by flubmasterq on 2007-04-01
Kay, I'm into the network, but when I go onto my computer part it says "Sorry, couldn't display all the contents of "Windows Network: quality-d6sppy8"."
And it doesn't display anything.

---

### Post by KiwiNZ on 2007-04-01
Automatix is an independant project to assist users install additional applications. Like any independent project there will be risks with its use.
 
Many users have used it with out issue. Others have used it and had problems. That  is something that occurs and is not only restricted to Automatix , any software can cause issues.
 
If you want to use Automatix I strongly suggest you read the Automatix Support forum that the creator has established. 
If you have any issues with it you should also refer to that support forum , that is where the expertise is .
 
After all it is your PC , you are free to use on it what you wish , that is one of joys of Open Source , freedom.
 
Ubuntu Forums does not provide support for Automatix.

---

### Post by flubmasterq on 2007-04-01
I'm going to post this again for the sake of it not getting lost on the last post on that page.

"Kay, I'm into the network, but when I go onto my computer part it says "Sorry, couldn't display all the contents of "Windows Network: quality-d6sppy8"."
And it doesn't display anything."

---

### Post by DirtDawg on 2007-04-01
Flub, it is very unclear exactly what you are trying to do, but you may have been led down a wrong path. I'm reading the situation as you are on a machine with both Windows and Ubuntu on it and you want to take some files from the Windows side and copy them onto the Ubuntu side. BUT you don't know where to find access to the Windows side. Is this correct? 

If what I just described is what you're trying to do, then you probably need to simply open nautilus (under Places>Computer, then click FileSystem) and look in either /mnt or /media for something called hda or hda1. Once you enter that folder, you will see all the familiar folders you are used to in Windows. Sorry I can't remember the names by default. When I installed Ubuntu, I named the folder I refer to now as, "windows", to avoid confusion. 

Windows formatting is called NTFS and Linux formatting is called ext3. Linux can read NTFS but cannot write to it and Windows cannot read or write ext3, but they can share a format called FAT32. I don't think you need to worry about any of this, though, if you're just trying to get files from the Windows drive.

Of course if the scenario I described above is not correct, and what you're trying to do is actually as complex as it seems to have become, then disregard this message. 

Good luck.

---

### Post by flubmasterq on 2007-04-02
> **DirtDawg said:**
> Flub, it is very unclear exactly what you are trying to do, but you may have been led down a wrong path. I'm reading the situation as you are on a machine with both Windows and Ubuntu on it and you want to take some files from the Windows side and copy them onto the Ubuntu side. BUT you don't know where to find access to the Windows side. Is this correct? 

If what I just described is what you're trying to do, then you probably need to simply open nautilus (under Places>Computer, then click FileSystem) and look in either /mnt or /media for something called hda or hda1. Once you enter that folder, you will see all the familiar folders you are used to in Windows. Sorry I can't remember the names by default. When I installed Ubuntu, I named the folder I refer to now as, "windows", to avoid confusion. 

Windows formatting is called NTFS and Linux formatting is called ext3. Linux can read NTFS but cannot write to it and Windows cannot read or write ext3, but they can share a format called FAT32. I don't think you need to worry about any of this, though, if you're just trying to get files from the Windows drive.

Of course if the scenario I described above is not correct, and what you're trying to do is actually as complex as it seems to have become, then disregard this message. 

Good luck.

That's EXACTLY what I needed.
Thanks so much!

---

### Post by flubmasterq on 2007-04-02
Okay, nevermind.
Now when I go to /media or /mnt, /mnt is empty and /media has the folders cdrom, cdrom0, floppy, and floppy0.  And all those folders are empty.
So I can't find it.
Help?

---

### Post by flubmasterq on 2007-04-02
...And now I found /hda in /dev, but when I click on it to access it, it says "Cannot open /dev/hda:  No application is known for this kind of file."

---

### Post by flubmasterq on 2007-04-02
I'm trying to mount the hda drive, but Terminal keeps asking for a password, and when I put in my profile password, it says it's wrong.

---

### Post by DirtDawg on 2007-04-02
Okay, sorry I'm a little rusty on this business. There's a section detailing what you're trying to do in the unofficial user guide [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only") (the link should take you directly to the relevent chapter, but it may take several moments to load). I think it should be what you're looking for.

EDIT: Just below the link i sent you is another section detailing how to mount your Windows partition on boot up, if you're interested.

---

### Post by flubmasterq on 2007-04-02
Thanks.
But that still doesn't tell me why Terminal isn't letting me do anything.
It asks for a password after everything I put in, and every password I have doesn't work.

---

### Post by DirtDawg on 2007-04-03
> **flubmasterq said:**
> Thanks.
But that still doesn't tell me why Terminal isn't letting me do anything.
It asks for a password after everything I put in, and every password I have doesn't work.

[EDIT] Before you start doing all the business mentioned below, perhaps you'd better make sure your password is totally ineffective. For example, can you use aptitude?
```
 sudo aptitude update 
``` In other words, if your password works with other commands, then the problem is with the mount command, I imagine, and not the password itself. I just don't want you to go through the rigamaroll if you dont have to.
[/EDIT]

You're having password issues now? How did that happen?

Oh well. Though **I've never done it**, a quick search with keywords "forgot password" reveals a trick.
Reboot your computer, and when you get to the GRUB screen(where you choose what OS to use), choose Recovery Mode. Once in recovery mode, enter the command:
```
 passwd flubmasterq 
``` Of, course, this is assuming your username is "flubmasterq". Just replace that with whatever your user name is. Apparently, (**again, ive never had to do this**), you will be asked a question or two and/or asked for a new password. Then enter 
```
 reboot 
``` This should give you a new password with which you should be able to use sudo again. Hopefully, this fixes the issue and I'm not just helping make things worse ;)

---

### Post by flubmasterq on 2007-04-03
Kay, thanks for all the help, but now I have more problems.
It won't let me type in the password.
Like, I got to the part where it asks for a new password, and it won't let me type anything in.

---

### Post by DirtDawg on 2007-04-04
> **flubmasterq said:**
> Kay, thanks for all the help, but now I have more problems.
It won't let me type in the password.
Like, I got to the part where it asks for a new password, and it won't let me type anything in.

Well, first I would suggest that maybe when you're asked to type in a new password, it's very possible that what you type in will not show up on the screen as a security precaution, but that it is actually there. After you hit the Return key, you may be asked to confirm the password. Like I said, I've never lost my password so I have no idea what to expect when resetting it.

However, if the problem is not that simple, and you don't find any solutions by searching through this forum, then the way I see it you have 2 options:

1) Post another thread explaining *exactly * what the problem is and maybe you will get a response and, after a little (or a lot) of tweaking, you will get the issue fixed. Or:

2) Accept that somewhere, somehow, you screwed something up that's more trouble than it's worth and reinstall Ubuntu entirely.

I've borked my installation more than once, especially when I first started, and you would be hard pressed to find someone in this forum who has not. If this is the path you decide to take, I encourage you to take your time. Work slowly and carefully. The last thing you want is to wipe your Windows partition because you're rushing through things. 

And if you use these forums for help in the future, I would strongly recommend not necessarily using the first solution you find/are given. Sometimes, people get a little *too* eager to help and can make things worse. This is especially true when getting any advice that requires use of the "sudo" command.

Good Luck

---

