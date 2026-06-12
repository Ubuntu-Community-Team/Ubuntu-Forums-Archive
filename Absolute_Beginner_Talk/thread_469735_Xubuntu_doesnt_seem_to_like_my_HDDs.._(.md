---
title: "Xubuntu doesnt seem to like my HDDs.. :("
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by hobs0n on 2007-06-10
Typed this in another thread I made but I thought Id make a seperate thread for the HDD problem.

 I just burned Xubuntu and tried to install it, after I pressed "install and/or run xubuntu" in the first menu on the bootcd it start complaining about HDD errors, it says "revalidation failed", "buffer I/O error on dev fd0 logical block 0" "ata5.01 failed to set xfermode (err_mask=0x40). After a while it start erroring on ata6 too and then after about 5-10mins the screen goes blank. I got my 4 of my 5 HDDs on the Promise Ultra 133TX2 PCI IDE controller card and I guess that Ubuntu doesnt like that controller card? The last HDD I have on the built-in IDE controller of the MSI K9AGM2-FIH Motherboard. Anyone got any idea whats going on??

EDIT: found a thread where Mikeshardlinux said he had the same card as I got and it worked. Why doesnt Linux like me?

EDIT2: WTF (( I disconnected the 4 Promise controler HDDs and only had the HDD on the built-in controller, booted up a xp install cd and deleted the partition and ran the Xubuntu install cd again, same error, tho now it only says "buffer I/O error on dev fd0 logical block 0" i think, I havent watched so long... I bought this HDD 4 days ago, I have a hard time it has just broke when I had windows server 2003 installed on it 2 days ago!

EDIT3: I forgot to mention that I only have a TV connected to the server by the composite output, not a regular screen.

---

### Post by confused57 on 2007-06-10
Have you tried the cd that you burned on another computer?  Did you burn it at a low speed(8x or less) as an image and was the md5sum of the iso OK?   The Promise controllers weren't supported on earlier versions of Ubuntu, but Feisty probably does, I don't know for sure.  Other that the cd you're using or your cd drive, I'm not sure what your problem might be.

---

### Post by hobs0n on 2007-06-10
> **confused57 said:**
> Have you tried the cd that you burned on another computer?  Did you burn it at a low speed(8x or less) as an image and was the md5sum of the iso OK?   The Promise controllers weren't supported on earlier versions of Ubuntu, but Feisty probably does, I don't know for sure.  Other that the cd you're using or your cd drive, I'm not sure what your problem might be.

I burned it with max speed with Nero and used the verify data so it works, burns everything in max speed with verify, always works. Im gonna try later to put the HDD on my main compter and see if that one can find any fault with it.

---

### Post by qamelian on 2007-06-10
> **hobs0n said:**
> I burned it with max speed with Nero and used the verify data so it works, burns everything in max speed with verify, always works. Im gonna try later to put the HDD on my main compter and see if that one can find any fault with it.

All you've done is verified that the data on the disc is good and can be -reread on the drive on which it was written.. The only way to ensure that a disc can be read on other drives is to burn at the lowest speed possible. The faster you burn a CD/DVD, the less likely it is that it will be readable in a different drive.

---

### Post by hobs0n on 2007-06-10
> **qamelian said:**
> All you've done is verified that the data on the disc is good and can be -reread on the drive on which it was written.. The only way to ensure that a disc can be read on other drives is to burn at the lowest speed possible. The faster you burn a CD/DVD, the less likely it is that it will be readable in a different drive.

Hmz that is true but one thing I forgot to mention was that I burned it with my external burner that I also connect to my server so its burned and read on the same drive and I really really dont think this is a problem of the Xubuntu CD being hard to read from...

---

### Post by hobs0n on 2007-06-10
I put the HDD in my main computer and partitioned it, formated it and double checked it, no errors what so ever. Hence Xubuntu is talking BS. When I had the HDD removed I started from the Xubuntu CD install again to check the CD so it was really working and it complained about the fd0 error again, I looked it up and fd0 is floppy drive, I dont even have a floppy drive!! So I disabled the floppy drive in the BIOS and ran the install cd again to check the cd again, it came some way, then it stopped and said "/bin/sh: cant access tty; job control turned off" I assume there are supposed to be lots more when it test the cd?

What the hell is wrong with Xubuntu, is it the buggiest OS that exists????

EDIT: I assume that its the drivers for my AMD 690G chipset that is very very buggy. Anyone got any smart idea to get Xubuntu to work on my server?

---

