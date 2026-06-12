---
title: "Soon to Install, Need Guidance"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by shadowofomioc on 2005-09-22
Greetings everyone.  I recently recieved my Ubuntu disks in the mail and have been utilizing the Live CD to get a taste for how the Ubuntu Linux GUI works and I find I like it immensely.  I'm planning on installing Ubuntu soon, but I have some general questions first before I install another OS on my old mans laptop here.  

Currently we have Windows XP on the computer, and this laptop also has 2 HDD's, the first of course being the resting place of the XP OS and the 2nd mainly there for storing pictures and the like.  We have about 5GB left on the 2nd HDD.

One of my main concerns is the partitioning aspect of installing the OS ( and of course accidently installing the OS and never being able to use Windows XP again lol ).  From what I've read it sounds like whenever you create a new partition on an HDD it pretty much formats the entire thing.  I'm wondering if there is a way to just create a new partition with some of that open 5GB of space on the 2nd HDD without messing up the HDD any.  My pop would be pissed lol, if that HDD got erased somehow.  I have the book Running Linux, and it speaks alot about utilizing Fdisk to create new partitions.  I'm wondering if I could pop in my Live CD of Ubuntu, and create partitions safely using the fdisk function of the linux BASH?  Basically, I need to know if theres a safe way to partition my 2nd HDD to create the primary Linux partition without screwing up the HDD.

The other aspect is of course successfully installing the OS with a dual boot setup, where my dad can simply choose to run Windows XP during boot.  Is this an easy process?  Does Ubuntu do this automatically if another OS is installed or do I have to do special tricks to make the dual boot setup work efficiently.  Pretty much, all I want to be able to do is run either Windows XP or Ubuntu upon booting the computer.

I really appreciate any sort of advice you can give me and straight information or steps I need to do before installing.  Especially with the partitioning and dual boot stuff.  Step by Step would be nice ( even though the show was horrid lol ), but anything is good right now.

---

### Post by Wolki on 2005-09-22
I'm not really an expert for dualboot anymore (didn't on my own machine for years).

[QUOTE=shadowofomioc]
One of my main concerns is the partitioning aspect of installing the OS ( and of course accidently installing the OS and never being able to use Windows XP again lol ).  From what I've read it sounds like whenever you create a new partition on an HDD it pretty much formats the entire thing.  I'm wondering if there is a way to just create a new partition with some of that open 5GB of space on the 2nd HDD without messing up the HDD any.[/quote]

5 gb isn't that much, but it should be be enough. If you can, give it another few gigs, you might want to play around with stuff.

It is possible to use the free space, the Ubuntu installer will offer you a choice of formating the entire drive or doing a custom paritioning. Using that you can choose to resize a partition.
You can also use a partitioning program for windows (such as Partition Magic) to do the partitioning.

Whatever you do, remember to defragment the drive first.
> 
  My pop would be pissed lol, if that HDD got erased somehow.  I have the book Running Linux, and it speaks alot about utilizing Fdisk to create new partitions.  I'm wondering if I could pop in my Live CD of Ubuntu, and create partitions safely using the fdisk function of the linux BASH?  Basically, I need to know if theres a safe way to partition my 2nd HDD to create the primary Linux partition without screwing up the HDD.


You can do that too, but it's even more complicated than the ubuntu installer.
> 
The other aspect is of course successfully installing the OS with a dual boot setup, where my dad can simply choose to run Windows XP during boot.  Is this an easy process?  Does Ubuntu do this automatically if another OS is installed or do I have to do special tricks to make the dual boot setup work efficiently.  Pretty much, all I want to be able to do is run either Windows XP or Ubuntu upon booting the computer.
Ubuntu should do that automatically. In rare cases windows won't boot anymore. I've had such a case where enabling LBA in the bios fixed it. It would be good if you have another pc with internet connection nearby, just in case your ubuntu won't go online and you XP doesn't boot. You can usually find help fast, either here or in the ubuntu irc channel.

If you have more questions, feel free to ask.

---

### Post by aysiu on 2005-09-22
If you ask me, you shouldn't do it. It doesn't sound as if it's your computer to mess with, and--especially if you're a newbie--you could really mess things up if you don't know what you're doing (which is fine, usually, if you back up your work and it's your own computer to mess up).

I think you'd be much better off 

1. messing around with the live CD for a little while longer
2. saving up to get a super-cheap computer to mess around with
3. going to Goodwill or checking Craigslist to see if there are any free or super-cheap computers you can play around with.

---

