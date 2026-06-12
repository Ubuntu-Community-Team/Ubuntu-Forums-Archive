---
title: "WINE anyone?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-04-21
Hi

I have installed Dapper Drake Beta (AMD64 bit version) and cannot get any *.exe programs to run.  I have managed to do this in the past using the 'WINE' emulator on the i386 version of Breezy Badger.  There appears to be no listing for 'WINE' in the repositries and it does not appear to be installed on this install... if that makes any sense.

Any help will be greatly appreciated.

Thank you

---

### Post by mostwanted on 2006-04-21
Enable the multiverse and universe repositories. WINE is not in the mian repository.

---

### Post by Kimm on 2006-04-21
I'm not sure wine will run on 64-bit Linux without some tweeking, you might need to set up a "fake" 32-bit system and run wine through that... if compiled as 64 bit the wine libraries would be 64-bit, and the .exe would be 32-bit, that just wount work, even windows has to emulate old apps.

I dont have a 64bit CPU, so I cant try this, but it looks cinda good.

[http://ubuntuforums.org/showthread.php?t=24575&highlight=HOWTO+chroot+wine](http://ubuntuforums.org/showthread.php?t=24575&highlight=HOWTO+chroot+wine)

---

### Post by Norfolk 'n' Good on 2006-04-21
Thank you for your responses.  It makes absolute sense that since I am running a 64 bit system, running 32 bit apps will require some tweaking.  I'm relatively new to Linux at the moment and software tweaking is beyond me at the moment.  It also explains why I cannot find WINE anywhere in the Dapper Drake repositories!  

Still, despite this small drawback I am pretty much converted to this wonderful operating system.

Cheers  :-D

---

