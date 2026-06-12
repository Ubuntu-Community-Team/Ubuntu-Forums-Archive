---
title: "dpkg error code (Yes, I've searched)"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Oliver Closov on 2008-04-13
Hi everybody,

E: Sub-process /usr/bin/dpkg returned an error code (1)

I apparently have a common problem, but so far none of the solutions i have seen posted (all throughout the web) have solved my problem.
My experience level is extremely low, so hand-holding is requested (sorry).
OK I will try to explain everything I have tried so far without getting too verbose.

apt-get upgrade

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdegames-kde4: Depends: bovo-kde4 (>= 4:4.0.0-0ubuntu1~gutsy1) but it is not installed
                 Depends: katomic-kde4 (>= 4:4.0.0-0ubuntu1~gutsy1) but it is not installed

(there were tons more but I have truncated the list) then it ended with...
E: Unmet dependencies. Try using -f.

So then I tried...
apt-get -f install

(this was ripped from somewhere in the middle of a HUGE list)

dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kbattleship-kde4 (from .../kbattleship-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kbattleship-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/hicolor/128x128/apps/kbattleship.png', which is also in package kde4games-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kblackbox-kde4 (from .../kblackbox-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kblackbox-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/icons/hicolor/128x128/apps/kblackbox.png', which is also in package kde4games-data

Errors were encountered while processing:
 /var/cache/apt/archives/libkdegames4-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb
 /var/cache/apt/archives/bovo-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb
 /var/cache/apt/archives/katomic-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb
 /var/cache/apt/archives/kbattleship-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb
 /var/cache/apt/archives/kblackbox-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb
 /var/cache/apt/archives/kbounce-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb

(Again, HUGE list - followed by...)

E: Sub-process /usr/bin/dpkg returned an error code (1)

(I am in an SSH from my MS box and I didn't config my history setting so I lost some of the other commands & outputs I have used, but I will try to remember them...)

apt-get --force-overwrite dist-upgrade
dpkg --clear-avail
apt-get check

uhhh, well a couple other things, but my limited understanding of the commands i am using makes it difficult to remember.
Please help.
Thanks,

Oliver

---

### Post by Martje_001 on 2008-04-13
I think synaptic can fix your problem, boot up from a livecd and do:
```
ssh -x 192.168.0.0.0 "sudo synaptic"
```
This will give you synaptic **from** the machine your connecting to, **on** the machine you're running ssh from.

---

### Post by zamb on 2008-04-13
I think those *.deb files in "/var/cache/apt" are corrupted and you should move them somewhere else:
```
cd /var/cache/apt/archives && sudo mv 'libkdegames4-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb' 'bovo-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb' 'katomic-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb' 'kbattleship-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb' 'kblackbox-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb' 'kbounce-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb' ~root/
```
The above command will move those corrupted files to /root just in case you need them later (in case my solution didn't help).

You should move any other "*.deb" file(s) that give some errors while unpacking.

If that didn't help just move the files back (and I'm sorry, I tried).

Ziyad.

---

