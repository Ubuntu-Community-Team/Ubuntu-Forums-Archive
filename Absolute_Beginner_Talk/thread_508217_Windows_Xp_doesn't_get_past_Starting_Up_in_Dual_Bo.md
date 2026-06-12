---
title: "Windows Xp doesn't get past Starting Up in Dual Boot"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by nbeerbower on 2007-07-23
I just installed Fiesty Fawn on a small partition. In order to get it up to atleast 2 gigs I needed to trim the Windows one down and now I can boot Ubuntu but Windows gets stuck on Starting Up...

Any suggestions? Should I get my Windows XP cd and remove Ubuntu (I'm willing to get rid of Ubuntu just to have Windows XP)? Please help! Thank you guys so much!

---

### Post by nbeerbower on 2007-07-24
Okay, If I delete the Ubuntu partition will the dual boot menu still show up or will it just load Xp?

EDIT: 
I'm gonna try doing that tomorrow and I don't want to make my computer unusable. So if someone would reply that would be great. :P

---

### Post by redwinder on 2007-07-24
> **nbeerbower said:**
> Okay, If I delete the Ubuntu partition will the dual boot menu still show up or will it just load Xp?

EDIT: 
I'm gonna try doing that tomorrow and I don't want to make my computer unusable. So if someone would reply that would be great. :P

my experience is that if you erase the ubuntu partition grub will give an error when it loads and you will not be able to load windows xp, you probably erased some important windows file when you were resizing the partitions, try to recover XP with the recovery CD

---

### Post by confused57 on 2007-07-24
> **nbeerbower said:**
> Okay, If I delete the Ubuntu partition will the dual boot menu still show up or will it just load Xp?

EDIT: 
I'm gonna try doing that tomorrow and I don't want to make my computer unusable. So if someone would reply that would be great. :P
No, don't just delete the Ubuntu partition...see this guide:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
just deleting the Ubuntu partition would definitely render your pc unusable.

I would recommend burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
see if SGD can boot Windows...if it can, then SGD can restore your Windows IPL code to the mbr.

If SGD cannot boot Windows and you have a Windows install cd, you might need to run "chkdsk":
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx)

---

### Post by nbeerbower on 2007-07-24
Okay guys. I'll try these, thanks!

---

### Post by nbeerbower on 2007-07-24
Damn, nothing worked. Even chkdsk, and now SGD is my primary booter... how do I put it back to GRUB? I can still use Ubuntu, but Windows still does the same thing.

I have three partitions, C:System(Windows System Files), D:Files(My Partition to save things in), and my Ubuntu partiton.

Is there anyway I can reformat both the windows and the Ubuntu partition then just reinstall XP? Would I get an error from GRUB? Should I uninstall Ubuntu? I'm so confused! Is there anyway I can remove Ubuntu and Grub so Windows XP starts automatically? Maybe I could just reinstall Windows?

Grrrr... How do I get rid of Grub?

If I got rid of Grub, then I could boot into ONLY Ubuntu, and then insert the XP disk, restart, boot from the disk, remove the Ubuntu partition, and reinstall Xp, Right?

EDIT: Or more simply would it work if I just reinstalled XP?

---

### Post by confused57 on 2007-07-24
> **nbeerbower said:**
> Damn, nothing worked. Even chkdsk, and now SGD is my primary booter... how do I put it back to GRUB? I can still use Ubuntu, but Windows still does the same thing.

I have three partitions, C:System(Windows System Files), D:Files(My Partition to save things in), and my Ubuntu partiton.

Is there anyway I can reformat both the windows and the Ubuntu partition then just reinstall XP? Would I get an error from GRUB? Should I uninstall Ubuntu? I'm so confused! Is there anyway I can remove Ubuntu and Grub so Windows XP starts automatically? Maybe I could just reinstall Windows?

Grrrr... How do I get rid of Grub?

If I got rid of Grub, then I could boot into ONLY Ubuntu, and then insert the XP disk, restart, boot from the disk, remove the Ubuntu partition, and reinstall Xp, Right?

EDIT: Or more simply would it work if I just reinstalled XP?
First, you could use a Windows install cd(not a recovery cd) to install Windows IPL to the mbr...enter recovery console by pressing "r", then enter the command FIXMBR.  Then see if your Windows will boot.

You can reinstall grub's IPL to the mbr with SGD or the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you decide to reinstall Windows...after you get Windows up and running, you can then use the Ubuntu live cd to install grub to the mbr.  You should be able to reinstall Windows to the partition it is currently on, without having to reinstall Ubuntu.

---

### Post by Orochi on 2007-07-24
When you say Windows gets stuck on starting up, what do you mean? Does it actually make it to the Windows logo, or does GRUB lock up when you choose Windows from the menu?

If nothign else works you can reinstall Windows to the C: partition. This will erase GRUB and make it so Windows XP always boots (although Ubuntu will still be on your drive). Then you can use your Ubuntu LiveCD to reinstal GRUB. The reason Windows isn't working is most likely that something got messed up when you resized your Windows partition (its pretty bad about that). Reinstalling is probably the easiest option.

---

### Post by nbeerbower on 2007-07-24
How do I erase Super Grub? Or switch Super Grub back to Grub? Also I heard sometimes this happens when the Windows Partition isn't on top. How can I change this? Because most people have apparently fixed it by doing that.

EDIT: Never mind. I just saw what you guys said about Ubuntu live cd. But I still need help doing the Windows drive thing, you know making the Windows Partition #1, on top, whatever.

EDIT: If I were to reinstall Windows XP would that remove GRUB? (Never mind I'm stupid I didn't see that in Orochi's post :P) Also FIXMBR did not work.

---

### Post by Orochi on 2007-07-24
I would reccommend reinstalling Windows. You can probably still access the contents of your Windows partition through Ubuntu and copy off any files you need prior to reinstalling. I don't think Windows needs to be the first partition on the drive. It needs to be the first drive connected to the computer, but not the first partition on that drive (if I understand correctly, I might be wrong).

If you reinstall Windows, it will overwrite grub with its own bootloader. You will then need to reinstall GRUB to regain access to Ubuntu.

However, if you give me more details on what exactly happens when you try to boot into Windows, I can determine more accurately if it's really a Windows problem that requires reinstallation or if its just that your GRUB settings are configured incorrectly.

---

