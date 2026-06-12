---
title: "Still new to Ubuntu! :)"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by U2XS on 2006-12-06
Hi Guys, I have tried to install Ubuntu Linux, Xubuntu Lunux and Mandriva Linux on several occasions across 3 different hard drives and it hangs every time! ](*,)  ](*,) 

This is very frustrating because I can only imagine that I am doing something wrong or that there is something wrong with my system.  Any thoughts/ideas would be appreciated.  Thanks

---

### Post by Bachstelze on 2006-12-06
It hangs... When ? What is the last thing you see ?

---

### Post by ferg on 2006-12-06
My 2 cents on this is that I got a cover DVD from a Linux mag of some sort. It had two distributions on it and neither would get very far in the install. Just hung about 5% in :S . Downloaded ISOs and burned them... worked fine. 

No idea if this applies to you or not but it might do. :)

---

### Post by igknighted on 2006-12-06
I would recommend re-burning the ISO's at a low speed, like 4x.  I would guess that there are errors on the CD.  Did you check the CD's before install?

---

### Post by Iowan on 2006-12-06
Different distros on different HD's with the same problems *does* sound like hardware issues - on *what kind of machine* are you trying to install?

---

### Post by U2XS on 2006-12-07
Hey Guys, thanks for all of the tips.  To answer your questions in order

It hangs at different points of different versions.  IE on Mandriva it hangs about 10% into it, on Ubuntu at about 90% and Xubuntu about the same.

I downloaded Xubuntu and Ubuntu from the websites and burned the ISO myself.  I Downloaded Mandriva from a torrent and also burned the ISO myself.

I did not check all CDs for errors, but I do remember checking one - no errors found.

My comp specs are Intel (R) Pentium (R) CPU 2.66 GHz CPU 2.67 GHz 512 MB of RAM.  (1) 4 GB Hard Drive (1) 20 GB Hard drive & (1) 40 GB hard drive.

_________________________________________________________

Since it may be a hardware error, I had another question.  Would it make sense to install this on another computer and then swap hard drives?  I thought it might create a conflict, so I didn't even try it, but maybe it would be better.  Any thoughts?

---

### Post by xpod on 2006-12-07
You could try the alternate cd`s for installing but it does sound weird ALL of them refusing to work with your specs.

I`d definetly try the alternate cd though..

Good luck

---

### Post by igknighted on 2006-12-07
Unless the computer had the same hardware you would probably have issues with that.  Issues that could be fixed most likely, but not a pleasent way to start.  On second thought however, if its a HD issue, trying to install to that HD on another comp could isolate it so you would know what the problem is.  Otherwise, my next guess would be a faulty CD drive.  If you are sure it isn't the ISO's, try isolating the problem by changing (if you can) the HD and CD drive.  Finally, there is a site (I can't remember what it is but a google search might turn it up) that will give you a very small iso that boots into an installer (I used this for SuSE, you could give that a try or maybe they have Ubuntu as well) and then the install proceeds from internet sources.  Might be worth a shot if the HD isn't the issue.

---

### Post by bulldog on 2006-12-07
I should try to install with only the disk connected which you want to install on.
Can't give any guarantee but you can give it a try.


Off topic,
Nice head,master xpod,how you're doing?
Hope all is well with the 'wild bunch':D

---

### Post by Tomosaur on 2006-12-07
One possibility is that your hard disk has it's boot sector protected. This would mean that when the bootloader is being intalled, an error will occur. Shoddy programming will cause this error to crash your system, and it should really be caught by the installer. This isn't definately what is happening, just something you may want to look into. You may be able to unlock the boot sector so grub/lilo/whatever can be installed.

---

