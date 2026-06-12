---
title: "Linux Live CD NTFS Write"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by OrganicPanda on 2006-09-10
Hey,

My brothers laptop has mysteriously dropped lots of system files on his windows xp installation and for some reason his windows cd wont boot so I was wondering if anybody knows of a linux live cd, because linux live cds seem to work, that can write to ntfs. I know it is possible because of the driver that came out a while back but I was just wondering if it had been implimented into any live cds yet, does anybody know of any?

cheers, 
OrganicPanda

---

### Post by IYY on 2006-09-10
The Ubuntu live CD can write to NTFS after a few terminal commands (this is a bit risky, though). Go to UbuntuGuide.org for more details.

However, another LiveCD like Knoppix, or Knoppix-STD might be better suited for your purpose.

---

### Post by Error47 on 2007-11-08
I am trying to copy a system file from my flash drive to my hard drive because windows will not boot. This is my only option. I only have the ubuntu feisty live cd at the moment, and I would like to write this file onto my NTFS hard drive. I couldn't find any information on UbuntuGuide.org . 

The only thing I have tried is to add the NTFS support program and install it through the Applications > add/remove software . It installed and worked, and when I clicked enable NTFS support it still didnt work. I was only able to enable it for external devices only though, the internal option did not work. 

Please help, 
thanks.

---

### Post by logos34 on 2007-11-08
> **Error47 said:**
> The only thing I have tried is to add the NTFS support program and install it through the Applications > add/remove software . It installed and worked, and when I clicked enable NTFS support it still didnt work. I was only able to enable it for external devices only though, the internal option did not work.

that's the way you do it...and the windows partition is mounted?  If so and still no option to enable internal device, try unmounting windows and remounting as root:

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows
(replace 'hda1' with actual partition)

now open ntfs-config again and see if it give you internal option

---

### Post by Error47 on 2007-11-08
It didn't work,I still can't write to my hard drive.

---

### Post by logos34 on 2007-11-08
Get [Parted Magic]("http://partedmagic.com/") (only around 30MB download)--has built-in ntfs-3g support, partition mounting tool and a lot of other features.

---

### Post by Error47 on 2007-11-08
I need a way to do it in Ubuntu please. I only have one cd-drive, and I am using it for the live cd. I cannot make another live cd.

---

