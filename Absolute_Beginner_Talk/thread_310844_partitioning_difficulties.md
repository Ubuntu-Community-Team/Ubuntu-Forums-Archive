---
title: "partitioning difficulties"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by electro_man on 2006-12-01
help i have totally screwed up my hard drive that it won't let me partition it during the windows installation. I'm stuck with two partition one about 115gb with which i was able to put windows on. windows and the other 8mb I just want to totally format the whole drive however it wont let me. I have even resorted to trying to use the  dos command >format:c however i can't get that to work either it says bad command. I have been trying to duel boot with ubuntu using the google video and a live cd which i now realise i needed the dvd. So once again how can i format the whole of my c drive.

 thanks ](*,)

---

### Post by firenurse4 on 2006-12-01
> **electro_man said:**
> I have even resorted to trying to use the  dos command >format:c however i can't get that to work either it says bad command.

The dos syntax to format the drive is [COLOR="DarkRed"]format C:[/COLOR]

I don't know if this will help but there is a live cd version of gparted that may help. You can download it from[ here]("http://gparted.sourceforge.net/livecd.php").

---

### Post by agustin.g on 2006-12-01
The [Ultimate Boot CD](http://www.ultimatebootcd.com/) seems to have quite a bit of disk management utilities, or you can use [Darik's Boot and Nuke](http://dban.sourceforge.net/) to totally wipe your HDD and start over. I personally have not tried any of these two products, so i don't know what to reccoment.

hope it helps

---

### Post by LDRoamer on 2006-12-01
I was in your situation not long ago where windows, and dos FDISK wouldn't partition the drive (it had been screwed up by Partition Magic). I suggest you try gparted (it worked for me). Download the live cd and boot from it. You can get it here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

You will need to be on a computer on which you can burn a CD from an iso image.

You can use it to delete all the partitions from the disk and create new ones. It will allow you to create FAT32 and NTFS partitions if you wish. This worked for me and I know have Winxp and Ubuntu on my disk with no problems.

Gparted is really easy to use and seems to work very well. This may not be the only solution but it did work for me.

---

### Post by mibadt on 2006-12-01
Use Qtpartd from any Knoppix you have (or can freely download).

---

