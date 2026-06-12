---
title: "Ubuntu won't boot - &quot;apt-get is not installed.  To install it...&quot;"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Lexyboy on 2007-08-07
Dear All,

Not sure what I did, but this morning my Feisty Box won't boot - it comes up with a list of programs which apparently aren't  installed, finally "apt-get is not installed.  Use 'apt-get install apt' to install it"

D'oh!

Anyway, it seems nothing's been removed - programs are there in /usr/bin/, but ubuntu isn't recongnising them.  Can anyone help out?  I suspect that it's to do with my path not being set correctly, but I don't know what's causing this (i.e. is there something more fundamental causing it), or how to fix it...

```
echo $PATH
/bin/:/sbin
```

Please help! :(

---

### Post by atomkarinca on 2007-08-07
try
```
sudo aptitude install apt-get
```
it may work.

---

### Post by Lexyboy on 2007-08-07
Thanks, but I already tried ```
/usr/bin/apt-get install apt
``` which told me it's already installed.  It seems everything's still there (including the directory of installed programs), but that $PATH isn't set.

How would I go about setting what $PATH is (permanently, not just for one boot)?  On the computer I'm using at the mo it is "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11" so I'm obviously missing a few...

---

### Post by hessiess on 2007-08-07
you may need to run fsck, i had a simaler problem

---

### Post by lemmy999 on 2007-08-07
Don't know if this will help but i had a similar problem recently. My solution was to revert to a previous version of the kernel in Grub, boot using recovery mode. then "startx" and install updates within the GUI.

Seems to have worked:)

---

### Post by FuturePilot on 2007-08-07
Yes. Run fsck. I've seen other people have that error and fsck fixed it.

---

### Post by Selage on 2007-08-07
Had the same problem, you can continu booting if you typ exit and hit enter (buts thats not the problem)

Mine was fix by doing fsck -l

not sure about the command, but you got an idea

---

### Post by Selage on 2007-08-07
Lol, 3ppl saying do fsck within the hour, so do it already :)

---

### Post by Lexyboy on 2007-08-07
Thanks everyone, will try fsck when I get back from work.  I thought fsck had to be run on unmounted partitions though, and presumably / is mounted when I get kicked out of startup...

Will post back when tried...

---

### Post by Lexyboy on 2007-08-07
Well... tried fsck -l with no luck, so exited and read up a bit more, so thought I needed to do it from the livecd, which didn't work, but got another fsck command, so rebooted and... it just worked!  Obviously sorted itself out by itself after I exited the first time (I hope...).

Thanks anyway!

---

### Post by hessiess on 2007-08-07
is it dual booted with windows? my problem fixed itself in the same way, but it cept cumming back untill i wiped the windows partition

---

