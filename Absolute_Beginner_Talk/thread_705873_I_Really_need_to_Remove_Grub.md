---
title: "I Really need to Remove Grub"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by turbobill on 2008-02-23
I have Ubuntu installed on my development machine as dual boot with WinXP.  Need to remove grub from XP machine.  Have tried Super Grub with no results.  Please help!  
Thanks, 
Wm

---

### Post by p_quarles on 2008-02-23
Not sure what you mean here . . . you want to remove GRUB from a dual-boot machine? Or from an XP-only machine?

Either way, the way to remove it is to write a Windows MBR over GRUB.

---

### Post by sandysandy on 2008-02-23
> **turbobill said:**
> I have Ubuntu installed on my development machine as dual boot with WinXP.  Need to remove grub from XP machine.  Have tried Super Grub with no results.  Please help!  
Thanks, 
Wm

why do u want to remove grub, if i may ask.

anyway, as u r familiar with Super Grub, use it to install windows bootloader to MBR. it will overwrite grub.

Edit: already answered in post above.

---

### Post by cboebel on 2008-02-23
You can also check out this thread: There are several references within it to removing/replacing grub.

[http://ubuntuforums.org/showthread.php?t=115788](http://ubuntuforums.org/showthread.php?t=115788)

---

### Post by turbobill on 2008-02-23
> **p_quarles said:**
> Not sure what you mean here . . . you want to remove GRUB from a dual-boot machine? Or from an XP-only machine?

Either way, the way to remove it is to write a Windows MBR over GRUB.

I want to remove GRUB from a dual boot machine.

What's the safest way to write a Windows MBR over GRUB.

I have Super Grub, but does it run from a Linux boot or from a Windows boot?  If from Windows, then something is wrong because so far it's not booting from the CD.

Thanks,
Wm

---

### Post by p_quarles on 2008-02-23
> **turbobill said:**
> I want to remove GRUB from a dual boot machine.

What's the safest way to write a Windows MBR over GRUB.

I have Super Grub, but does it run from a Linux boot or from a Windows boot?  If from Windows, then something is wrong because so far it's not booting from the CD.

Thanks,
Wm
And want do you want to replace it with? You do realize that once you do this, you will no longer have a dual boot machine, right?

There is no more or less safe to overwrite the MBR. Doing this replaces the old one with a new one. You can use a Windows installation disk or the Super GRUB disk.

---

### Post by Michl on 2008-02-23
I am wondering why you would want to remove grub from a
dualboot machine.  Grub allows you to choose whether to
boot windows or linux.  Isn't it true that without it you would
always boot into windows?

---

### Post by turbobill on 2008-02-23
> **p_quarles said:**
> And want do you want to replace it with? You do realize that once you do this, you will no longer have a dual boot machine, right?

There is no more or less safe to overwrite the MBR. Doing this replaces the old one with a new one. You can use a Windows installation disk or the Super GRUB disk.

Yes I realize, no more dual boot.  I'm setting up a separate Ubuntu server now, no more need for dual boot.

If I use a Windows install CD does it guide me through that process, and will it wipe out my entire disk?

---

### Post by turbobill on 2008-02-23
> **Michl said:**
> I am wondering why you would want to remove grub from a
dualboot machine.  Grub allows you to choose whether to
boot windows or linux.  Isn't it true that without it you would
always boot into windows?

I need the space!

---

### Post by p_quarles on 2008-02-23
> **turbobill said:**
> Yes I realize, no more dual boot.  I'm setting up a separate Ubuntu server now, no more need for dual boot.

If I use a Windows install CD does it guide me through that process, and will it wipe out my entire disk?
I don't remember exactly how using the Windows disk works for this, but I believe it gives you the option of restoring the MBR and doing nothing else. The Super GRUB disk definitely allows you to do this.

Alternately, you may want to try this method:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by sandysandy on 2008-02-23
> **turbobill said:**
> I need the space!

if i may point out your queries on removing GRUB have already been answered in above posts.

here&#347; what u will need to do

1. put super Grub disk in ur CD drive,

2. reboot ur computer.

3.  the computer reboots into super grub disk ( not windows and not linux).

4.  browse through super grub disk. go to windows section and use option to fix windows boot.

5.  reboot.

6.  u should now boot into windows. grub is replaced with windows bootloader.

regards

---

### Post by thelugnut on 2008-02-23
1. Insert Windows installation disk into CD 
2. Boot into the Recovery Console
3. When you get the promt, type <fixmbr>
4. Restart and log into Windows
5. Navigate to Control Panel>Administrative Tools>Computer management>Disk Configuration
6. Format the Unbuntu partition with ntsf (assuming you are using ntfs with Windows)

That's all, no fuss, no bother.

---

### Post by turbobill on 2008-02-23
Thank you SandySandy, but the Super Grub disk does NOT boot.  I guess I messed it up in the burning process.

Thanks again,
Wm

---

### Post by turbobill on 2008-02-23
Thanks to thelugnut for the most "to the point and concise" solution to my problem.

Thanks thelugnut,  much appreciated.

Wm

---

### Post by sandysandy on 2008-02-24
> **turbobill said:**
> Thank you SandySandy, but the Super Grub disk does NOT boot.  I guess I messed it up in the burning process.

Thanks again,
Wm

burn it as an ISO image to make it a  bootable CD.

all the best

regards

---

