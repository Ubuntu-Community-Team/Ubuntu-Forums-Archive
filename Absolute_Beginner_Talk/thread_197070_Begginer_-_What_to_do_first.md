---
title: "Begginer - What to do first?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Bainy100 on 2006-06-15
Hey Guys, 
My first post, so please go easy on me. Ive been around the forums for a few months now, but finally got my CD's a week ago and wanted to say hi.

To cut a long story short, im very new to Ubuntu and was just wanting a bit of help, advice or point into the right direction.

So i was wondering, what are my first steps? 
Like on a windows box, format, install windows, you reboot, you install your antivirus, you install firefox, get word packages etc..

So my question is, what do i install first to get a stable Ubuntu OS?

-Install ubuntu with my partition for dual boot. Would you recommend installing Ubuntu and then windows?
-Install Antivirus? Altho i havnt seen much about antivirus on ubuntu.
-Install firewall - Firestarter? Anything else?
-Then what do i install for everyday general use? Word processing and things....

Ive tried searching the forums, there are some usefull topics, but for a  begginer like me, i havnt seen much for a basic guide for first timers.

Hopefully will get some good feedback.

Cheers,
Bainy100

---

### Post by fordfan753 on 2006-06-15
No antivirus necessary.
Most people will want to get all the multimedia codecs, especially the video ones, working.
OpenOffice.org should be installed, and is compatible with MS Office.
I just do lots of little things, they usually involve setting up an SSH server and making everything look how I want it.

Lately a lot of people have been installing XGL or AIGLX to get the latest eyecandy goodness, but it's not a neccesity.

---

### Post by Nikusan on 2006-06-15
Install windows first. This way grub can detect your windows install and make it nice and simple for you to dual boot. Doing it the other way around is difficult because windows doesn't play nice with anything or anyone else.

After you're installed you don't really need any firewall or antivirus, however firestarter might be useful depending on what you want to do.

There are some awesome pages on the wiki that you can read once you're up and running.

Check out [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation) and [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) in particular.

---

### Post by Bloch on 2006-06-15
1. Install windows first and then ubuntu. It can be very tricky to install windows after ubuntu. Windows will want to take your whole disk.

2. When windows is installed, then put in your ubuntu installer CD and boot from the CD. There is an option to install on max free space, 90% of free space, 80 % of free space etc. I would choose 80% of free space to leave yourself some room on windows. But make sure you have about 6GB for ubuntu. (That's not an absolute minimum, but you need some space for extra programs and files)

3. No antivirus is needed for Linux at home. (for a company with a mixed network of MS windows and linux it's different)

4. No firewall is needed for home use.

OpenOffice is already installed.
Now the BIG problem. You need to install all the propietary stuff to play mp3's, DVDs, wmv, wma, flash, java, MS TT fonts, realplayer

This is made easier using automatix
You should read through the general guide to Ubuntu first
[http://help.ubuntu.com/ubuntu/desktopguide/C/index.html](http://help.ubuntu.com/ubuntu/desktopguide/C/index.html)

Last don't worry. It's going to run fine.

---

### Post by RudolfMDLT on 2006-06-15
Hi bainy!

Would you recommend installing Ubuntu and then windows? - NO!

Sorry but this is very important! Windows is a very unfriendly bugger and the bootstrap loader won't load your Ubuntu system. The easiest thing to do is install MS Windows first, get it stable and running so that when the crap does hit the fan in Ubuntu you can return to something you know well in order do get some help. Just jumping into Ubuntu, unless you have lots of free time is not a wise thing, the learning curve can be quit daunting.

Secondly, Ubuntu has everything, email, office and the rest you can download. The detail in getting the system setup is not a single post. You may encounter problems that each require some help. So read up on how to format you system and dual boot with windows. There are a couple of good how to's out there so I'll link some later on this post.

"i havnt seen much for a basic guide for first timers."

You won't find a magic have it all guide, like I said, there is a learning curve involved. 

Lets start with what  you do know and don't. Read the How to's. use google allot! :) and then, when you know what you want to do, you know where you want to get but struggle getting there we'll help all we can!
If you could, post your hard drive setup and what you want to use the computer for. Getting the portioning right the first time saves you allot of crap later on.

Just an example: When you install windows, you have 1 drive and on that drive you have a file named swap.sys. Everything stems from this one drive. In linux in general you have a root, from root you have a drive/partition for linux, a drive/partition for the swap file and hopefully you would have created a drive/partition for your home directory.

In English, If you have one drive, your gonna have to chop it in at least 3, maybe 4 peaces. 1 for windows, 1 to install linux in, 1 for swap and 1 for mounting your home folder in. 

Lets assume you have 1 hard drive. When installing windows, you are presented with a list of possible drives to install on. Here I would create a partition using 50% of the hard rive space. leave the other half unpartitioned. Install windows and get it up and running. The when you insert the dapper cd and boot from that you won't have to move any partition boundaries(these can cause crap). 

The how to's on getting started and installing dapper should help from here and cover the detail on how to install the system. I would just recommend when setting up windows to already have the drive cut in half.

Goodluck!

The Wiki:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
How to dual boot:
[https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28Boot%29%7C%28Dual%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28Boot%29%7C%28Dual%29)
A really nice guide to installing and setting things up:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

PS: the best advice was already given - "Last don't worry. It's going to run fine."

---

### Post by th3james on 2006-06-15
Hi, and welcome to the ubuntu community!

1. Put windows on first, then install ubuntu, as ubuntu will detect windows, and install a bootloader that will allow you to select either when you turn on your computer

2. The number of viruses that attack linux are negligible, so you don't need an antivirus, as you arn't succeptable to viruses, adware, and malware. Its great being able to surf the web without constantly worrying about getting attacked!!!

3. Firestarter is a good firewall, but alot of people run linux without a firewall, again due to the lack of security threats.

4. Ubuntu comes loaded with thousands of apps (all free) which cover most users general use, if your looking for a particular sort of program, or a linux equivalent of a windows program, searching the forum should find what you need.

easyubuntu and automatix provide a nice simple way to setup basic stuff on your ubuntu box, so this is usually my first stop when i install ubuntu. EasyUbuntu, imo, is probably easier for those new to the world of linux

[EasyUbuntu]("http://easyubuntu.freecontrib.org/get.html")
[Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646")

Have fun, and if you have any problems, searching the forum usually provides the answer, but if not, just ask.

oh, and if someone gives you command, and tells you to put into into terminal (easyubuntu will), you'll find that under Applications -> Accessories -> Terminal

---

### Post by Bainy100 on 2006-06-15
Thanx for the quick replies guys,

Nikusan il take a look at those wiki pages you have given me links to, much appreciated.

fordfan753, thanx, i think that i will deffinately be getting the codects, always watching videos and listening to music.

Another question, which is the best Messenger that everyone uses? Ive seen a few aMSN and a couple of others that people use. 
I use MSN on a daily basis so i deffinately need someting compatible. Which would be best?

Wow, getting lots of replies already.. Thanx for everything guys, going to let this post run and then get an overall picture of what steps to take...

---

### Post by dvarsam on 2006-06-15
Dear "Bainy100",

Welcome to Ubuntu!

[QUOTE=Bainy100]What do i install first to get a stable Ubuntu OS?

1. Install ubuntu with my partition for dual boot. Would you recommend installing Ubuntu and then windows?
2. Install Antivirus? Altho i havnt seen much about antivirus on ubuntu.
3. Install firewall - Firestarter? Anything else?
4. Then what do i install for everyday general use? Word processing and things....

Bainy100[/QUOTE]

Answer to Question 1:
NO! IF you want to Dual-boot, First install Windows & Then Ubuntu!
Windows does NOT recognize Ubuntu & will delete the whole Ubuntu OS...
Ubuntu on the other hand recognizes Windows & Installs on a diff Partition.
So, Create some Partitions:

a. For Windows: NTFS
b. For Ubuntu: leave it unpartitioned
c. Another Partition: FAT32 (to move files between the 2 OSs)
d. Another Partition: as Swap (twice the size of your installed System Memory)

Then install Windows on the NTFS Partition.
Then install Ubuntu on the Unpartitioned Space (format it as EXT3).

You are all set afterwards...

2. You do not need to install this - Ubuntu is safe from viruses.
3. You do not need to install this - Ubuntu, again, is safe.
4. Everything is already installed, it is up to you what you want to install later!

Good Luck!

---

### Post by Bloch on 2006-06-15
Important:
If it is not a fresh installation of windows, run defragment before installing ubuntu. Defragment is on the windows menu somewhere under system tools or something.

---

### Post by RRS on 2006-06-15
As stated above, install windows first. If you already have windows running on your machine then the hard part is over.

It's always a good idea to backup any data before installation "just in case". Also before installing Ubuntu run one or two defrags of windows.

I (and many others) have followed [this installation guide]("http://users.bigpond.net.au/hermanzone/index.htm"). It's easy to follow and quite complete.

You may also find [this site]("http://www.psychocats.net/ubuntu/index.php") usefull.

Hope this helps and welcome :)

---

### Post by Bainy100 on 2006-06-15
Thanx guys, learning a lot just in a few minutes from the replies i keep getting. Keep hitting refresh and there is another post!! 

Starting to get an overall view of what to do now.
Step 1 - Install Windows
Step 2 - Install Ubuntu
Step 3 - Install Automatix
Step 4 - Start collecting usefull programs.

Off Topic, thanx to everyone for the great welcome to the forums, everyone seem so genuine and happy to help... Not scared of posting anymore lol!

Anyone want to recommend a good Messenger compatible with MSN?

Cheers,
Bainy100

---

### Post by Nikusan on 2006-06-15
[QUOTE=Bloch]on the windows menu somewhere under system tools or something[/QUOTE]

I always crack up when someone gives windows directions like this (don't take offence, I do it myself). "Defragmenting"... such a quaint concept. ;) 


As far as msn goes, ubuntu comes with a great IM client called gaim which should suit you quite well for msn. Unfortunately (fortunately?) it lacks some msn features such as custom emoticons, wink and nudges. If you really need these features check out amsn and kopete. Both are available in the repositories.

---

### Post by Nikusan on 2006-06-15
Bainy100, are you familiar with how installing software from repositories works?

If not check out this excellent guide: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by dvarsam on 2006-06-15
Don't forget - Before you even start:

1. Backup all your Windows files.

2. If you do NOT have available Partition space for your Ubuntu, you need to decrease your Windows Partition. To do this:

a. Defragment your Windows Partition.
b. Use the program "Partition Magic". to decrease the Windows Partition Size.
c. Create the FAT32 Partition (from the Windows OS).
c. Go ahead & Install Ubuntu (2 Partitions: EXT3 & Swap)

Have Fun!!!

---

### Post by fordfan753 on 2006-06-15
If you're feeling adventurous you could compile GAIM from source. It will give you an IM program that can do nudges and custom emoticons among over things.

---

### Post by Bainy100 on 2006-06-15
Thanx to everyone who has replied, i have now got a much better idea on how to go about installing and getting Ubuntu set up.

fordfan753, Thanks for the idea, but i dont think im quite up to that yet lol. Maybe one day...

Cheers guys,
Bainy100

---

