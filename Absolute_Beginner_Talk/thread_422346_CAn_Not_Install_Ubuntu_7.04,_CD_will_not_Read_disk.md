---
title: "CAn Not Install Ubuntu 7.04, CD will not Read disk on Compaq M700 Armada"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by jamaica on 2007-04-25
I am trying to install ubuntu 7.04 but my cd drive for some reason will not recognize it. I have used the burned cd's on newer laptops and they recognize it but my old m700 will not.  I have not upgraded the bios and i know the cd works since I can read other windows cd's on it. Can you give me any help in how you to install ubuntu on my m700, e.g. other installations that can be accepted? I do not have a floppy drive only the cd.

Thanks for everyone's help.

---

### Post by jhnthn on 2007-04-25
Have you checked the Ubuntu CD for errors? I think there's an option to check CD for defects when it first boots... If you can't check it on the m700 try on one of your newer laptops.

---

### Post by shavenlunatic on 2007-04-25
try booting into your OS (if you have one installed on your laptop) and see if you can read the disk ok.

have you checked your boot sequence in the BIOS to make sure it isn't booting to your HDD first and/or ignoring the cdrom on boot?

---

### Post by shavenlunatic on 2007-04-25
also, it might seem a silly question (but I do know one numpty who did this).  You didn't write the liveCD to a DVD and trying to read it in a laptop with only a CD-ROM and no DVD?

---

### Post by jamaica on 2007-04-25
Shavenlunatic,
Thanks for all your suggestions.
I have tried the CD in my neer laptops and it works so i know the check sum is ok
I checked my boot sequnece the CD is set to first and I can hear the cd trying to read it but it just skips it. Also when i go into windows 2000 (on old laptop) it can not read the disk but my newer laptop can.
I burned it to a CD but in anycase my m700 reads DVD's and CD's.

Thanks again any more ideas?

---

### Post by kilou on 2007-04-25
I had trouble installing Feisty because my computer couldn't read the LiveCD (it could boot on it but always stopped before the install). This was probably because I burned it on a CD-RW although I successfully burned Edgy Live CD on a CD-RW. I didn't have CDs left so I had to find something else and tried to do a LiveUSB install (installing Feisty from a USB disk by copying the iso image and the disk and make it bootable). If your computer support that and you have a USB disk or a USB flash disk you could try that:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Drakkor on 2007-04-25
> I have tried the CD in my neer laptops and it works so i know the check sum is ok
Huh ? ,since when did booting a CD do a md5sum check ? 
I like to get the fundamentals out of the way first, and that would be checking the md5sum of the .iso file you 
downloaded to make sure it verifies, and is not corrupt in any way, then only if that's OK , "Check the CD
for defects" to make sure the CD you burned is OK.  Just because it may boot or even partially install,
doesn't mean it's a "good" CD :)

---

### Post by Nythain on 2007-04-25
so your other pc's can recognize, read, and boot the cd but your older laptop cant boot from it, and windows doesnt see it either... do other cd's work on that pc... how fast did you burn the disk, try downloading the alternate install disk and using it... make sure you burn at a REALLY slow speed... i know it sounds silly, but burn speed has been a random cause of lots of complications for people (myself included)... if none of that seems to help, possibly a malfunctioning cd drive???

---

### Post by jamaica on 2007-04-25
Jhnthn, Kilou, Drakkar and NYthain,

Ok do i did the mdsum check it passed, phew.

I downloaded the alternate cd and burned it at the slowest speed, no recognition by my cd in the old laptop. YEs i did the mdchecksum on this cd as well.

I tried my windows 2000 OEM cd and the old laptop recognized it. SO I guess my fear is that it can't read burned CD's. I ordered the Ubuntu cd but it takes 4-6 weeks ..dang.

I dont want to try the USB thing yet, i guess it would be my last chance, so any more ideas until i get the ubunto cd in the mail?

Thanks again for all the help!

---

### Post by jamaica on 2007-04-30
Just wanted to bump this post to see if anyone had any other ideas?
Thanks!

---

### Post by GrueTamer on 2007-04-30
I wouldn't be surprised if your cd drive was going dead.  This happened to me one time, and yup...that was the problem.

---

