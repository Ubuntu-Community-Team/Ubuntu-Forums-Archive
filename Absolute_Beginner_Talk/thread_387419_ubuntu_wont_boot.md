---
title: "ubuntu wont boot"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by daddyges on 2007-03-18
Hi folks. I have been trying to try out ubuntu but have no success in making the hard drive copy run. I have installed ubuntu onto partitions directly after widows xp pro 200gig hard drive 127 for xp then the install process partitioned the rest: had2 ext3 60 gb, hda3 extended 1.44gb, hda5 swap 1.44gb. the install process said that grub was loaded on hda0. I have wubi installed on windows which allows me to see hda2 (lists it as drive j:)
      played with windows boot.ini file to try and dual boot. ie copied ubuntu.bin to drive c: and entered c:\ubuntu.bin="ubuntu Linux"  (that eas a suggestion from someone on a different forum) but that just gave me the option to dual boot but just restarted the pc. any help? thanks ges

---

### Post by seshomaru samma on 2007-03-18
The easiest would be to install Grub (linux'x boot menu) to the MBR , this way you will not have to mess with Windows' boot.ini....
you can do it easily with the ubuntu live cd
instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
(make sure to use the output of stage 4 in stage 5)

---

### Post by oilchangeguy on 2007-03-18
also read this. 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
and i'd change your windows boot ini file back to the way it was.

---

### Post by daddyges on 2007-03-18
boot ini file changed back. tried the grub cd rom said it was successful but it still wont boot into anything except windows. will keep trying. ges

---

