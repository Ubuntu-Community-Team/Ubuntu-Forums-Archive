---
title: "Switching To Linux...."
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Gunblade on 2005-11-16
Ok after playing with many distro's since last June. I have pretty much chosen Ubuntu as my favorite on a desktop. I have always been installing the different distro's and testing them on a OLD Laptop, and a Gateway P4 machine from 2000. 

Well I no longer have those machines...and after helping a friend install a FTP server (his first time w/linux so i brought my Ubuntu CD's over) for our little group of friends. I decided I wanted to use Linux pretty much full time. 

The problem is I love some windows software, and I play games on my PC all the time. I tried using Ubuntu on a partition awhile...but it didn't really work out. So here are my questions. 

Is there a way for Ubuntu to read NTFS? I want access to my windows files, my music, my pictures, my videos etc. while I am using Ubuntu. If I can't looks like I will just continue using windows. 

Ubuntu pretty much introduced me to linux and has had me hooked. Ever since then I have learned a lot and try out other distro's all the time. So you guys are doing an awsome job, I have spread the word over here in Washington. Despite the fact that my parents work for MS lol D:

---

### Post by Kyral on 2005-11-16
Parents work for MS? Wow...talk about infiltration power! If you can get them running Linux...mwahahahaha

*Ahem* Sorry :D

Anyway, yes Ubuntu (and Linux in general) can read NTFS just fine. Its WRITING that is the problem. When you get to the partitioner, go to manual partitioning, select the Windows partition, select use without formatting, and mount it on /media/windows (one of the options). Then just continue on and when you reboot into Ubuntu you should have read access to the partition

---

### Post by kruz on 2005-11-16
yes
infact when i was dual booting on my desktop
i specifically formatted with fat32 for my fs
because of that fact that it has no security lol

n e wayz if you really need to modify files
you can copy them to ur desktop or w/e
change them
whatever u want
and when u boot back into windows
they have ext2 and ext3 fs reader/writers
actually ive heard of a plugin for M$ explorer
but i cant quote that dont hold me to it

hope this helps


mkdir /windows
sudo mount /dev/hda1 /windows

now about those parents......

---

### Post by Gunblade on 2005-11-16
OK wow a little confusing, guess I will go to the IRC for help when I am doing this. 

Alright so I have a free 20gig partition for Ubuntu. I have two harddrives one is 80gigs (where winxp_pro is, programs, games) and then a 160gig which I set to as "Documents and Settings" for windows. In that I have an archive of install files, CD/DVD images, music, video etc. This is all in NTFS of course.

If I install Ubuntu, on the partition, I can just browse the drives even though they are in NTFS and play say Mp3's from it? I am a little confused. I think I might as well just install Ubuntu now, and once I am done configuring it, ask in the IRC >_<"

---

### Post by aysiu on 2005-11-16
For a totally not confusing guide to dual-booting, check [this](http://users.bigpond.net.au/hermanzone/) out.

[QUOTE=Gunblade]
If I install Ubuntu, on the partition, I can just browse the drives even though they are in NTFS and play say Mp3's from it?[/QUOTE] Yes. This is correct. Once you get it installed follow these instructions to get the NTFS mount to work:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=Gunblade]
If I install Ubuntu, on the partition, I can just browse the drives even though they are in NTFS and play say Mp3's from it? I am a little confused. I think I might as well just install Ubuntu now, and once I am done configuring it, ask in the IRC >_<"[/QUOTE]

Hello.

Yes. It is quite possible to get what you want. You can make it so that you can easily play all your old mp3's and media files from your NTFS drives. I do it all the time. Once you go through the steps, it will just be done everytime you boot. Here is the best guide:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)

Look at other parts of it too. 

What you cannot do is save things to your NTFS drives in Linux, delete things from your NTFS drives in Linux, or move things inside your NTFS drive in Linux. You can do all the playing and using you want tot though.

I hope I helped.

---

### Post by Gunblade on 2005-11-16
Sweet that is exactly what I wanted to do! Not change anything just read. 20gigs is enough and if I download something in linux that I need to transfer to windows thats what my networked HD is for :D (side's backup)

Thanks so much! Heh, I will only be using windows to play games pretty much.

---

### Post by Gunblade on 2005-11-18
Maybe you guys/gals have seen me on the IRC as Gunlance or calebme asking for help...but I still have yet to find a solution. 

I can not log-in to Ubuntu. There is a problem with X. I have tried configuring it myself, and turning on kernel framebuffering...but nothing has yet to work. When i configure xorg myself I get an error and it shows me that a screen was not found. 

However everything default, gives me just a green screen w/lines.

So I downloaded 5.10 burned that to CD and tried installing it, same problem but at least I can CTRL+ALT+...uh I forget..to the basic terminal. Through that I have been using irssi to get help, but have yet to really get any. So somone can maybe post a link to some guide, faq, solution, or know an answer. I really need help. If I can not get this to work, guess I will just settle for another distro. 

If it would help to know; My graphics card is a Geforce 6600GT 128mb AGP8x

---

### Post by ThirdWorld on 2005-11-18
There are several how to and threads that could help you with this issue. I was able to mount my windows HDD. However i have to use the command line in order to accomplish it. I think it will be awesome if you can mount a windows HDD permanetely with a default application.

---

### Post by ThirdWorld on 2005-11-18
[QUOTE=Gunblade]Maybe you guys/gals have seen me on the IRC as Gunlance or calebme asking for help...but I still have yet to find a solution. 

I can not log-in to Ubuntu. There is a problem with X. I have tried configuring it myself, and turning on kernel framebuffering...but nothing has yet to work. When i configure xorg myself I get an error and it shows me that a screen was not found. 

However everything default, gives me just a green screen w/lines.

So I downloaded 5.10 burned that to CD and tried installing it, same problem but at least I can CTRL+ALT+...uh I forget..to the basic terminal. Through that I have been using irssi to get help, but have yet to really get any. So somone can maybe post a link to some guide, faq, solution, or know an answer. I really need help. If I can not get this to work, guess I will just settle for another distro. 

If it would help to know; My graphics card is a Geforce 6600GT 128mb AGP8x[/QUOTE]

i suggest you post a new thread so people can read it and help you.

---

