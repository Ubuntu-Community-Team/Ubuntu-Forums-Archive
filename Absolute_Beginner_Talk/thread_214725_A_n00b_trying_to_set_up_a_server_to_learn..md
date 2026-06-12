---
title: "A n00b trying to set up a server to learn."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Evil_Ether on 2006-07-13
What I have;
PIII800eb mhz CPU
Intel Board D815EEA
256 Ram
10/100 MBIT Network card
40 + 9 GB IDE Harddrives
120GB SATA HDD
Serial ATA and Parallel ATA PCI combo PCI Controller

The things I am trying to do;
1. Install the sata pci card. The CD has drivers for Redhat, Mandrake and Fedora but I don't know how to use them.
2. Have a server that will play my MP3s that I can control from any of my other Ubuntu boxes.
3. Have it as a file server. It only needs to share with other Ubuntu boxes.
4. Have a global user list. I don't know if this is the right term or not. (hence not been able to find out how to do it.)
5. Have the server download all the updates/apps I install and cache them so I only have to download them once for all the computers on the network. I don't know if this is possible but if it is it would be cool.

What I have done;
1. Installed Ubuntu on the 40Gb HDD from the server install disk
2. Set it up on my network
3. Added the repos
4. Installed the non free codecs

I know this is probably a lot to ask in one post but if you could point me toward a how to for these things I should be able to do it from there.

Thanks in advance.

Terry.

---

### Post by GuitarHero on 2006-07-13
I thought you just had to go to Places>Connect to Server

---

### Post by uzi09 on 2006-07-13
i think the correct term is "domain controller" and this is what you're looking for:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

that should take care of the "centralized user list" and file server, not 2 sure about mp3 server (or did you mean that you want one place to store all mp3's, which basically would make it a file server)

let us know how it goes. i'm really interested in setting this up as well, but need to do a new install cuz i didn't bother to keep seperate partitions for home and am running into various problems now.

---

### Post by Evil_Ether on 2006-07-13
It has no gui.

---

### Post by Evil_Ether on 2006-07-13
Thanks but I don't use windows at all. Is there a native Linux solution?

---

