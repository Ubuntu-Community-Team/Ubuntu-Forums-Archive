---
title: "to Much harddrive space  for ubuntu"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by dellboy on 2007-11-23
ok i have Just re instilled Ubuntu on my computer but gave to much space for Ubuntu and not what i wanted for windows xp i am still a Linux NOOB and Plus i am doing a computer course where i need to use windows from time to time. so what i want to do is have 71.5GB for Ubuntu and the rest of my space for windows but some how it ended up the other way around  giving xp the 71.5GB. and Ubuntu the rest of my hardrive space is there a easy way to take some of the space from Ubuntu and add it to my windows partition. at the moment i dont have much on ever  Ubuntu or xp at the moment.  But i just what to sort this out so i can carry on using my computer.

it be great if there was a easy way anyone new ever in Ubuntu or windows that let me do this. 

add more space from my Ubuntu partition to make my xp one bigger giving xp more space then Ubuntu like i wanted to do in the Frist place:)

ps i love ubuntu just i still need windows at the moment for a few things that i cant do i now its  sad :mad:

---

### Post by cotcot on 2007-11-23
Download the [[COLOR="Red"]GParted LiveCD[/COLOR]]("http://gparted-livecd.tuxfamily.org/") iso and burn it to a CD (the same as you to with a ubuntu install CD)

Boot the PC with the Gparted LiveCD. It gives you a graphical interface to work on your partitions.
You will be able to shrink the ubuntu partition, move it and extend the windows partition.

Do each of these steps one after the other.

I have done this multiple times, so I am not recommending something I have not experienced myself.

Succes !

---

### Post by GavinZac on 2007-11-23
alternatively, just install the ext3 drivers for windows, and you can use your /home/ directory to store stuff for both windows and linux :)

---

### Post by duruttye on 2007-11-23
This is what I would do:
open up gparted, the partition editor, from system, administration.
if you don't have it, you will have to install it, form the terminal (applications, accessories, terminal) and type this in:
sudo aptitude install gparted
then type in your password
after it is installed you can open it from the menu (above)
there you can shrink the partition. I'm not sure about beeing able to allocate more space to the windows partition, if it is in ntfs...
OR you can make another partition, the third one, which will be accessibile from both OS-es. Windows recognizes fur sure ntfs file system, i'm not sure about others, like ext3...

good luck

---

### Post by ronmarley1 on 2007-11-23
I would do as cotcot suggested above.  You will not be able to resize the Ubuntu partition using gParted from the System -->Administration menu as gParted cannot resize a mounted partition.  Use the gParted live CD, which can be downloaded here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
You will need to first shrink the Ubuntu partition, format the freed space as NTFS, then increase the size of the XP partition.  As cotcot said, do these steps one at a time.

---

### Post by erginemr on 2007-11-24
> **ronmarley1 said:**
> I would do as cotcot suggested above.  You will not be able to resize the Ubuntu partition using gParted from the System -->Administration menu as gParted cannot resize a mounted partition.  Use the gParted live CD, which can be downloaded here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
You will need to first shrink the Ubuntu partition, format the freed space as NTFS, then increase the size of the XP partition.  As cotcot said, do these steps one at a time.

+1 to that. I used GParted Live CD to chip off several GB's from Windows and allocate more space to Ubuntu in the past. You can safely use it.

---

### Post by cotcot on 2007-11-24
> **GavinZac said:**
> alternatively, just install the ext3 drivers for windows, and you can use your /home/ directory to store stuff for both windows and linux :)

Please note that the windows driver mounts ext3 as an ext2 and hence has no journaling. It does not mean that using the driver is not recommended. Only inform yourself about what it means. It is explained [[COLOR="Red"]here[/COLOR]]("http://www.fs-driver.org/faq.html#acc_ext3").

---

