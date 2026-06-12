---
title: "Dual booted with XP, Ubuntu will no longer load"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by dhar2112 on 2007-12-02
I can boot into XP fine, but for some reason Ubuntu will not load anymore.  It's a recent development.  
Can I just write over the "bad" Ubuntu with the newest version of Ubuntu with an ISO cd?  How do I do it without corrupting Windows? 

Thx

---

### Post by werewolfzx8 on 2007-12-02
> **dhar2112 said:**
> I can boot into XP fine, but for some reason Ubuntu will not load anymore.  It's a recent development.  
Can I just write over the "bad" Ubuntu with the newest version of Ubuntu with an ISO cd?  How do I do it without corrupting Windows? 

Thx

Did you install Windows XP after Ubuntu? If so, XP wrote over your GRUB with the MBR.

---

### Post by dhar2112 on 2007-12-02
No, clean XP install first, then Ubuntu.  It was working fine for awhile.

---

### Post by werewolfzx8 on 2007-12-02
> **dhar2112 said:**
> No, clean XP install first, then Ubuntu.  It was working fine for awhile.

So you're still able to choose Ubuntu from the GRUB menu? After you do so, what happens? Do you get an error?

---

### Post by jken146 on 2007-12-02
You can just reinstall Ubuntu if you wish.  If you do so, be careful to select the right partition for / i.e. the one you used the first time.

If you don't want to reinstall, try booting in recovery mode and post here any errors you get, and we'll try to see what's wrong.

---

### Post by dhar2112 on 2007-12-02
Yes, it says something about a file error, or missing file, then it goes into what I describe as something like Windows "Scandisk."  Then, nothingness.......

---

### Post by dhar2112 on 2007-12-02
Jken, how do I reinstall?  Reboot with the ISO cd?

---

### Post by werewolfzx8 on 2007-12-02
If you don't have any really important files, and if you don't mind installing applications over again, I'd say go for a fresh install, just make sure you choose the previous Ubuntu's partition, and not your Windows partition.

---

### Post by jken146 on 2007-12-02
Yeah, boot up the live CD and repeat the installation process as you did originally.

---

### Post by Dr Small on 2007-12-02
If Ubuntu is still there, and Windows is still there, but you just can't access Ubuntu, couldn't you just repair GRUB with the Super Grub Disc and fix grub, instead of reinstalling ?

---

### Post by werewolfzx8 on 2007-12-02
> **Dr Small said:**
> If Ubuntu is still there, and Windows is still there, but you just can't access Ubuntu, couldn't you just repair GRUB with the Super Grub Disc and fix grub, instead of reinstalling ?

You could also use the Ubuntu LiveCD to repair the GRUB. Although I don't remember the exact commands.

---

### Post by dhar2112 on 2007-12-02
it says /dev/sda2 has errors, going for force check

then, at the bottom of all of the lines of diagnostics, it says "apt-get install" is not present, and gives me a command to type in "apt-get install."  When I do, nothing happens.

So, I rebooted with the newest Live CD, but nothing happens when I select "Install Ubuntu from CD."  Same for "Check CD for errors."  The CD drive just stops spinning when I select either command.  Bad burn, perhaps?

---

