---
title: "my ubuntu freezes when i mount my 500gb ext3 partition"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Dred79 on 2007-07-26
Could someone guide me in the basic steps i should take to resolve this? I formated a 500gb ext3  partition using acronis because when i was in ubuntu  i tried the gnome partition manager and qtparted but they both froze when formating my ext3 partition. So i have acronis create it for me and it was working fine. i had Acronis name it /data cause i thought that would be better. i believe the actual mount point is /media/_data

Then recently i moved all my computer hardware to a new motherboard cause i wanted a micro case. I went from a DFI LANPARTY SLI expert to a evga nforce4 SLI matx. They are both the same chipset so i didn't think it would be a big deal. ubuntu detected sound and everything works fine.  but now i have this hard drive problem. I currently dual boot on my 36gig 10k rapter drive between windows XP and ubuntu. The 500gb is a maxtor drive that freezes the whole system whenever i mount it. 

I can look at the partition via gnome partition manager and i tried changing the flag it had which was boot to nothing. and it froze as soon as i unchecked it.

Here are my currently computer specs
AMD Opteron 165 not overclocked yet.
EVGA NV44 nforce4 SLI
2x7900GTX graphics cards SLI
36GB WD RAPTOR
500GB Maxtor
Lite on 20x lightscribe sata CDROM
ANTEC Aria Case
Everything is watercooled with 2 dangerden waterblocks and koolance waterblock.

Ubuntu 7.04 fiesty
Windows XP Pro blue screening still from motherboard swap and will fix that later.

If this is the wrong forum i apologize i am a noob and with windows blue screening i am trying to force myself to switch to linux i figured out how to get hellanzb to work and all my movies etc i just need my hard drive to work with all my data on it.

---

### Post by MrHippocampus on 2007-07-26
Interesting problem, try running a liveCD of another distro such as knoppix and see if it can mount the drive.

---

### Post by vpjr on 2007-08-25
hi,

how exactly are you mounting the drive? like "mount /dev/anotherhdd /home/yourdirectory/theotherdrive"?

regards,

ven

---

### Post by Inxsible on 2007-08-25
is the 500 gb an external drive ? if so, use my signature and use pmount to mount it.

else, post the output of the following commands

```
cat /etc/fstab
``````
df -h
``````
sudo fdisk -l
``` -l is lowercase L. Make sure your drive is connected when you enter these commands.

---

