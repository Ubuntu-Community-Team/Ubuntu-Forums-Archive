---
title: "Dual boot Backtrack/Windows"
date: 2012-05-07
forum: Any Other OS
---

### Post by tilt2kngiht on 2012-05-07
When I installed Backtrack 5 I accidentally went through the advanced partition option instead of dual booting.  I still have the Windows partition file and I can open it as if it were a iso image but I want to be able to boot it at start up. Is there any way I can get it to dual boot?

---

### Post by uRock on 2012-05-07
Moved to Other OS/Distro Talk.

---

### Post by tilt2kngiht on 2012-05-07
I can't figure out if it's possible to remount Windows?

---

### Post by tilt2kngiht on 2012-05-07
Is the only option to get the Windows 7 disk? Would it use the existing  windows partition after boot or would it wipe everything? Sorry if this  sounds stupid, I'm a n00b.

---

### Post by oldfred on 2012-05-07
Post the link to a run of the Boot-Info report that this creates.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by tilt2kngiht on 2012-05-08
Thanks mate. Only, I don't know how to burn that download to a CD or USB. Is it a terminal command?

---

### Post by oldfred on 2012-05-08
Boot repair has several ways to install. You can just download it into your Ubuntu liveCD or USB. 

It also has a couple of versions of liveCD of its own.

---

### Post by tilt2kngiht on 2012-05-08
Thanks. I got boot repair but the default setting just made windows disapear. Luckily I rebooted and the windows file returned. I'm going to do my research in advanced settings so it doesn't overwrite windows. If anything I'd like to delete or overwrite backtrack so I can set it up right.

---

### Post by oldfred on 2012-05-08
Post the link to Boot-Info report and we can see what you have.

---

### Post by tilt2kngiht on 2012-05-08
[http://paste.ubuntu.com/976881/](http://paste.ubuntu.com/976881/)

---

### Post by oldfred on 2012-05-08
The Windows boot partition sda1 is just for Windows in MBR. It looks like you created a /boot partition for Linux (which for most desktops is not required) and overwrote the Windows code.

Do you have a Windows 7 repair CD or full install DVD? You need to use gparted to move boot flag to sda2 and run Windows repairs on sda2.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Boot files - you are missing the first two, but you can repair your main install and put them there:
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=DarkRed]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe

---

### Post by tilt2kngiht on 2012-05-09
OK I'm going to use a friends repair disk. Will there be any issues using the Windows files as in wipe them? Is it going to be a problem that it's not the same disk that was originally installed?

---

### Post by uRock on 2012-05-09
> **tilt2kngiht said:**
> OK I'm going to use a friends repair disk. Will there be any issues using the Windows files as in wipe them? Is it going to be a problem that it's not the same disk that was originally installed?

As long as it is the same version and the same architecture, it should work. If it is not the same, then you can download the proper image via the links supplied by [COLOR="Red"]oldfred[/COLOR]

---

### Post by oldfred on 2012-05-10
I have used a Windows 7 repair USB to run chkdsk on my old XP. It did write a Windows 7 boot sector, but I was able to write an XP boot sector with some Windows commands. 

I have links we used to recommend for repairCDs, but they now charge $10. I think the more important version difference is 32 bit vs. 64 bit. If that is the same the repairs should work.

---

### Post by tilt2kngiht on 2012-05-10
I did try a windows7x64.iso from a certain Swedish web site. I used a USB but when it booted there was just a blinking backslash. I took a look at the gparted. I definitily just f'd up and overwrote sda1 (I think it's ext4 /boot now). Surely there's a way to do this without reinstalling Windows7.....What were those window commands?

---

### Post by tilt2kngiht on 2012-05-10
*that was just the repair disk .iso

---

### Post by oldfred on 2012-05-10
You also overwrote sda1, so you cannot recover it. 

But Windows works from one partition, but you have to have boot flag on sda2 not sda1 as Windows only repairs the boot flag partition.

From Windows repair:

You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  [COLOR=Red]do not run[/COLOR] if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by tilt2kngiht on 2012-05-12
Right, I got the iso and followed the command lines you suggested. Everything worked untill the last BootRec.exe/RebuildBcd. "The volume does not contain recognized file system.  Please make sure that all required file system drivers are loaded and that the volume is not corrupted." There is a chance of it being currupted because of a Brasero error during burning. I've fixed the error so I'll burn it again and give it another shot.

---

