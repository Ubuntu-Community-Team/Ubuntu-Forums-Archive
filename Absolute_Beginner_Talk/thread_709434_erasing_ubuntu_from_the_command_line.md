---
title: "erasing ubuntu from the command line"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2008-02-27
i guess something went horribly wrong in the installation cause i cant get internet to work and i cant get the live cd to work so i need to know if theres a command line that earases complitly ubuntu so i can install it again. thanx

---

### Post by Cypher on 2008-02-27
Nothing you do on your installation of Ubuntu should prevent you from getting the LiveCD to work. It's a little hard for you to delete all of Ubuntu when you're actually booted into it. You can erase quite a lot of it, but some of the key components you can't erase cuz you're using it.

The LiveCD is the definitve way of erasing everything on the HD and re-installing. Where and how is the LiveCD failing?

---

### Post by djbsteart1 on 2008-02-27
if the live cd is one rw and not just r, that can cause problems, i have a batch of rw's that only half will work as livecds.

---

### Post by shayvasa on 2008-02-27
i have 2 live cds that i ordered and none of them work...i also tried burning it on a rw and didint work either...with the originals live cds what happenes is that when it does enter the menu of the live cd that asks if i want to enter or install ubuntu i click the first option and then or it gets stuck and says the computer cant find the cd, reboot or it shows me a commnad line

---

### Post by shayvasa on 2008-02-27
come on people plz i need help

---

### Post by shayvasa on 2008-02-27
so if theres no way to delete from inside ubuntu is there a way to earase it without using the live cd?

---

### Post by dca on 2008-02-27
If the machine doesn't work, then it doesn't work.  What's the benefit of completely erasing the OS.  You can reinstall over it just by using the partitioner in Ubuntu...  if you want to reinstall Windows, the installer overwrites Ubuntu...

---

### Post by shayvasa on 2008-02-27
i want ubuntu but i cant earase it to reinstall it...can u explain better the partioner thing plz?

---

### Post by jan quark on 2008-02-27
you can also try to use the[ gparted live cd]("http://gparted-livecd.tuxfamily.org/")

and erase the ubuntu partition

---

### Post by Dr Small on 2008-02-27
> **shayvasa said:**
> i want ubuntu but i cant earase it to reinstall it...can u explain better the partioner thing plz?
You don't need to erase it to reinstall.
Simply insert the LiveCD and just Install it. It will overwrite the current drive.

---

### Post by bodhi.zazen on 2008-02-27
First you do not need to "erase ubuntu", just re-install

Second, if networking is not working on the live CD, re-installing is unlikely to be of much help.

Better to describe the hardware and nature of the problem.

---

### Post by shayvasa on 2008-02-27
Dr small how do i do that? what do i need to click cause it doesnt show the install button on the desktop

---

### Post by Dr Small on 2008-02-27
> **shayvasa said:**
> Dr small how do i do that? what do i need to click cause it doesnt show the install button on the desktop
1.) You must be loading the desktop off the LiveCD.
2.) If the installer icon is not on the desktop, it is in one of the menus.
3.) Install as normal, and just overwrite the entire drive.

---

### Post by Taino on 2008-02-27
> **shayvasa said:**
> i want ubuntu but i cant earase it to reinstall it...can u explain better the partioner thing plz?

When you are installing Ubuntu and are at the partioner screen and have set the partitions  the next step is to "write the changes to harddisk" that action overwrites your old install with a new install.

But it sounds like your not even making it that far? If you can boot the LiveCD to the menu screen then choose "safe mode" and get to a terminal prompt as root, then if you do a..

sudo cfdisk

You'll be in the command line partitioner and from there you can "delete" partitions and make new ones, deleting one removes all data in it, if you make a new one it'll be clean and empty.

---

### Post by ajeetraj on 2008-02-27
Alright, I understand your problem. Here is how I am going to advice you as I just used the same method on my own computer. I did it for Hardy but I am going to send you the link where you can get an ".exe" file to download and I am assuming that you have windows installed on your computer. 

With this method, you will not need any live CD just this exe file and then you are set for the new install. Just download the .exe file in windows, install it and then just follow the directions which is pretty simple and straight forward. After the installation, it will ask you to restart, when you restart, chose to boot up in windows and then it will give you two options: 1. to boot into normal windows or 2. if you want to boot ubuntu (live) which can be used for a fresh install as well. Of course, during that, you can easily delete or do whatever you want with your hard-drive. 

Its, easy but I will recommend this method on an ok internet speed as the .exe files is pretty small but during the installation, all the files are downloaded from the internet. 

here is the link: [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411")

Hope this helps!

Good Luck!

---

### Post by shayvasa on 2008-02-27
ok thanx all i managed to get into the live cd some how but i dont have internet in the live cd either...im now installing ubuntu again with the hope that it works..ill let u know

---

### Post by shayvasa on 2008-02-27
i got another problem now...the instalation of ubuntu gets stuck in 82%...

---

### Post by bodhi.zazen on 2008-02-27
You may need to install from the alternate CD

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by pieisgood4589 on 2008-02-27
> **shayvasa said:**
> i want ubuntu but i cant earase it to reinstall it...can u explain better the partioner thing plz?

I have no idea what you're asking. Use proper English, please! Jeez...

OK, you don't need partition knowledge unless you're trying to dual boot. Just pop in the install LiveCD when the computer is off, boot it up and it should boot off of the CD. If not, check your BiOS. And, an RW disk has just as much likelihood of reading as an R disk, so don't tell him not to use RW. Get your facts straight.

Once the LiveCD is booted, just double click "Install," follow the steps, and when you get to the part on where to install or manually edit the partition table, just select the option to install over an entire disk, and select your HD. That should do it.

Now then, onto my Diet Coke...:lolflag:

~pieisgood4589

---

### Post by shayvasa on 2008-02-27
pieis i did all that and it gets stuck in 82%. and i dont want to dual boot...i only want linux...no windows;)

---

### Post by bodhi.zazen on 2008-02-27
> **pieisgood4589 said:**
> I have no idea what you're asking. Use proper English, please! Jeez...

LOL, coming from someone with "you so funnay!" in the avatar, :lolflag:

---

### Post by djbsteart1 on 2008-02-28
> **pieisgood4589 said:**
> I have no idea what you're asking. Use proper English, please! Jeez...

OK, you don't need partition knowledge unless you're trying to dual boot. Just pop in the install LiveCD when the computer is off, boot it up and it should boot off of the CD. If not, check your BiOS. And, an RW disk has just as much likelihood of reading as an R disk, so don't tell him not to use RW. Get your facts straight.

Once the LiveCD is booted, just double click "Install," follow the steps, and when you get to the part on where to install or manually edit the partition table, just select the option to install over an entire disk, and select your HD. That should do it.

Now then, onto my Diet Coke...:lolflag:

~pieisgood4589

this isnt actually, well if it is then can someone explain why i have had those problems with rw. and it is advised on many distro sites not to use rw disks with their images.

---

