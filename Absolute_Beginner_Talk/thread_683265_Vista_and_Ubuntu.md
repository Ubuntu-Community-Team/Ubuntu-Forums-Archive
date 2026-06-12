---
title: "Vista and Ubuntu"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Gevora on 2008-01-30
Ok, I am seriously thinking about getting ubuntu, and i want to keep my Vista.  I have a Toshiba Satellite X205-S7483.  It has 2 hard drives, and i was thinking about putting ubuntu on the second hard drive, but i dont want to have to disassemble my laptop to do this.  I want to keep both hard drives in, and just install it on the second hard drive.  Also, I am concerned about losing the files on my Vista hard drive.  Can someone ease my fears about this and give me a way to install it the way i want to? Thanks.

---

### Post by Rocket2DMn on 2008-01-30
You can install Ubuntu to whichever hard drive you want, it doesn't have to be the master drive.  Of course, you should always have good backups before you do anything with drives and partitions to a computer.  During the install process you will prompted where to install Ubuntu, and you would select to wipe out the second hard drive and partition it for linux.  You will need a root partition ("/") and a swap partition which is usually 1.5-2x your RAM capacity.  You can make a separate /home partition if you want, but it's not necessary.  Having a /home partition is nice if you end up reinstalling because you can keep from overwriting it and thus save your configurations and any data stored on it.

---

### Post by oedha on 2008-01-30
may i ?
the point is how you manage the partition.......i always use Gparted
then you can design your vista buntu as you like...base on what rocket2dmn said
if you want to have one partition as a vista_ubuntu data ( just like mine ) in ubuntu you should install NTFS configuration tool......so your data can be used by both

~E~

---

### Post by Gevora on 2008-01-30
Alright, I'm new to this whole two OS thing....so I need some help.  I don't really understand partitions either.

---

### Post by Rocket2DMn on 2008-01-30
When you get to the install you will probably be presented with 2 drives, like sda and sdb (or hda and hdb).  Each partition will have a number next to it, like sda1, sda2, etc...  In windows you never really see partitions, everything is just sort of grouped together, but in linux we use partitions a lot more.  At the install, you will have to decide which hard drive to install to, which you will determine based on the size of the hard drives and the file system currently on it (since your drives are probably different sizes).  If you think it will be a problem, you can boot into Vista and format the hard drive you want to install Ubuntu on to something like FAT32 so when you go to install Ubuntu, it will be immediately obvious which drive you want to use.  
You will overwrite that FAT32 drive with the different linux partitions.  Your root partition will use ext3 format instead of NTFS or FAT32, and swap will use "swap" format.  If you use a separate /home partition, it will also be ext3.  Should you choose to have a separate /home partition, you will use only a few GB for the root partition and the rest for /home.  You can ask about specifics if you're still confused, just include the size of your HD.

---

### Post by oedha on 2008-01-30
ok then.....for me partition just like a "cupboard" each person has personal cupboard to put their belonging.....the same with vista and ubuntu.
for partition explanation...maybe you can check :
[http://www.tech-faq.com/hard-disk-partition.shtml](http://www.tech-faq.com/hard-disk-partition.shtml)
[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

~E~

---

### Post by Gevora on 2008-01-30
Yeah i still need some help.  Do I have to make those partitions prior to the install? My Vista HD is 110GB and the one i want linux on is 111GB

---

### Post by Rocket2DMn on 2008-01-30
So they are essentially the same size.  I would recommend formatting the soon-to-be linux disk to FAT32 so its easy to recognize during the install process.  You will make the partitions during the install (there will be no more FAT32, this is just for your reference so you don't overwrite windows on accident).

---

### Post by Lvcoyote on 2008-01-30
If your worried that much about identifying the proper drive during ubuntu install, just unplug the vista hard drive in side your laptop, that way ubuntu will only see the one drive you want to install too.  Its not very difficult at all to do, in fact your lappy manual should have the appropriate instructions.

---

### Post by oedha on 2008-01-30
mm....let the vista alone.
and work with the 111 on.....
split it into 3 parts : / , /home , swap ( twice of your RAM )
have you try to install ubuntu....you can found the partition manager on step 4 of 7

~E~

---

### Post by Gevora on 2008-01-30
So Rocket,
tell me about how this will affect my other hard drive.  Is there a chance that my vista may crash due to ubuntu?

---

### Post by Gevora on 2008-01-30
So Rocket,
Tell me about what it will do to my other HD.  Is there any chance my Vista might crash because of Ubuntu.

---

### Post by Rocket2DMn on 2008-01-30
As long as you don't install over vista, you'll be fine, that's the only real worry.  I'm assuming both these hard drives are internal, so it's not easy to disconnect one.  That is why I suggested the FAT32, because the Vista drive will be all NTFS.  It's just easy to see which drive is which during install.  Also, you should be able to see how full each drive is, so the drive you want to install Ubuntu on will be empty, which also makes it easy to recognize.
I'm just helping you play it safe.

---

### Post by Gevora on 2008-01-30
yes, they are both internal HD's.  What are possible complications that could happen during installation?

---

### Post by Rocket2DMn on 2008-01-30
Look, all I'm trying to do is make sure you don't overwrite windows - you can stop stressing and start installing.  I'm not meaning to make you nervous, there really isn't anything to worry about.

---

### Post by Gevora on 2008-01-30
Thanks for all this help.  If I decide to install from a download, how does that work?  Does it put an icon on my desktop and i just run it, or what?

---

### Post by Rocket2DMn on 2008-01-30
You download the LiveCD, burn the image to a disc, and then boot your computer from the cd.  It will load a live session, then you will be given the option to install.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
I gtg right now, but I'll check back in a few hours.  Good luck and welcome to Ubuntu!

---

### Post by Gevora on 2008-01-30
Thanks! If I have any questions, I'll ask.

---

### Post by Paqman on 2008-01-30
Have a read of this [guide to installing Ubuntu on a Windows machine](http://www.sp0rk.co.uk/Archive/Issue10/stayingin_install_ubuntu1.php), and the awesome [Psychocats](http://www.psychocats.net/ubuntu/) for more info.

---

