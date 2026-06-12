---
title: "Booting from USB"
date: 2010-11-16
forum: Apple Hardware Users
---

### Post by jackhe22 on 2010-11-16
Hey guys, I know this question has been asked and moaned about so many times with a Mac, but I think I have a cunning plan to make it work!!!

Doing some experimentation with the XP Home BootCamp on my MacBook, I installed Wubi. (Yes, installed Wubi, on a BootCamp partition, on a Mac). Amazingly, it works flawlessly! But I thought up something while considering the issues with booting from USB on a Mac.

Correct me if I'm wrong, but my theory is this:
Its the EFI and the Firmware which has compatibility issues with booting from USB....
But when running BootCamp to use a Windows Partition, it emulates BIOS, which nowadays is good with booting from USB..

So, If I select to boot from Windows, which then leads to another selection asking for Ubuntu (GRUB) or Windows, you could select Ubuntu, which chucks you up at the standard version of GRUB, which to my understanding does support from USB booting? Select your stick and your off.
If somebody would be willing to try this theory or correct me, maybe you could think up some easier way in which to boot from a USB with a Mac.:popcorn:

---

### Post by jackhe22 on 2010-11-18
Bump

---

### Post by dev d on 2010-11-20
Booting a computer from your USB flash drive may seem like a daunting  task, but it is actually quite easy. With the right equipment and some  basic knowledge, this very useful technique can be taken advantage of in  all sorts of different circumstances. 
[LEFT]The first thing you will need to do this is a compatible  USB flash drive. Most drives are bootable but some are not, so it pays  to ask before making a purchase or to do a bit of research online before  picking your drive. This is not something the average salesperson will   know nor do most companies make it clear on the packaging, so the  internet is your best source here. Try to find a drive which has been  used successfully in the past, like Corsair's Flash Voyager. The size of  the drive is going to be an issue depending on your requirements. If  you need to place an entire  operating system on the drive, for example,  you may need something a bit larger than what you have lying around.[/LEFT]
      [LEFT]The next step is to make sure that the motherboard  which you are working with supports USB booting. To do this simply enter  the BIOS (this can usually be done by press the Delete key while the  computer is posting) and go into the menu selection titled something  like, "Advanced Features". This process is a bit different for every  BIOS so you may have to search a bit. Once here look for the boot  devices, which will be placed in order: 1st, 2nd, 3rd, and so on.  Normally the computer will attempt to boot from the CD-ROM or a specific  hard drive first, but you want to change this to the USB drive. The  proper selection to do this varies depending on your BIOS version but it  be USB RMD-FDD, USB ZIP, USD HDD, USB CD-ROM, or something close to  these. Once these is chosen as the 1st boot device you can move your  hard drive and/or optical drive down the line (so they will be used if a  USB device is not present) or remove everything (so that the computer  will only boot from USB). A little trial and error may be needed here to  make sure you have chosen the right boot device. [/LEFT]
---------------------------------------------------------------------------------------
[  kruger national park tours]("http://www.touristotours.com/")
[  kruger national park tours]("http://www.touristotours.com/")
[  kruger national park tours]("http://www.touristotours.com/")

---

