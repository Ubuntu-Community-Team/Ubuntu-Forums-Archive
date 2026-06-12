---
title: "2 Harddrives Auto-Booting Into Windows Slave Drive.  Help??"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by SaltyMcCracker on 2006-10-25
Ok, 

I'm using 2 HDDs.  In 2003 I built this computer and installed windows xp on a 80GB hdd.  I recently decided to jump into the linux world, but I'm not ready to ditch windows.

So, I've acquired an old 40GB HD.

**So I set the windows drive to cable select, the linux drive to master** and installed ubuntu (but it didn't ask me to install GRUB)it doesn't recognize the 80 GB drive as a windows drive.  

Next I decided to try a different distro, Mandriva One.  Installed mandriva, and LILO (again didn't recognize hdb as a windows drive but added it manually).

Now when I restart the system goes straight into windows, no LILO.  So I figure, hey maybe I really don't know anything about  computers.  So I switch cables, jumpers...I pretty much **checked all hardware systematically**.  I went into bios and sure enough the 40 GB drive is listed as master and the 80 GB drive is listed as slave.  

When I unplug the slave drive, **LILO loads with a 10 second timeout, so its not that the time is set to zero.  **

So I decided to try Mandriva with GRUB.  Same thing happens.

I can't get into either distro with both drives attached without using a live cd so I can't edit the GRUB/LILO file.  Any help or input would be really appreciated.  Thanks guys!

---

### Post by jorn on 2006-10-25
Is there an option when booting to select bootdevice? Are both hd's listed there? Are both IDE devices? 
Have you tried not using 'cable select'?

---

### Post by SaltyMcCracker on 2006-10-25
> **jorn said:**
> Is there an option when booting to select bootdevice? Are both hd's listed there? Are both IDE devices? 
Have you tried not using 'cable select'?


I haven't seen that option.  I can enter bios setup by pressing del.  and AWD Flash mode by pressing F8.

I've tried the following jumper configurations.  HDD's will be simplified as a and b

1) a- master
   b - slave

2) a- master
   b- cable select

3) a- cable select
   b- cable select

---

### Post by thoffland on 2006-10-25
I know that this doesn't help you much, but I tried installing windows and ubuntu on my pc with two SATA drives and had a similar problem. the SATA drives are supposed to automatically figure one as a master and one as a slave. After installing ubuntu, I couldn't boot into windows. If I did a "fdisk /mbr" on the windows drive, then I could only boot to windows. I even tried manually connecting and disconnecting each drive so that I could run them separately, but the CMOS kept getting messed up so I just gave up. 

It was a good thing though, now I'm running only linux and have windows installed in vmware so I can take care of my online school needs. 

Maybe that's a good solution for you too. 80g is plenty of space, I'm running mine on 36g now, but will upgrade it to a larger drive soon.

---

### Post by Bachstelze on 2006-10-25
Wrong. "Master" and "Slave" don't exist in SATA.

@threadstarter, you should be able to configure which drive you want to boot from in your BIOS. When you set the boot devices (CD, floppy, USB, LAN, whatever), both drives should appear in the list. Also, try setting one as master and the other as slave, no cable select.

---

### Post by SaltyMcCracker on 2006-10-25
> **HymnToLife said:**
> Wrong. "Master" and "Slave" don't exist in SATA.

@threadstarter, you should be able to configure which drive you want to boot from in your BIOS. When you set the boot devices (CD, floppy, USB, LAN, whatever), both drives should appear in the list. Also, try setting one as master and the other as slave, no cable select.

I've done both of those suggestions.

---

### Post by Bachstelze on 2006-10-25
Now that's weird... Where did you install GRUB/LILO/whatever bootloader you installed ? I guess the easiest way would be to reinstall it on the MBR of the boot drive.

---

### Post by SaltyMcCracker on 2006-10-25
> **HymnToLife said:**
> Now that's weird... Where did you install GRUB/LILO/whatever bootloader you installed ? I guess the easiest way would be to reinstall it on the MBR of the boot drive.


I installed lilo on the master (linux) drive.  So you would suggest installing it on the windows drive?

---

### Post by Bachstelze on 2006-10-25
It definitely would work. I guess if you don't want to investigate the problem any further, that's the best thing to do, you won't notice any difference when using it anyway. But I can't help you with LILO configuration, GRUB all the way for me :)

You could also configure NTLDR (Windows bootloader) to have the option to chainload your LILO, but I don't know how to do that, either :p

---

