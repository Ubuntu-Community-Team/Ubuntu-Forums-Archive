---
title: "[SOLVED] 7.10 not letting me install anything."
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by nar57981 on 2007-10-20
Alright, I just backed up everything I cared about, and reinstalled linux on my computer. I got my wireless working (using the bcm43xx-gtk-installer-0.2.2) but when I go to add/remove programs it tells me that I have an incompatible computer to install the programs. The one thing that it did let me download, and it looks like it's not even working is the ad blocker for firefox.
At first I thought it was because I the drivers I was trying to install for my graphics card weren't compatible, But, I tried to install AbiWord, and it didn't work so I'm guessing that something is wrong.

I don't think it has anything to do with my wireless drivers, because I tried direct linking my computer into the router, and it still didn't install anything.
Does anyone know what might be wrong? Tell me if you need more info.

Thanks

---

### Post by FunkyJack on 2007-10-20
Try in terminal:

```
sudo apt-get update
```

---

### Post by ddrichardson on 2007-10-20
And post the *exact* error message.

---

### Post by anewguy on 2007-10-20
I am having a similar problem when going through add/remove under applications.  In 7.04 I could install KDE games in Ubuntu (i.e., gnome desktop) and it would install the needed libraries, etc..  Now in 7.10 I get the following:

Canonical Ltd. provides technical support and security updates for Kolf
Kolf cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

This is after having done apt-get update.  I assume there is some reason for not wanting to allow KDE apps in gnome anymore (perhaps it the new gnome), but this is disapointing even for something as stupid as miniature golf game.

---

### Post by nar57981 on 2007-10-20
Alright I just updated and I'm still getting the message.

> **ddrichardson said:**
> And post the *exact* error message.

AbiWord Word Processor cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

Everything used to be working fine in 7.04

---

### Post by ddrichardson on 2007-10-20
Try [this.]("http://ubuntuforums.org/showthread.php?p=3572152")

---

### Post by nar57981 on 2007-10-20
Thanks a lot, that got it all working.

---

### Post by anewguy on 2007-10-20
I wanted to post back here as soon as I figured out what was going wrong.  For my case, the repositories were all unchecked.  Just checking the 3 normally used corrected the problem.  Perhaps this is what is in the thread pointed to above - I just never followed it yet  since as soon as I found my problem I just wanted to post here.:)

---

### Post by Daveth on 2007-10-20
can you please mark your post as "solved" then. Pleased it worked out.

---

