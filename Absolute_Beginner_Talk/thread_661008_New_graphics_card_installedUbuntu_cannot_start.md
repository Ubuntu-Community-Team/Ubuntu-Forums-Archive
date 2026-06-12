---
title: "New graphics card installed:Ubuntu cannot start"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by sdim on 2008-01-07
Dear friends,Happy New Year to everyone.
I've just installed a new graphics card (NVidia EN 8500GT 512MB) and everything is OK in WinXP environment.Nevertheless,when I try to use the dual boot to start Ubuntu 7.04,after it runs some checks,it says something which I don't quite understand (I didn't make a note of it) and it just stays there,in the black screen,it won't boot up.

Any ideas?

Thank you.

---

### Post by philinux on 2008-01-07
I think you'll have to use the recovery option from grub the reconfigure xorg.

sudo dpkg-reconfigure xserver-xorg

---

### Post by snickers295 on 2008-01-07
through some googleing it seems the card don't work very well with ubuntu.
could you write down what it said and post it here?

---

### Post by p_quarles on 2008-01-07
Okay, so if WinXP works, that means that you must be able to get as far as the GRUB menu. Try booting into Ubuntu's "recovery" mode. Does it still hang up if you do that?

---

### Post by OffAxis on 2008-01-07
the log file should be in
/var/log/Xorg.0.log

take a look there. If you haven't installed Nvidia's proprietary driver, or a had a different card (ati) installed, there may not be an entry for the card or your monitor in the
/etc/X11/xorg.conf file.

You can also get a driver straight from nvidia's website for your card & Linux. The install script is pretty straightforward.

---

### Post by sdim on 2008-01-07
After I choose to boot Ubuntu from the dual Boot Menu,I don't get what usually comes on,i.e.the Ubuntu logo with the orange bar filling up.Instead,I get a black screen performing some checks,and after some seconds,there is this:_"/dev/sda2 contains a file system with errors,check forced"_,so it begins checking the disc,and when 100% is completed,after some other checks have been performed,I get this message: 
_"Duplicate or bad block in use!"_, and after that:_ "Multiply claimed blocks in inode:4341763:8704000"._ and  _"Multiply claimed blocks in inode:4341805:8704000"_.
Then the system comes to the terminal (console),as it is in normal mode.Nothing happens.The same thing happens in Recovery Mode.

Can anybody help?
Thank you in advance.

---

### Post by snickers295 on 2008-01-07
> **sdim said:**
> After I choose to boot Ubuntu from the dual Boot Menu,I don't get what usually comes on,i.e.the Ubuntu logo with the orange bar filling up.Instead,I get a black screen performing some checks,and after some seconds,there is this:_"/dev/sda2 contains a file system with errors,check forced"_,so it begins checking the disc,and when 100% is completed,after some other checks have been performed,I get this message: 
_"Duplicate or bad block in use!"_, and after that:_ "Multiply claimed blocks in inode:4341763:8704000"._
This last message is displayed twice,and then the system comes to the terminal (console),as it is in normal mode.Nothing happens.The same thing happens in Recovery Mode.

Can anybody help?
Thank you in advance.
not completely sure, but it sounds like somethings wrong with the  filesystem (correct me if I'm wrong), does anyone know how to repair it if that is the case?

---

### Post by sdim on 2008-01-08
I even tried connecting the screen to the old motherboard Graphics card jack,but nothing happened there,either.
Would it be better if I erased the whole Ubuntu partition and re-load Ubuntu 7.10 as a fresh installation?
I use Easeus Partition Manager through WinXP,so I could erase the Ubuntu partition through this.

---

### Post by caravel on 2008-01-08
> **sdim said:**
> After I choose to boot Ubuntu from the dual Boot Menu,I don't get what usually comes on,i.e.the Ubuntu logo with the orange bar filling up.Instead,I get a black screen performing some checks,and after some seconds,there is this:_"/dev/sda2 contains a file system with errors,check forced"_,so it begins checking the disc,and when 100% is completed,after some other checks have been performed,I get this message: 
_"Duplicate or bad block in use!"_, and after that:_ "Multiply claimed blocks in inode:4341763:8704000"._ and  _"Multiply claimed blocks in inode:4341805:8704000"_.
Then the system comes to the terminal (console),as it is in normal mode.Nothing happens.The same thing happens in Recovery Mode.

Can anybody help?
Thank you in advance.

Looks like file system corruption.  Have you done **fsck** from the terminal?  If it persists I'm not sure what you can do except reinstall. :confused:

---

### Post by snickers295 on 2008-01-08
> **sdim said:**
> I even tried connecting the screen to the old motherboard Graphics card jack,but nothing happened there,either.
Would it be better if I erased the whole Ubuntu partition and re-load Ubuntu 7.10 as a fresh installation?
I use Easeus Partition Manager through WinXP,so I could erase the Ubuntu partition through this.
you could just put the ubuntu install cd in there and format the partition there.

---

### Post by sdim on 2008-01-08
I've already done that once in the past and by some mistake it ruined my WinXP installation,as well.
Maybe I'm not capable of doing it correctly,so I think I'll proceed with a fresh 7.10 installation.
Many thanks to all the people who answered.

---

### Post by snickers295 on 2008-01-08
no problem.

---

