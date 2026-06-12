---
title: "First time with linux"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by midon on 2006-11-02
Ok First I know that there is a lot of infortmation out there and I have read a lot of it, but I doent understand. I have tried to do just like it ahows but I still cant figure it out.

Problem. I have a 7.5 gig Hdd for ubuntu it works fine no problems there 

I have a secound Hdd 40 gig I want to use for storage. I can see the drive in disk manager. and I can see it's w95 fat 32 I tried to format it to vfat and to mount it to /file hdd  but after I do this in disk manager I cant access the drive. I can find the folder /file hdd but it shows it to be only 4.2 gigs. thats what is left on hda. I also noticed in disk manager that the device was not active. I clicked on activate but it dident do any thing. I have restarted the computer and it still is the same.

Here is what I do know.

hda 7.5gb works fine

hdb 40 gb it shows up when I go to places-computer. I click it and I get this message "unable to mount selected volume error:device /dev/hdb1 is not removable Error: could not execute prmount"

when I do fdisk -l it shows me 

/dev/hdb1  boot *  start 1   end 4865   blocks 39078081  id b  system w95 FAT32

I need some one to show me what to do step by step. I looked at everything I could on here for anything related to mounting formating and secound hard drives. I tried some of the stuff but I still codent get it to work. Please Help

---

### Post by theicyj on 2006-11-02
I would recommend checking out [this guide]("http://www.psychocats.net/ubuntu/mountwindows").  I am by no means a Linux expert, but the following should work fine to based on the info you gave.

1. Make a folder that you want to be able to access the hard drive from. For instance: /home/username/hard_drive2

2. Open the terminal (Applications -> Accessories -> Terminal)

3. Type: 
> sudo gedit /etc/fstab
4. Type password

5. Now add the following line at the end of the file somewhere (noting to replace "/home/username/hard_drive2" with the address to the appropriate folder from step 1):

> /dev/hdb1 /home/username/hard_drive2 vfat iocharset=utf8,umask=000 0 0

6. Now save the file and close gedit.

7. Reboot and now you should be able to have access to the files on the hard drive by going to "/home/username/hard_drive2" or whatever folder you made!

---

### Post by pay on 2006-11-02
Welcome to Linux and Ubuntu
Edit: theicyj said the same thing as me (pretty much) and just beat me to it

Formating isn't necessary 
1) Add the drive the the fstab 
```
sudo nano /etc/fstab
```and add theses lines at the end
```
/dev/hdb1 /media/hdb1 vfat defaults 0 0
```

2) make the folder to which you want to mount it (if you mount it at /media then it will show up on your desktop)
```
sudo mkdir /media/hdb1
```

3) remount all drives
```
sudo mount -a
```or restart the computer

---

### Post by midon on 2006-11-02
> **theicyj said:**
> I would recommend checking out [this guide]("http://www.psychocats.net/ubuntu/mountwindows").  I am by no means a Linux expert, but the following should work fine to based on the info you gave.

1. Make a folder that you want to be able to access the hard drive from. For instance: /home/username/hard_drive2

2. Open the terminal (Applications -> Accessories -> Terminal)

3. Type: 

4. Type password

5. Now add the following line at the end of the file somewhere (noting to replace "/home/username/hard_drive2" with the address to the appropriate folder from step 1):



6. Now save the file and close gedit.

7. Reboot and now you should be able to have access to the files on the hard drive by going to "/home/username/hard_drive2" or whatever folder you made!

ok just tried this. I typed it all in and then saved but it told me this. "could not save file /ect/fstab unexpected erroe file not found" When fstab loded it was blank I still tried to type this in and save it but it woent save.

---

### Post by devilsadvocate1987 on 2006-11-02
you have a typo there. its supposed to be etc. and it will not be blank.

---

### Post by midon on 2006-11-02
> **devilsadvocate1987 said:**
> you have a typo there. its supposed to be etc. and it will not be blank.

ok now i noticed it. It came up with some stuff and there is a hda1 hda2 hda3 and then a hdc line were should I put the stuff for hdb1 at?

---

### Post by midon on 2006-11-02
never mind just did it and put it befor the hdc line restarting right now

---

### Post by midon on 2006-11-02
ok restarted I can see the new folder and when i click it it shows there is only 4.2gb left that tells me it's on the hda drive. I decided to check the dick manager and it shows the path correct but it still shows it as inaccessable. I click actavate but nothing happens.

---

### Post by midon on 2006-11-02
ok I have tried every thing I can think of and still nothing. I think I will reinstall ubuntu fresh on a spare 80gb hard drive and just patrition it to what I need. Thanks for the help yall did give me some good information.

---

### Post by floridauser007 on 2006-11-02
> **midon said:**
> ok I have tried every thing I can think of and still nothing. I think I will reinstall ubuntu fresh on a spare 80gb hard drive and just patrition it to what I need. Thanks for the help yall did give me some good information.

Well I think the controller plays a role in whether or not a partition greater than 8 GB is possible when using vfat (fat32).  From your primary drive being under 8.0 gb I highly suspect this.  I am no expert on this but here is something to look at:

[http://www.seagate.com/support/kb/disc/fat32.html](http://www.seagate.com/support/kb/disc/fat32.html)

Look at the part speaking of the controller and interrupt 13?

---

### Post by CatKiller on 2006-11-02
> **midon said:**
> ok restarted I can see the new folder and when i click it it shows there is only 4.2gb left that tells me it's on the hda drive.

I guess you're referring to the "Free space" indication in the bottom left of the Nautilus window? Unless you go into the folder you've got as the mount point - **really** in, so that the contents are displayed in the larger pane, that will continue to show the free space on the / partition.

---

