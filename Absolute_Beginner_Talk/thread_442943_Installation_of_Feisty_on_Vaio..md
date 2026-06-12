---
title: "Installation of Feisty on Vaio."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by thatsjay on 2007-05-14
Greetings everyone,

I am a newbie to both Linux and Ubuntu. I had been trying to learn about Ubuntu and had installed Feisty on my desktop with no problems. 

Last night, I was trying to install Feisty on my Sony Vaio VGN-S28GP (which is using a Win XP Pro).During the installation, the partitioning section to be exact, there was an error message "Resize Operation Failure" and I tried using manual partition and the same error appeared. 

I searched the forum and tried one of the method, which is turning off the pagefile and restart the installation and the same error message appeared during the partitioning section.

Any advice is appreciated.

Thank you.

cheers

---

### Post by zazen666 on 2007-05-14
Hi ,
I have had great success with a live cd called Gparted, which allows you to partion your HD. I used it when I recently installed xubuntu on my sony vaio VGN-S170p and worked fine.
hope that helps

---

### Post by Sef on 2007-05-14
> I have had great success with a live cd called Gparted,

[GParted]("http://gparted.sourceforge.net")'s download site.

---

### Post by thatsjay on 2007-05-14
Hi,

Please pardon my ignorance.

I am using the Live CD to install Feisty, does it mean I have to boot into Feisty and install Gparted before I start the installation? 


cheers.

---

### Post by ugm6hr on 2007-05-14
GParted is a linux program like Partition Magic on Windows.  I don't think it is on Ubuntu as default (although I'm not sure - it's definitely not on Xubuntu7.04).
If you have Partition Magic - just use that in Windows to create "empty space" on your hard drive before installing Ubuntu.  Otherwise you can use boot from a Live CD linux distro which includes GParted to do this.  The GParted CD is probably a good place to start:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
If this doesn't work on your laptop, PuppyLinux contains GParted (about 95MB download), and contains most drivers necessary for laptop functioning (and also software to write the .iso file to CD):
[ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-2.14-seamonkey-fulldrivers.iso](ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-2.14-seamonkey-fulldrivers.iso)
I have had a little difficulty resizing NTFS partitions with GParted, so make sure you've backed up your XP installation, or be prepared to re-install).
Hope that helps.

---

### Post by Big_Croc7 on 2007-05-14
The GParted Live CD (which boots, just like the Feisty install CD, but the only thing it does is run GParted) also contains a newer version of GParted, which might be more succesful.

Just a quick question: have you backed up the restore partition onto CDs/DVDs?

---

### Post by thatsjay on 2007-05-14
@Big_Croc7
Nope, I haven't backed up my restore partition. Is this necessary? 

@ugm6hr
Thank you for your advice. I will go and have a look at the websites for more information.

Thank you guys for your help.

---

### Post by Big_Croc7 on 2007-05-14
I ask because I have a Sony Vaio too, and it didn't come with any restore CDs; instead, if you want to reinstall windows you do this from a 'special' partition at the beginning of the disk.  If you're partitioning things there is a (small) chance that you might accidentally delete this.  Unless you back it up first, you won't be able to reinstall windows.

I think there's a program somewhere that guides you through making backup CDs or DVDs to restore your system later - it's probably a wise move, just in case ;-)

---

### Post by thatsjay on 2007-05-14
Hi Big-Croc7,

Thanks for the tip. i will backup all the data before I start installing Ubuntu onto the Sony Vaio. And I think I need to check whether the Vaio comes with the restore CD. 

cheers

---

