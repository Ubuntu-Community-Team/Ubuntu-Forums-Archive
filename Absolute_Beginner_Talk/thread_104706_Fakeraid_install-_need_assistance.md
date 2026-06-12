---
title: "Fakeraid install- need assistance"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Saldrin on 2005-12-16
Hello all. My first time attempting to use linux, I've been a windows for too long. And I'm suffering from extreme lack of knowledge of  linux.

I'm using the fakerade instructions from the wiki, and well to be honest, I have no idea what the author is talking about. I figured out I need to be using terminal and put sudo in front of my commands, but I don't understand the commands.

To back up, I am running (attempting) a dual  boot with XP already installed onto a raided system (fasttrack). I am currently running the liveCD and downloaded the dmraid package.

And now I'm stuck. I'm already steup with four partitions on my drives. Three I'm using with windows and the fourth I wanted to install ubuntu. I couldn't make heads or tails out of gparted, so I just made my linux partition from XP as ntfs. 

To be blunt: what do I do now? The fakeraid author talks about resizings and mke2fs.... no idea what those are or do... then he mounts his root and home. IIRC I can't make those because I can only have 4 partitions, right? So I tried to mount my 4th partition but I can't mount it. I tried the mkdir /target step and when I finish with the mount, which doesn't kick back any response, when I cd /target it tells me cd is not recognized command.

Basically I need uber noob instructions. I've never used linux or a unix system, and I have basically no idea what is going on. Could someone explain to me the basic steps in creating a partition in a raid enviroment and getting the install iso to recognize that partition please?

---

### Post by M_Cheevy on 2005-12-16
Saldrin,

Well, you do have a bit ahead of you, that's for sure, but in the end, success, and the feeling of accomplishment you'll get from figuring it out await you at the end.  I have just finished my own sata raid 0 install and can say it is possible.  I can also so, though the fakeraid article is very good, there are some gaps if you haven't done this before.  I'm planning on making some edits to the article but have a few more fish to fry first.  Basically, there are some topics you're going to want to read up on first:

Read up on "debootstrap installs" (google will yield as will the wiki), alot of the gaps in the fakeraid wiki are based on the assumption you have that.

Also read up on gparted.. it's not the be all and end all but it's a good partitioning program.  I would not suggest leaving your linux partition as ntfs.  in gparted you can convert it.  The problem you'll face is the number of choices.  Personally, I've tried jfs and reiserfs (fs = file system, or how the files are stored) and can say they both work.

There are some very good beginner's guides to Linux/Ubuntu and I would suggest you give them a good once over.. The thing with linux is, the time you spend reading is never a waste.

---

### Post by Saldrin on 2005-12-18
Thanks for the tips, I will research what you suggested.

I pretty much gave up trying to install for the moment. My primary use for my computer is gaming so I really want to keep the Win and raid setup. But like you said I didn't understand what exactly what the author was doing, how he got there, and what the commands mean.

I really need to know why I'm typing a command in the terminal. So as things change I know what to research and educate myself about that option(s). I don't like typing commands in and not knowing what they do. On my last attempt I lost everything. Not sure what I did, but I had to reset my cmos just to reinstall windows. Not ready to try again for some time I'm sorry to say.

I will read up on debootstrap installs, thank you for the tip.

I did convert my partitions to ext3, but I wasn't sure of the benefits or drawbacks. I've lived in a fat32/ntfs cave for too long, that these other formats mean nothing to me: I need to change that. There is a lot I need to know before attempting this again.

---

