---
title: "Need Help Install Xubuntu on an old iBook."
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by Hansophobia on 2008-07-31
My father owns an old iBook. After converting 2 of our 3 computers to Ubuntu or one of it's derivatives, I must say that we are extraordinarily happy with our new set up. Upon my discovery of Xubuntu, we have decided to try to get it to run on this old iBook. However, when I put Xubuntu into the drive of the computer, and restart it (or completely shut it off and then turn it on), it never even boots of the disk and is leaving me (and my family) quite puzzled. Does anybody know why this is. Should I instead be installing Ubuntu and then using sudo apt-get xubuntu-desktop (or something like that). I would rather have just xubuntu be on the system, as it is quite old and I am not sure how well it would run off that, as well as I don't have any Ubuntu disk on me (I gave the ones I previously used away) and my internet is too slow for almost all of these downloads.

If anybody has any help, it would be greatly appreciated!

---

### Post by mkvnmtr on 2008-07-31
You say the IBook is very old. Maybe you should give some information about the machine like speed and memory. Tell us how far it got in the boot process. On my IBook that is 4 or 5 years old I could not get 8.04.1 live disk to finish booting. It loaded the kernel and then went black. It was booted but had no splash screen so I could do nothing. I found that when it first identified the disk, in my case Ubuntu live disk 8.04.1 I needed to press tab. Then a page comes up with options to type in to boot. Pick the one you think has the most chance for success and type it in. You will see it at the bottom of the page. It is like using terminal. When you finish press enter. Give it plenty of time and if no success restart and return to the same place and try another entry. If you are not getting to the point your disk tells you what disk it is the disk may be bad. If you have Ubuntu opn other machjines you know how to burn a disk correctly. Good luck.

---

### Post by gabric098 on 2008-08-01
My 2004 ibook G4 boots only with this option:
live-nosplash-powerpc video=ofonly.
As mkvnmtr suggested you, try to type
> live-nosplash-powerpc video=ofonly
at the boot prompt.

G.

---

