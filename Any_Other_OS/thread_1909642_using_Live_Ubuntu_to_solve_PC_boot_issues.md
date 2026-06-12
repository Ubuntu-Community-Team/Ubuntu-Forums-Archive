---
title: "using Live Ubuntu to solve PC boot issues"
date: 2012-01-15
forum: Any Other OS
---

### Post by RememberWhenItRained on 2012-01-15
I have a friend who runs Win7 (and only win7) and recently ran into a problem where Win7 will not even reach the boot screen that says "Starting Windows" and instead shows a black screen with a blinking underscore.

I recommended loading Ubuntu on a CD or USB to both get internet temporarily and try to solve his PC issues.

Is this some kind of corrupted Windows config. file, or what? Also, how would you go about using Ubuntu to diagnose and solve this problem?

Any ideas? Much thanks.

(more reason to use linux,,)

---

### Post by ernestj on 2012-01-15
I am not sure of how Ubuntu can fix the problem. The good news is that you can run Ubuntu live CD and access the files and move them to a backup drive. There are other Linux software choices are made for PC issues including viruses. Good Luck.

---

### Post by mips on 2012-01-16
1. Do a diagnostics scan of the HDD using one of the manufacturers utilities or MHDD.
2. Insert the Win7 installation DVD and boot from it selecting the repair option, if you don't have the dvd you might have to boot from the recovery partition.
3. You can use a linux livecd to backup his data & email.

---

### Post by RememberWhenItRained on 2012-01-21
> **mips said:**
> 1. Do a diagnostics scan of the HDD using one of the manufacturers utilities or MHDD.
2. Insert the Win7 installation DVD and boot from it selecting the repair option, if you don't have the dvd you might have to boot from the recovery partition.
3. You can use a linux livecd to backup his data & email.


RE: 
1.He installed 11.10 without issue after booting from a disc. So i don't think it's a HDD problem. Something's screwed up in windows config. most likely. Either that or possible that it's a boot sector virus? I hope not, he did run for a good few months w/o antivirus. If it was though, would that still leave problems with GRUB or just windows?

2. No installation disc to speak of. MS is being stupid, and not including discs if you buy a computer preloaded with the Windows OS. Dumb, i know. Wasn't able to access safe mode or a recovery partition from Windows. All his [win7[ files are in order though, that's good.

3. Good thinking.

We should be able to run some kind of diagnostics from Ubuntu, right? Similar to what you can do with Hiren's or UBCD, but in ubuntu?
Also, possible to run an antivirus *for Windows* _in Linux*,*_right?
If it is a broken install or config file, i don't know how you'd fix it without a recovery disc though.

Could be problematic.

Any ideas? Thanks so much.

---

### Post by mips on 2012-01-21
> **RememberWhenItRained said:**
> 
If it is a broken install or config file, i don't know how you'd fix it without a recovery disc though.

Usually you have the option to create install discs from the hard drive, most manufacturers do this and don't give you the physical media. What brand/model pc is this?

---

### Post by RememberWhenItRained on 2012-01-21
> **mips said:**
> Usually you have the option to create install discs from the hard drive, most manufacturers do this and don't give you the physical media. What brand/model pc is this?

A Dell Inspiron 1440 I believe, running Win7 [i think]
Can you make the install disc when the host OS won't boot?

---

### Post by mips on 2012-01-21
First backup data&email with a ubuntu livecd to a external hard drive.

Before windows attempts to start loading try hitting the F8 or Ctrl+F11 or Ctrl+F10 repeatedly and hopefully you get a menu with repair option where you can reset to factory default configuration.
Try this and see if it works.

or you can try this,

1. Make bootable CD which contains Norton Ghost or other disk image software 
2. boot your system using bootable CD with Norton Ghost software, u can use Hiren's CD ISO image. if u dont know about hiren just google it. 

2. Once you boot up , open Norton Ghost click LOCAL-> PARTITION->FROM IMAGE 

3. now "look in" for "[DellRestore]FAT drive" and select this drive (this is recovery partition)

4. now go to "IMG" folder and select FI.GHO file 

5. Click Open and there you go... process started 

**[COLOR="Red"]All the above suggestions will mean you lose your data!!![/COLOR]**



.

---

