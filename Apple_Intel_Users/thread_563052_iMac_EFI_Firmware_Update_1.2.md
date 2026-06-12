---
title: "iMac EFI Firmware Update 1.2"
date: 2007-09-29
forum: Apple Intel Users
---

### Post by liberalist on 2007-09-29
I am very happy to have Kubuntu 7.04 running on my iMac Core 2 Duo as dual-boot. However, there is an EFI Firmware 1.2 update available (from Apple). Does this destroy or harm my rEFIt installation? 

See the website [http://www.apple.com/support/downloads/imacefifirmwareupdate12.html](http://www.apple.com/support/downloads/imacefifirmwareupdate12.html) for update details. Thanks in advance for your help.

PS: Does Kubuntu 7.10 include support for Airport Extreme (wireless) through restricted drivers manager?

---

### Post by cyberdork33 on 2007-09-30
the update may break refit, but you just have to reinstall it and you will be fine.

---

### Post by schauerlich on 2007-09-30
Will this be the same for a C2D MacBook w/ dual boot?

---

### Post by liberalist on 2007-09-30
I read in another thread (see [http://ubuntuforums.org/showthread.php?t=299571](http://ubuntuforums.org/showthread.php?t=299571) ) that for a (presumably first generation) MacBook, the update did not cause any trouble.

---

### Post by pxwpxw on 2007-09-30
I just ran the patch (1.1) on MacBook C2d, it seems to have fixed the dead keyboard problem (5 times out of 5).  And refit is alive and well.

[http://www.apple.com/support/downloads/macbookefifirmwareupdate11.html](http://www.apple.com/support/downloads/macbookefifirmwareupdate11.html)

And the 200MB efi partition#1 now has the efi firmware updater files 
```

# ls -lRn /media/disk/EFI/
/media/disk/EFI/:
total 1
drwx------ 3 0 0 512 2007-09-30 23:03 APPLE

/media/disk/EFI/APPLE:
total 1
drwx------ 2 0 0 512 2007-09-30 23:03 FIRMWARE

/media/disk/EFI/APPLE/FIRMWARE:
total 2154
-rwx------ 1 0 0  107536 2007-09-30 23:05 EfiUpdaterApp2.efi
-rwx------ 1 0 0 2097152 2007-09-30 23:05 LOCKED_MB21_00A5_07B.fd

```

Keyboard is still 100% success,. There is a much longer delay before the grub menu comes up after selecting the icon in the Apple or refit screen, maybe work has been done in there.

---

### Post by onyxrev on 2007-09-30
For me it appears that the update has caused Pommed to no longer respond properly.  The function keys seem to have changed somehow as I can no longer F2 the run menu, either.

---

### Post by cyberdork33 on 2007-09-30
> **pxwpxw said:**
> I just ran the patch (1.1) on MacBook C2d, it seems to have fixed the dead keyboard problem (5 times out of 5).  And refit is alive and well.

[http://www.apple.com/support/downloads/macbookefifirmwareupdate11.html](http://www.apple.com/support/downloads/macbookefifirmwareupdate11.html)

And the 200MB efi partition#1 now has the efi firmware updater files - in \EFI\APPLE\FIRMWARE

Keyboard is still 100% success,. There is a much longer delay before the grub menu comes up after selecting the icon in the Apple or refit screen, maybe work has been done in there.
Fixed the bootloader keyboard issues for me too. :D

---

### Post by cyberdork33 on 2007-11-06
Well, I recently found that my keyboard was broken in grub again. I checked my EFI partition for the first time in a very long while and found that the files the firmware update had left are now missing. I am just wondering if that might be related to why my keyboard isn't functioning again. (I can't even replug it to get it to work anymore.)

pxwpxw, can you check that your files still exist? I thought I backed mine up somewhere to play with later, but I cannot find them now. I am going to attempt to get them out of the firmware package again.

---

### Post by pxwpxw on 2007-11-07
> **cyberdork33 said:**
> Well, I recently found that my keyboard was broken in grub again. I checked my EFI partition for the first time in a very long while and found that the files the firmware update had left are now missing. I am just wondering if that might be related to why my keyboard isn't functioning again. (I can't even replug it to get it to work anymore.)

pxwpxw, can you check that your files still exist? I thought I backed mine up somewhere to play with later, but I cannot find them now. I am going to attempt to get them out of the firmware package again.

 Mine remain as found after the firmware update ( 1.1 macbook c2d ).  I assumed the files were only used during the update, but I left them just in case.
```

root@ubuntu:/home/admax# df /dev/sda1
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1               201633      2164    199470   2% /home/admax/aaa

root@ubuntu:/home/admax# find aaa/
aaa/
aaa/efi
aaa/efi/apple
aaa/efi/apple/firmware
aaa/efi/apple/firmware/EfiUpdaterApp2.efi
aaa/efi/apple/firmware/._EfiUpdaterApp2.efi
aaa/efi/apple/firmware/LOCKED_MB21_00A5_07B.fd
aaa/efi/apple/firmware/._LOCKED_MB21_00A5_07B.fd

root@ubuntu:/home/admax# ls -la aaa/efi/apple/firmware/
total 2163
drwxr-xr-x 2 root root     512 2007-09-30 22:03 .
drwxr-xr-x 3 root root     512 2007-09-30 22:03 ..
-rwxr-xr-x 1 root root    4096 2007-09-30 22:05 ._EfiUpdaterApp2.efi
-rwxr-xr-x 1 root root  107536 2007-09-30 22:05 EfiUpdaterApp2.efi
-rwxr-xr-x 1 root root    4096 2007-09-30 22:05 ._LOCKED_MB21_00A5_07B.fd
-rwxr-xr-x 1 root root 2097152 2007-09-30 22:05 LOCKED_MB21_00A5_07B.fd

root@ubuntu:/home/admax# ls -lah aaa/efi/apple/firmware/
total 2.2M
drwxr-xr-x 2 root root  512 2007-09-30 22:03 .
drwxr-xr-x 3 root root  512 2007-09-30 22:03 ..
-rwxr-xr-x 1 root root 4.0K 2007-09-30 22:05 ._EfiUpdaterApp2.efi
-rwxr-xr-x 1 root root 106K 2007-09-30 22:05 EfiUpdaterApp2.efi
-rwxr-xr-x 1 root root 4.0K 2007-09-30 22:05 ._LOCKED_MB21_00A5_07B.fd
-rwxr-xr-x 1 root root 2.0M 2007-09-30 22:05 LOCKED_MB21_00A5_07B.fd
root@ubuntu:/home/admax# 

```

---

### Post by cyberdork33 on 2007-11-07
yea I assumed so as well, but I am willing to try something...

I redownloaded the firmware update package and extracted the proper fd file for my iMac, and the updater efi executable. I was just waiting on your reply before I tried placing them in the EFI partition.

---

### Post by volanin on 2007-11-07
> **cyberdork33 said:**
> I redownloaded the firmware update package and extracted the proper fd file for my iMac, and the updater efi executable. I was just waiting on your reply before I tried placing them in the EFI partition.

Did it work?
:)

---

### Post by cyberdork33 on 2007-11-07
> **volanin said:**
> Did it work?
:)
Not yet. Will try tonight. Still at work at the moment without direct access to my mac.

---

### Post by cyberdork33 on 2007-11-07
Failure!
:(

---

### Post by pxwpxw on 2007-11-07
Did you check the Boot ROM Version to see if it has been changed somehow?

---

### Post by cyberdork33 on 2007-11-07
> **pxwpxw said:**
> Did you check the Boot ROM Version to see if it has been changed somehow?
No, I checked my boot rom version in system profiler to determine which fd file I needed to put in the EFI partition.

---

### Post by pxwpxw on 2007-11-07
> **cyberdork33 said:**
> No, I checked my boot rom version in system profiler to determine which fd file I needed to put in the EFI partition.

But is that the same version as when the kbd was good? I expect it was - but ....

Maybe there is something outside of the firmware that we don"t know about, reset SMC?
Would not expect Apple installer to mess with the firmware without updating the rom version.

---

### Post by liberalist on 2007-11-08
I have updated my EFI iMac firmware (1.2) and it worked flawlessly. So I don't know the exact cause of your problem.

---

### Post by cyberdork33 on 2007-11-08
> **pxwpxw said:**
> But is that the same version as when the kbd was good? I expect it was - but ....
I am pretty sure that it is since it is one of the boot rom versions on Apple's website that means you no longer need the fimware update...

Mine is at  IM51.0090.B09:
[http://www.apple.com/support/downloads/imacefifirmwareupdate12.html](http://www.apple.com/support/downloads/imacefifirmwareupdate12.html)

> **pxwpxw said:**
> Maybe there is something outside of the firmware that we don"t know about, reset SMC? Yea that is a good option. I may try that. The keyboard is worse than it was before for me. It NEVER works now, not even every once in awhile like we could get away with before.

> **liberalist said:**
> I have updated my EFI iMac firmware (1.2) and it worked flawlessly. So I don't know the exact cause of your problem. Yes, it worked for me as well after I updated the firmware, then the fix degraded. Have you installed Leopard as well? I am really starting to think that had something to do with it.

I did notice that I cannot create the EFI/APPLE/FIRMWARE directories in all caps like pxwpxw's original listing. It keeps forcing them to lowercase. I don't think that matter though, as EFI should scan each partition for an efi directory to look for executables. (this is how rEFIt works too, and it is all lowercase). I really think this part is a dead end.

---

### Post by pxwpxw on 2007-11-08
in rEFIt efi shell, it does not care about case.

---

### Post by pxwpxw on 2007-11-08
I just deleted all the files in the EFI partition (after making backups from refit efi shell ),
and restarted to the grub menu, keyboard is all ok sofar.
All still OK after several restarts to macosx (tiger) or linux, refit ok.

---

### Post by cyberdork33 on 2007-11-09
> **pxwpxw said:**
> I just deleted all the files in the EFI partition (after making backups from refit efi shell ),
and restarted to the grub menu, keyboard is all ok sofar.
All still OK after several restarts to macosx (tiger) or linux, refit ok.
*sigh*

I don't know. I reset the SMC controller. That didn't seem to have any effect either.

---

### Post by pxwpxw on 2007-11-09
**cyberdork33**
Sorry, sounds difficult. All it seems to leave now is maybe corrupt firmware, or else hardware, about as far as I can go. Apple discussions might respond.

---

### Post by cyberdork33 on 2007-11-09
> **pxwpxw said:**
> **cyberdork33**
Sorry, sounds difficult. All it seems to leave now is maybe corrupt firmware, or else hardware, about as far as I can go. Apple discussions might respond.

Keyboard works in rEFIt and in Ubuntu or OSX. It is just those legacy bootloaders. Oh well. I don't really need to do anything in grub anyway. *crosses fingers*

---

### Post by cyberdork33 on 2008-01-30
OK, update. I started using my Bluetooth Keyboard again (which works in grub and such), but was having some issues in Ubuntu, so in the process of rebooting and figuring that all out, I determined that my USB keyboard will, in fact, work in grub. The problem appears to be evident only if I have my mouse (not a mighty mouse) in the first USB port on the back of my iMac. I have yet to figure out the exact issue, but unplugging my mouse definitely got everything to work (besides the mouse, since it was then unplugged...)

---

