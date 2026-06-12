---
title: "New to Ubuntu and need help"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Uberuntu on 2007-11-16
Hi everyone, this is my first post in this forum. Ok, so I finally had enough of windows altogether. I just went through 2 weeks of formatting a doing clean installs of XP and its still messing up so I've finally decided to try out Linux and see what all the buzz is about. First off I downloaded the Ubuntu .ISO and put it on a disk. I aslo did the same for gparted. So I restarted the system and booted gparted and formated so there was nothing but unallocated space. Then I booted ubuntu and used the install. Now heres the problem, I get as far as the 'parition hardrive' section, and there is nothing to choose from. I have used gparted a handful of times since then trying different types of partitions but to no avail. If I am not doing something correctly please let me know. Thanks!

---

### Post by Inxsible on 2007-11-16
Have a look at this link which gives illustrated instructions on installing. I know its for dual booting, but you can simply use the entire drive to install and not worry about the windows bit

[www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing)

---

### Post by Uberuntu on 2007-11-16
Thanks for the link, i read it and reformatted the drive to ext3, but i am still having the same problem. If i log in to ubuntu and go to system/admin/(i think thats it) and use the partition editor there, it detects my hardrive but when i click on the 'new' button it gives me an error message and crashes on me. and if i just go right to ubuntu install, once i get to the partition window i have no options to choose from.

---

### Post by bumanie on 2007-11-16
If I am understanding your problem correctly, I think the best thing you could do is to leave your hdd formatted to ext3 and start  from scratch with a complete install.
When you get up to the partioning part,choose the 'use entire hard drive option.' Uubntu should make a /root and swap partition of ist own accord.
If you feel game you can choose 'manual' option and make a /root; /home and swap. In theory the OS will be installed on /root and if at some time things go wrong and you  have to reinstall, all your documents etc. should be safe in the /home partition.
If you are not very experienced, stick with 'use entire hard drive option' until you understand the system a bit better.

---

### Post by Uberuntu on 2007-11-16
i still dont even have the options to do any of that. its just blank. no manual. no use all. just a blank field. I found out the proper way to make the partitions (i wasnt allotting space for a linus-swap partition) and now when i boot ubuntu from the disk and i get that scrolling bar that goes back and fourth, it starts going through a bunch of code instead of going right into the ubuntu desktop. I am assuming that this is a good thing but it eventually gives me an error saying "failed to set xfermode". I looked this up and they say that this can be fixed  by editing the /boot/grub/menu.lst and adding ' irqpoll'. This is my first stab at linux and im still learning how to use all the features, such as the terminal but i figured that that is where i can open this file and edit it. so i used the code 'sudo nano /boot/grub/menu.lst' and i opens up another screen with nothing written in it. Im not sure what to do from here. Just to let you know, there is NOTHING on my computer right now. No windows, no ubuntu, nada. I am trying to accomplish the install from the live cd.

---

### Post by BrendanM on 2007-11-16
Reading your post, I'm a little confused as to whether you've actually gotten Ubuntu installed or not, or if you're running off the LiveCD without any graphics?

In any case, you might try using the Alternate Text-based Install CD. It's not as flashy, but I've found it works better on finicky systems. If your hardware is odd, you still might have to do extra tweaking to get your graphics to work right even after you've installed.

---

### Post by Uberuntu on 2007-11-16
Ya youve got it right, there is nothing installed on my system right now. I am trying to istall ubuntu 7.10 but it isnt recognizing that i have a hardrive. When i have my external hardrive plugged in it works, and i get the options for partitioning (i am referring to when i am in the graphical ubuntu environment using the installer). I think i might give that text based installer a shot.

---

### Post by ukripper on 2007-11-16
> **Uberuntu said:**
> Ya youve got it right, there is nothing installed on my system right now. I am trying to istall ubuntu 7.10 but it isnt recognizing that i have a hardrive. When i have my external hardrive plugged in it works, and i get the options for partitioning (i am referring to when i am in the graphical ubuntu environment using the installer). I think i might give that text based installer a shot.

go to terminal and type the following command and paste output here.

```
sudo fdisk -l
```

the above is 'small L' not '1'

---

### Post by Uberuntu on 2007-11-16
Ok i went to terminal and typed in that code and pressed enter and it didnt do anything it just went to the next line. did i do something wrong?

---

### Post by ukripper on 2007-11-16
> **Uberuntu said:**
> Ok i went to terminal and typed in that code and pressed enter and it didnt do anything it just went to the next line. did i do something wrong?

Well as you don't have ubuntu yet installed it won't show anything. 
lets try another command and paste here:
```
dmesg
```

---

### Post by Uberuntu on 2007-11-16
sorry it wont let me past it, says to many errors

---

### Post by ukripper on 2007-11-16
ok can you find out in that file if your partitions were detected with your hard drive

---

### Post by Uberuntu on 2007-11-16
no didnt see anything about them

---

### Post by ukripper on 2007-11-16
ok lets go through the process of installtion.
Where do you actually stop during installtion at what screen and can you post screenshot of that screen where it shows no HDD available

---

### Post by Uberuntu on 2007-11-16
[IMG]http://http://ubuntuforums.org/g/images/432137/small/1_Screenshot.png[/IMG]

---

### Post by Uberuntu on 2007-11-16
did that post? [IMG]http://ubuntuforums.org/g/images/432137/small/1_Screenshot.png[/IMG]

---

### Post by Uberuntu on 2007-11-16
i dont know if you can enlarge that pic but you can see that i have no partitioning options in that window. Also when i boot up and ubuntu is loading i get a error msg that says something like 'failed to set sxfermode'

---

### Post by ukripper on 2007-11-16
try this guide - [http://www.fsckin.com/2007/09/28/how-to-install-gutsy-gibbon-a-21-step-guide-for-technical-support/](http://www.fsckin.com/2007/09/28/how-to-install-gutsy-gibbon-a-21-step-guide-for-technical-support/)

---

### Post by philinux on 2007-11-16
One thing I would try is reboot the live cd and choose the option to check out the cd.

This will make sure it burned correctly in the first place.

---

### Post by ukripper on 2007-11-16
> **philinux said:**
> One thing I would try is reboot the live cd and choose the option to check out the cd.

This will make sure it burned correctly in the first place.

Can't agree more!

---

