---
title: "Strange Computer &amp; elusive Kubuntu"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by onederer on 2007-06-20
Greetings everyone!
I have a strange computer that's making me grow extra gray hairs.
For a couple of years now, I've tried to get Grub to dual boot in this system with WindowsXP Pro.  So far, no joy!  Here's why:
In this machine, Windows drive C: =** /dev/sdb1**, and Kubuntu sits on **/dev/sda1**.  It seems that Grub was never written to install itself on the drive that Windows would _not_ normally install itself into.  But in this machine, drive C:/ (/dev/hdb1) is really drive D:/ in a normal machine in a Windows environment. So that means that Kubuntu  is really installed in the equivalent of Window's C:/ drive (dev sda1).
Graphically this amounts to C:/ = /dev/sdb1 & Linux = /dev/sda1.
I found out how to access Kumbuntu by manually having to edit Grub every time that I need to use Linux.  This is getting too old and cumbersome.  I need a better way.  But I don't have the smarts to properly code Grub to make it properly run either Windows or Linux, when chosen.  I would also be happy to get this done using a floppy disk if necessary.

I've also come to another conclusion on how I could possibly access Kubuntu without needing Grub. But I don't have enough knowledge to do it on my own.  

If I were to boot up my Live Knoppix DVD, and use it to create a chroot to Kubuntu, then I could possibly fully run Linux with no problems??  But I need your help to do this, if you know how to do it.

The nasty computer is a SystemMax from TigerDirect.  It is an AMD64 machine, with 1gig of ram.  It has two Serial hard drives, which each one has it's own OS. WinXP on /dev/sdb1, and Kubuntu on /dev/sda1.  I you're going to ask why this is like this, I don't know why.  But I found out the hard way that WinXP will not install and run on the first drive (/dev/sda1). I even tried to switch the connectors on the mother board.  Then nothing would work.  Windows will not boot up in that kind of a configuration, and Grub cannot handle this setup as it stands right now.:(

So if any of you smart people has had experience in dealing with this, I would dearly appreciate it if you would share your knowledge with me.

Cheers!
:p

---

