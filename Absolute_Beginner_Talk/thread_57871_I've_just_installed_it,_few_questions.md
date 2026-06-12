---
title: "I've just installed it, few questions"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by yootje on 2005-08-18
I've just installed Ubuntu, the installation went pretty smoothly, the only thing is I get a IO-APIC error when I boot Ubuntu (he can't find timer xxxx), no troubles with it, yet.

Well, I have a couple of questions.

I live in the Netherlands and I choose for a us keyboard lay-out, but this is wrong, I can't type the at and when I type ), I actually type '. How can i fix this and what should I configure (can't find the question sign :P )

I have installed version 4.10, but it was updated when I installed it. Do I have version 5.04 now

Where did I configured my freakin root password :P Ubuntu asked me to type a username, then an other username  :-? and than a password. But when I try to su, nothing works.

I use Firefox and browsing works fine, but I can't download anything. Anyone who has a suggestion

When these questions are answered I think I can install the Nvidia drivers :)

Thank a lot in advance!

---

### Post by heimo on 2005-08-18
Hi! Welcome, new Ubuntu user.

If you installed 4.10, Warty, the upgrade during install was only to update to latest Warty packages. I strongly suggest upgrading to Hoary. This will probably make your Firefox and power management* problems go away.

About su/sudo: 
[https://wiki.ubuntu.com/UsingSudo]("https://wiki.ubuntu.com/UsingSudo")

Upgrade:
[https://wiki.ubuntu.com/HoaryUpgradeNotes]("https://wiki.ubuntu.com/HoaryUpgradeNotes")


*) I always mix ACPI and APIC. Anyway. :)

---

### Post by yootje on 2005-08-18
An other questions: do I have to mount my other (fat32) partitions before I can reach them, or is this automatically done

If zo, in which directory

Thanks!

---

### Post by heimo on 2005-08-18
[QUOTE=yootje]An other questions: do I have to mount my other (fat32) partitions before I can reach them, or is this automatically done

If zo, in which directory

Thanks![/QUOTE]

I'm not sure about that. You can run *mount* to check which partitions were mounted and /etc/fstab file for which partitions are mounted automaticly, and *fdisk -l* to list your disks and partitions. I suggest leaving this until upgrade is done.

---

### Post by yootje on 2005-08-18
[QUOTE=heimo]Hi! Welcome, new Ubuntu user.

If you installed 4.10, Warty, the upgrade during install was only to update to latest Warty packages. I strongly suggest upgrading to Hoary. This will probably make your Firefox and power management* problems go away.

About su/sudo: 
[https://wiki.ubuntu.com/UsingSudo]("https://wiki.ubuntu.com/UsingSudo")

Upgrade:
[https://wiki.ubuntu.com/HoaryUpgradeNotes]("https://wiki.ubuntu.com/HoaryUpgradeNotes")


*) I always mix ACPI and APIC. Anyway. :)[/QUOTE]
Me too ;)

Thanks a lot! I'm currently doing the upgrade, I will see what is fixed and what not :)

---

### Post by yootje on 2005-08-18
is there a way to do the upgrade in pieces? My computer freezes after a while, and this is not an Ubuntu problem, but a hardware problem, but when I could pause the process it'll do fine.

---

### Post by heimo on 2005-08-18
Hmm... Maybe. But the real solution would be to find out the cause of hangups and fix it. How often does it freeze? Do you get past the downloading of packages?

---

### Post by yootje on 2005-08-18
[QUOTE=heimo]Hmm... Maybe. But the real solution would be to find out the cause of hangups and fix it. How often does it freeze? Do you get past the downloading of packages?[/QUOTE]
I would love to fix it, I think the temperature is just too high, but I'm not sure. (Gentoo had the same problem, Windows XP too)

But right now I have no money and no time to fix it.

It goes beyond the point of downloading. I do it the apt-way, and sudo apt-get update was fine, then I typed sudo apt-get dist-upgrade, and that went fine for a long time. Everything was downloaded, configured also I believe, but I don't know for sure when it froze, I minimilazed (how do you spell that? :P ) the terminal and when I came back I couldn't do anything.

I will try it again tomorrow, when the computer is a bit cool again, but it would be nice if I could just pause the process after all the stuff was downloaded,

---

### Post by heimo on 2005-08-18
You can give -d flag for apt-get to download only. For example:  ```
apt-get -d upgrade
```

Packages are cached anyway (in /var/cache/apt/archives/) so you can just repeat apt-get upgrade or apt-get dist-upgrade untill it goes through. Apt-get is very good at recovering from partial install. Other good commands:
 ```
apt-get install -f  (tries to fix broken packages)
dpkg --configure -a (configure unconfigured packages)

```

---

### Post by yootje on 2005-08-18
[QUOTE=heimo]You can give -d flag for apt-get to download only. For example:  ```
apt-get -d upgrade
```

Packages are cached anyway (in /var/cache/apt/archives/) so you can just repeat apt-get upgrade or apt-get dist-upgrade untill it goes through. Apt-get is very good at recovering from partial install. Other good commands:
 ```
apt-get install -f  (tries to fix broken packages)
dpkg --configure -a (configure unconfigured packages)

```[/QUOTE]
So I can do sudo apt-get update , a few minutes later apt-get -d dist-upgrade and than a few hours later sudo apt-get dist-upgrade?

*looking for apt documentation now :)

---

