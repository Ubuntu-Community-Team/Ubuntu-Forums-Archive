---
title: "WINE + DVDShrink + DVDDecrypter= NOT WORKING"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by slayer666metallica on 2007-07-13
Hey guys; I just installed wine today so that way I could install DVD Decrypter and Shrink in order to take care of my dvd backup needs in linux. 


...but; 

1. DVD Decrypter doesn't detect any drives at all on start up.

2. DVD Shrink WILL detect the drive and show the name of the movie per "Open Disc" dialog; but will then deliver an error message saying : "Failed to read D:\ --Cannot Continue"



I even followed the instructions exactly as the Ubuntu HowTo said...but this is what I've been left with.


...any ideas?

---

### Post by slayer666metallica on 2007-07-13
UPDATE:


I just read somewhere about how you need to enable something called "scsi emulation' in linux for it to correctly recognize the drives...

..is this right???


if anyone knows what I should do to fix my prob; lemme know!

---

### Post by Sweet Spot on 2007-07-16
> **slayer666metallica said:**
> Hey guys; I just installed wine today so that way I could install DVD Decrypter and Shrink in order to take care of my dvd backup needs in linux. 


...but; 

1. DVD Decrypter doesn't detect any drives at all on start up.

2. DVD Shrink WILL detect the drive and show the name of the movie per "Open Disc" dialog; but will then deliver an error message saying : "Failed to read D:\ --Cannot Continue"



I even followed the instructions exactly as the Ubuntu HowTo said...but this is what I've been left with.


...any ideas?

Not sure about (just don't remember) the scsi emulation part, but from my experience in using WINE for almost the past year, there were times when DVD shrink just couldn't get past the encryption, and I'd get the same message. I'd then boot into Windows, and SOMETIMES DVD Shrink in Win, would be able to read and decode it, but sometimes not... Hit and miss. 

That's when I started using DVD decryptor in Windows, but think I've only had to use it like twice. Now, I've got a freshly installed Feisty, and totally got rid of Windows ! I'm currently debating whether or not to install WINE at all, because I'm hoping that somewhere out there is a native linux app which can make ISO's .

---

### Post by Malta paul on 2007-07-16
I am using 'DVDFab HD Decrypter' and 'DVD Shrink' with wine on Ubuntu 7.04 and they work fine :)

---

### Post by deadlikeoscar on 2007-07-16
Haven't installed DVD Shrink in Linux but for DVD Decrypter try going to Tools-->Settings-->I/O and selecting ASPI interface and see what it does.

---

### Post by jkeyes0 on 2007-07-16
Personally, I used to use DVD Shrink in windows, and I've moved to K9Copy in Ubuntu. I find it has pretty much the same functionality, and it's a native program (it's in the repos, just type "sudo apt-get install k9copy" to get it)

---

### Post by deadlikeoscar on 2007-07-16
I would recommend following this article and see if it helps.

[http://mrbass.org/linux/ubuntu/dvdshrink/]("http://mrbass.org/linux/ubuntu/dvdshrink/")

---

### Post by C.S.Cameron on 2007-07-17
In Decrypter set Tools, Settings, I/O to SPTI, (Default).
In System, Preferences, Wine Configuration, Applications, (add DVDDecrypter from Prog Files)
Set Windows version as NT 4.0
Works for me

---

### Post by crispy_420 on 2007-07-17
Run 'winecfg' to set up wine emulation and select drives you want to use.

Set OS as NT4.

Pick drives or let it search for them.

---

