---
title: "Unable to boot Ubuntu - 2 boot drives  one with XP"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by rplourde on 2007-06-20
I am new to Linux (Ubuntu) and am trying to setup my environment for dual boot (XP and Ubuntu). I don't want to replace the MBR and I am unable to setup grub to dual boot. 
From XP my env. look like this:
C: 152 gigs   NTFS  system
E: 27 gigs     NTFS  active
F: 157 gigs    FAT32  
    1.5 gig      swap unknown
    74 gigs              active

My boot sequence (from bios) is:
1. USB  FDD
2. CD/DVD
3. IDE maxtor (which is c: in fact)


From Ubuntu (after booting  V7.04 from CD) GPARTED is reporting:
/dev/HDA        /dev/HDA1         NTFS            152 gigs       boot
/dev/SDA
                     /dev/SDA1         FAT32           157 gigs       lba
                     /dev/SDA2         LINUX-SWAP   1 gig            ---
                     /dev/SDA3         EXT3             74 gig         boot

/dev/SDB   
                     /dev/SDB1         NTFS            27 gigs        boot
                     /dev/SDB2         FAT32             1 gig          hidden,lba


I did install UBUNTU on SDA3. When I do
sudo grub
find /boot/grub/stage1
I get (HD1,2)


With this setup, I boot Windows without any problem. However I haven't been able to get    to Ubuntu. 

Can somebody help? I saw many references to dual boot and GRUB but nothing  specific to my situation. 

Thanks.

---

### Post by Happy_Man on 2007-06-21
Could you boot from a LiveCD and give us the output of the command: ```
sudo fdisk -l
```

---

### Post by drowner on 2007-06-21
> **rplourde said:**
> I am new to Linux (Ubuntu) and am trying to setup my environment for dual boot (XP and Ubuntu). I don't want to replace the MBR and I am unable to setup grub to dual boot. 
From XP my env. look like this:
C: 152 gigs   NTFS  system
E: 27 gigs     NTFS  active
F: 157 gigs    FAT32  
    1.5 gig      swap unknown
    74 gigs              active

My boot sequence (from bios) is:
1. USB  FDD
2. CD/DVD
3. IDE maxtor (which is c: in fact)


From Ubuntu (after booting  V7.04 from CD) GPARTED is reporting:
/dev/HDA        /dev/HDA1         NTFS            152 gigs       boot
/dev/SDA
                     /dev/SDA1         FAT32           157 gigs       lba
                     /dev/SDA2         LINUX-SWAP   1 gig            ---
                     /dev/SDA3         EXT3             74 gig         boot

/dev/SDB   
                     /dev/SDB1         NTFS            27 gigs        boot
                     /dev/SDB2         FAT32             1 gig          hidden,lba


I did install UBUNTU on SDA3. When I do
sudo grub
find /boot/grub/stage1
I get (HD1,2)


With this setup, I boot Windows without any problem. However I haven't been able to get    to Ubuntu. 

Can somebody help? I saw many references to dual boot and GRUB but nothing  specific to my situation. 

Thanks.

Hi and welcome

when you said 'I dont want to overwrite the MBR', do you mean that during installation you DIDNT let grub write to the MBR?

---

### Post by LaRoza on 2007-06-21
If you didn't write Grub to the MBR, it would be easier if you did. Just in case you are worried about not being able to boot Windows, you can easily restore the MBR with the Super Grub Disk. Check my sig if you want it, it is a handy tool.

---

### Post by atria on 2007-06-21
You can recover the mbr by using your windows xp/windows vista cd as well.

```

fixboot C:
fixmbr

```

Dont worry, go ahead and install grub ;)

---

### Post by rplourde on 2007-06-22
I removed one of my USB drive. So now I have two disks:
1.  internal IDE XP NTFS only (Windows bootloader).
2. external USB drive 
           partition1 - FAT32
           partition 2 - swap
          partition 3 - Ubuntu

I did reinstall 7.04 from CD on external USB drive. At the point during the installation where I got the message about the boot I  did specify (hd1,2). 
After installation was completed, I rebooted my machine (BIOS was changed to boot external USB before internal IDE), didn't get any GRUB messages except the message "Missing operating system".

---

