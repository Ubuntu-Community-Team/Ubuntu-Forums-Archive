---
title: "Edgy Eft: System &gt;&gt; Administration &gt;&gt; Disks?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-11-01
I just installed Edgy and I cannot find the disc-admin utility. Has it been discontinued? If not, where can I find it?

---

### Post by kent41 on 2006-11-01
> **zugu said:**
> I just installed Edgy and I cannot find the disc-admin utility. Has it been discontinued? If not, where can I find it?

Sorry its gone:confused:

---

### Post by kent41 on 2006-11-01
> **zugu said:**
> I just installed Edgy and I cannot find the disc-admin utility. Has it been discontinued? If not, where can I find it?
deleted

---

### Post by zugu on 2006-11-01
And how do I find out how much space is in use on a certain partition?

---

### Post by %hMa@?b&lt;C on 2006-11-01
it might be in the repos as "disk-admin" or "gnome-disk-admin"

---

### Post by 23meg on 2006-11-01
Accessories / Disk Usage Analyzer

---

### Post by annda on 2006-11-01
those packages don't seem to be there, but there's always the reliable

```
df
```

highly recommended!

---

### Post by SoloSalsa on 2006-11-01
It's a shame!  I need it to mount my second partition!
Is there some other GUI included on the disks, that won't need a download to use?

---

### Post by zugu on 2006-11-01
> **23meg said:**
> Accessories / Disk Usage Analyzer

Never liked Baobab! I just need my plain bar, showing how much of a partition is used.

> **annda said:**
> those packages don't seem to be there, but there's always the reliable

```
df
```

highly recommended!

I know df is a powerful tool, but I don't want to read man pages at this time or ask around about command line parameters and flags.


I'll try searching in the repos. If it's not in there, then it's a shame.

---

### Post by monkeydust on 2006-11-01
Is there any official word on why this utility "dropped out"? Because i've found it really useful! Is there a replacement?

For me, another reason to stick with Dapper...

---

### Post by zugu on 2006-11-01
Maybe because they added Baobab - a.k.a. Applications>Accesories>Disk Usage Analyzer - instead.

For all of you who think Baobab is actually an improvement, just try to find the amount of free space on a certain partition, then you'll know this is actually regressive. Maybe it should be called "Folder Usage Analyzer".

Disk-admin, or whatever it was called, was very important to me - I could mount and un-mount disks and partitions with a click or two, and it offered a simple, yet comprehensive report of the amount of free/used disk space. RIP.

---

### Post by annda on 2006-11-01
@zugu: it's ok if you don't want to delve into CLI (i'm really lazy that way, and i absolutely don't understand manpages), but df is totally straightforward - just type the 2 letters and you'll get the info you need. no need to clog the system by GUIs for the simplest things - just a suggestion...

---

### Post by zugu on 2006-11-01
Sorry, I must've thought about "du" ;)

---

### Post by nickburns on 2006-11-01
The newer and I think better partition viewer is called gparted

sudo apt-get install gparted

then it shows up in System >> Administration >> GNOME Partition Editor

It works and feels the same...

---

### Post by wpwood3 on 2006-11-01
I installed "pysdm" and it works for me. It is a graphical storage device manager.

Go to System > Administration > Synaptic Package Manager and do a search for pysdm.

---

### Post by LostInBrittany on 2006-11-05
> **nickburns said:**
> The newer and I think better partition viewer is called gparted

sudo apt-get install gparted

then it shows up in System >> Administration >> GNOME Partition Editor

It works and feels the same...

With gparted you cannot mount partitions, or at least I cannot seem to find how. I can only umount.

I liked the look and feel and usability of old disk manager. Any word of why it has dissapeared? Any way to reinstall it ? Please?

---

### Post by bodhi.zazen on 2006-11-05
LOL to ya'all :lol:

Just another reason to learn the CLI if you ask me.

In the time it takes you to find your GUI you can learn how to mount and edit fstab. Then you will not have such problems.

[How to fstab](http://ubuntuforums.org/showthread.php?t=283131http://ubuntuforums.org/showthread.php?t=283131)

As far as df, you can get partition information with:

```
df -h # will give output in Mb/Gb, much easier to read

mount # Lists mounted partitions.

sudo fdisk -l #lists all partitions.
```

That is a small "L" and not the number 1

[Intro to the CLI](http://doc.gwos.org/index.php/CommandLineBeginners)

8)

---

### Post by LostInBrittany on 2006-11-05
Hey, stop there...

The problem, you see, is that I KNOW how to use *fstab*, I know how to use *mount* and *umount*. I began with linux in '94, and I am able to type *vim /etc/fstab* and manage all my partitions.

But if I use Ubuntu instead of other distros is for the small things like that missing disk manager.

---

### Post by bodhi.zazen on 2006-11-05
I understand. Perhaps stay with dapper if the CLI is such a hassle.

And post a "bug" to the developers (I do not know how often they read these forums).

---

### Post by zugu on 2006-11-06
> **bodhi.zazen said:**
> I understand. Perhaps stay with dapper if the CLI is such a hassle.

And post a "bug" to the developers (I do not know how often they read these forums).

The missing disk-admin and some other problems made me switch back to Dapper. But I was very unpleasantly surprised when I saw that there's no Firefox 2, no Gaim 2 beta, no VLC 0.8.5 in the repos.

So basically, neither Dapper or Edgy are good enough for me right now. This is very, very sad.

---

### Post by steve.horsley on 2006-11-06
If you just want the bars, try gnome-system-monitor.

I didn't think much of the GUI disk administrator anyway. And I think the change in /etc/fstab to using UUIDs instead of device names (what is all  **that** about?) is probably what finished it off.

---

### Post by SoloSalsa on 2006-11-06
It's not all about the bars!  It's about an EASY, convenient, graphical drive list.  One the fly, one can see the properties AND (un)mount floppy disk drives, hard disk drives, and optical disk drives.  There are alternative graphical disk usage estimators, but really, no one has suggested a graphical way to mount and unmount. GRAPHICAL.

---

### Post by tenshi-no-shi on 2007-03-05
I know this is a bit off topic but I was wondering how one turns off that annoying feature that automatically opens a mounted disk (usb / cdrom) when it is mounted. the only way I know how to do it is with the non-existent disk-manager

Edit: never mind I fount it through the Removable Media options. but still that was stupid to remove that.

---

