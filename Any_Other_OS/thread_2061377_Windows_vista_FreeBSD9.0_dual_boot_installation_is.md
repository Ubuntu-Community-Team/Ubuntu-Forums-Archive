---
title: "Windows vista FreeBSD9.0 dual boot installation issue"
date: 2012-09-22
forum: Any Other OS
---

### Post by Sebi13 on 2012-09-22
I have a workstation that runs with a dual boot configuration(Ubuntu 9.04 and Win vista(home premium)). 
        Yesterday I tried installing FreeBSD 9.0 over the Ubuntu partition.  During the installation you are being prompt to choose between ada0 and  ada1(I wanted to use the entire disk) -- win being on ada0 and ubuntu on  ada1 so I choose the second option. The installer gives me an error at  this point: "Operation cancelled -- pre-check failed".

After this step you are shown the layout of the partitions. In my case it was something like:

    ada0                   <#disk size>     MBR
           ada0s1       <#disk size>     ntfs  <== win
    ada1                   <#disk size>     freebsd-boot
           ada1p1         64KB               freebsd-boot
           ada1p2       <#disk size>    freebsd-ufs  /
           ada1p3       4.0GB           freebsd-swap none
    da0             1.9GB           BSD
    da0a         534MB           freebsd-ufs

where da0 is a USB which contains the image of freebsd. The installation  completes succesfully and the installer recommends rebooting the  machine. When I reboot, GRUB(installed with ubuntu) gets confused and  throws the following error:

 stage1.5
 GRUB loading, please wait...
 Error 17

     Is there an easy way(without resorting to format the drives and start all over again) to fix the boot entries?
  Is there any way to fix the boot entries by using the ubuntu live cd? I am simply trying out freebsd and am stuck at this point.

---

### Post by Bachstelze on 2012-09-22
You need to install the FreeBSD bootloader instead of GRUB. I don't know how to do that in FreeBSD 9.0, though, because the installer has changed. (And anyway, I strongly recomment using 8.3 for now, 9.0 is still new and somewhat buggy.) If you really want to use 9.0, someone at [http://forums.freebsd.org/](http://forums.freebsd.org/) will probably be able to help you.

---

### Post by nothingspecial on 2012-09-22
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Majorix on 2012-09-22
I think you are a bit confused. You say you want to dual boot with Vista but then you say you wanted FreeBSD to use the whole disk.

@Bachstelze:
I think the 9.x series is old enough, and it introduces improvements. I see no reason to stay with 8.x.

---

### Post by oldfred on 2012-09-22
Since you have two drives, are you booting from the correct drive? 

You may have had grub legacy in the Windows sda drive and BSD installed its boot loader to sdb?

---

### Post by Sebi13 on 2012-09-22
> **Majorix said:**
> I think you are a bit confused. You say you want to dual boot with Vista but then you say you wanted FreeBSD to use the whole disk.

@Bachstelze:
I think the 9.x series is old enough, and it introduces improvements. I see no reason to stay with 8.x.

  I have two separate drives. Vista was installed on the first one. Later I installed ubuntu 9.04 on the whole second drive. Now I installed freebsd 9.0 on the second drive and overwrtten the ubuntu partition. This messed up menu.lst and now GRUB can't load any of the OSes. I want to install boot0cfg(after freebsd completes) and use it instead of GRUB. 
  The only problem is that I'm not familiar with bootloaders(boot0cfg). If I install it will it overwrite grub or not?

---

### Post by Bachstelze on 2012-09-22
> **Majorix said:**
> 
@Bachstelze:
I think the 9.x series is old enough, and it introduces improvements. I see no reason to stay with 8.x.

I have tried 9.0 on two (very different) machines, both were hard freezing several times a day. No problem with 8.3. (I mean 9.0-RELEASE, not 9-STABLE, I haven't tried the latter.)

---

