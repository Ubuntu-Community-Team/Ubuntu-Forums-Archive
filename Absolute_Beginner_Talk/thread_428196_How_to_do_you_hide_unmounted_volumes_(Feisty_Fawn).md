---
title: "How to do you hide unmounted volumes? (Feisty Fawn)"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by JavaIsRobust on 2007-04-30
This question may be a little weird, but bear with me.

I have a quad boot system.  XP + Vista + Ubuntu 7.04 + Ubuntu 7.04.

When I installed the second Ubuntu, it automatically mounted the first three OS's.  I don't want any users being able to mess with these partitions so I need them unaccessible.  I went into fstab and commented them all out.  Well, that unmounted them on each reboot which is good.  The problem is under Places>Computer, the three partitions still show up and if double clicked, they are automatically mounted.

How can I stop these from showing up under 'computer'?  I don't want users to even know they exist.  Is this a new feature in Feisty because I don't remember having this problem in Edgy.  I might be wrong, but in Edgy, if a partition isn't mounted, it doesn't show up as an unmounted icon under 'computer'.


[PHP]~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2613    20988891    c  W95 FAT32 (LBA)
/dev/sda2            2614        5226    20988922+   7  HPFS/NTFS
/dev/sda3            5227        7839    20988922+  83  Linux
/dev/sda4            7840       24321   132391665    f  W95 Ext'd (LBA)
/dev/sda5            7840        7872      265041   82  Linux swap / Solaris
/dev/sda6            7873       13870    48178903+  83  Linux
/dev/sda7           13871       24321    83947626    6  FAT16
[/PHP]

[PHP]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ae315f6a-a55b-4e38-94d1-aa8a332822e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=1439-AB5B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=14E66426E66409F6 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
#UUID=2e774e70-8e30-419f-820f-e32bed70cc0a /media/sda3     ext3    defaults        0       2
#UUID=036f231f-dd92-42cb-b81f-78d092ce9099 /               ext3    defaults        0       2
# /dev/sda5
UUID=19128d76-9745-16a7-c7c1-591e8cdccf13 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
[/PHP]

---

### Post by dfreer on 2007-04-30
hmmm. try changing the mount points from /media/xxxx to /mnt/xxxx in /etc/fstab, and then rebooting.

---

### Post by JavaIsRobust on 2007-04-30
I commented those lines out so I can't see how they would be the problem.  I'll try it though.

---

### Post by JavaIsRobust on 2007-04-30
That just mounted them somewhere else like I thought.  What I want is for them to not show up at all.

---

### Post by JavaIsRobust on 2007-04-30
bump.. anyone?

---

### Post by mikewhatever on 2007-04-30
I suppose one way of doing it would be to back up the present fstab and then delete the lines you've commented out.

---

### Post by JavaIsRobust on 2007-04-30
I tried and still the same as before.  I can't see how deleteding commented lines out would do anything anyways.

---

### Post by uyguy on 2007-04-30
I have the same problem. I have an NTFS partition for the Windows virtual memory, which i don't want to be shown. I have it unmounted, but it is still showed as unmounted. Any ideas?

---

### Post by JavaIsRobust on 2007-04-30
> **uyguy said:**
> I have the same problem. I have an NTFS partition for the Windows virtual memory, which i don't want to be shown. I have it unmounted, but it is still showed as unmounted. Any ideas?

I'm glad somebody understands my problem.  The only idea I have is you can right click on it and try move to trash and then have it deleted.  I'm just afraid to mess something up.  Plus, there should be a more correct way to do what we want to do.

---

### Post by JavaIsRobust on 2007-05-01
Somebody has to know how to fix this.  Anyone?

---

### Post by endlessurf on 2007-05-01
so i have not done this my self yet but this is what i assume you do.

gksudo gedit /etc/fstab

This will bring up a file that list all the mounted partitions.
example

# /dev/sda6
UUID=be30f8fc-2a09-4208-a3e8-dcd846f0341c /               ext3    
defaults,errors=remount-ro 0       1

Change it to
# /dev/sda6
#UUID=be30f8fc-2a09-4208-a3e8-dcd846f0341c /               ext3    
#defaults,errors=remount-ro 0       1

And i believe they will not mount again. Note though you will have to find which sda each one is so you can put the # on the right partitions.  To get it to work again back out the #

---

### Post by endlessurf on 2007-05-01
whoops wasn't paying attention

---

### Post by endlessurf on 2007-05-01
Just throwing darts with my eyes closed but did you  gedit both fstab on both feisty? might help?

---

### Post by JavaIsRobust on 2007-05-01
Well on the first feisty I want it to be able to access both windows but not the second feisty install.  The second feisty install I don't want it to be able to access any of the other installs.  Therefore, both of the fstab should be different.  Editing one shouldn't affect the other.

---

### Post by JavaIsRobust on 2007-05-01
bump

---

### Post by tom56 on 2007-05-01
Add noauto to the options, e.g.

```
UUID=E0BCC439BCC40BCA /windows        ntfs    noauto,defaults,nls=utf8,umask=007,gid=46 0       1
```

This stops the partition being mounted on boot

---

### Post by JavaIsRobust on 2007-05-01
Still does the same thing.  Keeps them umounted but they still show up un 'computer' so you can automatically mount them.  I don't want them even reconighed by this OS.

---

### Post by gohanssjn on 2007-05-01
I am having these same issues.  Any other ideas welcome!

---

### Post by JavaIsRobust on 2007-05-01
I'm glad to see that i'm not alone on this.

---

### Post by JavaIsRobust on 2007-05-01
bump

---

### Post by ilGaspa on 2007-05-02
I've your same problem: even if i completely delete the mount lines from fstab and delete the mountpoints from /media, the removed partitions still show in the nautilus resources sidebar... :-( even tried rebooting...

---

### Post by Zalbor on 2007-05-02
I had a similar problem. Try mounting them somewhere else than /media. It sounds crazy, but worked for me!

---

### Post by ilGaspa on 2007-05-02
you mean trying mounting them somewhere else even if completely umounting failed? O_o

---

### Post by gohanssjn on 2007-05-02
Yeah, still can't make it so FF NEVER see's the drive.  Ever.

It's always in my lists even if it's not mounted on the desktop...

---

### Post by Zalbor on 2007-05-02
> **ilGaspa said:**
> you mean trying mounting them somewhere else even if completely umounting failed? O_o
That's what I mean. I don't know why it works but in my case it did. I've mounted all my fat/ntfs partitions under /win, and they don't appear on "Computer" or the drivemount-applet anymore. But if I try to make them NOT be automatically mounted, they do.

---

### Post by aidanr on 2007-05-02
have you tried using "nouser" and "ro" to make it so it's read only and only root can mount it? or tried some of the other options like umask= uid= guid= etc, there's a detailed guide [here]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by ilGaspa on 2007-05-03
> **Zalbor said:**
> That's what I mean. I don't know why it works but in my case it did. I've mounted all my fat/ntfs partitions under /win, and they don't appear on "Computer" or the drivemount-applet anymore. But if I try to make them NOT be automatically mounted, they do.

> **aidanr said:**
> have you tried using "nouser" and "ro" to make it so it's read only and only root can mount it? or tried some of the other options like umask= uid= guid= etc, there's a detailed guide [here]("http://ubuntuforums.org/showthread.php?t=283131")

Now I'm at work, but as soon as I get home (I'm italian so It'll be in 12 hours more less) I'll try both solutions and post the results :) thanks ^_^

---

### Post by dfreer on 2007-05-03
sorry, somehow I forgot to subscribe to this thread and completely found it again my chance.

From my experience, it seemed like if you took a drive and mounted it somewhere completely different from /media, nautilus would completely *forget* about the drive and it wouldn't show up under "Places" or in the sidebar of nautilus. But after reading through the thread it seems that doens't seem to work now.

I know this has already been tried, but try doing this:
(1)commenting out the lines in /etc/fstab
(2)check /etc/mtab and see if there is any listing in there concerning the devices you wish to hide, and comment those lines out.
(3)completely remove the /media/xxxx and /mnt/xxxx directories that these devices were mounted at. For example, if /dev/hda1 was mounted at /media/hda1, delete /media/hda1. umm this should go without aying but make sure that these drives are unmounted FIRST!!
(4)reboot and see if the shortcuts are still there.

if not, try checking ~/.nautilus/metafiles and see if there is a shortcut in there.
Also check ~/.gtk-bookmarks for the same thing.

---

### Post by vodalus on 2007-05-04
I am experiencing the same thing (unwanted partitions that the user cannot mount anyway showing up in the nautilus side bar).  This did not used to be the case and nothing I have done makes them go away.  I have a number of backup partitions and old systems on my drive and do not want this stuff showing up in nautilus.

Has anyone filed a bug report on this as it is certainly a regression in Feisty?

In addition, data DVDs are no longer show up on the desktop or the nautilus sidebar.  Thus I must eject them using the button on the drive.  Has anyone else seen this problem?

---

### Post by Zalbor on 2007-05-05
I have a problem with DVDs too. Nautilus seems to recognize them as unwritten discs and asks me to burn files on them. I have to use sudo to mount a DVD correctly.
The same thing happened on edgy.

---

### Post by vtel57 on 2007-05-06
I'm experiencing this very same issue with Debian Etch right now. It's driving my nuts. This is NOT a distro-specific issue. It's a Gnome-Nautilus issue. It also has absolutely NOTHING to do with fstab parameters.

What's happening on my system is that Nautilus - Computer:/// is showing all my partitions on my three drives, including the duplicates of my mirrored RAID array. All I want visible when I click on the Computer icon in Nautilus is my floppy, Zip, DVD, file system, and storage drive.

I've searched for days trying to find a way to remove the superfluous partition icons from Computer. It's NOT a volume manager issue either. None of these partitions are mounted nor capable of user-mounting. They don't exist in fstab at all. 

Don't bother editing /.nautilus/metafiles/computer:%2F%2F%2F.xml either. All it determines is icon type, placement, emblem, etc. within the Computer window.

I know there must be a solution for this, but I can't seem to find it. I don't have this problem in my other Gnome distros... Ubuntu, Fedora Core, SuSE. I sure would like to fix this.

---

### Post by dfreer on 2007-05-06
File a bug report guys (I would but I do not have this problem ATM), and then post the link to it here so that other's can follow it (and not post a duplicate bug).

---

### Post by vtel57 on 2007-05-06
I've determined that this is a hal problem. I may have found a script that fixes it. If it works, I'll post it here. :)

---

### Post by vtel57 on 2007-05-06
OK... it worked like a champ. Here's your solution, folks:

1) In terminal:

```
 # mkdir /usr/share/hal/fdi/preprobe/95userpolicy
```

*use sudo in Ubuntu

2) In terminal:

```
 sudo gedit /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi
```

3) In gedit:

Create an a script that forces hal to ignore certain drives/partitions on your system at startup. Here's an example of mine:

> <?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
        <device>
                <match key="block.device" string="/dev/hda1">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda2">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda7">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda8">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda9">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda10">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda11">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda12">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda13">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda14">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda15">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/hda16">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sda1">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sda5">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sda6">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sda7">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sdb1">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sdb5">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sdb6">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
<device>
                <match key="block.device" string="/dev/sdb7">
                        <merge key="info.ignore" type="bool">true</merge>
                </match>
        </device>
</deviceinfo> 


Wherever you see "/dev/...", this is the partition that I'm forcing hal to ignore. Just use my script and add your own partitions. Delete all the entries that you don't need, but be sure to leave the </deviceinfo> tag at the very end.

4) Save your gedit file... just click "Save". It's already set to save in the proper location.

5) Reboot.

Your unwanted icons on the desktop and in Nautilus --> Computer should now be gone.

Enjoy!

~Eric

PS: Credit for this goes to the following:

[http://www.g-loaded.eu/2005/09/19/a-different-approach-hal/](http://www.g-loaded.eu/2005/09/19/a-different-approach-hal/)

[http://bbs.archlinux.org/viewtopic.php?pid=203817](http://bbs.archlinux.org/viewtopic.php?pid=203817)

[http://gnomesupport.org/forums/viewtopic.php?t=11831](http://gnomesupport.org/forums/viewtopic.php?t=11831)

---

### Post by vodalus on 2007-05-07
> **vtel57 said:**
> I know there must be a solution for this, but I can't seem to find it. I don't have this problem in my other Gnome distros... Ubuntu, Fedora Core, SuSE. I sure would like to fix this.

Thanks for the HAL fix, I'll try it tonight.  But the question remains, why does this not happen on these other systems (or on Ubuntu 6.06 as well, the previous version I used)?  I doubt that the 10ignore-disks.fdi file is generated by them (although I will check this tonight as well).

---

### Post by vtel57 on 2007-05-07
I'm not sure why I didn't experience this problem in my other Gnome distros. However, I do know that it fixed it for me. Hope it works for you too!

Luck!

~Eric

EDIT: My Ubuntu definitely does NOT have the 10ignore-disk.fdi file. I just checked. *shrugging shoulders* :)

---

### Post by CiriusX on 2007-05-09
> **vtel57 said:**
> OK... it worked like a champ. Here's your solution, folks:

1) In terminal:

```
 # mkdir /usr/share/hal/fdi/preprobe/95userpolicy
```

*use sudo in Ubuntu

2) In terminal:

```
 sudo gedit /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi
```

3) In gedit:

Create an a script that forces hal to ignore certain drives/partitions on your system at startup. Here's an example of mine:



Wherever you see "/dev/...", this is the partition that I'm forcing hal to ignore. Just use my script and add your own partitions. Delete all the entries that you don't need, but be sure to leave the </deviceinfo> tag at the very end.

4) Save your gedit file... just click "Save". It's already set to save in the proper location.

5) Reboot.

Your unwanted icons on the desktop and in Nautilus --> Computer should now be gone.

Enjoy!

~Eric

PS: Credit for this goes to the following:

[http://www.g-loaded.eu/2005/09/19/a-different-approach-hal/](http://www.g-loaded.eu/2005/09/19/a-different-approach-hal/)

[http://bbs.archlinux.org/viewtopic.php?pid=203817](http://bbs.archlinux.org/viewtopic.php?pid=203817)

[http://gnomesupport.org/forums/viewtopic.php?t=11831](http://gnomesupport.org/forums/viewtopic.php?t=11831)

----------------------------
Hi vtel57,
 excellent fix, this P.I.T.A. bug has driven me nuts for days. Worked first time. Many thanks.
CiriusX.

---

### Post by vtel57 on 2007-05-09
HA! Yeah... it was causing me to pull my hair out, too. I was bound and determined to find a fix. I knew there had to be one out there somewhere. Glad you got it squared away on your system.

Have FUN! :)

~Eric

---

### Post by vodalus on 2007-05-09
Yes, this worked for me as well.  Thanks a bunch.

I am also having an issue with data DVDs not showing up on the Desktop or in Computer.  They get mounted and I can use them but I have to remove them with the eject button on the drive.  Just to be sure I did not muck anything up in my account, I added a new account and that does the same thing.  The DVDs I am having problems with are not "named" (I made them with growisofs before I discovered I could add a name).  I'm not sure if this is part of the problem (I tried a named data CD and it mounts correctly).  Does anyone have any idea how to fix this issue?

---

### Post by pt123 on 2007-06-10
Thanks vtel57


Any idea if this has been classified as a bug or a more simpler option will be provided.

---

### Post by vtel57 on 2007-06-10
Hey folks!

Glad this fix has worked for you guys. I recently had to use it on Linux Mint (based on Feisty). It works there too! :)

As far as it being a bug... I really don't think so. I think it's just an integral part of the way the newer kernels are handling devices.

If you think this is bad, wait till you get a distro that uses the new libATA drivers for the kernel, where ALL partitions, be they IDE or SATA are considered sd* by the kernel. Oh, and there's a 15 partition limit. The operating system will not be able to access or use any partitions above #15 on the drive. How's that for a PITA. I had to custom compile my own kernel in Zenwalk Linux to get around this garbage. 

Y'all have FUN now! :)

---

