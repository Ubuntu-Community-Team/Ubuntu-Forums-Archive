---
title: "Wanting to use Ubuntu, but scared about uninstalling"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Romoko on 2007-10-14
Hey there! I'm very excited about Ubuntu! And I have downloaded, and burned to a disk. Then I got it all worked out, and did a Live CD boot up, just to get a little taste. LOVED IT! 

NOW! I do have one problem, I'm running on a Asus A8j with vista. And I have heard some horror stories about uninstalling ubuntu if I don't like it. BUT I don't have a Vista OS disk. I do have however a Recovery DVD from ASUSTeK. Would this be able to do the same thing?

Also, I do have a Operating System CD from my dell, a Microsoft Windows XP, would this be able to repair my Vista from GRUB? 

Either way, let me know!

Thanks a ton!
~Romoko

[Specs] 
Asus Notebook, A8
Inter Duel Core Processor 2.0 Ghz
2 Gigs of Ram
Vista Business
NVIDIA Go 7700 512 dedicated ram

---

### Post by HermanAB on 2007-10-14
Defragment the Vista drive and partition the disk down the middle BEFORE installing Ubuntu into the now freed up space and all should be well.

---

### Post by Romoko on 2007-10-14
Either I don't understand you, or you don't understand me. From what I gather, you want me to defrag. But It's not a matter of free space, I have plenty of HD left. I just don't want to get in a situation where **GRUB wont let Vista start up** (once you've uninstalled Ubuntu)

---

### Post by -grubby on 2007-10-14
if you want to fix the master boot record if you uninstall Ubuntu than you can always boot up a windows CD and go to repair and type "fixmbr"

---

### Post by Sef on 2007-10-14
Read [Psychocats Ubuntu]("http://psychocats.net/ubuntu/index.php") before installing.  

With Vista, use its partitioner to shrink the partition that it is on.

---

### Post by Romoko on 2007-10-14
> **nathangrubb said:**
> if you want to fix the master boot record if you uninstall Ubuntu than you can always boot up a windows CD and go to repair and type "fixmbr"

I don't have a windows CD (If you're talking about a window OS), And yes, I've read the READ FIRST section, and it doesn't quite answer my question. 

I do have a Asustek Computer Recovery CD, will I be able to use that instead?

---

### Post by Frak on 2007-10-14
> **Romoko said:**
> I don't have a windows CD (If you're talking about a window OS), And yes, I've read the READ FIRST section, and it doesn't quite answer my question. 

I do have a Asustek Computer Recovery CD, will I be able to use that instead?
Yes, a Recovery CD is, in a sense, just another Vista disc.

---

### Post by Romoko on 2007-10-14
Okay, I just booted my laptop up with my recovery disk, and got three options. 

1) Partial Restore of initial partition. 
2) Full HD Restor
3) Install Missing Diver partition

Would any of these options work? 

Also, I found this at : [http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE]("http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE")


"To replace Grub's MBR code with the equivalent code for NTLDR and make the MBR point directly to Windows like it used to, you just use the same software you used when Windows was installed in the first place. This will overwrite GRUB's version of the 'IPL' in your MBR (or 'boot sector'), and  replace it with the Windows version again.
The way to do that is very simple, exactly the same way you did it the first time. (Remember?)
You just re-install Windows....Well, that is one way to do it, but it will take you a while. There are a couple of faster ways..."

---

### Post by Frak on 2007-10-14
If your MBR goes out, you can also use the [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to restore an invisible version of Grub to boot Windows with.

---

### Post by Sef on 2007-10-14
> Okay, I just booted my laptop up with my recovery disk, and got three options.

1) Partial Restore of initial partition.
2) Full HD Restor
3) Install Missing Diver partition

Would any of these options work? 

Either one or two would work depending on how badly your system was broken and what you wanted to install.

---

### Post by Romoko on 2007-10-14
GREAT! Ill start the Ubuntu install now! Woot!

Oh, and should I install my 7.04, or download 7.10 and burn it and install it instead? Can you upgrade from 7.04 without downloading 7.10 all over again?

---

### Post by Frak on 2007-10-14
> **Romoko said:**
> GREAT! Ill start the Ubuntu install now! Woot!

Oh, and should I install my 7.04, or download 7.10 and burn it and install it instead? Can you upgrade from 7.04 without downloading 7.10 all over again?
Yep, in about 4 days your update-manager will tell you to upgrade to Gutsy Gibbon by clicking "Distribution Upgrade".

---

### Post by Romoko on 2007-10-14
Thank you so much for your help! Ubuntu is installed and I am now buried in forums looking for the millions of answers I have.

Thanks again!
~Romoko

---

