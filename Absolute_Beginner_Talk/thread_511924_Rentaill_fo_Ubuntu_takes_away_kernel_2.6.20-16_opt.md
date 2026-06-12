---
title: "Rentaill fo Ubuntu takes away kernel 2.6.20-16 option"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2007-07-28
Hi,

I am a very new Ubuntu user.  I am having the following problem:

I've needed to reinstall Ubuntu several times on my computer because I've messed up settings while experimenting (trying tog et Beryl to work with my ati card, etc.)

Anyhow, I just completed the fifth complete reinstall off of the live cd, reformatting my /home /swap and / partitions.  Now, when the computer loads and Grub comes up (for the dual boot with Winxp)  I don't have the option of selecting kernel 2.6.20-16 anymore.  Only kernel 2.6.20-15 is available.  What happened to kernel 2.6.20-16?  Can I get it back?

Any suggestions?

Thanks very much. I'm looking forward to using ubuntu! (I feel abd I can't really use Beryl or Compiz but XGL with the proprietary drivers has been buggy for me...so I guess I'll wait until ATI releases better drivers (Will they?!)...

Thanks again. All help welcome with Kernel issue.

---

### Post by por100pre1 on 2007-07-28
Try updating first:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tepidarium on 2007-07-28
> **por100pre1 said:**
> Try updating first:

```
sudo apt-get update && sudo apt-get upgrade
```

Yeah!  I updated and now I get the newest kernel. Thank you for your help!

---

### Post by por100pre1 on 2007-07-28
Glad to help, by way, welcome to the forums.

---

### Post by Happy_Man on 2007-07-28
Just keep going, and install all the updates. One of those is the update to the new kernel. :D

EDIT: Wow, I'm late. Ignore me.

---

### Post by por100pre1 on 2007-07-28
> **Happy_Man said:**
> 
EDIT: Wow, I'm late. Ignore me.
 
You are a hard worker, Happy_Man. You don't deserve to be ignored, you deserve to be respected. Thanks for helping! :)

---

### Post by ugm6hr on 2007-07-28
> **tepidarium said:**
> I've needed to reinstall Ubuntu several times on my computer because I've messed up settings while experimenting (trying tog et Beryl to work with my ati card, etc.)


If you need to keep reinstalling - I would suggest you keep a backup of /var/cache/apt/archives each time before you reinstall - then copy to the same location after the reinstall.

That way, when you Update or try to install programs following the reinstall, you won't have to download them all from the archives again.

Might save a bit of time (and broadband bandwidth) if you're still messing with Beryl etc.

---

