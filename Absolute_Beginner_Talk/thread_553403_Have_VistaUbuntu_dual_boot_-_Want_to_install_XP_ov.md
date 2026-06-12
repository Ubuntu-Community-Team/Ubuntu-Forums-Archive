---
title: "Have Vista/Ubuntu dual boot - Want to install XP over Vista. Possible?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by StephanW on 2007-09-17
Good evening,

I currently have Vista/Ubuntu dual boot on my machine.  I'm getting annoyed by Vista so I want to reinstall XP on my machine, over the Vista partition.

Is this possible to do without having to reinstall both XP and Ubuntu?

-Stephan

p.s. I'm only keeping Windows for school, not because I want to.

---

### Post by oilchangeguy on 2007-09-17
should be possible. you'll need to reinstall grub.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by prcm311 on 2007-09-17
Probably... but you'll have some interesting boot screens.  Right now you must have both a Vista and an Ubuntu, this may add a third.  You may want to do some research into editing Vista's boot screen (as well as XP's and Ubuntu's) to simplify things.  Otherwise to boot to Ubuntu will take three menus.

How are your drives setup?  One drive three partitions?  More than one physical drive?  What OS is on the master?  Or do you have cable select on?

---

### Post by bodhi.zazen on 2007-09-17
Yep, go ahead and install XP

You will need to re-install GRUB after :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by oilchangeguy on 2007-09-17
> **prcm311 said:**
> Probably... but you'll have some interesting boot screens.  Right now you must have both a Vista and an Ubuntu, this may add a third.  You may want to do some research into editing Vista's boot screen (as well as XP's and Ubuntu's) to simplify things.  Otherwise to boot to Ubuntu will take three menus.

How are your drives setup?  One drive three partitions?  More than one physical drive?  What OS is on the master?  Or do you have cable select on?

do you dual boot? because you don't have multiple boot screens. one screen multiple choices.

---

### Post by StephanW on 2007-09-17
It's on a laptop, so right now I have two seperate partitions on one drive.  Vista on one partition, ubuntu on the other.  What I want to do is install XP over the Vista partition so that I only have XP/Ubuntu dual boot (2 partitions).

So, after installing XP over the Vista partition - I could reinstall GRUB using the Ubuntu CD?

---

### Post by bodhi.zazen on 2007-09-17
> **StephanW said:**
> So, after installing XP over the Vista partition - I could reinstall GRUB using the Ubuntu CD?

Yes, see the  link I gave you. It is a snap.

---

### Post by oilchangeguy on 2007-09-17
> **StephanW said:**
> It's on a laptop, so right now I have two seperate partitions on one drive.  Vista on one partition, ubuntu on the other.  What I want to do is install XP over the Vista partition so that I only have XP/Ubuntu dual boot (2 partitions).

So, after installing XP over the Vista partition - I could reinstall GRUB using the Ubuntu CD?

yes

---

### Post by StephanW on 2007-09-17
bodhi.zazen - Thanks for the link! Helped me out a bunch.

---

