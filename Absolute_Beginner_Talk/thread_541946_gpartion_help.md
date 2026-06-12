---
title: "gpartion help"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by leedsdevil on 2007-09-03
Hello all , I have been using Ubuntu on my wifes PC with no partions at all worked fine for the most part. Untill i lost internet this is the start of it all.Now i down loaded the Gpartion live Cd . I got it running now. but i dont know how to really use it and what or how it should look . i know that i need 3 partions one being home and swap and i belive root or boot . ok i guess i need to know are what ext they all should be and if the swap is at the end? i had look at the guild here on the forums to much info for a newbie ack very confused lots of good info but it didnt help .if there is a easy guide out there just for the 3 partions link it or very simple steps. im now a converted to linux just wish i knew alot more lol ok Thanks to all whom reply

---

### Post by thelocust on 2007-09-03
I attached what my gparted looks like. I have 2 primary partitions (boot and root) and then 1 extended partition split 3 ways home, backup and swap. hope this helps.

---

### Post by diatribe on 2007-09-03
the three partitions should be / /home and /swap in that order.  swap size should be determined by the amount of ram in your machine, /home is your personal directory and / is the main partition

---

### Post by Duck2006 on 2007-09-03
I would partition the drive as
10Gb for / root
1Gb for swap at the end of the drive
the rest of the space for home partition
Docurmentation is on the gparted site

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by leedsdevil on 2007-09-03
Ah thanks now i know what it should look like and the file ext . now how to get the program to work for me... and once i reinstall linux ubuntu do i have to mount?

---

### Post by diatribe on 2007-09-03
once you have installed ubuntu when you reboot it will automatically mount the new partitions, it may be helpful to read over the gparted documentation so you do not do any damage to your disk.  what you are aiming for though is to remove the current partiton, then create three new ones of whatever size.  also, you may want to make your / partiton bigger  than /home unless you plan on installing all of your programs in your home directory

---

### Post by leedsdevil on 2007-09-03
yes a BIG THANKS to all who have just helped me that link and screen shot worked so far i need that to see what it is i wanted alsume folks

---

