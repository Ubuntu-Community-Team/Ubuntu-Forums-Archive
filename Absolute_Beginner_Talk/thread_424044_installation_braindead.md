---
title: "installation braindead"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by croxi on 2007-04-26
right, well, I´ve recently downloaded UBUNTU 7.04, burned it to CD and tried to install it on my laptop. Every time I try to install it, the laptop ignores the CD and carries on booting up Windoze and I´m sick of it. 

What am I doing wrong? Any help would be really welcome...

---

### Post by taurus on 2007-04-26
How did you burn it?  Did you burn it to a CD as an image file, NOT data file?  Also, did you look in the BIOS to make sure you have CD-ROM as the first device in the boot order.

---

### Post by jfinkels on 2007-04-26
> **croxi said:**
> right, well, I´ve recently downloaded UBUNTU 7.04, burned it to CD and tried to install it on my laptop. Every time I try to install it, the laptop ignores the CD and carries on booting up Windoze and I´m sick of it. 

What am I doing wrong? Any help would be really welcome...

You may have to change the boot order in your BIOS. When the computer first turns on, press <Delete> or <F2> to enter setup (there should be an instructional message telling you which button it is). Once you are in your BIOS setup, find "boot order" and change it so that the system boots from CD drive before hard disk drive.

---

### Post by croxi on 2007-04-26
I burned the CD using Nero 7 and it was done as a data file. Oh, and I didn't know I needed to change the BIOS, so you learn something new every day. 

Thanks for that.

---

### Post by taurus on 2007-04-26
You must burn it as image file.  And when you insert the CD under Windows, you should see a bunch of files and directories instead of one large file that you downloaded.

Therefore, you need to go back and burn it again and try to burn it at a slow speed like 4x if you can.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

### Post by croxi on 2007-04-26
ok, well, I´ve changed the BIOS to CD and the CD STILL isn't being recognised. 

it just gets ignored like before. Any suggestions anyone?

---

### Post by Ateo on 2007-04-26
> **croxi said:**
> right, well, I´ve recently downloaded UBUNTU 7.04, burned it to CD and tried to install it on my laptop. Every time I try to install it, the laptop ignores the CD and carries on booting up Windoze and I´m sick of it. 

What am I doing wrong? Any help would be really welcome...

Maybe you need to update your BIOS. If you have set it to boot from CD, then it should. Can you boot from other bootable CDs? Like your copy of Windows?

---

### Post by doomster on 2007-04-26
as you said , you burned the cd as an data disk. you wiill have to select "Burn image file" from nero, else you will have one cd  with an iso file inside it. 
select from nero "Burn a image cd to disk", and select the downloaded image of ubuntu. 
after that, the cd will be bootable:)

---

### Post by croxi on 2007-04-26
I´m technically still a basic user, so I never had to update my BIOS, and I don't know how.

---

### Post by croxi on 2007-04-26
> **doomster said:**
> as you said , you burned the cd as an data disk. you wiill have to select "Burn image file" from nero, else you will have one cd  with an iso file inside it. 
select from nero "Burn a image cd to disk", and select the downloaded image of ubuntu. 
after that, the cd will be bootable:)

just doing that right now actually, so I´m learning quicker than I thought. 

cheers

---

### Post by taurus on 2007-04-26
You don't have to update the BIOS.  Just burn it again but this time, burn it as an image file.

Again, you should see a bunch of files and directories if you burn it properly.  But if you see one large file, then it will _never_ boot because you basically just copy the image on your harddrive to a CD.

---

### Post by croxi on 2007-04-26
got it sorted now, thanks to everyone for the help

---

### Post by croxi on 2007-04-26
One last question, though, is that when I installed UBUNTU 7.06 onto the laptop, when I come to switch off the machine to test and see if its 100% sorted, it just goes back to Windoze. so what's wrong with what I´m doing?

Is there a solution?

---

### Post by croxi on 2007-04-26
I tried to load up UBUNTU and it seems that I need to have the CD in the machine for the OS to work, what's the best way that I can do it, so that I can forget having to use the CD every time i want to swap between UBUNTU and WINDOZE

---

### Post by taurus on 2007-04-26
You need to install GRUB (Linux bootloader) to MBR so you can use it to boot either Ubuntu or Windows.

---

### Post by croxi on 2007-04-26
what do I do with the partition manager if it won't do an automated partition and keeps asking me to specify a particular amount of space I think is sufficient for a partition. But I don't know what amount I should make a partition. 

I have the following on my "edit partition" screen :-

DEVICE                       TYPE                         MOUNT POINT              FORMAT      SIZE        USED

/DEV/HDA                    

    /DEV/HDA1             fat32                       /MEDIA/HDA1                                    4194mb    1500mb
    
    /DEV/HDA2             ntfs                          /MEDIA/HDA2                                    45823mb  0mb

What should I do regarding this? Which one should I use?

---

### Post by jfinkels on 2007-04-26
> **croxi said:**
> what do I do with the partition manager if it won't do an automated partition and keeps asking me to specify a particular amount of space I think is sufficient for a partition. But I don't know what amount I should make a partition. 

I have the following on my "edit partition" screen :-

DEVICE                       TYPE                         MOUNT POINT              FORMAT      SIZE        USED

/DEV/HDA                    

    /DEV/HDA1             fat32                       /MEDIA/HDA1                                    4194mb    1500mb
    
    /DEV/HDA2             ntfs                          /MEDIA/HDA2                                    45823mb  0mb

What should I do regarding this? Which one should I use?

Right now, it appears as if your hard disk is full and has no unallocated space. If you want to install Ubuntu, you will have to delete one of the partitions (either /dev/hda1 which uses the fat32 filesystem, or /dev/hda2 which uses the ntfs filesystem) to make room for Ubuntu. Do you know what is on each of the partitions? Most likely, your Windows operating system is on /dev/hda2, the ntfs partition.

Tell us what your partitions contain, and then we'll see if we can help you rearrange and make some room.

---

