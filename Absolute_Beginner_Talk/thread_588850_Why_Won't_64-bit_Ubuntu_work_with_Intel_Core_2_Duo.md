---
title: "Why Won't 64-bit Ubuntu work with Intel Core 2 Duo?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Crypto77 on 2007-10-23
Ok basically I have 1.86 ?Intel Core 2 Duo processor with 64-bit Vista installed. When I attempt to install from the Gutsy Gibbon 64-bit Live Cd I get an "I/O error" and am left with the reboot as my only option. I have the standard (ie non 64-bit version) and it my machine has no problems reading from or installing from that disk. Whats up? I know my system can handle a 64-bit OS as I am running 64-bit Vista - so how come it won't work with Ubuntu?

---

### Post by aidanr on 2007-10-23
Could be a bad burn, I'd use the check cd for defects option.

---

### Post by Crypto77 on 2007-10-23
I'll check it again, but I downloaded it two separate times and burned each of them to two separate disks - didn't fix anything.

---

### Post by skymera on 2007-10-23
have you enabled 64-bit in bios?

i know i can turn mine off/on

---

### Post by Crypto77 on 2007-10-23
Well I just re-installed Vista a few hours ago so without even checking the BIOS I am pretty sure that it is enabled.  Ok when I went to check the cd for defects I get the same "I/O error"

---

### Post by nynoah on 2007-10-23
This may be a dumb question, but do you have any other hard drives hooked up when you are trying to install your system.  I had a problem like this.  I had another hard drive in my computer running 64bit Kubuntu.  For some reason it was messing with the clean install on another hard drive for my 71.0 64bit Gutzy Gnome.

---

### Post by Crypto77 on 2007-10-23
Nope - only one hardrive

---

### Post by nynoah on 2007-10-23
Hmmm well I would check out the bios then.  Just wondering, have you tried to install the i386 version to see if that works for you?  I know it is not the answer you wanted.  But just wondering what would happen to the system if you tried the lesser version?

---

### Post by shad0w_walker on 2007-10-23
Have you tried booting with options such as :

noacpi
noapic

I had issues getting Ubuntu running on my 64 bit system (32 bit version admitedly) because of a dodgy BIOS version, flashing it sorted it out for me.

---

### Post by trak87 on 2007-10-23
> **Crypto77 said:**
> I'll check it again, but I downloaded it two separate times and burned each of them to two separate disks - didn't fix anything.

No need to keep downloading the file. But 1) you must check the downloaded iso file's md5sum value (a string of numbers) against the value provided at the download site. This should be done every time one downloads a new version of Ubuntu. There's no other way to insure that you got the exact file. To do this run *md5sum <filename>* at the terminal. Then compare the resulting number with the official one. And 2), you must burn the iso file in "image" mode, a mode suitable for iso files, and not data mode.

Btw, bittorrent seems to be the most accurate way to download the iso files.

---

### Post by Crypto77 on 2007-10-23
After checking the BIOS I cannot find any options as to allow or disallow 64-bit priveleges.  The lesser or "standard" version of Ubuntu does work, but I would rather use the 64-bit version if possible.  I have no version of Ubuntu installed so running terminal is not an option.

---

### Post by shad0w_walker on 2007-10-23
You can still verify the md5sum in windows using this tool: 

[http://portableapps.com/apps/utilities/winmd5sum_portable](http://portableapps.com/apps/utilities/winmd5sum_portable)

---

### Post by Crypto77 on 2007-10-23
I will try that but I seriously doubt that is the issue as I have downloaded the iso twice from the Ubuntu site (specifically the Gigenet server) and get the same message each time.

---

### Post by Crypto77 on 2007-10-23
> **shad0w_walker said:**
> You can still verify the md5sum in windows using this tool: 

[http://portableapps.com/apps/utilities/winmd5sum_portable](http://portableapps.com/apps/utilities/winmd5sum_portable)

Software won't install in a x86 architecture or so it tells me.

---

