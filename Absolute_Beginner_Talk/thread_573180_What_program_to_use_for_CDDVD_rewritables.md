---
title: "What program to use for CD/DVD rewritables?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-10-11
What program to use for CD/DVD rewritables?
I've tried GnomBaker but that couldn't delete or format the DVD rw.
I tried the built-in Ubuntu CD/DVD writer it couldn't delete or format DVD rw either.

So I went back to Windows XP and used this open-source burner that Aysiu recommended some years back in his tutorials.  And deleted and formatted the DVD rw.
[http://cdburnerxp.se/](http://cdburnerxp.se/)
Then when I try to use that DVD rw disc in Ubuntu it says something about not being able to mount it.
When I try some other DVD rw disc with the same brand that have already been written on it popups on the Desktop just fine.

> [COLOR="Red"]Cannot mount volume.
Invalid mount option when attempting to mount the volume.[/COLOR]



So what burner program handles DVD rw discs best?
GnomeBaker didn't work nor did K3b.

---

### Post by wpshooter on 2007-10-11
I don't use DVD but CD-RW media.  I know that there is an erase CD-RW on the menu in K3b that works just fine.  

I don't remember right off hand but have you looked to see if there is an erase function for DVDs just below the one for CD-RW ?

---

### Post by Gazneth on 2007-10-11
K3b or Brasero should do what you need, they are both full featured burning programs.:)

---

### Post by jingo811 on 2007-10-11
I found the solution to the problem.  I went into Windows XP and used the burner that Ubuntu officially recommends for burning Ubuntu isos.
[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)
Then I used Infrarecorder to format the DVD rw discs that wouldn't want to be mounted or formatted in Linux.  Now you don't get that error message when you put in the disc.  But it will still give you that error if you try to open up "/cdrom" in Nautilus.

That's OK just write some small file to the DVD rw with Graveman and things will be OK to Ubuntu again.

---

### Post by rahimveron on 2007-10-11
Just install K3B as it can format both CDrw and DVDrw. Dont miss this great burning suite, K3B. Install it from Synaptic.
If you are double clicking on a blank dvd then that would give an error as it is empty. Burn it through K3B and then you can easily access it. 
K3B has never failed me.

---

