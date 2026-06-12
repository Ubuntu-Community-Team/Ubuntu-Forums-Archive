---
title: "Partition my system to Install another Linux Distro"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by manmohanpv on 2007-12-21
Hi Frnds

Looking for a help.

I have a inspiron 1420 notebook runnning ubuntu 7.04.

I'm thinking to add one more linux distribution to my system and have a multiboot setup

The output of parted (print) shows me following details:-

#######################################
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  82.3MB  82.2MB  primary   fat16             
 2      82.3MB  2237MB  2155MB  primary   fat32             
 3      2237MB  2443MB  206MB   primary   ext3         boot 
 4      2443MB  160GB   158GB   extended               lba  
 5      2443MB  5083MB  2640MB  logical   linux-swap    
 6      5083MB  160GB   155GB   logical   ext3  
##########################################

Please advice how can i go ahead the make it?

Thanks & Best Regards
manmohanpv
    
 6      5083MB  160GB   155GB   logical   ext3

---

### Post by nowshining on 2007-12-21
are u using the gui?

---

### Post by manmohanpv on 2007-12-21
Yes, i do

Is there any GUI based tool for doing this?

-M

---

### Post by ReverendJ1 on 2007-12-21
I think you are looking for GParted. If I remember correctly (sorry, I am not at home in front of my Ubuntu box) it is called "partition editor' or something similar in the menu. It should be under Applications -> System Tools.

---

### Post by thelatinist on 2007-12-21
Use GParted (the GUI partition editor for Gnome).  System > Administration > Partition Editor.  You can resize and move your partitions until you get it right and then click "apply" to apply your changes.  Because GParted can only work with unmounted partitions, though, you should probably use it from a Live CD.  Either use the Ubuntu LiveCD or download a GParted LiveCD (less resource-intensive and doesn't mount any partitions by default).

---

### Post by manmohanpv on 2007-12-21
I have a snapshot of the Gparted view of my drive.

[http://bp1.blogger.com/_cjWR5DDX0kE/R2xk61i4j4I/AAAAAAAAAPA/DTO6gu_zyZY/s1600-h/Image006.jpg](http://bp1.blogger.com/_cjWR5DDX0kE/R2xk61i4j4I/AAAAAAAAAPA/DTO6gu_zyZY/s1600-h/Image006.jpg)

Now pls tell me which one should select and resize.

Happy Holidays!!

-M

---

### Post by eolson on 2007-12-21
The only one that even looks big enough is the bottom one.

It's been years,  but many moons ago,  I dual booted Red Hat and Mandrake.   Think I loaded Mandrake second,   but just followed the directions on the install disk.  It's been so long,  I don't remember what the directions were.  I do remember that it wasn't a big deal.  After you got by the desktop Linux was Linux.   One used Gnome (Red Hat) and Mandrake use KDE.

---

### Post by thelatinist on 2007-12-22
> **manmohanpv said:**
> I have a snapshot of the Gparted view of my drive.

[http://bp1.blogger.com/_cjWR5DDX0kE/R2xk61i4j4I/AAAAAAAAAPA/DTO6gu_zyZY/s1600-h/Image006.jpg](http://bp1.blogger.com/_cjWR5DDX0kE/R2xk61i4j4I/AAAAAAAAAPA/DTO6gu_zyZY/s1600-h/Image006.jpg)

Now pls tell me which one should select and resize.

Happy Holidays!!

-M

/dev/sda6 is the one to resize.  It's your largest and has the most free space.

I notice you used a camera to take that screenshot.  You do know that you can just press the PrtScn key to get a perfect screenshot of your current desktop, right?  It will bring up a dialog asking you where to save it and everything.

---

### Post by nowshining on 2007-12-22
or 

alt + Print Screen

to get a snapshot of the current window (make sure ur cursor is in the windows u want to take a pic. of

---

### Post by manmohanpv on 2007-12-26
I booted my system with a Gparted CD. i guess it doesnt allow to take screenshot by pressing that key.

looking for more explanatory information on how to install another linux distro on my dell ubuntu box. For example, installing knoppix or backtrack or gentoo, some thing non-commercial ones...will it do partition by its own?

---

### Post by Presto123 on 2007-12-27
I'm a bit curious why you have a Fat16 and Fat32 on this thing. Looks really cluttered, but I like as little mess as possible.

In that Gparted, You can click on the partition you want mounted and it should allow you to resize the partition at the top. I suggest with that size of a HD that you use at least 20-30 gb for what you want. Just enter that in the bottom but remember it goes by MB. 

I wouldn't worry about formatting it just yet and let the partitioner included on another Live disk format that for you. Just watch out when you run through the partitioner, because it might say "Guided, Use Entire Disk".

---

### Post by bodhi.zazen on 2007-12-27
Basically it is very straight forward and very similar to your first install.

You can share the swap partition across disro's, even with BSD if you want.

The only problem may be with grub. Normally it is automatic.

IMO it is best to chainload your linux distros. This is a little more advanced, but it is easier in the long run.

===========

mini how-to

The advantage of chainloading is that each distro will take care of kernel updates automatically once it is set up (otherwise you will need to do this manually).

Basically one distro becomes a /boot partition. For example imagine you have 2 linux distros installed, I will call them A and B.

OK, now when you install each distro install grub into BOTH the MBR and the root ( / ) partition for each distro.

So for A it is no problem.

When you install B, edit /boot/grub/menu.lst

Edit the stanzas for A to :

title A
root (hdx,y)
chanloader +1

When you boot A you will get a second grub screen, choose A

Once it is working, change the grub settings (default OS and a low time out)

Again the advantage is , when you update A and add a new kernel, the second grub screen will automatically incluede the new kernel and you will not have to manually update the /boot/grub/menu.lst on distro B

if that makes sense ...

If not, ignore all that, go ahead and install B and I doubt you will have any immediate problems.  You may need help if you update a kernel ...

---

