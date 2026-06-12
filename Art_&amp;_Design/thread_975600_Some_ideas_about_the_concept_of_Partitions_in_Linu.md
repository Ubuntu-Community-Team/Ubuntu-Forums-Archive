---
title: "Some ideas about the concept of Partitions in Linux"
date: 2008-11-08
forum: Art &amp; Design
---

### Post by rocksoccer on 2008-11-08
Recently, I pay more and more attention to Linux, and started to try some Linux distribution. Although I have some experience of Linux server operation, Ubuntu desktop is my first desktop try. 

In the process, as a long time Windows user, I do find a lot of difficulties to get adopted to the new operating system. What I want to say here is not to persuade people to switch from Linux to Windows. Rather, I hope some of my words can provide the Linux developers some ideas about their futuer development. As a graduate with some background in Human-Computer interactive systems, I will try to give some explanation from some HC interaction and ergonomics aspects.

 **1. Partitions**–Partition is an important concept in Windows, although it actually exists in all operation systems. But Windows exposes the concept to users so directly. I don’t know the initial intention of this design. From my observation, these days, more and more people use Partitions in Windows as a tool to help them to organize files. Very often, you can see in Windows, there are several partitions named Movie, Music, Work and etc, which clearly indicate the use, as well as the perception from the users, about Partitions.

 In other words, if Windows completely hide the concept of Partitions, and provides a special type of folders, most users should feel too much difference.

 While in Linux, Partition is not visible. It is not difficult to understand the design. It removes the concept of Partitions from most users. But where is the bridge to connect the high level concept of folders and mount point to the low level concept of Partitions? You can say reinstall operating system is not a basic operation for most daily use, but it is absolutely an common operation for most users to store their files into another partition other than the OS partition. How do people do this in Linux? One of the important points is how people can do this without any touch on Terminals. At least I didn’t find a good tool on the Internet.

 In conclusion, the difficulty caused by file systems is not whether Linux has a tool with GUI to manage Partitions, and the relationship among Partitions, mount point, and folders. It is important for Linux developers to know how people use the ideas of Partitions.

 Partition is a technical concept for developers, however, users misuse it as a special type of folders, if you think users do make some mistakes. PLEASE remember, in ergonomics, USERS are ALWAYS CORRECT.


 **2. What is “/”?**–I think this is one of the most terrible design in Linux. At least, for any person who has no background of computer at all, they can never guess what “/” means.
 While, in Windows, in C drive, in most cases, users can easily find a folder called Windows. Even if the name cannot indicate everything clearly, I think most users can naturally feel the connection between the folder and the operating system.
 Should Linux change something about this?


 [COLOR=#ff0000]**Today’s conclusion:**[/COLOR] ***[COLOR=#ff0000]Linux, Please DON’T FORGET Users! DON’T FORGET ERGONOMICS![/COLOR]*** A little more personal explanation about the problems. I think it is the distance between the designers and the developers that caused today’s situation. During the very early days of Linux, it was developed by the technology guys. In fact, it is only possible to be developed by these people. Can you image some designers to develop an OS from the very low level? That is not about design at all. I, hopefully most of you can know what technical guys know about computer except technologies!

From:
[http://rocksoccer.xtreemhost.com/wordpress/archives/166](http://rocksoccer.xtreemhost.com/wordpress/archives/166)



Do you have any ideas?:popcorn:

---

### Post by oedipuss on 2008-11-08
> **rocksoccer said:**
> 
 **2. What is “/”?**–I think this is one of the most terrible design in Linux. At least, for any person who has no background of computer at all, they can never guess what “/” means.
 While, in Windows, in C drive, in most cases, users can easily find a folder called Windows. Even if the name cannot indicate everything clearly, I think most users can naturally feel the connection between the folder and the operating system.
 Should Linux change something about this?


What kind of weird assumption is this? How is C:\WINDOWS more evident than /home/username/ ? Just because you as a long time windows user are more used to the concept of the drive letter doesn't make it universally more natural. 
By the same logic, the slash symbol '/' which is used to delimit directories in linux, can, at the beginning of a folder hierarchy naturally mean a kind of base (or, evidently, 'root') folder. And in fact this way you have only one symbol that is used consistently, as opposed to 'C:\' which introduces both the drive letter concept, and ':' (which to be honest I don't know why it's there). 

About partitions, there are many good tools to manage them both graphically and from the command line, such as disk-manager, and gparted, or fdisk for that matter. 
Also, gnome already shows all partitions as separate bookmarks, both in the 'Places' menu and in nautilus. You can mount and eject them easily from there, without touching the terminal, and manage their mountpoints and permissions from disk-manager. I don't quite see what kind bridge you are talking about, that isn't already there.

---

### Post by bashveank on 2008-11-08
> **rocksoccer said:**
> Recently, I pay more and more attention to Linux, and started to try some Linux distribution. Although I have some experience of Linux server operation, Ubuntu desktop is my first desktop try. 

In the process, as a long time Windows user, I do find a lot of difficulties to get adopted to the new operating system. What I want to say here is not to persuade people to switch from Linux to Windows. Rather, I hope some of my words can provide the Linux developers some ideas about their futuer development. As a graduate with some background in Human-Computer interactive systems, I will try to give some explanation from some HC interaction and ergonomics aspects.

 **1. Partitions**&#8211;Partition is an important concept in Windows, although it actually exists in all operation systems. But Windows exposes the concept to users so directly. I don&#8217;t know the initial intention of this design. From my observation, these days, more and more people use Partitions in Windows as a tool to help them to organize files. Very often, you can see in Windows, there are several partitions named Movie, Music, Work and etc, which clearly indicate the use, as well as the perception from the users, about Partitions.

 In other words, if Windows completely hide the concept of Partitions, and provides a special type of folders, most users should feel too much difference.

 While in Linux, Partition is not visible. It is not difficult to understand the design. It removes the concept of Partitions from most users. But where is the bridge to connect the high level concept of folders and mount point to the low level concept of Partitions? You can say reinstall operating system is not a basic operation for most daily use, but it is absolutely an common operation for most users to store their files into another partition other than the OS partition. How do people do this in Linux? One of the important points is how people can do this without any touch on Terminals. At least I didn&#8217;t find a good tool on the Internet.

 In conclusion, the difficulty caused by file systems is not whether Linux has a tool with GUI to manage Partitions, and the relationship among Partitions, mount point, and folders. It is important for Linux developers to know how people use the ideas of Partitions.

 Partition is a technical concept for developers, however, users misuse it as a special type of folders, if you think users do make some mistakes. PLEASE remember, in ergonomics, USERS are ALWAYS CORRECT.


Um, I think you're confusing Windows with Linux. Windows DOES NOT have any means of editing the partition tables without additional software, Ubuntu does. Also, Windows does not have a folder structure dedicated to partitions, just C drive, D drive, E drive, etc..., Linux, again, does.


 > **2. What is &#8220;/&#8221;?**&#8211;I think this is one of the most terrible design in Linux. At least, for any person who has no background of computer at all, they can never guess what &#8220;/&#8221; means.
 While, in Windows, in C drive, in most cases, users can easily find a folder called Windows. Even if the name cannot indicate everything clearly, I think most users can naturally feel the connection between the folder and the operating system.
 Should Linux change something about this?

I think for someone without a tech background both / and C are confusing. What's the difference anyway? Does the additional C: magically make the folder structure less confusing? I don't think so.  Most users will never have to look at C:\ or / anyway, so what's the point?

---

### Post by tvtech on 2008-11-08
> 3 Hours Ago 03:17 PM
rocksoccer 	
Some ideas about the concept of Partitions in Linux
Recently, I pay more and more attention to Linux, and started to try some Linux distribution. Although I have some experience of Linux server operation, Ubuntu desktop is my first desktop try.

In the process, as a long time Windows user, I do find a lot of difficulties to get adopted to the new operating system. What I want to say here is not to persuade people to switch from Linux to Windows. Rather, I hope some of my words can provide the Linux developers some ideas about their futuer development. As a graduate with some background in Human-Computer interactive systems, I will try to give some explanation from some HC interaction and ergonomics aspects.

1. Partitions–Partition is an important concept in Windows, although it actually exists in all operation systems. But Windows exposes the concept to users so directly. I don’t know the initial intention of this design. From my observation, these days, more and more people use Partitions in Windows as a tool to help them to organize files. Very often, you can see in Windows, there are several partitions named Movie, Music, Work and etc, which clearly indicate the use, as well as the perception from the users, about Partitions.


seriously your willing to say that? by default windows just creates one massive partition and slowly eats it till you don't have enough space to defrag it and your computer grinds to a screeching halt.  okay I know when you fill a linux drive to max pretty much the same thing happens only worse.  but... if your clever you set your partitions on install so this wouldn't happen. 

as far as root /  goes.  who cares c:>  makes little to no sense other than your at a prompt if you don't know what to type in either system type help amazing things happen.

---

### Post by pietjanjaap on 2008-11-09
You have to learn, this takes time, then after a while you think the same as windows(because you know how it works, linux).

Windows only has a to z drive's(partitions), linux you can make more.
Linux has all things you can do with parttions(like raid,lvm), inside of linux, with windows you have to pay more.

---

