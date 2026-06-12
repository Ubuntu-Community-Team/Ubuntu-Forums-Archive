---
title: "Installing latest version of Ubuntu on 2 hard disks"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by teabuntu on 2007-09-08
Hello everyone,
I'm new on this board, and to Ubuntu as well as to Linux. I'm in the process of waiting for the Ubuntu CD which I requested from Shipit.  In the mean time, I'm trying to learn as much as I can about Ubuntu and the whole new world of Linux.  I've been using Windows all my life, and this is the first time that I'm attempting to use a Linux distribution.

Since I am a complete computer novice, I have come to the conclusion that the best for me to use Ubuntu would be on a separate hard disk, possibly on a USB flash drive or an external hard drive.  I have Dell Inspiron 640M/E1405, with Windows XP SP2 Home Edition.  I'd like to keep my current hard disk in my 640M as is, and not fiddle around with it.  However, I'm not sure if that would be possible and the following are questions which I would like some help on:

* Would my idea of using 2 separate hard disks work on my computer system?  Also, would I be able to install Ubuntu on a USB flash drive, or does it have to be an external hard drive?
* If it works, then how do I go about setting up my external disk so that I can run Windows as well as Ubuntu?  Can I run it at the same time by somehow having some way of switching from one to the other while they are both running at the same time, or would I be able to have only 1 OS running at any particular time?  
* Does Ubuntu change any of the BIOS codes or any other files associated with Windows as well as with any of the files and codes that enable my computer to work?  In other words, does Ubuntu come with a feature which changes BIOS codes, change drivers, utility files or any other files automatically on its own and I (being a novice computer person) wouldn't know about it? 

My ideal goal would be to have Ubuntu installed on a USB flash drive, and switch back and forth between Windows and Ubuntu without having any of the codes such as BIOS etc, being changed.  I realize that using Ubuntu or any of the Linux distributions for that matter requires the use of various programming codes (eg: sudo etc).  I wish I could be adventurous enough to try out and use them, but at this stage right now, I'm not too comfortable using codes or changing any of the functionality of my computer.  I see a huge gap between what is required (in terms of understanding what you're doing when using command codes) and where I am in terms of my computer knowledge.  Although I have said that "sudo" is a programming code, to be honest, I'm not sure if it really is such a thing.  BTW, what are they exactly?  Is there a specific kind of name for these commands? (I know there are various programming languages out there.  Is there a name for the commands used in dealing with Ubuntu or Linux in general?)  If anyone knows of a good website which talks about all these command "codes" or programming languages, I would really appreciate it.  

Thank you for taking the time to read this, and for any advice you may have,
teabuntu

---

### Post by overdrank on 2007-09-08
Hi and welcome, you can run the live cd on your system to see if you will have and issue with your system before you try to install and then you can search the forums and ask question to resolve the issues.  And this link you can search and see if you find compatible hardware on your system
[http://hardware4linux.info/](http://hardware4linux.info/)
As for installing on a pin drive I would recommend this link 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
As for the commands here is a couple of links to get you started
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Good luck and welcome again! :KS

---

### Post by Ianman on 2007-09-08
Hi teabuntu,

Welcome to the wonderful world of Linux! I will try and answer your questions as best I can...here we go:

- It is indeed possible to install Ubuntu on a USB stick (as long as it is big enough) and I think it is even possible to install it on an external USB hard drive. However, that may not be necessary in your case seeing as you are so new to Linux. I would recommend that you use the Live CD option for now. When you get your CD, pop it in the dirve and boot from the CD. Most modern computers have a "one time boot" selection menu. For Dell computers I think it is the F12 button when you first turn the computer on. Just have a look at the start up screen...it usually flashes by quickly. Once you get the menu, select to boot from CD and Ubuntu will start. You can run Linux entirely from the CD without having to install anything or change any hardware settings! This is usually the best option if you are completely new to Linux.

- There is only one way that I know of that will allow you to run Windows and Linux at the same time and that is with Virtualization. This could be another option for you if you just want to try Linux. There is a software package called VirtualBox with is open source (free). You can run it in Windows and install and run Linux in Windows if you understand what I mean. It does require a fair amount of ram to work properly however as you are indeed running both systems at the same time. This configuration also negates the need to change your bios settings or anything else on your current system! You can get VirtualBox from [http://www.virtualbox.org/](http://www.virtualbox.org/)

- If you install Ubuntu in a Dual Boot configuration, it will not change any BIOS settings. It does however add a so called boot loader to your system enabling you to select which OS you want to use when you start the computer. I wouldn't use this method though considering your current experience level. Keep it simple! ;-)

- The codes you are referring to are commands that you can enter on the command line in Linux. Even though LInux has come a long way with regards to User Iinterfaces, a lot of the work is still done on the command line. You can control and configure pretty much everything from the Linux command line and it is a very powerful tool. But the beauty is, if you are new to Linux, you don't even need to use the command line. You can install and configure software using only the mouse if you want to, but I will admit, using the command line is a lot faster in many cases. To be honest, I too was terrified of the command line (Terminal in Linux terms) in the beginning, but now that I have a basic understanding and know a few basic commands, I can't live without it!

I hope you find this information helpful. If you have any more questions before you take the leap, don't be afraid to post them here!

Good luck.

Ian

---

### Post by teabuntu on 2007-09-08
Hello,
and thank you both for taking the time to reply to my post.  I really appreciate it!  You have both given me a lot of invaluable information, and a lot more to think about.
Thanks again!
teabuntu

---

