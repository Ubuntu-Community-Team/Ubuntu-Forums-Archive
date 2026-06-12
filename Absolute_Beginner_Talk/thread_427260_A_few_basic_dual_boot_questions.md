---
title: "A few basic dual boot questions"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-04-29
Well, I have almost all of the parts for my new PC, just waiting on the CPU and case to get here (never use business shipping over the weekend), and i'll be happily setting it up.

I'm fairly comfortable with the entire process of physically putting it together and using it, but I do have a couple questions.

First off, the "install XP first, then ubuntu and use GRUB" is correct right? I've seen this in a few places, and it seems to be the most popular, but I want to make sure this is the easiest way to do it.

Secondly, what the heck is the swap space for? I keep seeing people say to use a swap partition, even if it's only a few MB, but they never actually say why. I have no interest in sharing applications or space between XP and ubuntu. Ubuntu is my OS, and XP is for gaming ONLY, so I don't need to be tempted to use it for anything else (not to mention, I don't want XP screwing with my ubuntu), so is this still needed?

Thirdly, kinda random, but will dual booting cause my hard drive to be any more noticeably slower? I'm probably going to do it anyway, but I am curious.

Lastly, somewhat related to the above, do I need to worry about XP accessing Ubuntu files? I've never gotten anything worse than spyware, and even that is incredibly rare (Firefox+AVG), but in the absolute worst case scenario of one of those viruses of yore that wipes your C:/ drive, is there any chance it will effect my ubuntu installation?

---

### Post by lluisanunez on 2007-04-29
When you install XP you can make a partition for W and leave space for Ubuntu. Write down their sizes as they will be seen and called differently in linux. 
The swap partition is for memory -linux will use it when your RAM is all busy. It's recommended to have twice the size of your RAM.
There isn't any reason for dual booting slowing down your disk. Dual booting is alternative: you boot one or the other OS, but not both.
As for virus and spyware, you shouldn't worry. They won't work in linux

---

### Post by Malta paul on 2007-04-29
1) yes to first question, not a bad idear.
2) The swap partition is to supplement your ram memory {windows also uses disk space depending on the size of your memory )  
3) Dual booting will not slow your computer.
4) XP can not access Ubuntu files unless you have a special windows programe to do so.

Good luck with your computer build, I did the same! Don't foget to set you BIOS correctly for you config.  Here are a couple of reference that may help :) 
 [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

---

### Post by thefoolisme on 2007-04-29
> **Feba said:**
> 

First off, the "install XP first, then ubuntu and use GRUB" is correct right? I've seen this in a few places, and it seems to be the most popular, but I want to make sure this is the easiest way to do it.

Secondly, what the heck is the swap space for? I keep seeing people say to use a swap partition, even if it's only a few MB, but they never actually say why. I have no interest in sharing applications or space between XP and ubuntu. Ubuntu is my OS, and XP is for gaming ONLY, so I don't need to be tempted to use it for anything else (not to mention, I don't want XP screwing with my ubuntu), so is this still needed?

Thirdly, kinda random, but will dual booting cause my hard drive to be any more noticeably slower? I'm probably going to do it anyway, but I am curious.

Lastly, somewhat related to the above, do I need to worry about XP accessing Ubuntu files? I've never gotten anything worse than spyware, and even that is incredibly rare (Firefox+AVG), but in the absolute worst case scenario of one of those viruses of yore that wipes your C:/ drive, is there any chance it will effect my ubuntu installation?

Yes, if you are planning a dual-boot then it is recommended to install WIndows, and then Ubuntu.  THe grub installation is part of the Ubuntu installation, so you don't have to worry about doing this seperately.  The main reason for installing WIndows, then Ubuntu is because Windows has a superiority complex, and assumes that a user wouldn't possibly want to install another OS, so it will write over the MBR and grub if you do it the other way around.

The Swap space is the equivalent to a page file in Windows.  If the PC is running low on RAM, it will use the Swap space for temporary storage.  It is needed, and the recommended size is usually 1 1/2 to 2x the amount of RAM.  However, I don't think anyone makes their swap over 2GB.  

You will not notice any lag in your hard drive, other than the extra few seconds it takes to choose an OS in Grub.  In fact, you will probably even notice that Ubuntu boots faster than XP.

No, you don't need to worry about XP accessing Ubuntu files, as far as I know.  I believe there are ways to set it up so you can( i.e. Samba), but it won't happen on it's own.  My PC in WIndows doesn't even see the Linux partition because it's a different file system setup (xfs or ext3 instead of NTFS), so your linux files should be OK.  Now, you might consider setting up a partition that both OSs can access for file accessability.  That's what I did, so either OS can see the MP3s I have, or documents I've typed.  That might be worth looking into.  

Hope this answers your questions.

---

### Post by Feba on 2007-04-29
Thanks for all the replies! 

Ok, thanks for explaining the swap space, a lot of people seemed to be giving it random sizes, which seemed odd to me. Now that it's explained, my choice is a lot easier. I'll probably set it for twice my RAM size (4GB of HDD space), since I can always partition it down later. The swap space should be made with Ubuntu's partition manager, not XP, right?

I didn't figure I would see the hard drive get slower, just curious about that mostly. 

And again, I didn't figure it would be able to mess with ubuntu, but I wanted to be sure. 

And thefoolisme, thanks for the suggestion, but like I said, XP is for games only. Probably going to install drivers, firefox, trillian, and nothing else but games. 

I've been using Ubuntu for awhile now, and I just really prefer it to windows. Only thing windows has going that makes me even consider putting it on my computer is games, and I must admit, they are my weakpoint.

---

### Post by freebeer on 2007-04-29
> **Feba said:**
> The swap space should be made with Ubuntu's partition manager, not XP, right?


Correct.  Win XP wouldn't know anything about a swap space anyways.  :-)

---

### Post by riminicat on 2007-04-29
Just a warning, when you are done installing both os's and you boot into windows, there is a chance that windows will rewrite the mbr so make sure you also install grub to the same partition as your hard drive and then get a rescue disk... this saved my laptop

---

### Post by Feba on 2007-04-29
What do you mean? A hard drive has partitions, not the other way around.

This computer is only going to have a single 500GB hard drive.

I figure I'm going to split it like this:

Win XP: 46GB
Swap: 4GB
Ubuntu: 450GB

I understand the windows could overwrite the MBR, but what would I do against that? I already have an old system rescue CD sitting around, what would I do with it though?

---

### Post by mikewhatever on 2007-04-30
You can easily put grub boot loader back to the mbr following this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by Feba on 2007-04-30
mike, did you read the thread? This is the biggest problem with linux guides as far as i've seen, people will tell you to do something without explaining why you're doing it, and on these forums they seem to give answers without understanding the problem- and i'm not just talking about my threads.

---

### Post by riminicat on 2007-04-30
Feba, I'm a noob but I'm going to try and help you, I hope this makes sense, sorry if it doesn't.

There is no way to keep windows from overwriting the MBR as far as I know, I searched for days to find a way to get it to stop.

To help save trouble and to keep from reinstalling os's over and over again, you can use the rescue cd to install grub to the same partition that you are going to install Ubuntu (install Ubuntu first, then use a rescue cd to install Grub.)

Then, if windows does happen to overwrite the MBR, you can still boot into windows or Ubuntu.

Does this make sense/help at all?

P.S. If you have time, boot using your rescue disk on a pc and type "gag" into it and see what happens, some rescue disks have gag and will let you boot an OS if the MBR is rewritten, but you must have Grub on the Ubuntu partition for this to work.

---

### Post by riminicat on 2007-04-30
Hey Feba, this is what helped me get the dual boot thing kinda sorted out:

> 3.2 Installing GRUB natively



Caution: Installing GRUB's stage1 in this manner will erase the normal boot-sector used by an OS.



GRUB can currently boot GNU Mach, Linux, FreeBSD, NetBSD, and OpenBSD directly, so using it on a boot sector (the first sector of a partition) should be okay. But generally, it would be a good idea to back up the first sector of the partition on which you are installing GRUB's stage1. This isn't as important if you are installing GRUB on the first sector of a hard disk, since it's easy to reinitialize it (e.g. by running `FDISK /MBR' from DOS).



If you decide to install GRUB in the native environment, which is definitely desirable, you'll need to create a GRUB boot disk, and reboot your computer with it. Otherwise, see Installing GRUB using grub-install.



Once started, GRUB will show the command-line interface (see Command-line interface). First, set the GRUB's root device1 to the partition containing the boot directory, like this:



     grub> root (hd0,0)



If you are not sure which partition actually holds this directory, use the command find (see find), like this:



     grub> find /boot/grub/stage1



This will search for the file name /boot/grub/stage1 and show the devices which contain the file.



Once you've set the root device correctly, run the command setup (see setup):



     grub> setup (hd0)



This command will install the GRUB boot loader on the Master Boot Record (MBR) of the first drive. If you want to put GRUB into the boot sector of a partition instead of putting it in the MBR, specify the partition into which you want to install GRUB:



     grub> setup (hd0,0)



If you install GRUB into a partition or a drive other than the first one, you must chain-load GRUB from another boot loader. Refer to the manual for the boot loader to know how to chain-load GRUB.



After using the setup command, you will boot into GRUB without the GRUB floppy. See the chapter Booting to find out how to boot your operating systems from GRUB.

Footnotes



[1] Note that GRUB's root device doesn't necessarily mean your OS's root partition; if you need to specify a root partition for your OS, add the argument into the command kernel.

---

### Post by mikewhatever on 2007-04-30
> **Feba said:**
> mike, did you read the thread? This is the biggest problem with linux guides as far as i've seen, people will tell you to do something without explaining why you're doing it, and on these forums they seem to give answers without understanding the problem- and i'm not just talking about my threads.

To best of my understanding, I have answered your question, which is right above my post. Do forgive me if I haven't.

> Just a warning, when you are done installing both os's and you boot into windows, there is a chance that windows will rewrite the mbr so make sure you also install grub to the same partition as your hard drive and then get a rescue disk... this saved my laptop
This is total rubbish. The only time Windows will overwrite grub in the mbr is when Windows is installed after Ubuntu.

---

### Post by Feba on 2007-04-30
>  Does this make sense/help at all?Yes it does, and thank you.

---

### Post by riminicat on 2007-04-30
ok

---

### Post by confused57 on 2007-04-30
> **Feba said:**
> What do you mean? A hard drive has partitions, not the other way around.

This computer is only going to have a single 500GB hard drive.

I figure I'm going to split it like this:

Win XP: 46GB
Swap: 4GB
Ubuntu: 450GB

I understand the windows could overwrite the MBR, but what would I do against that? I already have an old system rescue CD sitting around, what would I do with it though?

Since you have 2 Gb of ram, you probably don't even need a swap partition...1 Gb max.
If you install Windows first, the Window's IPL code will be installed to the mbr of the hard drive, then when you install Ubuntu, grub will overwrite the mbr...grub should recognize your Window's OS & add an entry to boot Window's.

Mike's reply was how to use the live cd to restore grub to the mbr, if Window's IPL code overwrote grub, which it won't since you installed Windows first & Ubuntu second.

You might want to consider setting up a separate home partition when you install Ubuntu, maybe 25 Gb for root and the rest for home...that way, if you need to reinstall Ubuntu, your configuration and data files will still be intact and it would just be a matter of reinstalling Ubuntu to the root partition & using the same home partition.

See this guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by riminicat on 2007-04-30
> **confused57 said:**
> 

Mike's reply was how to use the live cd to restore grub to the mbr, if Window's IPL code overwrote grub, which it won't since you installed Windows first & Ubuntu second.


Look into MBR a little, windows can still write over the MBR after you boot into it, not that it will on every computer but it can on some.  I think the reason it happens to my laptop is because I got the laptop from my college, and we aren't actually supposed to Dual Boot, so I think they made it so it would over write, I talked to the IT Employees and they said it will over write in the student laptops, they told me to use Lilo but I don't want to.

If you search on google, a lot of people reported they're MBR being written over after booting into windows, but maybe it depends on the computer and how windows was set up.

---

### Post by alan yeates on 2007-04-30
I added Ubuntu to my windows ME machine, no real problems at all for 6 months, then the drive decided to stutter prior to breathing its last. Luck was in however as I purchased Acronis true image and cloned everything to a new drive, including GRUB,:)  despite warnings that Linux loaders could be destroyed. No doubt there is a techy way of doing all this, but I am all for an easy life, and this implies that incremental backups will be trouble-free from both OS's in one go!

---

### Post by confused57 on 2007-04-30
> **riminicat said:**
> Look into MBR a little, windows can still write over the MBR after you boot into it, not that it will on every computer but it can on some.  I think the reason it happens to my laptop is because I got the laptop from my college, and we aren't actually supposed to Dual Boot, so I think they made it so it would over write, I talked to the IT Employees and they said it will over write in the student laptops, they told me to use Lilo but I don't want to.

If you search on google, a lot of people reported they're MBR being written over after booting into windows, but maybe it depends on the computer and how windows was set up.

I'm well aware of this "phomenon" on certain computers, it's usually a function of the bios that prevents overwriting the Window's IPL code from the mbr...this is usually programmed by the computer manufacturer or in your case possibly by your college IT people.  Since the OP is building his computer from scratch, he "shouldn"t" run into this problem...if he does, it's probably just a matter of going into bios setup & making a few minor changes.   Some bios have an antivirus feature that will also restore your mbr, if it thinks a virus has corrupted the mbr, which it would think grub is a virus.

---

