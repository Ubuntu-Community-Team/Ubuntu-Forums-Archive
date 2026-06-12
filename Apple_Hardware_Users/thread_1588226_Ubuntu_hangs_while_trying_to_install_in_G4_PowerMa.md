---
title: "Ubuntu hangs while trying to install in G4 PowerMac"
date: 2010-10-04
forum: Apple Hardware Users
---

### Post by GoCool on 2010-10-04
Hi,
I have a G4 PowerMac and I was trying to install Ubuntu 10.04. While running the live dvd it gets stuck at the ubuntu logo at boot up and doesnt go past it. 
I am using the Ubuntu for PPC, and I am new to Mac so not sure how to get the configuration. But I see two partitions of each 75GB when I opened the Disk Utility to see what is inside.
Please advise.

---

### Post by GoCool on 2010-10-04
I saw a beautiful sticky for Intel-mac. I scoured through the forum for a similar sticky for PPC but little luck. I think there is no linux made to date for a PPC Mac. There are claims but nothing works, be it Ubuntu, Arch, Yellow Dog..
They work for Intel Mac but not for PPC Mac.
Any inputs on this? Any success stories?

---

### Post by linuxopjemac on 2010-10-04
Have a look at MintPPC
[http://mac.linux.be/content/screenshots-mintppc-9](http://mac.linux.be/content/screenshots-mintppc-9)
[http://mac.linux.be/content/mintppc-9-released](http://mac.linux.be/content/mintppc-9-released)

---

### Post by GoCool on 2010-10-04
Sure. Will give it a try. 
But where to download it?

---

### Post by thepotatobasher on 2010-10-08
I'm a complete linux noob and I got it installed a few days ago

I'm using the lucid build 10.04 using an original Powerbook G4 (powerpc). 
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

My internal dvd drive is broken so i had to load from a firewire external drive.  I was having a great deal of difficulty with CD-R's (was taking like a 1/2 hour to load and errored out in install) so I decided to try and burn the iso on a DVD-r and the livecd opened almost instantly. 

If you can't get your mac to boot by holding 'c' try to boot through cd by holding 'option' down.  IF you still cant boot try to boot through open firmware mode
here are some boot commands for mac
[http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.shtml](http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.shtml)

if you have to boot through open firmware it gets complicated.  this is what i had to do. 
dev / ls 

this will show you what devices you have
find your cd drive

next type:
boot [address]:,[path]

for me this was something like:

boot /pci@f4000000/firewire@e/node@0010b9210040ad70/sbp-2@c000/disk@0:,\install\yaboot
(granted i had to use a firewire device so mine will be much different from yours.  if you have difficulty, make sure there aren't spaces between your slashes
then i just used the default options to load ubuntu

---

