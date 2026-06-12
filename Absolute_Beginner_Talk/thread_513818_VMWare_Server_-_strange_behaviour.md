---
title: "VMWare Server - strange behaviour"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by VictorR on 2007-07-30
After switching from Windows to Ubuntu I wanted to keep some Windows programs (particularly Google Picasa and Earth). With some troubles I finally managed to install VMWare Server and make working my original Windows 2000 installation without creating its extra virtual copy.

When I restarted Ubuntu I noticed that I had constant 100% CPU load. The process responsible for that was VMWARE-WMX (probably also known as vmmon in the system log). I killed this process and tried to start my Windows virtual machine. It seemed working well but I noticed some disk damage on Windows partition.

My question is: does anybody know what vmware-wmx is intended for and how to fix its strange activity?

The configuration:
Computer Athlon-XP 2600 , 1 GB RAM
hda - Windows 2000 prof, two other NTFS partitions for data
sda - Ubuntu 7.04 (installed later), GRUB on sda.
Dual boot system - Windows can run separately or as a guest OS under VMWARE Server on Ubuntu from the same partition (Windows has 256 MB memory in this configuration; it also has two hardware profiles).
The damage I have mentioned above was with Windows indexing service. I disabled this feature and fixed the disk. But after starting Ubuntu got 100% CPU again from vmware-wmx, which continued for at least 15 minutes until I killed the process.

Any ideas? Would very appreciate.

---

### Post by razeshkale on 2007-07-31
First thing is there is no Need to Run WINDOZ on your machine for Google earth there is Ubuntu version for that you can install on Ubuntu and enjoy your way
second about Vmware i think your memory allocation must be too less and you must be running some STUPID WINDOZ programme on your Host machine that causes this Problem
your machine configuration looks Great and you can really enjoy Ubuntu with Dual boot on this machine
 
as on my office machine got 1GB Ram (Standard Dell D620 Latitude machine configuration ) and i allocated 500MB for Ubuntu but dont forget that 
you are using Vmware and Vmware itself takes lot memory than Ubuntu as Ubuntu can run with 256MB with Lightning speed

so your cause is Vmware resources, check your host is running exrtra Background programmes or not?
then allocated sufficient memory as you going to run on Vmware(else not required)
this could Kill your Problem
Cheers

---

### Post by VictorR on 2007-07-31
Thanks for your reply.

As far as I know Google Earth for Linux is a Wine adapted Windows version. On my computer it did not work at all. After 5 minutes of convulsions it usually stopped with black screen and some white patches on it. Definitely not what I expect.

The tricky thing with VMWare is that it has been installed on the computer for a couple of weeks, while I was trying to get Windows working. Everything was fine (except the problem above). Then I changed the graphic card to NVidia, and made another attempt to launch virtual Windows, which surprisingly was successful. I felt very happy, tested it with some applications (Google Earth as well) and switched the computer off. Next morning I turned it on and found that it was very busy doing something with VMWare-wmx. Look, I did not start VMWare-server. Something triggered auto-start of this process with Ubuntu startup. After waiting for about 15 minutes I killed the process, then launched vmware-server and booted virtual Windows, which worked fine, except some problems with its hard drive (see my previous post). I shut down everything, booted clear Windows, fixed its disk, and restarted to Ubuntu again. Even before Compiz could loaded itself I saw vmware-wmx consuming CPU load. I killed it again and since that have been working happily, trying by the way to find out what vmware-wmx was doing with my computer and how to get this stuff sorted. Googling for the name gave me two English non-relevant pages,  one Russian one and about five in Chinese or Japanese. That's what I have so far.

---

### Post by hyper_ch on 2007-07-31
Google Earth for Linux works fine. Add the medibuntu repository and install it through synaptic.

---

### Post by VictorR on 2007-07-31
You are right - Google Earth is much better now. But my question was not about Google stuff, but rather some strange vmware component.:(

---

