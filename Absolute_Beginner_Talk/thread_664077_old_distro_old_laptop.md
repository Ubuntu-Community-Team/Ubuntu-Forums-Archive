---
title: "old distro old laptop"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by happyparadox on 2008-01-10
Several years ago I downloaded Ubuntu 5.04 "Hoary Hedgehog" to a CD and then loaded it onto a Dell Latitude with 512 megabytes of ram.  The clock speed is short of 1000MHz.

Well I got great help from Ubuntu forums getting it on the machine and running but then ran into a snag with the CD player.  It won't contents of files on the CD so I pushed it aside and never got back to it. I still want Ubuntu on that machine but don't have a clue how I can resolve the issue.  I have the latest Distro on DVD and I wonder if getting it on the Dell would help resolve the issue more easily.

The "Hoary Hedgehog" OS is running fine but can't do anything like use a CD or get online.  I love this old Dell and don't need anything more as far as a laptop is concerned and I really want to make it a GNU/Linux machine.

Any ideas for the Linux illiterate?

---

### Post by Blutack on 2008-01-10
Erm...install the new one!

Gutsy is to Hoary as XP is to 3.1
Seriously.  Chances are all your issues are fixed, and the speed will not be much different (probably faster).

---

### Post by Wiebelhaus on 2008-01-10
How much ram?

Allot - [Mint]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Flinuxmint.com%2F&ei=wsKGR7KbJ6TIggTzu4ydCg&usg=AFQjCNF-_Llp72ExmBwewuJ3l0PKv5Atow&sig2=QEJ3OUbAARDC69KZoGZihw")

Alittle - [Fluxbuntu]("http://fluxbuntu.org")

---

### Post by LaRoza on 2008-01-10
Try Gutsy, Ubuntu or Xubuntu. The latest versions may have fixed the problems, in fact, I bet they did.

---

### Post by alwiap on 2008-01-10
> **LaRoza said:**
> Try Gutsy, Ubuntu or Xubuntu. The latest versions may have fixed the 
problems, in fact, I bet they did.
Yeah, I would imagine xubuntu 7.10 would work nicely.  I used it with great results on an ancient Dell a 
friend had a little while ago.

---

### Post by Blutack on 2008-01-10
I used to run ubuntu on an 800mhz P3 with 356mb of ram.
Wasn't rocket fast but usuable.  KDE was faster interestingly.

---

### Post by happyparadox on 2008-01-11
My problem right now is how to install.  The CD player isn't working with the "Hoary Hedgehog". And "Hoary" won't shake hands with my INTERNET provider so I can't download directly to that machine.

---

### Post by happyparadox on 2008-01-11
Thanks for the info so far.  I'm trying to figure out how to get the new version loaded on the laptop.  I have the live CD on my desktop to see what I can learn. I have an external hard drive for backup and thought it might be clever to install the ubuntu onto it.  Haven't gotten that far but thinking.

---

### Post by zipperback on 2008-01-11
> **happyparadox said:**
> Several years ago I downloaded Ubuntu 5.04 "Hoary Hedgehog" to a CD and then loaded it onto a Dell Latitude with 512 megabytes of ram.  The clock speed is short of 1000MHz.?

The current version of Ubuntu Gutsy 7.10 will install on that system just fine. (1ghz + 512mb ram)

If you want a lighter weight desktop you could also try out xubuntu from [http://xubuntu.org/](http://xubuntu.org/)


- zipperback
:popcorn:

---

### Post by happyparadox on 2008-01-11
Well, wait a minute I forgot some information.  The CD player in the laptop works in that it plays and will open but it wouldn't open the files on the CD. I assume that is an issue with ubuntu and the programs on the CD not getting along well.   It will play music off a CD though.

---

### Post by Casual Fan on 2008-01-11
If you're saying that you can't burn a CD to install Gutsy, then order a CD from Canonical in the mail. When it comes, change your bios settings to read the CD drive first, then pop the CD in the drive and boot.

It doesn't matter at all what Hoary would or would not do. Gutsy is light years beyond it. If you can run the Gutsy live CD, you can install it.

---

### Post by happyparadox on 2008-01-12
Thanks!  I can download it onto my Desktop PC and burn a CD.  The live CD I got with the Official Ubuntu book tells me how to make the proper adjustment to the bios. Will Gutsy overwrite Hoary or am I going to have to remove it?   

But the Hoary won't read the live CD or at least I don't know how to make that work.  So that's got me confused.

---

### Post by happyparadox on 2008-01-12
OK, I tried to boot with the live CD.  I reset bootup to start with the CD ROM and things started nicely before stopping here:

*Checking root file system...
/ contains a file system with errors, check forced.
/:
Inode 1028253 has imagic flag set.

/:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
*                     (i.e. , without -a or-p options)

*fsck failed.  Please repair manually and reboot.  Please note
*that the root file system is currently mounted read-only.  To 
*remount -n -o remount,rm/

CONTROL-D will exit from this shell and REBOOT the system.

bash: dircolors: command not found
root@(none):~ #

---

### Post by zipperback on 2008-01-12
> **happyparadox said:**
> Well, wait a minute I forgot some information.  The CD player in the laptop works in that it plays and will open but it wouldn't open the files on the CD. I assume that is an issue with ubuntu and the programs on the CD not getting along well.   It will play music off a CD though.


Does your system boot from cd and if so, does it boot the live cd correctly?

- zipperback
:popcorn:

---

### Post by happyparadox on 2008-01-12
It boots correctly on my desktop pc but on the laptop, no.

---

### Post by zipperback on 2008-01-12
> **happyparadox said:**
> It boots correctly on my desktop pc but on the laptop, no.


Ok so which computer are you trying to install this on?

-zipperback
:popcorn:

---

### Post by happyparadox on 2008-01-12
The laptop

---

