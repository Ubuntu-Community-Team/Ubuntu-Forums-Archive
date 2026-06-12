---
title: "Can't boot Windows on Dual Boot system"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Julian David Pitt on 2006-10-11
I have a two hard drive system with XP on the main drive and Dapper on the other. Both drives are fine and both systems used to boot ok. For some reason though recently I cannot get into Windows, when I select it from grub the system just seems to hang. Can anyone tell me how I can fix this please.

---

### Post by apjone on 2006-10-11
hey post your grub menu.lst here and what dev device your O/S are on please.

---

### Post by Julian David Pitt on 2006-10-11
title		Ubuntu, kernel 2.6.15-27-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by gn2 on 2006-10-11
[http://ubuntuforums.org/showthread.php?t=275661](http://ubuntuforums.org/showthread.php?t=275661)

---

### Post by Julian David Pitt on 2006-10-12
Hi GN2
Appreciate the response but all I was after was a diagnosis of my grub menu.lst to see if that could tell me what was wrong. It all used to work ok and I could boot into Windoze and Ubuntu but then it seemed to stop. I guess I could have some corruption on the Windoze drive so I shall check that first. Cheers for the help.

---

### Post by gn2 on 2006-10-12
> **Julian David Pitt said:**
> Hi GN2
Appreciate the response but all I was after was a diagnosis of my grub menu.lst to see if that could tell me what was wrong. It all used to work ok and I could boot into Windoze and Ubuntu but then it seemed to stop. I guess I could have some corruption on the Windoze drive so I shall check that first. Cheers for the help.

Grub in your MBR. There's the corruption.

fixmbr then install Grub on the Ubuntu drive (with Windows drive switched off)

And there will be no more Grubby mess on the Windows drive.

---

### Post by bulldog on 2006-10-12
> **gn2 said:**
> Grub in your MBR. There's the corruption.

fixmbr then install Grub on the Ubuntu drive (with Windows drive switched off)

And there will be no more Grubby mess on the Windows drive.

Think it has nothing to do with GRUB,but a corrupt windows.

Leave your GRUB where it is,nothing wrong with it.:D

---

### Post by gn2 on 2006-10-12
> **bulldog said:**
> Think it has nothing to do with GRUB,but a corrupt windows.

Leave your GRUB where it is,nothing wrong with it.:D

So how does he boot Windows if his Grub is OK?

O.P. should at least try fixmbr to eliminate Grub as the cause of his problem.

Simple diagnostics.


Grub on MBR = NASTY NASTY NASTY!!!  [-(

---

### Post by apjone on 2006-10-13
it all looks ok................ hmmmm

---

### Post by Julian David Pitt on 2006-10-15
HI Apjone
Tried to boot Windows again last night with no joy at all. It just comes up there was a problem starting windows last time and asks if you wants to start in safe mode etc. It then freezes and I have to restart the system again. I have checked the Windows drive for corruption and there does not appear to be any, help ??

---

### Post by Bigbluecat on 2006-10-15
It does not look like a grub problem as windows starts to boot. As far as I know grub is only pointing at the rigth partition for windows boot.ini.

I guess it could be a problem with windows boot.ini. I think the bootcfg command from windows recovery mode will re-write this but please reseach  - it's only a guess. And I can't see why this would suddenly change.

Did the system hang when you tried to boot in safe mode? It was not so clear from your last response.

EDIT: I forgot to ask if the windows splash screen shows. If it does you are past grub and definitely into windows problems territory

---

### Post by JayTee on 2006-10-15
If it's coming up to a Windows boot menu but then freezes you've got corruption in your Windows installation. Boot from the Windows CD and when it gives you the choices of Install Windows or Recovery Mode choose Install Windows. It will find the existing partition and Windows install and at that point it will give you the choice to repair or hit esc to not repair. Press R to repair. It will look like it's reinstalling but it's just copying a fresh set of system files to replace any potentially damaged ones. Once it's done with the text mode setup it will want to reboot. Since you have GRUB on your MBR you'll need to manually choose the Windows boot option. Setup should continue from there in GUI mode and will want your regional settings and your product license key. Don't take the time estimates seriously. It takes alot less time than the Windows setup program thinks it will The advantage to this method is that it will fix any corrupted OS files and correct some registry entries but won't wipe the whole thing clean and start over so you won't have to reinstall all your applications and adjust all your preferences again. The only negative to this method is you'll have to run Windows Updates afterwards to get your system files back up to current versions.

---

### Post by Julian David Pitt on 2006-10-16
> **Bigbluecat said:**
> It does not look like a grub problem as windows starts to boot. As far as I know grub is only pointing at the rigth partition for windows boot.ini.

I guess it could be a problem with windows boot.ini. I think the bootcfg command from windows recovery mode will re-write this but please reseach  - it's only a guess. And I can't see why this would suddenly change.

Did the system hang when you tried to boot in safe mode? It was not so clear from your last response.

EDIT: I forgot to ask if the windows splash screen shows. If it does you are past grub and definitely into windows problems territory

Hi Bigbluecat
The system did not hang when safe mode is selected and I think I shall refrain from using the bootcfg command for fear of overwriting my mbr. Also the splash screen does ot show at all so I guess it is not really into Windows at all. Thanks for your help.

---

### Post by Julian David Pitt on 2006-10-16
Hi Jay Tee
I have used that repair method before successfully but this time I am loath to do it for fear of messing up the whole system. I do not think I have any corrupt system files somehow as everything was worlking fine one minute and then not at all. Do you know if you can run the system file checker from the recovery console at all.?

---

### Post by bulldog on 2006-10-16
Safe mode boots fine.
That indicates there is a driver or something like that what's causing the issue.

In safe mode there are no drivers loaded.

Did you install something the last time you booted windows?

---

### Post by Bigbluecat on 2006-10-16
OK.

If I understand your post correctly Windows will boot in safe mode.

In normal mode it does not reach the windows splash screen but hangs.

This is probably where I hit my limit on Windows as I don't know any details of the boot differences in safe mode or normal mode for windows.

The follwong two sites have been useful to me in solving boot issues.

Super Grub Disk

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)
 
And Herman's grub page:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

However I have used them to solve Linux boot issues. I'm not sure if they will be relevant in your case.

At one point I had a catastrophe and could not boot Ubuntu or Windows. That time I used the windows recovery disk and restored the standard windows MBR. When I was happy wiht that I reinstalled grub and fixed teh menu.lst.

Good luck.

---

### Post by Julian David Pitt on 2006-10-19
Hi Bigbluecat
I have tried the super grub disk with no success. It will not boot Windows at all whichever option I select. I shall have to do a repair installation I reckon. I tried using recovery console but even after deleting the boot.ini and rebuilding the boot configuration it still fails to boot.

---

### Post by gn2 on 2006-10-19
> **Julian David Pitt said:**
> Hi Bigbluecat
I have tried the super grub disk with no success. It will not boot Windows at all whichever option I select. I shall have to do a repair installation I reckon. I tried using recovery console but even after deleting the boot.ini and rebuilding the boot configuration it still fails to boot.

Would now be a good time to point you to my new and improved how-to thread?
[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Julian David Pitt on 2006-10-21
I can now boot Windows after a fresh install but of course my primary drive now boots straight into Windows. The only way I can get into Ubuntu is by using the Grub super boot disk. If I try GN2 method of using the Bios to select IDE1 to boot from I get the Grub menu but cannot boot any of the options. The Supergrub disk shows me the same menu and lets me boot Ubuntu ok so what is happeniong there? I guess I now need to reinstall Grub but I have no idea how to do this, guess I had better search the threads.

---

### Post by confused57 on 2006-10-21
> **Julian David Pitt said:**
> I can now boot Windows after a fresh install but of course my primary drive now boots straight into Windows. The only way I can get into Ubuntu is by using the Grub super boot disk. If I try GN2 method of using the Bios to select IDE1 to boot from I get the Grub menu but cannot boot any of the options. The Supergrub disk shows me the same menu and lets me boot Ubuntu ok so what is happeniong there? I guess I now need to reinstall Grub but I have no idea how to do this, guess I had better search the threads.
When the grub menu displays and the Ubuntu entry is highlighted, press "e" for edit, and try changing your root from (hd1,0) to (hd0,0), or vice versa...then try to boot.  This change is only temporary, but you can see if Ubuntu will boot this way.

You can reinstall grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by Julian David Pitt on 2006-10-26
Thanks for the suggestion, setting to (hd0,0)did the trick. The only way I can get to the grub menu though is to select the second hard drive from the Bios. I guess I can leave it that way and just edit boot/grub/menu.lst, or should I reinstall grub?
Cheers

---

### Post by Capn McButterNuts on 2006-10-26
I'm having the same problem, can't work out what I've done wrong.


[slimy tosser]("http://www.elysee.fr/elysee/anglais/the_president/biography/biography.39706.html")

---

### Post by bulldog on 2006-10-26
> **Capn McButterNuts said:**
> I'm having the same problem, can't work out what I've done wrong.


[slimy tosser]("http://www.elysee.fr/elysee/anglais/the_president/biography/biography.39706.html")

You have two drives?
And on which of the two is Ubuntu? The master or the slave or do you have Sata drives?

Have you the possibillity to change your bootdevice by pressing F11 or something like that?

---

### Post by confused57 on 2006-10-26
> **Julian David Pitt said:**
> Thanks for the suggestion, setting to (hd0,0)did the trick. The only way I can get to the grub menu though is to select the second hard drive from the Bios. I guess I can leave it that way and just edit boot/grub/menu.lst, or should I reinstall grub?
Cheers
No, you shouldn't have to reinstall grub...you can just edit your /boot/grub/menu.lst to boot Ubuntu by changing the root to (hd0,0).

You should be able to boot Windows by adding an entry similar to this at the very end of the menu.lst file:

```
title                Windows XP
root                (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Just set your computer to boot first to the Ubuntu drive & you should be able to use grub to select Ubuntu or Windows.

---

