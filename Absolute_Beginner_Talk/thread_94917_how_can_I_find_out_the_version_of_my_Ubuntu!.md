---
title: "how can I find out the version of my Ubuntu?!"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by bijan on 2005-11-25
Hi, how're ya?

This is my first post in here, so, please be kind to me ;)

You know I'm much of a SuSE user, but I'm tired of SuSE restrictions and all the misplaced files and ... And since OpenSuse just got started, so, it doesn't seem like they can get powerful enough to call them a real community in the next few month. Not to mention that I hate Fedora, coz I think they have a devoted team to deface all the nice functions that might look handy to users just before each new release! I tried Gentoo, but since I don't have a fast internet connection and at the same time I really don't wana configure everything myself (no need actually) it's too boaring for me.

So, I saw this ubuntu distro in a local store, and since I heard abotu it from friends, not to mention I like the name a lot (the way it sounds!), plus the logo that's fabulous, I told myself let's give this one a try too! I installed it and I just think it's beautiful. Even though I had problems in connecting to itnernet, but I like it.

My silly problem is: It's only written Ubuntu 2005 on the cover of the CD, but I can't see any sign anywhere (including the installation step) about the true version number, like you guys say Ubuntu 5.04 or I dunno, just an exact version numbe! I know that it's too dumb, but I can't make it! Would you please tell me how to find out about my version number?!

Cheers,
bijan

---

### Post by AmboyGuy on 2005-11-25
Try  (Ctrl+Alt+F1), You should see something like -- Ubuntu 5.04 "Hoary Hedgehog" -- (Ctrl+Alt+F7) gets you back to the GUI.
My CD set came from shipit.ubuntu.com and has the version printed on the Install & Live CD disks.

I have the latest security patched kernel for Hoary " 2.6.10-6-686 #1 Fri Nov 18 12:37:17 UTC 2005 i686 GNU/Linux "
That apt-get/synaptic is great, even though I've only got an old 33.3K Sportster modem currently working. 
(I'm lucky enough to have a 3Com/USR 56K Data/Voice/Fax Winmodem based on an AD1806JS chip that I, so far, haven't been able to coax into working.)

---

### Post by kalin on 2005-11-25
A universal way is to look in the text file "/etc/lsb-release", I would guess there's the version details of any Linux Standard Base (LSB) compliant distribution.

In general *IX-es keep a text file called "version-something", or "something-version", or "xxx-release" in /etc. Typing "ls -d /etc/*version* /etc/*release*" in a terminal should reveal that specific file.

```

user@ubuntu:~$ ls -d /etc/*version* /etc/*release*
/etc/debian_version  /etc/lsb-release

```

Ubuntu keeps two of them, one is corresponding to a Debian version ("/etc/debian_version" - I guess the one it's synchronized with before freeze), and the other is the Ubuntu version itself (the "/etc/lsb-release" one).

---

### Post by soonindallas on 2005-11-25
kalin got there before me for the distribution descriptors.

you can see the kernel version by typing

```
uname -a
```

in a terminal

---

