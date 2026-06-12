---
title: "About to dual boot ubuntu and vista"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by nanajeebus on 2007-07-18
I'm about to install Ubuntu, but before I go any further I just want to make sure I haven't made any horrible mistakes here.

I set up an extended partition with 15 gigabytes of space, then a logical partition with 1 gigabyte of space using gparted. I chose the manual partition option and set the 1 gigabyte one to be used as swap and the 15 gigabyte one as "ext3" with it's mount point as "/".

The migration assistant didn't show anything for me to migrate, and now I'm at the "ready to install screen." Going from [this]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") link it says " "Windows Vista/Longhorn (loader)" should be under the migration assistant, regardless of whether or not it found a user account to migrate. However, on mine it doesn't say anything. Should I be okay to install anyways, or did I do something wrong?

Just wanted to ask before I potentially ruined my computer.

---

### Post by expatCM on 2007-07-18
I have never seen Vista and so cannot be sure that the migration assistant is always going to find existing account information but....  it is only a "nice to have" feature, it is not essential.   However, if you go ahead and for some very unusual reason have a total disaster and everything dies, it is not impossible to rebuild the Windows file allocation table (and not difficult) and get Windows back to normal operation.

The probability of having such a disaster is very very slight.

---

### Post by Happy_Man on 2007-07-18
Well..... you did use Vista's shrinking utility, right? If you did, and checked the right option, then everything should be OK. Just to be sure, exit the installer and run it again, triple-checking every step to make sure you're doing it right. At least that way, it won't be your fault if something blows up. :p

But you'll be fine....

---

### Post by nanajeebus on 2007-07-18
Ah, okay. Just trying to be absolutely sure I didn't make a huge "no no" during the installation process.

Thanks for the reply, and I'll get on with the installation. :)

> **Happy_Man said:**
> Well..... you did use Vista's shrinking utility, right? If you did, and checked the right option, then everything should be OK. Just to be sure, exit the installer and run it again, triple-checking every step to make sure you're doing it right. At least that way, it won't be your fault if something blows up. :p

But you'll be fine....

Yep, used the shrinking utility. And I've ran through installer about five times making sure I set everything right. I'm so overly cautious. >.<

---

