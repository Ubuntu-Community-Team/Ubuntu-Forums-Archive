---
title: "Dual boot problems with two Dapper installs"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Porta on 2006-10-23
Hello there;

Last night i removed winXP from my computer on the primary harddisk(master) by installing Dapper on that particular partition.
I already had  Ubuntu installed on my second harddrive.(slave)
After this i couldn't boot into my original set-up on that second HD even though it is listed in the GRUB-menu at start-up.

Is there anyway to resolve this mess i've got myself into ](*,). I would really like that because there is a lot of info on that install i would like to use, and i know it's still 
there because Gparted shows me it is.

regards
Porta

---

### Post by Bachstelze on 2006-10-23
What's the use of having two Dappers ?

---

### Post by Porta on 2006-10-23
The first one i used was, and is on that second drive, so it's the one i used when i was dual booting with windows.

greetings
Porta

---

### Post by doobit on 2006-10-23
It's there, and you can access the home directory in root by mounting the drive after you boot and navigateing to it. You will probably get to boot into it by changing the hd numbers in the grub menu.lst to refelct the actual location of the hard drive. For example, if it's hdb with the boot partition hdb1, then grub should say (hd1,0) as the boot location.

---

### Post by Bachstelze on 2006-10-23
So basically there's one you do not want, right ?

Then delete its partitions with GParted then restore GRUB to boot the other. To restore GRUB, boot from a live CD, mount the root partition of your system somewhere and reinstall GRUB on it, like this :

```

sudo mkdir /mnt/root
sudo mount -t ext3 /dev/hda1 /mnt/root
sudo grub-install --root-directory=/mnt/root /dev/hda
```

(replace drive names with correct values of course :))

---

### Post by Porta on 2006-10-23
Thanks for the reply's on this matter, i have to go and try out some things as suggested, i will report back on this. ;) 

Greetings
Porta

---

### Post by Bachstelze on 2006-10-23
And next time, if you want to install more than one Linux distro, remember to create a separate /boot partition to use with all of them, it makes muti-booting way easier ;)

---

### Post by Porta on 2006-10-24
Well, i deleted one of the installs and got the system working again, just have to install some programs and everything is aok again!! :D 

Thanks for the help
Porta

---

