---
title: "Installation problems - Edubuntu"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by hodad on 2007-02-07
Hello, 

I'm trying to install Edubuntu on an old pc for my kids.  PC stats:

Pentium III 450
1998 Asus P2-B
10 GB (i think) hard drive
327,680 KB memory

Install goes OK until near the end, when it hangs up in "software install".  Asks me if I want to continue, which I do.   I get to the "grub" install, and get get "grub package failed to install into /target/.  Then I get to "lilo" and get the same thing.   

Am i running out of HD space or something?  Have done a md5hash check on the .iso file and it's good.

Any help would be appreciated!  THanks

---

### Post by taurus on 2007-02-07
How fast did you burn the ISO image?  Try to burn it again at a slower speed like 4x.  And before you go into install, you can check the CD to make sure it's good.

---

### Post by hodad on 2007-02-07
I ran md5sum to verify checksum, and it was OK.  As a matter of fact, I tried installing both 6.10 and 6.0 (both clean copies).  Come to think of it, I ran it before burning the CD's, though.  I'll try md5sum on the "burned"copies, to see if they're OK.

THanks!:)

---

### Post by rccharles on 2007-02-08
> **hodad said:**
> 

Install goes OK until near the end, when it hangs up in "software install".  Asks me if I want to continue, which I do.   I get to the "grub" install, and get get "grub package failed to install into /target/.  Then I get to "lilo" and get the same thing.   

Am i running out of HD space or something?  Have done a md5hash check on the .iso file and it's good.

Any help would be appreciated!  THanks

I had a similar problem with Ubuntu.  I said to complete the install without installing a boot loader.  I was able to boot with superGrub.

I didn't prove this, but I think for me it was something to do with configuring the internet connection and having a live internet connection when I was installing Ubuntu.  When Ubuntu was configuring grub, Ubuntu installer seemed to be going to the internet for grub and not finding grub.  To get Ubuntu to install without problem, I didn't configure the internet on the install.  I configured the internet after the install. Again, I am not saying this is the problem, but something strange happened.

I was able to boot the disk with superGrub.

An option would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

This wouldn't be a permanent solution, but it would get you started.


Robert

---

### Post by hodad on 2007-02-08
Robert,
Thanks for the help.  Turns out that I also am configuring a standalone (no internet access).  WIll try both of your suggestions later today.

---

### Post by rccharles on 2007-02-08
> **hodad said:**
>  Turns out that I also am configuring a standalone (no internet access). 

I had a live internet connection when I experience the problem.

Robert

---

