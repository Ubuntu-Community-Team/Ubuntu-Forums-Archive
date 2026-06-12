---
title: "grub help needed please"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by heyzeus on 2006-09-21
I have a dual boot xp and ubuntu. I recently re-installed xp and can no longer boot into it from grub. I can get into ubuntu no problem.
  It appears to boot from root (hd0,1) which is where xp is and was when I bought the computer. Here's what I get when I choose to load xp from grub:

root (hd0,1)
   filesystem type unknown 0x7
save default
makeactive
chainloader +1

ntldr is missing
   press ctrl alt del to restart

sda2 (hd0.1) is where xp is.
  I found the ntldr and ntdetect and boot.ini etc. They exist on sda1 which is a Dell utilities partition. I just don't know how to use/change grub so it can find the ntldr

---

### Post by indytim on 2006-09-21
You might want to try the following as one approach to Grub repair (nice to have iregardless).

[http://freshmeat.net/projects/supergrub/]("http://freshmeat.net/projects/supergrub/")

Good Luck,

IndyTim

---

### Post by heyzeus on 2006-09-21
Thanks tim. That does look pretty handy.

I assume that I should just be able to use some terminal commands to point grub in the right direction of my ntldr.

Thanks,
heyzeus

---

### Post by heyzeus on 2006-09-21
I have a dual boot xp and ubuntu. I recently re-installed xp and can no longer boot into it from grub. I can get into ubuntu no problem.
It appears to boot from root (hd0,1) which is where xp is and was when I bought the computer. Here's what I get when I choose to load xp from grub:

root (hd0,1)
filesystem type unknown 0x7
save default
makeactive
chainloader +1

ntldr is missing
press ctrl alt del to restart

sda2 (hd0.1) is where xp is.
I found the ntldr and ntdetect and boot.ini etc. They exist on sda1 which is a Dell utilities partition. I just don't know how to use/change grub so it can find the ntldr


I guess what i'm wondering is:
 If where it reads "root (hd0'1)", should actually read "root (hd0'0)" which I believe is sda1(Dell utilities) where the ntldr etc. is located. If so how do I change that?

---

### Post by bodhi.zazen on 2006-09-21
If windows is on sda2 then grub should read (hd0,1)

**Watch the commma.**

To edit your grub menu:```
sudo gedit /boot/grub/menu.lst
```

---

### Post by undertherift on 2006-09-21
Assuming you can boot your linux?

In ubuntu all this info lives in /boot/grub/menu.lst (Scroll to the bottom, it'll be there).

I'm not sure exactly what the problem is - Why can't you just type..? (when the grub menu comes up, hit C to go to the command line).  

```

root (hd0,1) <- if this is where the WinXP resides
makeactive
cahinloader +1
boot

```

If this does work, then change it in /boot/grub/menu.lst.

If this doesn't work, i would suggest getting your XP cds, loading the recovery console, running fixboot,or fixmbr so that you can log back into your windows.  Then use a live cd to reinstall grub on to your MBR. But someone else may have a better solution than this - this is what i've done in the past.

Good luck

---

### Post by heyzeus on 2006-09-21
Thanks guys, I got it working.

All I had to do was change root (hd0,1) to root (hd0,0) in menu.lst and grub could find the ntldr in the 65mb Dell utilities partition to boot up windows.

I had already tried fixboot and fixmbr then reinstalled grub but, that hadn't worked. Grub was looking for the ntldr where it didn't exist. 

Thanks again

---

