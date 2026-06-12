---
title: "root problems during installation"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by xxneilxx on 2008-04-20
HI i started to install 8.04 onto a Partion on my second harddrive. SIne i scanned all the choces in the partion menu, i had to go manual. The reason being i need to instal ubuntu in a partion within my second hardrive. It has 20GB space. 

1) In the manual partition section, i located the D drive
2) i selected edit partition, i allocated 10GB to EXT 3 Journal
3) I selected format
4) I left the last part " / " as it was
5) I clicked ok, i saw that my drive was formated, and i clicked forward. 
6) a message popped up saying i didnt specify a root directory
7) since i didntread the manual setup guideline online, i went bak and choe " /boot"
8) after that it still asked me to specify a root directory
9) I cancelled the installation, and i went to the live desktop of Ubuntu. There I saw my NTFS drive for windows, my Fat32 drive E for storage, and my drive D. I coundt acess this drive at all from ubuntu.
10) i loaded up xp, and i went to my computer i could see and acess my d drive, 
11)Ext2IFS showed me that my drive d was now a EXT2 drive.

Before i go back to trying to install it again, i need some help with regards to 
1) root directory
2) swap
3) EXT 3

Since my drive d is a partion already, do i need to further partion this to make a swap and a EXT 3. Why is my Drive D an EXT 2 and not an EXT 3.

Any ideas

---

### Post by LowSky on 2008-04-20
root is labeled as /
thats it

home would be /home

maybe this will help
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)


and dont call the drives by letter, thats a  bad Windows habit, lol

---

