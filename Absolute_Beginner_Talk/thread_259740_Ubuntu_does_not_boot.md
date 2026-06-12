---
title: "Ubuntu does not boot"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by ramcosca on 2006-09-17
Well, here we go again.

Tries booting but then stops.

First it says GRUB loading, blah, blah, then...
```
    Booting 'Ubuntu, kernel 2.6.15-26-386'

root (hd0,0)
  Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
    [Linux-bzImage, setup=0x15784f]
initrd /boot/initrd.img-2.6.15-26-386
    [Linux-initrd @ 0xe869000, 0x676626 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
```This is the normal part, I believe... then it shows the brown Ubuntu screen... does the first task, then the second task (load root drivers, I think it is) just doesn't do it, then shows (under the code that I wrote up there)...```
mount: Mounting /dev/hda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
# _
```
That's about all it does. The _ it shows is blinking, so I believe it's on terminal. What do I do? ](*,) 


Darn, typing all that took about 20 minutes, lol. :rolleyes:

---

### Post by Najand on 2006-09-17
Are you sure /boot and /root are on the same partitions?
If you are on the terminal use "sudo fdisk -l" ("fdisk -l" if you are on recovery mode) and write the output here please.... Sorry, I know it is hard to type the entire thing.

---

### Post by wieman01 on 2006-09-17
Is this a dual-boot system? Is Ubuntu installed on HDA1?

---

### Post by ramcosca on 2006-09-17
> **Najand said:**
> Are you sure /boot and /root are on the same partitions?
If you are on the terminal use "sudo fdisk -l" ("fdisk -l" if you are on recovery mode) and write the output here please.... Sorry, I know it is hard to type the entire thing.
Uhmmm, ok, no, it isn't terminal. Sure looks like it. And yes, same aprtitions. I only have one.
```
# sudo fdisk -l
/bin/sh: sudo: not found
# _
```
> **wieman01 said:**
> Is this a dual-boot system? Is Ubuntu installed on HDA1?No dual-boot. I did a native install; deleted whole partition on hard drive and it's only one hard drive...

---

### Post by ramcosca on 2006-09-17
How do I enter recovery mode?

---

### Post by Najand on 2006-09-17
Well, let me see... then it is just grub command prompt... 
Don't you have it in your grub menu? If you cannot see grub menu during booting, before it start booting push "Esc" key.
If it couldn't help use the live cd.

---

### Post by wieman01 on 2006-09-17
It would be helpful if you attached a screenshot of GParted so that we get to understand how your partitioning looks like. You could achieve that using the Live CD as Najand has pointed out.

But then... Hang on... Could you also post your "/etc/fstab" please? I think there is something wrong with it:
> mount: Mounting /dev/hda1 on /root failed: Invalid argument
Could it be that you have specified "/root" rather than "/" for the root partition?

[COLOR="Red"][By the way... These are "terminal" commands. Fire up a terminal and execute these commands.][/COLOR]

---

### Post by ramcosca on 2006-09-17
> **Najand said:**
> Well, let me see... then it is just grub command prompt... 
Don't you have it in your grub menu? If you cannot see grub menu during booting, before it start booting push "Esc" key.
If it couldn't help use the live cd.Tried the recovery mode thing, still shows the "can't access tty" thing, stuck on the same place.
If I try the Live CD... what will it do? Wouldn't my only choice there (for fixing this) be reinstalling Ubuntu?

> **wieman01 said:**
> It would be helpful if you attached a screenshot of GParted so that we get to understand how your partitioning looks like. You could achieve that using the Live CD as Najand has pointed out.

But then... Hang on... Could you also post your "/etc/fstab" please? I think there is something wrong with it:

Could it be that you have specified "/root" rather than "/" for the root partition?
Or maybe to get a screenshot of GParted... I'll see what I can do. Live CD, then... what? What do I do, "gparted" on terminal, right? If not, I'll see what I can do to find it.

What do you mean "/etc/fstab"? ... uhm... Filesystem > /etc/fstab? Please explan what to do in this one; I do not understand.

---

### Post by Najand on 2006-09-17
Well, use Live CD and use the command:
```

sudo fdisk -l

```

---

### Post by wieman01 on 2006-09-17
Alright. There is a file on your "root" partition that controls the mounting of your harddisks. The file is "/etc/fstab" which you can open this way **[COLOR="Red"](after booting with Live CD)[/COLOR]**:
> sudo mount /dev/hda1 /mnt
> sudo gedit /mnt/etc/fstab
Is there a line saying "/root"? If so delete the "root" so that it says "/" only.

But to play safe, post the content of the file first. We can help.

[COLOR="Blue"][By the way... These are 'terminal' commands. Fire up a terminal and execute them by type the commands & pressing enter.][/COLOR]

---

### Post by ramcosca on 2006-09-17
Fired up a terminal, ¨sudo gparted¨, got a screenie, here it is.

[IMG]http://i9.tinypic.com/4cl2u0z.png[/IMG]

---

### Post by ramcosca on 2006-09-17
> **Najand said:**
> Well, use Live CD and use the command:
```

sudo fdisk -l

```
It reads:
```
Disk /dev/hda: 20.0 GB, 20003880960 bytes

(imagine that this is some sort of table vvvv )
Device    | Boot | Start | End  | Blocks    | Id | System
/dev/hda1 | *    | 1     | 2344 | 18828148+ | 83 | Linux
/dev/hda2 |      | 2345  | 2432 | 706860    | 5  | Extended
/dev/hda5 |      | 2345  | 3432 | 706828+   | 82 | Linux swap / Solaris
```

> **wieman01 said:**
> Alright. There is a file on your "root" partition that controls the mounting of your harddisks. The file is "/etc/fstab" which you can open this way **[COLOR="Red"](after booting with Live CD)[/COLOR]**:
> sudo mount /dev/hda1 /mnt
[QUOTE]sudo gedit /mnt/etc/fstab
Is there a line saying "/root"? If so delete the "root" so that it says "/" only.

But to play safe, post the content of the file first. We can help.

[COLOR="Blue"][By the way... These are 'terminal' commands. Fire up a terminal and execute them by type the commands & pressing enter.][/COLOR][/QUOTE]Tried the first (sudo mount /dev/hda1 /mnt) and it says...
```
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```I uh... understand Chinese better than I understood that error, lol.

Then... (sudo gedit /mnt/etc/fstab)

A gedit window opened... uhm... empty. #-o

---

### Post by Najand on 2006-09-17
Try to check your filesystem using:
```

sudo fsck -pfv /dev/hda1 

```

---

### Post by wieman01 on 2006-09-17
Najand:

What do you think? The second error Ramcosca has got looks a bit odd, not to say serious. Any idea?

Ramcosca:

What happens if you try:
> sudo mount -t ext3 /dev/hda1 /mnt

---

### Post by ramcosca on 2006-09-17
Ok, heres the fsck... brb with the other one.

```
ubuntu@ubuntu:~$ sudo fsck -pvf /dev/hda1
fsck 1.38 (30-Jun-2005)
/dev/hda1: recovering journal
/dev/hda1: Note: if several inode or block bitmap blocks or part
of the inode table require relocation, you may wish to try
running e2fsck with the '-b 32768' option first.  The problem
may lie only with the primary block group descriptors, and
the backup block group descriptors may be OK.

/dev/hda1: Block bitmap for group 128 is not in group.  (block 2312007)


/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
ubuntu@ubuntu:~$

```

The other one, the mount one: ```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$

```

I found myself a floppy, so as to make exchanging text files easy, lol.

---

### Post by wieman01 on 2006-09-17
I am pretty sure now that there is a problem with your file-system / hard-drive. Since I am not in front of my Linux machine at this moment, I can't help you right now. 

But you need to fix it first before you can boot Ubuntu. Can you try what the output is suggesting?

---

### Post by ramcosca on 2006-09-17
This: "dmesg | tail  or so"?
If so, how?

---

### Post by ramcosca on 2006-09-17
If all this fails, I can just do (yet another) clean install of Ubuntu. I've done around... 10 in the past few weeks, not exaggerating. Always gave me some kind of problem... but it was always after booting. Now i had the system up and running, all nice and smooth. Don't know what happened to it. I am not one to go around messing with the code or all that... simply because I do not know how to do so. I am simply learning. I have learned a few things already, but still have a loooooong way to go. :frown:

---

### Post by wieman01 on 2006-09-17
I was more thinking of these commands:
> sudo e2fsck -b 32768 /dev/hda1 
> sudo fsck -vf /dev/hda1
But just a thought. Sorry, buddy, I cannot help you any further. If you're saying that you have had a number of related issues, are you sure this does not relate to a failed/damaged hard-disk?

---

### Post by ramcosca on 2006-09-17
You know what? Thanks, many, many thanks for your help guys but I think I might as well just reinstall everything. I don't wanna make you guys go through so much trouble and if it's something serious (as was previously suggested, from what I understood) I might as well just reinstall and save you guys the trouble. Thanks for the help, though. Highly appreciated. :)

[Edit] Previous issues were not hard drive related.

---

### Post by Najand on 2006-09-17
Hmm, seems like a bad problem with the harddisk... Try installing it again.

---

### Post by ramcosca on 2006-09-18
Reinstalled. Hope it doesn't give me any more problems. :)

Also installed on desktop... full install, no dual boot, to hell with Microsoft and their filthy schemes.

Now have a new problem, lol. How to get online using a Wifi dongle. Will search.

[Edit] Problem solved. Works like a charm. Now I can say I've completely gone Ubuntu. Open Source FTW.

---

