---
title: "EMERGENCY PLEASE HELP ME! Please anyone?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by eldara5 on 2007-07-23
UPDATE:
Ok i got me my windows disks but when booting from them i recive the Blue screen of Death, It says something about making sure my hardware is installed properly, but as you should know bit hard to do with an unbootable computer how can i fix this?







Guys i did a stupid thing and i need some help, i wanted to get rid of ubuntu and put it back to windows only because my father was complaining (Hes going to buy me a new computer for ubuntu) so i deleted all the partions on my hard drive except the windows ones, and then made the windows one big again.
Now after i reset my computer i had a error that it couldnt find GRUB, so my computer wont boot up again, how do i get rid of grub and set my computer to boot up from windows again.
Now my computer is extreemly broken how can i fix it again please somone help me

Thanks in advance,
Eldara

Ive googled it but i dont have the windows CD disks i broke them so i cannot boot from that there must be a way to either remove or fix grub from the linux terminal on live CD, isnt there?

---

### Post by oilchangeguy on 2007-07-23
you're going to need to borrow a friends windows disc. you need to repair the master boot record. or, does your computer have a floppy drive? if so you can use a windows 98 boot floppy.

---

### Post by splintercellguy on 2007-07-23
You could try to use Super GRUB to repair the MBR.

---

### Post by oilchangeguy on 2007-07-23
see [www.bootdisk.com](www.bootdisk.com) you can create a 98 boot disc from there. you may also be able to create an xp boot cd. see the site for details.

---

### Post by geek_Man on 2007-07-23
Definately try Super GRUB Disk.

---

### Post by wolfen69 on 2007-07-23
i had to do something similar. i put in the xp cd, hit R for revovery cosole and did FIXMBR.

---

### Post by anewguy on 2007-07-23
This is a very common post in this forum, so I'll post an answer here I hope more people see:

BEFORE you ever delete Ubuntu on a dual boot system, do the following:

- boot Windows
- follow this link and down the mbrfix program - it's free:

        [http://www.download.com/MbrFix/3000-2094_4-10485991.html]("http://www.download.com/MbrFix/3000-2094_4-10485991.html")

- after you have downloaded the program, unzip it and put it in the root (c:\) foler
- open a command line window (via accessories)
- cd \
- type  mbrfix /drive 0 fixmbr /yes
- with XP you can go to disk management and delete the Ubuntu partitions
- reboot Windows - it will run a chkdsk when it first comes up but that is okay - I haven't had any problems yet and I have done this several times!

That's it.  Do it BEFORE you ever try to delete Ubuntu.  You won't need to download a cd image, use another OS diskette, etc.  It easy.  It works.:)

---

### Post by eldara5 on 2007-07-24
Thanks for the replys guys your really helpful im trying to get a bootdisk working no luck yet gonna need to lend my mates Windows disk but hes in work  a few people have said:

Super GRUB Disk

Where can i get this?

---

### Post by LaRoza on 2007-07-24
See my sig, it works for any Windows, including Vista.

-EDIT it is easy to use, just follow the directions. You have a lot of choices, but the right one should be easy to find.

---

### Post by mlentink on 2007-07-24
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by jimbob on 2007-07-24
I tried to make a Super GRUB disk but after unzipping the image and trying to write it to the floppy I get an error that it is too large to fit.  Floppy holds 1.44Mb and image is 1.47Mb.
I followed these instructions:

How to make your Super Grub Floppy Disk
In Ubuntu or other Linux,
To make a Super GRUB floppy disk in Ubuntu
   1) Put your sgd_0.9575_english_floppy.img.bz2 file in your home/username directory if it isn't there already.
   2) Right click on it and click 'extract here'. You should get a new file out of it called super_grub_disk_floppy_english_0.9575.img
   3) Put a blank floppy disk in your machine's floppy disk drive.
   4) Open a terminal
   5)  Use this 'dd' command to write SGD to the floppy disk, or you can copy mine and paste it into your own terminal if you want.
Do not include the herman@red:~$ part, (unless your name is herman and you have a computer named red too).

Code:
herman@red:~$ dd if=super_grub_disk_floppy_english_0.9575.img of=/dev/fd0

That command should make the floppy drive light come on and you should hear some moaning and groaning noises coming from your floppy drive for a minute or so, then you should have a new Super GRUB floppy Disk.

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by adrian15 on 2007-07-24
At last something interesting to look at!
What version did you use the 0.9598 one?

I have to fix it! :tongue:

Meanwhile you can burn a cdrom or try an older version or a newer version.

adrian15

---

### Post by jimbob on 2007-07-24
> What version did you use the 0.9598 one?


Yes ...
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sailor2001 on 2007-07-24
that [www.bootdisk.com](www.bootdisk.com) works.... download a win 98. that works on xp also

---

### Post by lemonseed on 2007-07-24
This option is probably major overkill for your situation but it's saved my neck quite a few times.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

It has SuperGrub included plus many many useful tools.

---

### Post by adrian15 on 2007-07-24
> **lemonseed said:**
> This option is probably major overkill for your situation but it's saved my neck quite a few times.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

It has SuperGrub included plus many many useful tools.

If you try to burn a cdrom I advise you to use Super Grub Disk if you are in a hurry because its less than 2 MB meanwhile UBCD is 300 MB or more in size.

adrian15

---

