---
title: "LiveCD issue: no Gnome?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Iendicis on 2007-09-12
So, I start up Ubuntu, it gets to the menu, and I click the Run and Install option. It loads fine and dandy. But then while the orange bar is inching to the right, eventually it blacks out, goes to a text screen, and gives a very long stream of errors mostly attributed to the C drive (at least a hundred errors, more like five hundred before it stops). Not being familiar with Ubuntu, I can't say I understand. After the list of errors and failures, it drops to a command prompt and leaves me there, without Gnome.

I typed a few words in, I tried to log in, start Gnome, whatever. Nothing. A log in screen would not let me go in, no matter what I did, and no other commands worked. Eventually I stupidly typed in "startx" and it loaded KDE (oopie, my Slax instincts kicking in!) which gave me a brown screen and a flickering cursor. So I gave up and rebooted again. The same thing happened.

From C drive I'm thinking the hard drive, but it's a Live CD. I plan on trying it once more.

Ubuntu: Desktop, Feisty, i386
CPU: An aging Pentium III - 750 mhz
Ram: 512 mb (between 256 x2, I think)
Hard Drive: 60 GB, 10 free (no partitions, all for Windows XP)
Graphics: An aging Geforce 200 MX (I know, I need to upgrade, shut up. :))

I'm really looking forward to Ubuntu, but this is the first Linux problem that I've run into that I really have no idea what to do with. Google has yielded nothing, because I'm not sure what I'm dealing with. I'd appreciate any thoughts or comments.

:popcorn:

Love smilies here. :)

---

### Post by reckless2k2 on 2007-09-12
install using the alternate cd

---

### Post by Iendicis on 2007-09-12
I don't want to install, though, I want to see the Live CD first. I'm holding out for a second hard drive, and I'm sampling before 7.10 in October.

---

### Post by BrendanM on 2007-09-12
Are you sure you downloaded the Ubuntu live CD and not the Kubuntu one? I thought the normal Ubuntu live CD didn't even include KDE, right?

---

### Post by snevensmores on 2007-09-12
I'm a noob myself, so I'm likely mistaken, but does anyone else think that, with that aging hardware, Xubuntu with xfce might be a better choice than trying to use gnome?

---

### Post by Iendicis on 2007-09-12
> **BrendanM said:**
> Are you sure you downloaded the Ubuntu live CD and not the Kubuntu one? I thought the normal Ubuntu live CD didn't even include KDE, right?
I mistakenly started ip KDE; it didn't work, but it still came up and gave be a brown screen all the same. It was Ubuntu original.

As for the other comment, my computer isn't **that** old. It's got a good healthy bit of Ram, so this will work fine...unless Ubuntu doesn't work...I'm still running XP, even. I've looked into Xfce, bit it's a little too minimalist. I'll edit again to add that I have run Slax and Wolvix on my machine for a little over a month, which have KDE and Xwindows, respectively, and those have run fine.

---

### Post by superbenny on 2007-09-12
> **Iendicis said:**
> I don't want to install, though, I want to see the Live CD first. I'm holding out for a second hard drive, and I'm sampling before 7.10 in October.
first of all, in that command line, try typing 

```
gdm
```

thats the command to start gnome (correct me if im wrong, im a kubuntu-er myself)

if that doesnt work,

are you using a cd that you burned yourself? if so:
check the iso to make sure nothing corrupted
or just order a free stable release cd from shipit
(free shipping, dont even need to give your credit card or anything)

---

### Post by Sef on 2007-09-12
> I'm a noob myself, so I'm likely mistaken, but does anyone else think that, with that aging hardware, Xubuntu with xfce might be a better choice than trying to use gnome?

No, the computer has enough ram to work fine.

More likely the download was bad ([md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") done?), or burned at more than 4x, or cd is bad.

---

### Post by Iendicis on 2007-09-12
> **superbenny said:**
> first of all, in that command line, try typing 

```
gdm
```

thats the command to start gnome (correct me if im wrong, im a kubuntu-er myself)

if that doesnt work,

are you using a cd that you burned yourself? if so:
check the iso to make sure nothing corrupted
or just order a free stable release cd from shipit
(free shipping, dont even need to give your credit card or anything)

Sweet, will try. Thanks!

---

### Post by Iendicis on 2007-09-12
> **Sef said:**
> No, the computer has enough ram to work fine.

More likely the download was bad ([md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") done?), or burned at more than 4x, or cd is bad.

I made a CD-RW at 4x speed with Nero 7. My drive's max write for RW is 4x.

I downloaded the file with Free Download Manager.

I checked the CD's integrity, it stopped and stayed in one spot for about ten minutes (five and a hal;f of the little bar hash marks).

Should I use a different CD type? Is CD-R better?

EDIT: Hash check came up positive; the CD burning sucked. I shall try again!

---

