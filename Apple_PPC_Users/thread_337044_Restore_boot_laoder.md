---
title: "Restore boot laoder"
date: 2007-01-12
forum: Apple PPC Users
---

### Post by Auria on 2007-01-12
Hi, i installed Ubuntu PPC as a dual-boot on my mac - and this was a very bad idea because nothing works. (sad to say it because i'm a big open-source supporter - will try again when i get a computer with better supported hardware)

Now i want to remove it -- however, i'm afarid that by doing so i erase yaboot and the computer refuses to boot anymore. Is there a way i can uninstall safely?

thanks

---

### Post by 3rdalbum on 2007-01-13
The good news: Erasing the Ubuntu partition is easy (just use Gparted from the Live CD). Yaboot isn't taking up very much room at all, so it's easier just to leave it on there.

To stop Yaboot from loading up at startup, boot up a Mac OS CD, go into Startup Disk and click on your Mac OS drive. You might also be able to use this method from the installed Mac OS; I've not tried it this way.

Now your Ubuntu will be gone, and the Mac will boot straight into Mac OS.

I don't know how long you've been trying to get Ubuntu running well on your Mac, but if decide to stick with Ubuntu for a little while longer, PM me and I'll see if I can help you with your problems.

---

### Post by Auria on 2007-01-13
Ok thanks for your answer =)

> 
The good news: Erasing the Ubuntu partition is easy (just use Gparted from the Live CD). Yaboot isn't taking up very much room at all, so it's easier just to leave it on there.


but what do you mean by leave it there? You suggest that i shrink the psrtition instead of erasing it? Or is yaboot not located on the Ubuntu partition?

it's because i read windows users needed to reinstall the original boot laoders otherwise the computer wouldn't boot anymore - but what you tell me suggests that the original boot driver is still there and i just need to choose a default startup disk

> 
I don't know how long you've been trying to get Ubuntu running well on your Mac, but if decide to stick with Ubuntu for a little while longer, PM me and I'll see if I can help you with your problems.


Ahah if you really want to :p But i've already asked for help many times and got no answer

My main use of computers is for music and programming.

neither my mic nor my lin-in work are deteted
I asked for help, but got no answer  ](*,) [http://www.ubuntuforums.org/showthread.php?p=1988902#post1988902](http://www.ubuntuforums.org/showthread.php?p=1988902#post1988902)

midi doesn't seem to work either (calling timidity from the terminal works, but doesn't seem to work through ALSaA despite following 3 tutorials about it) - so looks bad for music.

Printing only works via TurboPrint, that's a bit of a shame i don't want to pay for printing drivers (at least not unless Ubuntu becomes my main OS)

As for programming, my fav IDE (code::blocks) offers no PPC binary, and refuses to build. I posted a thread on their boards asking for help, but the only answers i got were links to the build instructions i had already followed... I tried Anjuta, but seemed very makefile-oriented, and i couldn't find any option to add existing files to it. Furthermore it had many glitches, so not really interesting. I also try KDevelop (or whatever it's called) but it also seems autotools-oriented, and my project stop building after i tried linking to a library. Strangely, removing the library didn't fix the problem...

GDC (Gnu D compiler) doesn't work either, even though PPC binaries are provided

So yeah... frustratin experience :P

---

### Post by 3rdalbum on 2007-01-14
Okay, I understand. I'm a musician too, and my line-in doesn't work on the Powermac either. It just looks like us PowerPC users are unwanted again :-)

On Ubuntu, if you do the command "sudo fdisk -l", you will get something similar to this:

```

/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2        Apple_Driver_ATA Macintosh                54 @ 64       ( 27.0k)  Unknown
/dev/hda3        Apple_Driver_ATA Macintosh                74 @ 118      ( 37.0k)  Unknown
/dev/hda4      Apple_Driver_IOKit Macintosh               512 @ 192      (256.0k)  Unknown
/dev/hda5           Apple_Patches Patch Partition         512 @ 704      (256.0k)  Unknown
/dev/hda6         Apple_Bootstrap untitled               1954 @ 1216     (977.0k)  NewWorld bootblock
/dev/hda7               Apple_HFS untitled 2          2615303 @ 4199128  (  1.2G)  HFS
/dev/hda8               Apple_HFS untitled 3          5780519 @ 6814431  (  2.8G)  HFS
/dev/hda9         Apple_UNIX_SVR2 untitled            3945313 @ 3170     (  1.9G)  Linux native
/dev/hda10        Apple_UNIX_SVR2 swap                 250645 @ 3948483  (122.4M)  Linux swap
/dev/hda11             Apple_Free Extra                    10 @ 12594950 (  5.0k)  Free space

```

/dev/hda6 (on my machine) contains Yaboot. It's not even a megabyte, so it's not worth deleting. And I know from experience that if you start up your Mac OS and then select the blessed System Folder in the "Startup Disk" control panel, it changes your Mac's firmware settings so it will boot straight into Mac OS.

In fact, I could never get Yaboot to recognise the Mac OS partition, so I used this method to set the computer to boot straight into Mac OS. If I wanted to use Ubuntu, I used to enter Open Firmware and type in this command: boot hd:6,yaboot.  (which started up Yaboot on /dev/hda6).

So yeah, get rid of the Linux partitions. That's not something I've done before, but you may be able to delete them and then create a new partition in the resulting empty space; it may even work without erasing the whole hard disk. Of course, I would highly suggest making a backup of everything important!

---

