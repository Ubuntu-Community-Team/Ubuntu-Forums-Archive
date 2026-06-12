---
title: "Problems burning DVD:s"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by topic58 on 2006-05-24
Hi, I got a big problem when trying to burn DVD:s. The operation very often fails. I have today enabled DMA, but still failure. What's the problem?
Before enabling DMA I tested this:
clabbe@desktop:~$ sudo hdparm /dev/hdc 
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
clabbe@desktop:~$ sudo hdparm -d1 /dev/hdc

and then I did this:
clabbe@desktop:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

Still it wont work. I have been using both Graveman and Nautilus with the same result. Tried full speed and 1x in burning. Nothing.
Anyone who can help me out here? CD-burning works fine, but not DVD. Using Graveman with DAO mode.

---

### Post by divague on 2006-05-24
I used to have problems burning cd:s, i don't remember if it was the same problem :-k , but i installed k3b and i worked fine.

---

### Post by topic58 on 2006-05-24
Tried that too. It won't work either. Why does CD:s work so nice - but not DVD:s??

---

### Post by topic58 on 2006-05-24
How come it's so much easier to burn a CD than a DVD? What's the difference more than the amount of data they can store?

---

### Post by mostwanted on 2006-05-24
Different file-system, different driver procedures.

---

### Post by topic58 on 2006-05-24
Hey, someone out there who have a clue? What am I doing wrong? Any settings? Using Breezy and waiting for Dapper to come.

---

### Post by patrick295767 on 2006-05-24
I solved in the past burning with my DVD hardware via : 
  
Using K3B
and when burning DVD, I selected : IGNORE
  
That can help you, Let me know !  
  
Greetz

---

### Post by topic58 on 2006-05-24
I was able to burn a DVD-R in k3b using ignore speed. But I could not open it after. BUT I was able to open it and watch it in my laptop. (?)

---

### Post by patrick295767 on 2006-05-25
Depends on the quality of the hardware to RE-read it !! (even on same DVD device)
  
Also, is the IGNORE successfully working in order to BURN ??
do you now get all time with k3b burning with IGNORE option : "Burnt Successfully" ??
  
that's really amazing linux for burning dvd (k3b & ignore & via nfs network even)
you can watch movies, burn dvd ... do anything you want : my burning never fails !

greetz

---

### Post by finite9 on 2006-08-15
Ubuntu 6.06 (not upgraded from flights) amd64 on Acer Aspire 5021WLMi laptop with dual-layer 16x DVD burner in-built.  Have latest updates from main repository and latest kernel, but I use 2.6..15-25-amd64-k8 kernel not -26 kernel.

I burn CDs no probs whatsoever in Gnomebaker.
I cannot burn DVDs at all, nor can I import previous sessions from a multisession DVD.  No difference if it's DVD-RW or DVD+RW.

I get an error when trying to burn a new DVDRW disc with the error everyone else is reporting.

For starters, will those people who keep recommending K3B cease and desist!  I realise that you all mean well, and are only trying to help, but I have chosen Gnomebaker for a reason and I want to use that app. not K3B.  I don't want a load of Qt libs on my system just because one app needs them.

Seems like this is a big issue, I don't have a fix, but lots of threads are suggesting:

use latest kernel with all patches/updates
run Gnomebaker with SUID or gksudo
always use BurnFree
DMA must be enabled
& lastly make sure theres enough space in /tmp for an image of the contents to be burnt on the DVD disc.

Well, going off the other posts in this thread, it seems like there are major compatibility problems with the kernel and cdrecord, and cdrecords homepage says as much.  Woould be nice if some guru could post a workaround though so we can get this working until its fixed for real.

---

### Post by finite9 on 2006-08-18
Turns out I was mistaken big-time about not being able to burn DVDs :( Sorry.

I can burn CD, CD-RW, CD-RW multisession, DVD-R, and DVD+R, with Gnomebaker.

I cannot import a ession from a DVD-RW - I get errors.  Obviously this means I cannot burn a multisession DVD-RW disc.

I have heard that programs that use other methods (not growisofs) to burn DVDs work fine, like Nero for Linux for example, but I have not tested.

---

