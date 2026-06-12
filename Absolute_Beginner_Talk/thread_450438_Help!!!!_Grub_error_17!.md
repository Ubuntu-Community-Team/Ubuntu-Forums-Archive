---
title: "Help!!!! Grub error 17!"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by krugman on 2007-05-21
Hello!

I finally got enough time to install Feisty. First, it was great since everything was recognized, the resolution was perfect, the wireless ok, beryl was working...

Then, I tried the hibernate, which was said not to work and indeed, it didn't. So, I rebooted my laptop and choose to boot to Vista/longhorm (loader) as Grub calls it. Then, it loads something ansd says "recovery.dat not found" with a big "error" message on the screen. Then I reboot again, and here comes the error 17, which to my undestanding indicates that the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

However, since I am still a newbie, I don't know what to do from that point. I would really like not having to reinstall Vista and lose everything!

Thanks!:p

---

### Post by Najand on 2007-05-21
Grub Error 17 : "Invalid device requested"
This error is returned if a device string is recognizable but does not fall under the other device errors.
Can you be more specified about your system. Probably the output of "sudo fdisk -l" and the "/boot/grub/menu.lst" file would help a lot.

---

### Post by Inxsible on 2007-05-21
If you hibernated...or rather tried to hibernate from Ubuntu, you CANNOT select Windows on your next boot.
 
Try getting into Ubuntu and then perform a clean shutdown. Then try Windows again.
 
Of course, this is assuming that you tried the hibernate from Ubuntu (since you stated that it was said not to work and it didn't )

---

### Post by krugman on 2007-05-21
Yes, I did hibernate from Ubuntu.
But, how can I boot into Ubuntu since I Get the error 17?
Do I have to boot through the live cd?

My laptop is an ASUS U1F, i.e. 1.06 Ghz Core duo and a 80 Gb HD. I have 4 partitions: 1 is hidden and for the recovery of vista, one is vista (ntfs), the other is data (ntfs too) and the last one is the root system of ubuntu. Oh, and I have a swap partition also.

---

### Post by Inxsible on 2007-05-21
> **krugman said:**
> Yes, I did hibernate from Ubuntu.
But, how can I boot into Ubuntu since I Get the error 17?
Do I have to boot through the live cd?
 
My laptop is an ASUS U1F, i.e. 1.06 Ghz Core duo and a 80 Gb HD. I have 4 partitions: 1 is hidden and for the recovery of vista, one is vista (ntfs), the other is data (ntfs too) and the last one is the root system of ubuntu. Oh, and I have a swap partition also.
 
Do you get the Grub error 17 on selecting the Windows Vista/Longhorn (Loader)
 
or do you not see the Grub menu at all ? Try a hard reset and see if the Grub comes up again ![-o<

---

### Post by krugman on 2007-05-21
no I don't even get to see the grub menu. I have also tried to reboot many times.
Now, I am loading Ubuntu thanks to the live cd

---

### Post by Najand on 2007-05-21
Try Live CD and do the "fdisk" command. If every partitions were fine, then we can go through it to restore grub again.

---

### Post by krugman on 2007-05-22
Well, actually, I have reinstalled Ubuntu and it works ok!
I can boot in vista or in Ubuntu.

I have a few questions nevertheless:

1. it would be great if it were possible to automatically come back from hibernate to the last OS used. I mean, maybe not automatically, but so that the OS selected by Grub is the one we hibernated from. Is it possible?

2. I would like to share my firefow profiles between Vista and Ubuntu. I know this is possible since I have already done that before. However, since the partition where my profile reside is an NTFS one, I need something like NTFS 3G right? Because right now, I can see my partitions, but I can't write on it it seems. Do you think it's risky to share two profiles this way?


thanks!

---

