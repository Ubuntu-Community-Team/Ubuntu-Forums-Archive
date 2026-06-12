---
title: "Can you burn an install boot cd from a Mac for a PC and it actually work?"
date: 2010-07-03
forum: Apple Hardware Users
---

### Post by al148 on 2010-07-03
Been messing with this all night.  I cannot get all the files to burn properly.  I am also creating a floppy to force the PC to boot from CD.  Trying to wipe out an old Windows NT OS that is password protected (old comps from a company that did not wipe the OS before giving away).  Thanks for any help!!

---

### Post by khuttger on 2010-07-04
So what OS are you using to burn?

---

### Post by krishnandu.sarkar on 2010-07-04
Sorry....But could not understand your question. What is your problem??

---

### Post by al148 on 2010-07-04
OS X 10.6 - I am trying to use my Macbook to burn an install cd for an older PC to boot from.  All of the flies do not burn correctly.  So now I am trying anything to get this to work.  I am trying to remove Windows 2000 NT from the older computer and replace with Linux since I do not have the password for Windows.

Thanks for the help!

---

### Post by khuttger on 2010-07-04
How do you know that it is not burning correctly? 

Try getting ISOBurn or something, maybe the settings arent right =/

---

### Post by krishnandu.sarkar on 2010-07-04
Ok....do as khuttger said. Do you've the Ubuntu ISO??? If not then download it. Burn the ISO and format the whole PC(Older one)

---

### Post by al148 on 2010-07-04
Not all of the files end up on the disc.  Did the .iso and still won't boot.  So trying the Floppy to force the old computer to boot from CD.  The BIOS has an alternative option and not Boot from CD.  Just didn't know if going from a mac to a pc some of the files were lost some how?  I read every FAQ and I still can't get it to work. I will not give up!!

---

### Post by al148 on 2010-07-04
I used Infrared like Ubuntu suggested.

---

### Post by jflaker on 2010-07-04
> **al148 said:**
> Been messing with this all night.  I cannot get all the files to burn properly.  I am also creating a floppy to force the PC to boot from CD.  Trying to wipe out an old Windows NT OS that is password protected (old comps from a company that did not wipe the OS before giving away).  Thanks for any help!!

an ISO is a disk image, whether it is a hard disk, a cd or a floppy, it shouldn't get changed during the burn.  You would, however, need to use an ISO utility to do this, just copying the ISO file to a cd won't work (need to say this because I've seen people do this.).

However, if you burn the cd at a high speed, you may have trouble reading it on an older system for one or both reasons....the high speed cheap CD's aren't really reliable at the speed they advertised and were burned at and/or the PC the cd will be read in either has a slower cd drive or the drive is deteriorated and can't reliably read that cd.

I have always burned at at the slowest speed supported by the ISO utility so that most any computer will not have trouble reading it and the blank CD performs well.  I've never had issues with a slow burnt CD...except that it is also slow on the read...but thats a tradeoff.

another option is to try UNetBootin ([http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")) to make a USB drive version of the Live CD.

---

