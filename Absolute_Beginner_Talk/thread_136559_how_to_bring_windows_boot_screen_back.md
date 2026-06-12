---
title: "how to bring windows boot screen back?"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by sallam on 2006-02-26
Greetings

If I want out, how can I make windows take control, at computer start up, as it did before installing ubuntu?
I do not want to be asked what system to boot with, I just want windows to start itself like before.

---

### Post by mjfleck2000 on 2006-02-26
What version of Windows do you wish to return to?

Windows 98
Windows 2000
WinXP

I have replaced the boot up menu with only Windows.  I was going back to Winodws 2000.  
I placed the Windows 2000 Install CD in the computer.
Rebooted.
(Darn, my memory is getting fuzzy here now.  It has been a LONG time since I removed Linux and replaced Windows. )
There is a point in the Windows install were you can press F6 (I believe) to go to a repair console.
Once I am at the repair console, I type the command "fdisk /fixmbr ".
This command writes a new Windows boot up menu to the hard drive.
After the command, I reboot (remove the Install CD) and, Voila!, you have your menu back.
I think you can do the same procedure for Windows 98 or WinXP.

I hope this helps.

Let us know if you need more help.
Also, let us know if this worked for you so that others may find your problem AND the solution.

Mike

---

### Post by theturner on 2006-02-26
If I recall correctly, it's a simple
```
fdisk /mbr
``` in Windows.
Then again, I might be wrong, haven't been using Windows since six years.

---

### Post by mjfleck2000 on 2006-02-26
Thanks theturner,
I haven't done the fixmbr trick for quite a while.  I will try it using VMware... then I will post the results here again.

Mike

---

### Post by monolegis on 2006-02-26
all you have to write in recovery console is "fixmbr". Always workes for me. No hassel.

---

### Post by mjfleck2000 on 2006-02-26
Okay,
Just tried this using VMware.
F6 is NOT the key to use.
Run the install CD until you see:

[I]Welcome to Setup
To set up Windows 2000 now, press enter
To Repair a Windows 2000 installation ,press R
To quit set up without installing Windows 2000, press F3
[/I]

So, press "R"
Then press "C" ( to contiune set up)
Then press "C" (to use the recovery console)


Then, the command to use is  "fixmbr".
You do NOT use "fdisk /mbr or fdisk /fixmbr".  The command is simply "fixmbr".
Windows will ask if you are sure, type "yes" and press enter.  Windows should write a new mbr (a new Windows menu).

Mike

---

### Post by patrick295767 on 2006-02-26
[QUOTE=sallam]Greetings

If I want out, how can I make windows take control, at computer start up, as it did before installing ubuntu?
I do not want to be asked what system to boot with, I just want windows to start itself like before.[/QUOTE]
 
There is a wingrub existing ... (in the wiki)
  
As I do, I have a fat32 partition, and u could use the boot.ini that is stored there.
bellamy explains  [http://jc.bellamy.free.fr/fr/jcb.html](http://jc.bellamy.free.fr/fr/jcb.html) 
the way to work with boot.ini, to boot both linux and windows, 
you can say to use windows as default
(one bootable fat32 partition is used)
  
You could also make sure that the grub is installed, and to set up that the default system is windows after 2 sec  onds (it's not much) ... it's the easiest one to do when u have linux in ur machine.
  
If you wanna remove the grub : boot with dos : fdisk /MBR
Ir you wanna make it windows again, installation windows cd, then go in recovery (admin passwd required) 
and restore as explained above MBR of windows ... 

There is a lot of ways to plays with partitions and booting ... 

I hope U'll find the one u'd like the best ... 

Greetings 

Patrick

---

