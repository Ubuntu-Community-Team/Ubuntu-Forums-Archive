---
title: "Boot Error - Kernel or hardware problem?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Hishgraphics on 2007-04-02
I just got back from vacation.

When I booted up the computer (P3, 933Mhz, 256+128MB RAM, 20GB+80GB HDD - Egdy installed) it worked fine - although the bootup sequence took much longer than usual before it asked for username & password.

Suddenly, when I was checking out a Youtube page Firefox froze for a long time. Then a bug report appeared. I tried copying it, but it froze again. I hit the CPU reboot button.

Now when booting from Edgy in the hard disk, it crashes. The last time it crashed it told me:

```
<0>Kernel panic - not syncing: Fatal exception in interrupt
```

I tried out the Edgy liveCD, and after decompressing the kernel it crashed and says:

```
incomplete distance tree
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
```

I also tried to boot the Knoppix LiveCD. It also crashed and endlessly displayed:

```
atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying to access hardware directly.
```

Does anyone know if it's a kernel problem or a hardware problem? (I'm guessing it's a hardware problme since it can't even boot up a LiveCD.)

Thanks for your help in advance.

---

### Post by Majorix on 2007-04-02
If you have a Windows disk then format your harddrives using that. For some reason in the past it worked for me when Linux gave an error about the harddrive. Won't hurt.

---

### Post by Hishgraphics on 2007-04-02
I dont have a Windows CD, but I'll try to borrow one if I can in the next couple of days.

Thanks for the tip.

Update:
I also tried out Kubuntu Edgy liveCD.... same thing. Nada.

I don't think it's the BIOS.

I'll try to fix the problem if I can, but I'm bracing myself for the simple fact that the home desktop's original 20GB HDD upon which once housed an XP and now houses an Edgy is at the end of its life.

---

### Post by torgrot on 2007-04-02
I feel your pain.  There are some utilities available from most of the disk drive makers to test the drive.  They usually require boot from a floppy or a CD.  I have used the tools from both Western Digital and Seagate.  Let them run over night doing a comprehensive read/write test.  You can usually wipe the disk by writing zeros to the whole disk with these and then start over if there are no hardware problems with the disk.

torgrot

---

### Post by FreakTech on 2007-04-02
You can also get gparted for free and reformat using it.

---

### Post by Majorix on 2007-04-02
How can he launch gparted when he can't launch Linux...

---

### Post by FreakTech on 2007-04-02
If he can't load a live cd he has either a bad disk or a memory problem, since it runs of the cd and in memory.  Has absolutely nothing to do with the hard drive

---

### Post by Hishgraphics on 2007-04-02
I'll be trying to reinstall using the alternate iso. However, I had to go to work (at work now) I'll have to wait another 8 hours before I can try it out.

RE:Windows installer disk

Last night I managed to reach the "remove partition" page on an XP installer CD. After the first partition is history, the CD freezes up. Can't even format to NTFS if I wanted to (not that I want to) hehe.

---

### Post by Durito on 2007-04-02
I'm getting the same kernel panic error, but I can boot into safe mode fine. It was running great just after install, but now it's experiencing kernel panic whenever the PCMCIA wireless card is in, whether inserted before booting or after log-on.

---

### Post by Hishgraphics on 2007-04-03
Nope.

Alternate installer iso (burned at 4X) doesn't work. I'm getting a Kernel Panic - not syncing: Attempted to kill init!

I can't run anything on the computer now. Even when I got to the partition page of the Windows XP, now I can't even boot up the WinXP CD.

---

