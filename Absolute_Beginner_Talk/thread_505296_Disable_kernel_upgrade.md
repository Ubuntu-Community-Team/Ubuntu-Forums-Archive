---
title: "Disable kernel upgrade"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Luke771 on 2007-07-20
I got got a total noob to try Linux, and Ubuntu is the obvious choice, but the guy is so computer illiterate that I'll have to install the OS for him.

It's gonna be a dula boot because he feels better knowing that if he runs into a problem like for instance, having to quickly do something he already can do in Windows and  not finding out hot to do that in Linux, suff like that.

My plan is to edit /boot/grub/menu.lst in such way that when he starts the pc, he sees a two-line menu where the two available choices will be called quite unmistakeaby, LINUX and WINDOWS.

the problem with that is that as soon as the update manager gets a new kernel, after restart he'll get a new menu.lst with all the option as they look by default: Ubuntu, kernel <version>, Ubuntu kernel <version> recovery,   then the two lines relative to the old kernel (before upgrade), and memtest, and finally windows.

To keep the n00b-friendly setup, the simplest thing to do would be t disable the automatic kernel upgrade; I thinik I remember something about uninstalling a package, but I don't remember exactly which one.
please help?

---

### Post by gvoima on 2007-07-20
Just install Windows first (I mean at the beginning) on the harddrive.
Then install ubuntu from a liveCD. The installation will automaticly add windows to grub menu and keep it there after grub updates. That's quite simple :)

Just remember to leave some extra space for ubuntu at the end of the drive. Windows extended partitions can be a pain in the a** sometimes.

---

### Post by tomcheng76 on 2007-07-20
just make a file similar to this
$ cat /etc/apt/preferences
Package: vnc4server
Pin: version 4.1.1+xorg1.0.2-0ubuntu1
Pin-Priority: 1001

it will apply pin on vnc4server version 4.1.1+xorg1.0.2-0ubuntu1, any new update of vnc4server wont be downloaded

---

### Post by darren1270 on 2007-07-20
This may be a stupid reply but..... why not just leave as is and when he wants to boot windoze.... just arrow down....and hit enter??????

Why go through all that when he may or may not like Ubuntu??:)

---

### Post by Luke771 on 2007-07-20
gvoima, darren: maybe I didn't express myself well,  that was not what I was asking about. Thanks anyway.

Tomcheng: can you please explain a bit more? What kind of file would that be? How does it prevent kernel upgrades?

Anyone: I heard once that uninstalling linux-image [no version number] (I guess it would be linux-image-generic, now) would do just that: disable automatic kernel upgrades.  Is that possible? (maybe I'm mixing it up with something else)

---

### Post by tomcheng76 on 2007-07-20
> **Luke771 said:**
> gvoima, darren: maybe I didn't express myself well,  that was not what I was asking about. Thanks anyway.

Tomcheng: can you please explain a bit more? What kind of file would that be? How does it prevent kernel upgrades?

Anyone: I heard once that uninstalling linux-image [no version number] (I guess it would be linux-image-generic, now) would do just that: disable automatic kernel upgrades.  Is that possible? (maybe I'm mixing it up with something else)

please read
[http://ubuntuforums.org/showthread.php?t=43631](http://ubuntuforums.org/showthread.php?t=43631)
there are many methods

---

