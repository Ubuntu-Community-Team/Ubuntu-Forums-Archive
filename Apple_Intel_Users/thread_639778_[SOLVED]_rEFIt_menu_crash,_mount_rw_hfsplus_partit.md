---
title: "[SOLVED] rEFIt menu crash, mount rw hfsplus partition to rename EFI folder"
date: 2007-12-13
forum: Apple Intel Users
---

### Post by edwford on 2007-12-13
I have tried to make my ubuntu (gutsy :) ) partition on my macbook automount my hfsplus partition for mac osx, this isnt just to access files, because I can easily read all my files, I need to rename a folder in my hfsplus partition. This is the EFI folder used by rEFIt. I need to do this so that rEFIt won't load at startup, because rEFIt crashes not allowing me to select my OS, however if I press the alt/option key i can bypass rEFIt, but this just lets me boot either Ubuntu, a CD (Linux live),  or rEFIt (NOT OSX!!!!). Gladly I still have Ubuntu :) . I desperately need help in finding a solution however it may be to this problem, I can't make any alterations in OSX, because I can't load it. I also don't currently have my Tiger CD's, they are at home, and I am away. And finally I can't get onto the internet on the said macbook, because i have not got the wifi drivers installed on it, however a friend has kindly allowed me to use their laptop. So i may be able to download the drivers and install them if it is absolutely needed. Any help in solving this hard problem will be greatly appreciated.

---

### Post by cyberdork33 on 2007-12-13
> **edwford said:**
> I have tried to make my ubuntu (gutsy :) ) partition on my macbook automount my hfsplus partition for mac osx, this isnt just to access files, because I can easily read all my files, I need to rename a folder in my hfsplus partition. This is the EFI folder used by rEFIt. I need to do this so that rEFIt won't load at startup, because rEFIt crashes not allowing me to select my OS, however if I press the alt/option key i can bypass rEFIt, but this just lets me boot either Ubuntu, a CD (Linux live),  or rEFIt (NOT OSX!!!!). Gladly I still have Ubuntu :) . I desperately need help in finding a solution however it may be to this problem, I can't make any alterations in OSX, because I can't load it. I also don't currently have my Tiger CD's, they are at home, and I am away. And finally I can't get onto the internet on the said macbook, because i have not got the wifi drivers installed on it, however a friend has kindly allowed me to use their laptop. So i may be able to download the drivers and install them if it is absolutely needed. Any help in solving this hard problem will be greatly appreciated.Do you have any external devices plugged into your computer? Try unplugging them during bootup, as that can cause problems in rEFIt.

---

### Post by edwford on 2007-12-13
> **cyberdork33 said:**
> Do you have any external devices plugged into your computer? Try unplugging them during bootup, as that can cause problems in rEFIt.

I have my Live CD in atm, but I've already tried disconnecting it. any other ideas? :( 

Please

---

### Post by cyberdork33 on 2007-12-13
> **edwford said:**
> I have my Live CD in atm, but I've already tried disconnecting it. any other ideas? :( 

Please

If you have already disabled journaling, then you just need to access the filesystem with root privs.

Otherwise...
Please keep in mind that **_this is dangerous_**. Do this at the risk of making your HFS+ partition unusable in the future.

```
sudo mount -t hfsplus -o rw,force /dev/sda2 /mnt/temp
```sda2 may need to be changed to match your partitioning.
/mnt/temp should exist already previous to running the command.

---

### Post by edwford on 2007-12-13
> **cyberdork33 said:**
> If you have already disabled journaling, then you just need to access the filesystem with root privs.

Otherwise...
Please keep in mind that this is dangerous. Do this at the risk of making your HFS+ partition unusable in the future.

```
sudo mount -t hfsplus -o rw,force /dev/sda2 /mnt/temp
```
sda2 may need to be changed to match your partitioning.
/mnt/temp should exist already previous to running the command.


O.k. I tried this, and it just mounted it as usual, I'm not sure if journaling is enabled or not, it is probably at whatever the default is. It won't allow me to rename the EFI folder, (or just read/write in general). It also won't let me change the permissions because i am not the owner...

Is there a way i can "login" so to say, to access the folders? I don't think it will let me unless I put in my password etc. My ubuntu login name and password is the same as my OSX one, if that makes any difference whatsoever. 

:confused:

---

### Post by cyberdork33 on 2007-12-13
> **edwford said:**
> O.k. I tried this, and it just mounted it as usual, I'm not sure if journaling is enabled or not, it is probably at whatever the default is. It won't allow me to rename the EFI folder, (or just read/write in general). It also won't let me change the permissions because i am not the owner...

Is there a way i can "login" so to say, to access the folders? I don't think it will let me unless I put in my password etc. My ubuntu login name and password is the same as my OSX one, if that makes any difference whatsoever. 

:confused:
make changes as root as your ubuntu user does not "own" the files on your osx partition.

ala:
```
sudo mv efi efi_bak
```

---

### Post by edwford on 2007-12-13
> **cyberdork33 said:**
> make changes as root as your ubuntu user does not "own" the files on your osx partition.

ala:
```
sudo mv efi efi_bak
```

O.k. I did this, i renamed the efi folder that is in /mnt/macosx it was renamed successfully

however now when i boot up my macbook it automatically loads ubuntu, and doesn't have mac osx as an option. however if i press the alt/option key i can still choose everything i could when i made my original post. Do i have to rename the efi folder in my user folder? I'm still stuck :confused:

---

### Post by cyberdork33 on 2007-12-13
> **edwford said:**
> O.k. I did this, i renamed the efi folder that is in /mnt/macosx it was renamed successfully

however now when i boot up my macbook it automatically loads ubuntu, and doesn't have mac osx as an option. however if i press the alt/option key i can still choose everything i could when i made my original post. Do i have to rename the efi folder in my user folder? I'm still stuck :confused:

Well, my guess is what it really what I figured initially, that your Mac is not recognizing the OSX partition as bootable. (rEFIt doesn't do the booting, it just uses the EFI).  You are probably going to need the OSX disc to fix the system (some file is not blessed properly?). Ubuntu starts because it is seen as the only bootable system.

---

### Post by edwford on 2007-12-13
> **cyberdork33 said:**
> Well, my guess is what it really what I figured initially, that your Mac is not recognizing the OSX partition as bootable. (rEFIt doesn't do the booting, it just uses the EFI).  You are probably going to need the OSX disc to fix the system (some file is not blessed properly?). Ubuntu starts because it is seen as the only bootable system.

ok... so i guess I have to wait till i have an install disc to use, and then use some sort of repair on the disc? do i just boot from the disc? 

Will I be able to use any install disc i.e. borrow one off of somebody? or will I have to use the one that came with my macbook?

I don't think I will be able to get one until 4 days from now. :(

---

### Post by cyberdork33 on 2007-12-14
> **edwford said:**
> ok... so i guess I have to wait till i have an install disc to use, and then use some sort of repair on the disc? do i just boot from the disc? 

Will I be able to use any install disc i.e. borrow one off of somebody? or will I have to use the one that came with my macbook?

I don't think I will be able to get one until 4 days from now. :(
you just need to boot a osx disc and use the disk utility to do a repair.

---

### Post by edwford on 2007-12-16
> **cyberdork33 said:**
> you just need to boot a osx disc and use the disk utility to do a repair.

It's all fixed now thanks for the help, ended up being the stupidest problem, My "Macintosh HD" was renamed to a load of jumbled letters, im guessing by accidental keypad pressing, and i guess when i turned off my computer i hadn't fixed it, and rEFIt didnt recognise this. However upon using the OSX install disc, i was able to tell it to boot from the strangely named hard drive and then i just renamed it and everything works fine now, i can also now finally use the internet on both ubuntu and osx 

I'm a happy chappy, thanks for the help :)

---

### Post by edwford on 2008-03-02
O.k Problem solved btw, this happened because the "Macintosh HD" had been renamed prior to shutdown and this caused rEFIt to be unable to detect the OSX partition. However via booting using the Install CD I was able to easily change the name back to Macintosh HD. And then it worked instantly. It was just a matter of getting hold of that CD.

---

