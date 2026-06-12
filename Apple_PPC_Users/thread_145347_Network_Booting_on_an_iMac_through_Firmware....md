---
title: "Network Booting on an iMac through Firmware..."
date: 2006-03-16
forum: Apple PPC Users
---

### Post by SectionThree on 2006-03-16
I just inherited a 400 MHz iMac (slot-loading, 1999-2000) with 256 MB RAM, but the DVD-ROM drive is shot and the hard drive (which was running OS 9) won't boot. I hooked it up to my LAN and tried to boot it up from my working 266 MHz iMac (the one I'm using now) to no avail. I think this is possible, and I acknowledge my lack of experience with Open Firmware. Does anyone have any idea how to do this, or will I have to spring for a new drive? Also, if I have my Breezy install CD in my working iMac, can I boot up the "nonworking" one over the network from the CD (I don't care a lick about the data on the 10GB hard drive on the "new" machine, it can be wiped for all I care)...
 
 I want to use this for an "anything goes" ppc Linux machine where I'm free to do anything I want without fear of serious crashes because I can wipe it and start anew... that kind of thing...

---

### Post by Rxke on 2006-03-18
A good place to start looking might be NetBSD's  network booting HowTo: [http://www.netbsd.org/Documentation/network/netboot/intro.macppc.html](http://www.netbsd.org/Documentation/network/netboot/intro.macppc.html)

I'm not sure booting from the CD on the other machine will work, though, or you must have the files on it available through a server-setup there (your old machine) see the links on the bottom of that HowTo, they lead to setups for Linux 

       1. bootpd (Open Firmware 1 and 2) or dhcpd (Open Firmware 3)
       2. tftpd
       3. nfs
       4. client filesystem
       5. finishing up 

[http://www.netbsd.org/Documentation/network/netboot/tftpd.html](http://www.netbsd.org/Documentation/network/netboot/tftpd.html)

---

### Post by SectionThree on 2006-03-31
Thanks! I'll give it a try and let you know how it works out.

---

### Post by Rxke on 2006-03-31
I'm not sure my answer was/will be helpful, though... I had just discovered the writeups re: OF booting on NetBSD, and it looked like the most detailed writeup I'd ever seen (but I was trying to boot a machine w/ OF 1.2, which needed some patching. I think the iMac is OF v.3, so you'd probably use DHCP, I guess... 

it should be possible but depending on how bad your HD is fsked up, it will be hard.. or harder, I guess. I once installed Debian w/o using any floppies or CD, but I had a bootable machine (os9) to start with, and could install the bootimage under os 9... I think, if you could start a partitioner and put the bootfiles on it, you're halfway there...

---

### Post by Rxke on 2006-03-31
it says:....

0 > boot enet: 0,ofwboot.xcf netbsd.ram.gz   #to specify a kernel other than "netbsd"

so it should work, if you have the other computer as server w/ the linux kernel...

---

