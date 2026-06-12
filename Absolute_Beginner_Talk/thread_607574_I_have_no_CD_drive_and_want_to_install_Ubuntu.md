---
title: "I have no CD drive and want to install Ubuntu"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by darkyre on 2007-11-09
Is there a way around booting the install from a cd?
I have the Gutsy Gibbon .iso on my hard drive, and intend to install Ubuntu on a partition for dual-boot.

I have never actually used any Linux distros before, so anything too complicated might confuse me :/

I do have the appropriate software to mount the CD, but that doesn't help me when booting as far as I know.

Help?

---

### Post by Daveth on 2007-11-09
Hi.
Welcome to the ubuntu forum.
You should have a read of

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

specifically the installation without a cd drive section.

---

### Post by darkyre on 2007-11-09
Haha, I looked through a few threads and got overwhelmed with all the different ways to install it and didn't end up finding that one.

Thanks a lot!
Sorry to be spammy.

---

### Post by Daveth on 2007-11-09
no problem. Let us know how it goes- you can always come back if you get stuck:)

---

### Post by Joakim Stokland on 2007-11-09
I'm just curious - why do you not have a CD drive? If it is because you have an old computer you should consider an older version of Ubuntu than 7.10. Remember that 7.10 is a new and heavy OS.

Anyway, good luck and feel free to come back!
Joakim

---

### Post by anemptygun on 2007-11-09
> **Joakim Stokland said:**
> ...If it is because you have an old computer you should consider an older version of Ubuntu than 7.10. Remember that 7.10 is a new and heavy OS.

If this is the case then look into fluxbuntu, or maybe xubuntu (which is slightly heavier). Or just do a server install and choose your own gui ;)

---

### Post by oilchangeguy on 2007-11-09
just a thought. ubuntu (or linux in general) is not a cure all for an old otherwise un-usable computer. if you're wanting to try linux for the first time, you're not going to get a good first impression using an old, under powered computer. if this is the case, i'd suggest using the computer for parts, or a door stop.  but don't think that using any version of linux is going to rescue that win 95 machine from the trash pile. yes some versions will run on former 95 machines. but what's the point?

---

### Post by Bancho on 2007-11-10
My laptop has no CD drive, and I was able to install Gutsy using unetbootin.  [http://lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html")

Once you install unetbootin and reboot it will begin the ubuntu install process, which will download all the packages for you.  The disc image you already got will be irrelevant at that point.  

It went very smoothly for me.  So it might be worth a shot.

---

### Post by TadH on 2007-11-10
whats the point of having a laptop with no cd drive?

---

### Post by abn91c on 2007-11-10
try using Wubi to install ubuntu  [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Goop on 2007-11-10
Maybe the CD drive didn't work properly so s/he removed it, mine won't so I have to take a no-CD route.

---

### Post by Joakim Stokland on 2007-11-10
Perhaps it is possible to extract the iso-file to a thumbdrive and boot from that? I don't know if it is possible, it's just an idea...

Joakim

---

### Post by zach12 on 2007-11-10
> whats the point of having a laptop with no cd drive?
ther are some newer dell lappys without a cd drives 
Oh and by the way
wubi rocks:guitar:

---

### Post by Duck2006 on 2007-11-10
What specifications is the system that you are trying to install linux to?

---

### Post by rykel on 2007-11-10
Hi, interesting thread... I was sooo fed up with all the freezes, "Failure to initialize HAL" errors, non-automount of my USB external hard disk etc. after upgrading from Feisty to Gutsy that I decided to wipe out and reinstall the OS...

And I remembered that my CD drive no longer writes to disc!

Well, thanks to the Community Docs pointed earlier in this thread, I downloaded and copied the Ubuntu ISO to a partition (which I created using Partition Editor) and rebooted the PC... wow, I got a pleasant surprise, a super fast Ubuntu LIVE desktop in less than a minute! (This is the desktop that was supposed to be the Live CD part of Ubuntu, except that it was now started from a partition, which explains the speed.)

Next, I simply installed Ubuntu and now, I have a shiny new installation. Hurray.

---

### Post by hydraconsole on 2007-11-10
What type of partition did you use to store the Ubuntu ISO? Was it NTFS, FAT32, or ext3?

---

### Post by rykel on 2007-11-10
I did not store the Ubuntu ISO... I followed the instructions in the Community Documentation and simply "mounted" the ISO and copied all the contents over to a partition. The partition was 800MB ext3. Right now, it still shows up on my desktop after a fresh install, but I would be removing it soon to make space for other stuff...

---

