---
title: "help in downloading debian"
date: 2012-10-18
forum: Any Other OS
---

### Post by normann on 2012-10-18
hi,I would like to download Debian Wheezy for a raspberry pi, to sd card. Need help please,been told i need "dd' can not find in the packages thanks

---

### Post by AlexDudko on 2012-10-18
dd is a part of coreutils package. It should be installed in your system.
to write the image to a drive use this command:
> sudo dd if=/way_to_image_file of=/destination_path
the destination path would be sdb if you have only one hard drive otherwise it could be sdc, sdd and so on.

---

### Post by ikt on 2012-10-18
Just writing to say BE CAREFUL WITH DD!

I doesn't have the nickname 'disk destroyer' by accident :p

---

### Post by zhogan85 on 2012-10-18
> **normann said:**
> hi,I would like to download Debian Wheezy for a raspberry pi, to sd card. Need help please,been told i need "dd' can not find in the packages thanks

Pretty straightforward instructions on the RaspberryPi wiki, as.

[http://elinux.org/RPi_Easy_SD_Card_Setup#Copying_an_image_to_the_SD_Card_in_Linux_.28command_line.29]("http://elinux.org/RPi_Easy_SD_Card_Setup#Copying_an_image_to_the_SD_Card_in_Linux_.28command_line.29")

---

### Post by zhogan85 on 2012-10-18
> **ikt said:**
> Just writing to say BE CAREFUL WITH DD!

I doesn't have the nickname 'disk destroyer' by accident :p

+1

Be very careful not to mix up "if" and "of".

---

### Post by oldos2er on 2012-10-18
Moved to Other OS/Distro Talk.

---

### Post by normann on 2012-10-26
Hi guys, thank you for all your help. I downloaded via torrent.Debian is my home folder now to get to sd card.I right click and send to card will that work.I tried imagewriter but it will not accept it

---

### Post by zhogan85 on 2012-10-26
Did you follow the link I posted previously? There are step by step directions there. If that doesn't work, or if you still have questions, please reply.

---

### Post by normann on 2012-10-26
hi, i downloaded torrent 2012-09-18 wheezy-raspberry zip-.Now in my home folder what now

---

### Post by zhogan85 on 2012-10-26
Did you follow the link I posted? It has a step by step guide, that is very easy to follow, and I don't want to retype all of that info here.

[http://elinux.org/RPi_Easy_SD_Card_Setup#Copying_an_image_to_the_SD_Card_in_Linux_.28command_line.29]("http://elinux.org/RPi_Easy_SD_Card_Setup#Copying_an_image_to_the_SD_Card_in_Linux_.28command_line.29")

The next step is to extract the image with either the unzip command, or the file manager.

---

### Post by mips on 2012-10-26
> **normann said:**
> Hi guys, thank you for all your help. I downloaded via torrent.Debian is my home folder now to get to sd card.I right click and send to card will that work.I tried imagewriter but it will not accept it

1. Show us the full path & name of the .iso file
2. With the SD card inserted post the output of ***sudo fdisk -l***

---

### Post by normann on 2012-10-30
Hi Guys, Well at last Ihave done it. The zip file was in a different folder, I accidently came accross it. Now I am up and running.Thanks for all your patience. Hope you are coping alright with weather,Norman

---

### Post by normann on 2012-10-30
Hi guys where do I say problem solved thanks n

---

### Post by oldos2er on 2012-10-30
> **normann said:**
> Hi guys where do I say problem solved thanks n

At the top of the thread, click the drop-down menu by Thread Tools.

---

