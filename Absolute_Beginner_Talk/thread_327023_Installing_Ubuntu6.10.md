---
title: "Installing Ubuntu6.10"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by electroman5 on 2006-12-28
Help!!!! I am a newbie to all forms of Linux and Ubuntu is no exception, lol. I downloaded the ISO file (698MB)  and cannot load it on my Pentium500 (512 Mb RAM). I have everything burnt on a CD but it will not boot from it or even load under Win 2K. Looks to me that an installer file is missing ??? BTW- I am using a NTFS partition. When I put my burnt CD in, it will auto start and show Ubuntu and some add-ons such as FireFox but that`s as far as I can get from there. If I `explore` the CD , all files are there except a setup file. What can I do to load this ???? Thanks, GK.

---

### Post by deadgobby on 2006-12-28
Check you BIOS to set the CDROM to read first. Reboot the system with the cd in the drive. You should be ready to rock.
Gobby
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by pseudonym on 2006-12-28
You won't be able to do anything with the CD in Win2k other than browse it. What you need to do to install Ubuntu from the CD is go into your computer's setup, or BIOS, menu and check that you are set to boot from CD first. You can usually access this menu by pressing 'delete' shortly after starting your computer. Find a menu for boot order and change it to put CD ahead of Hard Disk, then save your settings and reboot with the Ubuntu CD in the drive. The installer should then load itself and you can proceed to install Ubuntu.

EDIT - Oops - beat me to it.

---

### Post by riven0 on 2006-12-28
> **electroman5 said:**
> Help!!!! I am a newbie to all forms of Linux and Ubuntu is no exception, lol. I downloaded the ISO file (698MB)  and cannot load it on my Pentium500 (512 Mb RAM). I have everything burnt on a CD but it will not boot from it or even load under Win 2K. Looks to me that an installer file is missing ??? BTW- I am using a NTFS partition. When I put my burnt CD in, it will auto start and show Ubuntu and some add-ons such as FireFox but that`s as far as I can get from there. If I `explore` the CD , all files are there except a setup file. What can I do to load this ???? Thanks, GK.

Hi electroman,

you have to restart the comp with the livecd in the drive. Make sure you select the cd drive as bootable in your BIOS.

---

### Post by KenSentMe on 2006-12-28
Ubuntu can run besides Windows, not in Windows. So you need to boot your system from the Ubuntu install cd. To do that you have to tell your system to boot from a cd. You have to open the pc's BIOS, mostly this is done by pressing F2 or DEL when starting up (before you see the Windows logo). Then you have to look for something like the option to set the Boot Device Priority or something. Set that to boot the cd before the harddisk. Then save your settings(F10  most of the times) and restart the system with the cd in the drive. Your computer will start the liveCD.

For more directions and help check the documentation at:

[http://help.ubuntu.com](http://help.ubuntu.com)

---

### Post by kolinab on 2006-12-28
Hi,

Sounds like you're on the right track. What you want to do to install linux is to leave the CD in the drive and totally reboot your computer. So exit windows, and hopefully the CD will run and boot you into what is called a 'live session.' Initially this will make no changes whatsoever to your hard drive and you can play with things and see how linux works on your hardware. Then when you're ready to install you can click the 'install' icon and you'll be off and running.

Let us know if the CD doesn't boot - often we have to make a small change to the boot options of the computer to allow us to boot from the CD.

Before you decide to install you'll likely want to backup any data files you have as installing involves reformatting portions of your drive. Hang around these forums, read the help files around here and you should be off to a good start. One of the first decisions you will want to make is if you want to get rid of windows entirely, or do a 'dual boot' which will enable you to boot from ubuntu or xp as you choose. But back up your data in any case!

I'm sure others will have tips for you - I just made the switch a few weeks ago and am finding these forums to be an excellent help resource.

Be sure to check [http://help.ubuntu.com](http://help.ubuntu.com) and have fun! Use the forum search feature when you need help but don't be afraid to post your questions here. 

K

---

### Post by electroman5 on 2006-12-28
HI all....this old Pentium III will boot from the CD. I know about bios settings.That`s how I loaded Win2K but it will Not boot from my burnt Ubuntu 6.10 CD.....strange! I am going to try a fresh boot-install on completely wiped spare HDD using FAT32. Hopefully, that will work.
I am going bald from pulling my hair out by the roots over this. hahahahaha
Wish me luck.....GK  :D

---

### Post by jvc26 on 2006-12-28
If it doesnt boot from the burnt iso looks like it is a bad burn - have you md5 checksummed it? If that fails then you need to redownload it. If it comes up ok, change bios to boot from cd and see what happens. If no avail looks like you have a bad burn and so you need to burn the ISO to cd again. Make sure you use a very low speed to minimise burn errors.
Il

---

### Post by electroman5 on 2006-12-28
Illuvator...you were right! Yep, I have a bad burn.....aaaauuuhhhhh. I ran MD5 like you suggested and it couldn`t read start.ini  . Here I go again.....but....more carefully! lol. Thanks, GK

---

### Post by thankyousam on 2006-12-28
huh?

---

### Post by electroman5 on 2006-12-29
> **thankyousam said:**
> huh?
A bad burn, as mentioned, is when a CD-Rom is missing some files or has corrupted files due to too high a burner write speed. My CD was burnt at 32X by a friend. Personally I find that 8X speed works like a charm, albeit slow. Anywaayyy, I am ordering a CD from Ubuntu and then I`ll give it another try. Cheers, GK

---

