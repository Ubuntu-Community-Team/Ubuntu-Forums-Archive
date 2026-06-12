---
title: "LiveCDs won't work!"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2007-12-24
I am putting together a new Ubuntu build, and got everything set up correctly. Well, I put the Ubuntu Gutsy Live CD in, and it won't boot.

I tried PCLinuxOS and it booted. I re-burned another CD on lowest speeds and it still wouldn't work. It went to a screen and said fatal terminal error or something on one of the installations.

Geubuntu LIVECD wont even work. it stops at HILD or something like that. So nothing is working!! FEDORA AND PCLINUXOS Work, but NO distros of Buntu. WTF?

I went in GPArted, erased the partition, and re-partitioned it, and then tried it again and same thing.
On Geubuntu it stops at a printing section when loading up or the one right before it.
Gutsy it stops when it has 4 "BARS" left to load.

HELP please!

---

### Post by Tristicus on 2007-12-24
Oh, and in Fedora, it said it failed to load so had to run GNOME failed server or something like that.

---

### Post by Lord DarkPat on 2007-12-24
it's probably a faulty iso. re-dload it and check.
And even i get the fedora live error. It says something about Blocked I/O or something.

---

### Post by Tristicus on 2007-12-24
It isn't a faulty ISO because I have used the ISO for my other Ubuntu system and it works perfectly.

---

### Post by diatribe on 2007-12-24
precise error messages might be more helpful

---

### Post by Lord DarkPat on 2007-12-24
maybe it's corrupt. Or if it is only the GNOME ubuntu, try kubuntu and instll ubuntu-desktop, remove kubuntu-desktop.

---

### Post by Tristicus on 2007-12-24
Might just try that but really don't want to DL anything on this slow internet connection (Not slow, but cuts out a lot...stupid DSL)

---

### Post by Lord DarkPat on 2007-12-24
borrow it from a friend, maybe(I know most of 'em are on windbloze, I guess). Or, try ShipIt. But, by the time you get the CD, the download will finish even on a 56k modem

---

### Post by Tristicus on 2007-12-24
I am downloading it now, but if it doesn't work, I will be ticked. And I don't know why GNOME won't start....

---

### Post by overdrank on 2007-12-24
> **Tristicus said:**
> I am putting together a new Ubuntu build, and got everything set up correctly. Well, I put the Ubuntu Gutsy Live CD in, and it won't boot.

I tried PCLinuxOS and it booted. I re-burned another CD on lowest speeds and it still wouldn't work. It went to a screen and said fatal terminal error or something on one of the installations.

Geubuntu LIVECD wont even work. it stops at HILD or something like that. So nothing is working!! FEDORA AND PCLINUXOS Work, but NO distros of Buntu. WTF?

I went in GPArted, erased the partition, and re-partitioned it, and then tried it again and same thing.
On Geubuntu it stops at a printing section when loading up or the one right before it.
Gutsy it stops when it has 4 "BARS" left to load.

HELP please!

Hi and you can try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash  before the -- then press enter. This will allow  you to see any errors.

---

### Post by Tristicus on 2007-12-24
I will try that. Thanks!

---

### Post by Tristicus on 2007-12-24
It stops at CUPSD which says COMMON UNIX PRINTING SYSTEM before it.
???
Thats weird.

---

### Post by Fatjoint on 2007-12-24
I would try the alternate-iso.  The runs the installer in text mode if there's a problem with the GUI version.

---

### Post by Lord DarkPat on 2007-12-24
That prbbly means "No Text" CUPSD is how everythign appears on the screen(I guess)

---

### Post by Tristicus on 2007-12-24
Which means....

---

### Post by Tristicus on 2007-12-24
[http://www.answers.com/topic/common-unix-printing-system](http://www.answers.com/topic/common-unix-printing-system)
This is what it is, I just don't know why it won't load or w/e.

---

