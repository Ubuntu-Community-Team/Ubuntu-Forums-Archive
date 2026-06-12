---
title: "my computer isn't fun anymore because..."
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-03-09
...it freezes all the time.
I tried looking at some of the other threads on this, but 5-pages in to the thread, there were lots of *varied* inputs about when the crashes happened and stuff about dual-core processors and *kernel replacement*, at which point I got freaked and decided to post this. (So please don't direct me there and if you're a moderator - or whoever has the authority to do it - please don't merge my thread with one of those. Thanks.)
I'm using Gutsy, and it freezes a lot. Things slow down to a crawl and the cursor moves like 15 seconds after I move the mouse. I can reboot using Alt+SysRq+B.
I wish I could remember when it all started, but I don't. I do remember that things were just about ok in the beginning - I installed Gutsy a few days after it was released.
I'm not sure what all information would be useful, but here goes: I've never used Compiz, I do not have an additional graphics card, and the processor is just an old-fashioned single core Pentium.
I try to figure out what applications I am using when the freezes happen, and have a mixed bag of information. I should probably mention that some of the times, it's a particular application that freezes up and slows everything down. In such cases, I can at times "Force Quit" that application before everything else dies too. These applications have been: Exaile, Listen, Rhythmbox, OpenOffice, Synaptic and Add/Remove, Swiftweasel, Frostwire - uh, that's pretty much everything! At other times, the freezes have happened even when I was just changing my wallpaper, and sometimes it simply doesn't appear to be application-specific. For example, I'll be using Swiftweasel, Frostwire and Alexandria and things will just generally freeze.
Now I know Hardy will be out in a couple of months and all will be well again, but in the meantime, I would like my computer to be fun again. I would also like to be able to work on it without worrying about so many freezes.
This would be a good time to mention that I barely know what a kernel is, I certainly can't fix or replace it. So smaller solutions, please.
Any help will be appreciated, thanks.

---

### Post by handydan918 on 2008-03-09
These things can be caused by memory issues (bad ram). I can't recall if *buntu has memtest as an option in the grub menu, but if it does, try that. Let it run a long time, like over night, and see if it comes up with any ram errors.

---

### Post by caffienefree on 2008-03-09
Could you tell us how much memory you have?

If you don't know offhand, type **free** into a terminal, then post the output.

---

### Post by kleo skywalker on 2008-03-09
> **caffienefree said:**
> Could you tell us how much memory you have?

If you don't know offhand, type **free** into a terminal, then post the output.

By memory, do you mean RAM? That's 512MB.

And this is what I get when I run **free**:
>              total       used       free     shared    buffers     cached
Mem:        506888     500352       6536          0       1372      80064
-/+ buffers/cache:     418916      87972
Swap:            0          0          0

---

### Post by Efros on 2008-03-09
Have a quick look at you processer Heat sink and fan assembly, make sure that its not clogged with dust, usually this would cause a shutdown through overheating but I have seen systems that just hang. I would also check memory as a previous poster has suggested, also it may be your disk/IDE interface causing this.

---

### Post by chewearn on 2008-03-09
I have an old computer that started freezing every year or so.  To fix it, I have to disassemble the wiring to harddisks, floppy, cd-rom, unplug the memory modules and the AGP card.  Clean up the electrical contacts, and plug everything back in.  It worked every time, and the computer is still running (used to be Windows XP, but now with ubuntu).

---

### Post by kleo skywalker on 2008-03-09
> **Efros said:**
> Have a quick look at you processer Heat sink and fan assembly, make sure that its not clogged with dust, usually this would cause a shutdown through overheating but I have seen systems that just hang. I would also check memory as a previous poster has suggested, also it may be your disk/IDE interface causing this.

I'm really incompetent when it comes to opening up the case and stuff, but I had it all cleaned up recently.
What do you mean by disk/IDE interface?
And exactly how do I do this memory check? (There's a problem with that though - it's not possible for me to leave the computer running overnight, and power cuts are sure to interrupt the process during the day. Depends on how long it takes. How long *does* it take?)

---

### Post by S15_88 on 2008-03-09
just a thought but it might have something to do with not having a swap partition?

anybody else support this theory?

Thanks, ALain

---

### Post by kleo skywalker on 2008-03-09
> **S15_88 said:**
> just a thought but it might have something to do with not having a swap partition?

anybody else support this theory?

Thanks, ALain

I do have a swap partition. I know this for sure because I "manually partitioned" my hard disk and created a swap partition of over 1GB.

---

### Post by mimada on 2008-03-09
Try booting with the live CD and see if there's a performance difference.

---

### Post by kleo skywalker on 2008-03-09
> **mimada said:**
> Try booting with the live CD and see if there's a performance difference.
I can't connect to the internet using the LiveCD and many of the applications I use won't be there. So what would be the point? (That's a real question, is there something I'm supposed to find out by using the LiveCD?)
Also, the LiveCD is so slow, it'd be the next geological age by the time I figure anything out!

On a different note, I forgot to mention that I dual-boot with Linux Mint (which I almost never use).

---

### Post by mimada on 2008-03-09
Booting with the live CD will give some clues about where your problem lies. If your mouse doesn't freeze under the live CD we can then determine that there's a problem with your installation rather than some hardware or compatibility issues.

---

### Post by halitech on 2008-03-09
try booting into Linux Mint and see if you have the same issue there. I fyou do then we are certainly dealing with hardware, if not, its something software on the Ubuntu side.

---

### Post by alzie on 2008-03-09
I was having a similar problem but not as extreme.  I found a thread that mentioned Htop to see what was going on.  My cpu was staying at 100% apparently from Java.  After removing and reinstalling java I ended up going back to 7.04 and my issues went away.  I've since re-upgraded to 7.10 again and I don't seem to be having issues now.

---

### Post by eldepeche on 2008-03-09
> **kleo skywalker said:**
> I do have a swap partition. I know this for sure because I "manually partitioned" my hard disk and created a swap partition of over 1GB.

Yeah, but the output you posted from the "free" command shows 0 total bytes of swap space. Can you post the output from the following commands?
```
mount
cat /etc/fstab
fdisk -l
```

---

### Post by eldepeche on 2008-03-09
Also, rebooting with Alt+SysRq+B isn't any better than hard resetting. Raising Elephants Is So Utterly Boring is what you want as a last resort. (Alt+SysRq+R E I S U B with a few seconds in between each one.) Check [this](http://en.wikipedia.org/wiki/Magic_SysRq_key) out.

---

### Post by kleo skywalker on 2008-03-10
eldepeche, here is what I get when I run those commands:
```
mount
```
> /dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```
cat /etc/fstab
```
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0fda0904-d680-4033-9fbd-607929561558 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=fbd44c05-94ab-4737-911c-f286308b84c3 /home           ext3    defaults        0       2
# /dev/sda3
UUID=9331a582-d2c1-41a1-b2b6-8c407078dd00 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```
fdisk -l
```

Uh, nothing happens when I do this one.

And I'll try booting with the LiveCD and into Mint to see how it goes. (What am I going to in the LiveCD session though? I don't want to finish the session and exit my room to discover that chimeras have taken over the planet because it's 300 years later.)

---

### Post by eldepeche on 2008-03-10
OK, from what you posted, it looks as if /dev/sda3 is meant to be the swap partition, since it's mentioned in fstab, but it isn't currently mounted. Try running 
```
sudo swapon -a
```
and post the output.

---

### Post by kleo skywalker on 2008-03-10
```
sudo swapon -a
```

> swapon: cannot canonicalize /dev/disk/by-uuid/9331a582-d2c1-41a1-b2b6-8c407078dd00: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/9331a582-d2c1-41a1-b2b6-8c407078dd00: No such file or directory

---

### Post by Therion on 2008-03-10
I'm going to suggest you simply try Ultimate Edition (see my sig line) because it just works.  I've recommended Ultimate Edition to many other people who were having trouble with getting a "plain vanilla" Ubuntu install up and running smoothly, and it's never failed.  I would suggest trying a LiveDVD first, and if you decide to do a full-blown install from there, drop me an email or PM first so I can save you a couple headaches when it comes to your video driver install.

---

### Post by eldepeche on 2008-03-10
You shouldn't have to reinstall to get your swap partition mounted. That's pretty serious overkill, if you ask me. If you want, go ahead, but if this is your only issue, I think you ought to try to fix it, and reinstall as a last resort.

I'm not sure how this would have gotten messed up if you set it up on your initial installation, but it shouldn't be too hard to fix. Sorry to keep asking you to run commands and post the output, but it does help me figure out the problem. Can you post the output from:
```
ls -l /dev/disk/by-uuid/
sudo fdisk -l
```
That last letter is a lowercase L, by the way, not a numeral 1. 

I am guessing that somehow your swap partition got reformatted, and thus was given a new UUID, so that the one listed in fstab doesn't refer to the proper device anymore.

---

### Post by kleo skywalker on 2008-03-11
> **eldepeche said:**
> You shouldn't have to reinstall to get your swap partition mounted. That's pretty serious overkill, if you ask me. If you want, go ahead, but if this is your only issue, I think you ought to try to fix it, and reinstall as a last resort.
Yeah, I'm not keen to reinstall either (I'm going to once Hardy is released anyway, so.)
> I'm not sure how this would have gotten messed up if you set it up on your initial installation, but it shouldn't be too hard to fix.
Could installing Mint have messed up the swap thing? Though Gutsy used to hang before too; in fact I installed Mint hoping for some respite but didn't like it much so barely used it.
> Sorry to keep asking you to run commands and post the output, but it does help me figure out the problem.
You're trying to help, so no problem at all!
```
ls -l /dev/disk/by-uuid/
```
> total 0
lrwxrwxrwx 1 root root 10 2008-03-11 17:13 0fda0904-d680-4033-9fbd-607929561558 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-03-11 17:13 9331a582-d2c1-41a1-b2b6-8c407078dd15 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-03-11 17:13 ac7010db-d58b-46fa-bf29-380b517a36e8 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-03-11 17:13 fbd44c05-94ab-4737-911c-f286308b84c3 -> ../../sda2
```
sudo fdisk -l
```
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d475

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2188    17575078+  83  Linux
/dev/sda2            2189       29121   216339322+  83  Linux
/dev/sda3           30152       30401     2008125   82  Linux swap / Solaris
/dev/sda4           29122       30151     8273475   83  Linux

Partition table entries are not in disk order

---

### Post by eldepeche on 2008-03-11
Aha! Edit your fstab file by running ```
gksudo gedit /etc/fstab
```and change this line:
```
UUID=9331a582-d2c1-41a1-b2b6-8c407078dd00 none swap sw 0 0
```
It should read:
```
UUID=9331a582-d2c1-41a1-b2b6-8c407078dd15 none swap sw 0 0
```
The only difference is that the 00 at the end of the big long series of letters and numbers becomes a 15 instead.

When you installed Mint, it reformatted your swap partition, which changes the UUID. After that, it stopped mounting on boot, so you run out of memory easily.

Pretty much every distro other than Ubuntu uses device locations rather than UUIDs. I consider it a security feature the way Ubuntu does it: if one of your partitions has been messed with, better not to mount it than to mount something it doesn't recognize.

Let me know if this works, and if it does, change the thread title so that it says SOLVED.

---

### Post by kleo skywalker on 2008-03-13
> **eldepeche said:**
> Aha! Edit your fstab file by running ```
gksudo gedit /etc/fstab
```and change this line:
```
UUID=9331a582-d2c1-41a1-b2b6-8c407078dd00 none swap sw 0 0
```
It should read:
```
UUID=9331a582-d2c1-41a1-b2b6-8c407078dd15 none swap sw 0 0
```
The only difference is that the 00 at the end of the big long series of letters and numbers becomes a 15 instead.

When you installed Mint, it reformatted your swap partition, which changes the UUID. After that, it stopped mounting on boot, so you run out of memory easily.

Pretty much every distro other than Ubuntu uses device locations rather than UUIDs. I consider it a security feature the way Ubuntu does it: if one of your partitions has been messed with, better not to mount it than to mount something it doesn't recognize.

Let me know if this works, and if it does, change the thread title so that it says SOLVED.

I did this sometime yesterday, and even though I haven't used my computer much since then, it hasn't hung so far. I'll wait and watch for a bit longer and hope it stays that way!
Thanks!

---

