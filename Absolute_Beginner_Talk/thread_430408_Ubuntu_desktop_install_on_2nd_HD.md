---
title: "Ubuntu desktop install on 2nd HD"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Nimis on 2007-05-02
Again another beginner question

Iam running Xp pro on 1 HD. 

Is it possible to install Ubuntu desktop ,ubuntu-7.04-desktop-i386.iso,  on my 2nd HD and then choose if I wish to boot to Xp or Ubuntu.

*EDIT*
Does both drives have to be set to Master ?

---

### Post by Famicommie on 2007-05-02
Yes. Ubuntu also installs a program called Grub, which will present you with the option of booting into windows or linux when you turn your computer on.

---

### Post by Nimis on 2007-05-02
Thanks for your quick reply.. I just aded an EDIT..

---

### Post by Famicommie on 2007-05-02
To your EDIT: no. I have been running Ubuntu 6.06 on my slave drive for six months without any problems.

---

### Post by adza on 2007-05-02
Nimis,

     This is one of the easiest things i've ever done in ubuntu... :) To begin, open the BIOS in your machine and set the boot priority of you HDD's to boot from the linux (2nd) drive first, this will ensure that you boot with GRUB boot loaded. (set cdrom boot first, HDD second - this will then allow you to boot from cd first - it is a good idea to change this back once finished if you are concerned about physical security... ie, someone booting from livecd on you machine)

    Next, install ubuntu from livecd onto the 2nd HDD (I allowed the auto partitioning of this drive as i wanted to use the whole drive).

   Reboot the machine, and start being happy :)

---

### Post by Luffield on 2007-05-02
Note that Windows may freak out when it looses one of the hard drives - if you were using your second hard drive to store files from Windows and then you format it to EXT3 when you install Ubuntu, Windows won't be able to read the EXT3 file system and will work very slowly because of this.
It happened to me when I installed Ubuntu, but it was in the 5.10 days, I hope my memory serves me right here... Anyway I had to disable the second hard drive on the Windows device manages or whatever it's called. It was a 2-minute job.

Good luck!

---

### Post by Nimis on 2007-05-02
****EDIT****

[SIZE="4"]Problem Solved[/SIZE] :) 


I appreciate the replies that Ive gotten so far.

What I should of done in my first post was to explain what _exactly_ my goal is by installing Ubuntu.
About winxp files on my 1st drive it's not a problem. I can always acess them by setting the drive to Slave.
The system will be running our Clan Counter-Strike Source SRCDS server and _nothing else_

Now Ive downloaded the Ubuntu Server Edition ubuntu-6.06.1-server-i386
and check the files using md5summer, all ok, then burned the iso, all ok.

Inserted the cd  and it booted. The main Menu of Ubuntu came up with the following:

Install to Hard Drive
Install a Lamp Server
Check CD for defect
Rescue a broken system
Memory Test
Boot from Harddrive

The first option was highlighted "Install to Hard Drive" but I was not able to move to any other options or even press Enter for the first option , no responce from my keybord.

What can the problem be ?


----------------------------------------------------------------------------------------------
Installtion will be on a:
MB= Gigabyte 8INxp
 P4   2.8Mhz
1gb ram 266mhz
120gb Segate (NOT SATA, old IDE cables) Master

-----------------------------------------------------------------------------------------------


/Nimis

---

