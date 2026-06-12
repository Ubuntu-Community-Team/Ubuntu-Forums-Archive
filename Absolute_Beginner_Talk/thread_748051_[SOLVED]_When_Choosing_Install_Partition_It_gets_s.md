---
title: "[SOLVED] When Choosing Install Partition It gets stuck, and stays there for hours"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by R6V2 on 2008-04-07
Well, After wasting 6 cd's, I've wasted another, I guess it's a corruption on my CD. I have got Linux running as the desktop, (From the CD) and I click the Install icon, like it says, and then at Step 5 of 6 is when it gets stuck with the swirling icon (Thinking), and I even left it there overnight. So, should I retry this, at the slowest speed when burning? Or any other suggestions, because so far I love Linux, but I don't really like booting it off the CD. (IM USING UBUNTU .06!) (If that matters)

Thanks everyone for your help. My other topic was solved. I've always loved Windows, but now I think that's different, if I can get it installed! :)

---

### Post by R6V2 on 2008-04-07
Is this like just a bug or something? Do I need a newer version? The tutorial to dual-boot says that I shouldn't use .10 version because of some conflicting problems, where it would erase your partition.

---

### Post by prshah on 2008-04-07
> **R6V2 said:**
> Well, After wasting 6 cd's, I've wasted another, I guess it's a corruption on my CD. I have got Linux running as the desktop, (From the CD) and I click the Install icon, like it says, and then at Step 5 of 6 is when it gets stuck with the swirling icon (Thinking), and I even left it there 


If you suspect the CD, there is an option to test the CD at bootup. If that works fine, we know it's not a CD issue. Why not check that first, then we can see how to proceed?

---

### Post by mikeyphi on 2008-04-07
Hi there and welcome!

There could be several reasons for your problem......
Suggestions: Go here and download Ubuntu 7.10 (or wait 2 weeks for 8.4) 

[http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)

I assume you still have Windows? Which version?
Do you have a RAID installed?

Also - if you continue to have the same problem with a newer release of Ubuntu - you should try the "Alternate" install CD - it's text-based and requires more user input but (usually) has no problems.

---

### Post by fela on 2008-04-07
you can check whether it downloaded right by checking its md5 to the one on the website, like this ```
md5sum filename.iso
``` (where filename.iso is the livecd)

you could also try the alternate (text based) installer cd...

---

### Post by R6V2 on 2008-04-07
Can I still use Dual-Booting with .10 release of Ubuntu, my main goal is to dual-boot Windows XP Service Pack 2, and Ubuntu Linux, on the same harddisk. So that at startup, I can either access both.

Hey, how would I actually test the CD at startup? (I'm very good at computers) But don't exactly know how.

Thanks for your super-fast replies guys!

---

### Post by mikeyphi on 2008-04-07
> **R6V2 said:**
> Can I still use Dual-Booting with .10 release of Ubuntu, my main goal is to dual-boot Windows XP Service Pack 2, and Ubuntu Linux, on the same harddisk. So that at startup, I can either access both.

Hey, how would I actually test the CD at startup? (I'm very good at computers) But don't exactly know how.

Thanks for your super-fast replies guys!

Yes - Dual boot with XP is no problem. Just be careful during the partition section of install that you read and answer prompts!! If in doubt use the Manual option - but unless you are very unlucky the normal option to resize your windows partition should be OK (Always back up personal data!!)

The LiveCD should have a Test option on the first menu screen.

---

### Post by R6V2 on 2008-04-07
Alright, yeah im supposted to use the default for it. I have backed up my data, because I do alot of scripting and was shaky about using a new OS, that has been known to accidentally wipe a drive. I will reboot and test the CD :).

---

### Post by R6V2 on 2008-04-07
Ok, well I checked the CD for errors, and there were none, so why is it freezing with the little icon when I choose forward on the ubuntu installer?

---

### Post by mikeyphi on 2008-04-07
> **R6V2 said:**
> Ok, well I checked the CD for errors, and there were none, so why is it freezing with the little icon when I choose forward on the ubuntu installer?

Sometimes problems if you have RAID set on your drive.
Could you give some computer specs - especially amount of RAM?

---

### Post by R6V2 on 2008-04-07
Ok, well I tried the .10 version now, and having some more problems, I have over 70 gigs free on my HD, and Ubuntu installer wont let me choose a percentage of that, like 40%, it only gives me the option to clear my drive, manual edit it, or use the largest continous space...?

If Linux is this hard to install, I might aswell stay with Windows.


EDIT: Hey, well I saw your post, When shutting down it says: 

Stopping RAID:   FAILED

If that means anything.
Hmm, I got a asus motherboard, I think around 512MB of ram or more...I'm on the CD of linux, I have a special program that tells me everything.

---

### Post by mikeyphi on 2008-04-07
Have a look in your BIOS to see if you have a RAID set up

You RAM is enough!

Before resizing windows partition - defrag windows

Then: Run the LiveCD - open gparted and see if it lets you resize your windows partition (leaving free space)

I would then go for Manual Partition - and use the free space (less about 500Mb for Swap partition) for Ubuntu ( / ) partition

---

### Post by R6V2 on 2008-04-07
So I should turn off RAID, and then defrag windows, then run gparted, and resize my windows partition, then install and use the Manual?

---

### Post by mikeyphi on 2008-04-07
> **R6V2 said:**
> So I should turn off RAID, and then defrag windows, then run gparted, and resize my windows partition, then install and use the Manual?

Perhaps you should tell us what sort of RAID you have? Before you start!!

Some info here: (copy & paste)

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=RAID&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=RAID&titlesearch=Titles)

---

### Post by R6V2 on 2008-04-07
> **mikeyphi said:**
> Perhaps you should tell us what sort of RAID you have? Before you start!!

Some info here: (copy & paste)

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=RAID&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=RAID&titlesearch=Titles)
I feel stupid now, how exactly do I see what kind of RAID I have and whats on? I looked in my BIOS, unless my RAID is:

CPU LELVEL 1-3

---

### Post by R6V2 on 2008-04-07
Ok, well it appears Linux doesn't like me, and doesn't want me to install it, and im not getting very helpful feedback, because it still was the same before I asked this. I guess im going to stay with windows, and give up on Linux, I thought I liked it, maybe not...

---

### Post by jkeyes0 on 2008-04-07
Your subject says it gets stuck when trying to choose a partition. Have you tried partitioning the drive with another CD, like the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/")?

---

### Post by DariusS on 2008-04-07
in order for a clean resize of your windows partition, all the NTFS data has to be in one area on the disk, thus defrag. there are alternates to the default windows defragger that work better, but can't think of any off the top of my head right now...
a single defrag is not always sufficient however. you may need to continuously run it until you see fewer fragmented spaces. once you get all your data into a nice, neat pile, then try to manually edit the partition for linux??

---

### Post by R6V2 on 2008-04-07
No, because, I have to choose: Forward to continue with the install, and that's when it locksup I guess...I've tried 3 different versions, and the .10 version doesn't even reconize that my harddrive has 70GB left, so it makes me wipe it for linux, and I don't want to wipe it incase something  goes wrong. So...

---

### Post by R6V2 on 2008-04-07
Can someone please help me get Linux installed. I want linux on my computer with Windows XP. I'm defragging right now.

Problems: Using .04 release, my computer freezes during the install of Ubuntu on step 5 of 6m it just sits there.
Using the .06 Release, same as above.
Using the .10 Release, When running the installer, on step 4 of 7, I cannot access my drive, so it wants to wipe my drive for linux. It reconizes my drive as having 8MB left, when infact it has 70GB of free space. I want linux to take up 60GB, but so far there is no luck. This is my last attempt at getting Ubuntu working. If this doesn't work, or no one can diagnose my problem, then I'll have to stay with Windows XP. Some dude said something about changing my RAID, no clue how to do that. (I know what it is) And I don't want to wait 4 weeks for the new release, because I want Linux now! Please Please Please Please Please Please Please Help!! I want linux bad, but it appears linux hates me. I need all the information that I can get so I can get Linux working on here! I have provided the most information I know, and hope to get some high-quality magnificent answers to solve my inpentrable problem, that know one seems to have encountered.

---

### Post by Crafty Kisses on 2008-04-07
How about we get some more system specs? To be honest, if you don't have the patience to work with Linux, and try to work out the issues, then Linux is not for you, and that's why a lot of people like Windows, because they have used it for so long, they can't stand change. So remember Linux is just a choice.

---

### Post by jkeyes0 on 2008-04-07
> **R6V2 said:**
> Can someone please help me get Linux installed. I want linux on my computer with Windows XP. I'm defragging right now.

Problems: Using .04 release, my computer freezes during the install of Ubuntu on step 5 of 6m it just sits there.
Using the .06 Release, same as above.
Using the .10 Release, When running the installer, on step 4 of 7, I cannot access my drive, so it wants to wipe my drive for linux. It reconizes my drive as having 8MB left, when infact it has 70GB of free space. I want linux to take up 60GB, but so far there is no luck. This is my last attempt at getting Ubuntu working. If this doesn't work, or no one can diagnose my problem, then I'll have to stay with Windows XP. Some dude said something about changing my RAID, no clue how to do that. (I know what it is) And I don't want to wait 4 weeks for the new release, because I want Linux now! Please Please Please Please Please Please Please Help!! I want linux bad, but it appears linux hates me. I need all the information that I can get so I can get Linux working on here! I have provided the most information I know, and hope to get some high-quality magnificent answers to solve my inpentrable problem, that know one seems to have encountered.

I think I know what the problem is with the free space. You have 70Gb of free space that you see in windows, correct?

That space is "free", but it is already formatted to work with Windows. what some of the other people have been saying is that you need to resize your existing partition (using the Manual option in the installer, or the Gparted live cd) then use the rest of the space for Ubuntu.

If you're going to resize that partition, you would be best served to go back into windows and defragment the drive before doing so, just to make sure no data is lost or corrupted in the process.

---

### Post by R6V2 on 2008-04-07
Ok, well the manual option, what do I need to set it at? Because I don't want to lose Windows.

I'm running defrag right now, at 70%, I'll run it again too.

MS Windows XP SP2
AMD AthlonProcessor, 767MB RAM, NVIDIA GeForce3 Ti 200.
HardDisk
Drive Index: 0
Cylinders: 12161
Heads: 255
Sectors: 63
Sector Size (Bytes): 512
Drive Size (MB): 95393

MotherBoard
ASUSTeK Computer INC.
A7A266
Serial: xxxxxxxxxx...xx..
Version REV 1.xx

---

### Post by R6V2 on 2008-04-07
I tried using gParted, the partition editor, but I didn't know how to use it, can anyone give me a step-by-step guide on using any partition editor so I can get linux running? Ahhh! I want Linux!!

---

### Post by mikeyphi on 2008-04-07
> **R6V2 said:**
> I tried using gParted, the partition editor, but I didn't know how to use it, can anyone give me a step-by-step guide on using any partition editor so I can get linux running? Ahhh! I want Linux!!

This is a good guide: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Ask again if there are further problems.

---

### Post by R6V2 on 2008-04-07
Yes, that is a good guide, but I need to know 1 thing, and I can have Linux installed. I have the software: gParted Partition Editor. The problem, how exactly do I use this software to partition my drives?

---

### Post by mikeyphi on 2008-04-08
> **R6V2 said:**
> Yes, that is a good guide, but I need to know 1 thing, and I can have Linux installed. I have the software: gParted Partition Editor. The problem, how exactly do I use this software to partition my drives?

The gparted guide is here: [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Probably best to look at "Resizing partitions with gparted"

---

### Post by R6V2 on 2008-04-08
Well Guys, everything was a success, I wiped my whole drive, installed Linux, and then windows, im so happy now! :)

---

### Post by mikeyphi on 2008-04-08
> **R6V2 said:**
> Well Guys, everything was a success, I wiped my whole drive, installed Linux, and then windows, im so happy now! :)

Glad to hear you got there in the end!

---

