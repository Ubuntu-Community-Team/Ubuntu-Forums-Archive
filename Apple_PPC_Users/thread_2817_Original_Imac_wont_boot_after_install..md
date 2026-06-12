---
title: "Original Imac wont boot after install."
date: 2004-10-31
forum: Apple PPC Users
---

### Post by Toad on 2004-10-31
I'm attempting to install Ubuntu on a 233Mhz G3 Imac for a friend. I Walked through the entire install without any issues and was prompted to reboot. On reboot i get a message stating "Please wait. Loading Kernel" and it stays there forever. I tried leaving it up for 20+ minutes, but no progress after that.

I found this bug in the ubuntu bugzilla that seems to be documenting the same issue, except i chose reiserfs instead of the default ext3 as my root filesystem.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2613](https://bugzilla.ubuntu.com/show_bug.cgi?id=2613)

Help!

---

### Post by cerulean coil on 2004-11-01
There are other people having troubles with older iMacs, although nothing as bad as you are reporting.

[iMac thread 1.](http://ubuntuforums.org/showthread.php?t=2340) 
[iMac Thread 2.](http://ubuntuforums.org/showthread.php?t=2568) 

These threads also link to each other.

A basic summary of their contents would be that iMac installs seem to go better when you burn the iso slowly to a CD-RW on a Windows machine.

Hope this helps.

---

### Post by Toad on 2004-11-01
I figured out my problem.

My friend had upgraded the hard drive to a 80 GB one. So I had to reinstall and make the root partition to be 7 GB. I converted the rest of the space  (~70 GB) into the /home partition. It boots just fine.

I did have more trouble with the iMac Keyboard not being recognized and I had to use a regular USB keyboard to continue on with the post-reboot install stages. 

So if anyone has any ideas about how to get the iMac keyboard to work, please post on here.

Thanks

---

### Post by Castaa on 2004-11-01
[QUOTE=Toad]I figured out my problem.

My friend had upgraded the hard drive to a 80 GB one. So I had to reinstall and make the root partition to be 7 GB. I converted the rest of the space  (~70 GB) into the /home partition. It boots just fine.

I did have more trouble with the iMac Keyboard not being recognized and I had to use a regular USB keyboard to continue on with the post-reboot install stages. 

So if anyone has any ideas about how to get the iMac keyboard to work, please post on here.

Thanks[/QUOTE]
 If you go to the computer menu->Desktop Preferences->Keyboard

You can set your key board to a Macintosh keyboard.

I'm not sure if this is your problem but it might be work trying.

---

### Post by cerulean coil on 2004-11-01
[QUOTE=Toad]I figured out my problem.

My friend had upgraded the hard drive to a 80 GB one. So I had to reinstall and make the root partition to be 7 GB. I converted the rest of the space  (~70 GB) into the /home partition. It boots just fine.[/quote]

Rock and roll.  :grin:

---

### Post by ubuntu77 on 2005-03-05
I am another Linux newbie, trying to install Ubuntu Linux 4.10 (warty) on a Rev. D blueberry iMac 333.  I get the same problem... hangs forever at "Please wait, loading kernel...".  During the install, I let the partitioning program use the "guided partitioning" option with all the default values.  It produces the following on my upgraded IBM Deskstar 60GB HD:

IDE1 master (hda) - 61.4 GB
    #1  32.2 KB                 Apple
    #2  1.0 MB        boot    untitled
    #3  60.9 GB      ext3    untitled
    #4  512.8 MB    swap   swap            (I upgraded the RAM to 256MB)

#2 and #4 have the white on black smiley face icons next to type, and #2 also has the crooked downward arrow next to its smiley face.

Toad said he figured out his problem by making his root partition 7 GB and his home partition about 70 GB.  So in order to get my iMac to work, does that mean I need to make my boot partition > 1 GB vice the 1 MB it is now, or do I need to split up the ext3 partition into 2 partitions, say a 6 GB (for root) and a 54 GB (for home)?

Please help!

 :sad:

---

### Post by Toad on 2005-03-06
Leave your boot partition alone. Take the 60.0 gb ext3 partiton and try splitting that up into 2 with one being 7 GB and the other the rest. 

df on the imac right now produces:
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             6.5G  1.8G  4.4G  29% /
tmpfs                  62M     0   62M   0% /dev/shm
/dev/hda5              68G   39G   30G  57% /home

```

also
```

$ sudo fdisk -l /dev/hda
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled            13671875 @ 2018      (  6.5G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 1000641 @ 155300847 (488.6M)  Linux swap
/dev/hda5         Apple_UNIX_SVR2 untitled           141626954 @ 13673893  ( 67.5G)  Linux native

```

Hope that helps.

---

### Post by ubuntu77 on 2005-03-06
Hi, Toad!

Thanks for answering my post.  Last night (Saturday night, PST), I did some research on partitioning schemes and I partitioned my internal 60GB IBM Deskstar as follows:

/ 2GB ReiserFS
/boot 128MB ReiserFS
/tmp 2GB ReiserFS
/var 4GB ReiserFS
/usr 4GB ReiserFS
/usr/local 4GB ReiserFS
/home 40GB ReiserFS

So, I now have a functioning ubuntu system! Cool! Your advice was right on the money, I just needed to educate myself to understand what you meant by what you originally said.

I do have two other minor issues, though.  I don't have 3D OpenGL acceleration because ATI doesn't make video drivers for linux ppc. :(  The other issue is my internal speakers don't work, but if I plug in external speakers to my sound out port, that works fine.  DJ_Max advised me to play around with my audio and sound settings (I assume under GNOME, as that is what I'm using).  Have you had a similar issue with your installation?  If so, how did you work around it?

Thanks for your help!

PS: My iMac specs:
iMac Rev D Blueberry
G3 333Mhz, 256MB RAM, internal IBM Deskstar 60GB HD
Tray loading 24x CD-ROM
ATI Rage Video
Ubuntu 4.10 (Warty Warhog) only (no dual boot with Mac OS 9 or X)

---

