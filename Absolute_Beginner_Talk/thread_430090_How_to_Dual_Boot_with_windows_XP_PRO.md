---
title: "How to Dual Boot with windows XP PRO"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by delilahjed44 on 2007-05-01
Hey, I have a 8100 Dell demensions, total physical memory> 256 MB and 58.49 available physical memory, 3.59 used and 32.9 free, not sure what that all means, just going by the detailed info I read in properires.  Now my question is, how do I get this dual boot thing going so I can have Ubuntu in the dual boot.  I saw about G-parted, was not for sure which I should download and use, even so if I did I would not know the steps to do this with.  Now, I do not have service pack 2 at the present with my Windows XP PRO, should I download this first? and then what should I do with the G-parted as I do not know if there is full support with it.

Thank you
Sherri

---

### Post by bobplano on 2007-05-01
i'm not sure about the service pack, but dual-booting usually requires you to resize your windows partition, which you should defragment first. gparted doesn't need to be installed because it's on the ubuntu live cd. just choose an automatic option that lets you resize your windows partition or do manual and resize it yourself then make the required ubuntu partitions

---

### Post by delilahjed44 on 2007-05-01
Hey thanks for the reply, with it let me ask, as I submitted in firs post, how much should I do for both? are there choices with the live CD, say 50/50 or do I have to put that amount in, as per say divide the 256 ram iin half? see this is what I am concerned about, and do I keep my windows with the C and re-create  a letter for Ubuntu or is this displayed as well? I am wanting to make sure there is enough space for both as its my understanding Ubuntu in itself requires 256, well if that is all I have, how can I dual boot? I just want to make sure that before I attempt this it does not create a big problem.  I had the full install of Ubuntu, for several months, then had to un-install it because it would not run my programs no matter what I did.  So this is my reason I am back into windows.  Dont want to be, but wine was not the answer and two months of research here there everywhere was not the answer, so I am wanting to get this dual boot thing right.

Sherri

---

### Post by bobplano on 2007-05-01
the ram is only used by one OS at a time unless you are running them at the same time, which you shouldn't be if you are just dual-booting. C: is just the drive so i don't think ubuntu gets assigned another letter, but don't hold me to this. what the live cd is saying with the 50/50 is it is splitting the hard drive space in half.

---

### Post by antoz on 2007-05-01
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

The links above offer a lot of help, cheers,A

---

### Post by Robynsveil on 2007-05-01
> **delilahjed44 said:**
> Hey, I have a 8100 Dell demensions, total physical memory> 256 MB and 58.49 available physical memory, 3.59 used and 32.9 free, not sure what that all means, just going by the detailed info I read in properires.  Now my question is, how do I get this dual boot thing going so I can have Ubuntu in the dual boot.  I saw about G-parted, was not for sure which I should download and use, even so if I did I would not know the steps to do this with.  Now, I do not have service pack 2 at the present with my Windows XP PRO, should I download this first? and then what should I do with the G-parted as I do not know if there is full support with it.

Thank you
Sherri
Hi Sherri... you might want to have a read of this site:
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Follow each step very carefully - you can't go wrong... and good on you for having a go with Ubuntu!

[Added]
In short, he recommends: [I recommend printing out his instructions and studying them a bit]
1. cleaning up and defragging your Windows partition
2. Downloading and burning the Linux System Restore CD available [here]("http://www.sysresccd.org/Main_Page") - ESSENTIAL!
3. Repartitioning your hard drive, making the Linux partition right next to the Windows boot partition - and write down the hdx name of that partition, where x is the number, like hd2
4. Install Linux WITHOUT installing grub - don't go with the default, or it'll stuff up your system like it stuffed up mine (what a panic *that* was!!)
5. After the intall, you edit the boot.ini file in WindowsXP as per his instructions



Cheers,
Robyn

---

### Post by TopHatCat on 2007-05-01
Personally I installed Windows XP first (which is a given) and I used Partition Magic through XP to fiddle around with the partitions I wanted to use. After that I rebooted with a Feisty live CD and installed to a different partition and afterward GRUB lets you select which OS you want to load whenever you restart your machine.

---

### Post by confused57 on 2007-05-01
You might want to install the SP2, before trying to set up a dualboot...I've seen a couple of people who haven't been able to boot Windows without it when setting up a dual boot:
[http://ubuntuforums.org/showthread.php?t=422189&page=3](http://ubuntuforums.org/showthread.php?t=422189&page=3)

Your dualboot may work without it, but it might save you some frustration if it doesn't.

---

### Post by delilahjed44 on 2007-05-01
Hey ok. I am specualing that the last 3 answers here have to do with my number one choice in the CD to partition drive which sais

PREPARE DISK SPACE:
Resize IDE 1 master partition #1 (hda 1) and use free space

Now there are 3 choices to use, so will this be a process if I begin this choice?

Thanks Sherri

---

### Post by Ozitraveller on 2007-05-01
I'd recommend this site as well.

Illustrated Dual Boot Site
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Includes:
> 

Choice of three different Ubuntu 'Alternative CD' install guides,

Ubuntu+FAT32   Dual boot Ubuntu Fiesty Fawn and Windows with FAT32 file system 




Ubuntu+NTFS  Dual boot Ubuntu Fiesty Fawn with Windows with NTFS file system
                               (creating a FAT32 shared data partition at the same time) 

Separate /home  Dual boot Ubuntu Fiesty Fawn with Windows with NTFS file system
        (creating a separate /home for Ubuntu as well as a FAT32 shared data partition)



---

### Post by Robynsveil on 2007-05-01
> **delilahjed44 said:**
> Hey ok. I am specualing that the last 3 answers here have to do with my number one choice in the CD to partition drive which sais

PREPARE DISK SPACE:
Resize IDE 1 master partition #1 (hda 1) and use free space

Now there are 3 choices to use, so will this be a process if I begin this choice?

Thanks Sherri
Hi Sherri,
Looks to me like you just gone ahead with the install of Ubuntu from the CD Boot and selected the default... is that right? Be careful - I did this the first time, and it stuffed up my system.

You need to clean up and optimize your Windows installation (including defrag and installing SP2) *before* you 
try to install Ubuntu. Then, you will need to re-partition your drive to give you some free space - this is your hard drive, not your RAM. Then, be careful what you chose with your boot manager - do not chose GRUB, or you might not be able to get back into Windows.

Cheers,
Robyn

---

### Post by delilahjed44 on 2007-05-01
Ok this is what I am talking about, I imagine many poeple get confused because even so by these directions they are yet unclear.  As I chose NTFS the second choice, it then refers that this may not work so now its Fat 32, then a slew full of possible commands following that, what the heck is the right answer? I dont want to be locked into the middle of this mess with this that and the other thing, its nice to have choices but in something this serious the right choice is the only choice, not choose A, then suddenly it maybe B then on and on, sorry but this is a mess to me.

Sherri

---

### Post by delilahjed44 on 2007-05-01
> **Robynsveil said:**
> Hi Sherri,
Looks to me like you just gone ahead with the install of Ubuntu from the CD Boot and selected the default... is that right? Be careful - I did this the first time, and it stuffed up my system.

You need to clean up and optimize your Windows installation (including defrag and installing SP2) *before* you 
try to install Ubuntu. Then, you will need to re-partition your drive to give you some free space - this is your hard drive, not your RAM. Then, be careful what you chose with your boot manager - do not chose GRUB, or you might not be able to get back into Windows.

Cheers,
Robyn

HI Robyn, no I have not done anything as yet, what it is I want to do looks like it may or may not be the answer, one sais yes you have to have grub in order for it to see windows/linux and then one says no do not install grub? then again as I just posted its A, then A turns into B, this is why I am hesitating at all, you get the feel like your on the way and then the rules change.

Sherri

---

### Post by apunc1 on 2007-05-01
> **delilahjed44 said:**
> Hey ok. I am specualing that the last 3 answers here have to do with my number one choice in the CD to partition drive which sais

PREPARE DISK SPACE:
Resize IDE 1 master partition #1 (hda 1) and use free space

Now there are 3 choices to use, so will this be a process if I begin this choice?

Thanks Sherri

This option will resize you windows partition and install ubuntu on its own partition and a swap partition. 

It sounds like since you are talking about fat32 that you want to a /shared partition to share files with windows and ubuntu. You need to choose option 3: manually partition the hard drive.

in the scheme to dual boot with ubuntu, windows, shared files and swap your paritions will be formated as such

windows nfts
ubuntu (shown as /) ext3
/shared fat32
swap

the [http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning) really helped me to visualize the partitions because sometimes they can be hard to wrap your head around if you've never partitioned any hard disk before. The psychocats link also offers some reasonable sizes for the above mentioned partitions.

sidenote: if you want to add a /home partition in addition to the previously mentioned patitions, it is also ext3. from the psychocats link:
> 
/home partitions are wonderful things. It would be the equivalent of Windows of having a partition that was the C:\Documents and Settings folder. That would include My Documents, My Pictures, My Music, and all your hidden settings, too. Likewise, a /home partition in Ubuntu has all your settings. Ordinarily, it would have your files, too, but in the scenario pictured above, your files would live in the FAT32 partition.

does this make more sense?

---

### Post by Robynsveil on 2007-05-01
> **delilahjed44 said:**
> HI Robyn, no I have not done anything as yet, what it is I want to do looks like it may or may not be the answer, one sais yes you have to have grub in order for it to see windows/linux and then one says no do not install grub? then again as I just posted its A, then A turns into B, this is why I am hesitating at all, you get the feel like your on the way and then the rules change.

Sherri
Hi Sherri,
You are in the Ubuntu installer, right? I just want to figure out if you are G-Parted (like Partition Magic) or in the Ubuntu Install from CD... whever you do, do not install GRUB...

---

### Post by antoz on 2007-05-01
from the install disk I would select "edit partition table manually" it gives a lot more control as to where things get installed. 
If you decide to go with the option select largest free space it will shrink your windows partition, you will get a screen with a slider that is where you have to be carefull the bit on the left with the number of GIGS is what your window partition will end up not the new Ubuntu so you need to move that till you get to the size you want your windows to remain.
I made that mistake the first time and ended up with a small windows partition, lucky for me at the time I got cold feet and aborted the install and later just resized my partition again with the lice CD.
This is why I would recommend doing your partitions first before you start the installer but if it is easier for you to let Ubuntu do it just make sure your windows partition is the size you wanted.

The links gave you earlier should really help as I can see Ozzietraveller gave you the same link, Hermann's instructions are really easy to follow. Hope this answers a few questions. A

PS:once installing just make really sure your windows ntfs partition is [COLOR="Red"]**NOT checked to format**[/COLOR]

---

### Post by delilahjed44 on 2007-05-01
> **Robynsveil said:**
> Hi Sherri,
You are in the Ubuntu installer, right? I just want to figure out if you are G-Parted (like Partition Magic) or in the Ubuntu Install from CD... whever you do, do not install GRUB...

HI Robyn, again, no I have done nothing, I have a full install of windows XP PRO NTFS as original post indicated, I am now therefore schooling myself on what to do, how to do it, and if I will indeed do it at all.  I have read variations to the grub and well on just about everything and nothing is actually clear.  I will say for a newbie its almost impossible to wrap your head around what the URL suibmitted sais to do as the last person indicated.  You can expect a loss on that one, it is actually out of the function for a newbie.  That would be me. 

Sherri

---

### Post by Robynsveil on 2007-05-01
> **delilahjed44 said:**
> HI Robyn, again, no I have done nothing, I have a full install of windows XP PRO NTFS as original post indicated, I am now therefore schooling myself on what to do, how to do it, and if I will indeed do it at all.  I have read variations to the grub and well on just about everything and nothing is actually clear.  I will say for a newbie its almost impossible to wrap your head around what the URL suibmitted sais to do as the last person indicated.  You can expect a loss on that one, it is actually out of the function for a newbie.  That would be me. 

Sherri
Hi Sherri... I'm a total newbie too... and like you said, reading these links and stuff can make your head swim. It's a matter of either too much information, or not *enough* information. Anyway, I've been able to get Ubuntu installed - one tiny accomplishment - and that's what I want to share with you. The first thing I would do is make sure your Windows system is optimized. You can access a fair few tools just by right-clicking on My Computer and selecting 'Manage'. From there, you can see what room you have after your Windows partition. If there is no room (free space), you will need to create some. Holding down the Windows key and pressing 'E' will get you the browser, and rightclicking on the C Drive and selecting 'Properties (bottom of the menu) will get you a dialog. The first tab on this displays Windows in pie form. The second tab is Tools - you need to run scandisk and defrg from this one *before* you try to do a Linux install. I ran into dramas - the Ubuntu install froze - and it was because there were problems with the Windows partition.

Does any of what I just say make sense? :)
Cheers,
Robyn

---

### Post by delilahjed44 on 2007-05-01
> **Robynsveil said:**
> Hi Sherri... I'm a total newbie too... and like you said, reading these links and stuff can make your head swim. It's a matter of either too much information, or not *enough* information. Anyway, I've been able to get Ubuntu installed - one tiny accomplishment - and that's what I want to share with you. The first thing I would do is make sure your Windows system is optimized. You can access a fair few tools just by right-clicking on My Computer and selecting 'Manage'. From there, you can see what room you have after your Windows partition. If there is no room (free space), you will need to create some. Holding down the Windows key and pressing 'E' will get you the browser, and rightclicking on the C Drive and selecting 'Properties (bottom of the menu) will get you a dialog. The first tab on this displays Windows in pie form. The second tab is Tools - you need to run scandisk and defrg from this one *before* you try to do a Linux install. I ran into dramas - the Ubuntu install froze - and it was because there were problems with the Windows partition.

Does any of what I just say make sense? :)
Cheers,
Robyn

HI Robyn, yes of course I see what your saying, I am all to familiar with windows, I listed the space I had in original post on this topic.  I had Ubuntu for two months, I loved it, but could never get any help on installing my German lanquage programs, I did the wine thing and all requirments, nothing was a take, so I took a chance and re-installed Ubuntu again, only this time I used the installation as a plot to get around GRUB, it worked and I am fully back into windows and running my programs with no problems of course.  I am hoping as of today the emerge of Dell and Ubuntu desktops that they will indeed supply formats that will enable my programs to run.  For now it was about me just being able to dual boot and have Ubuntu back in full force.  As of now, I may just wait, I can see the dual boot is going to be another issue I wish not to deal with.  It is complicated and unclear, but possible, I would just assume my machine run at full capacity with windows until Ubuntu comes up with a way to run my programs.  The dual boot will have to be scrutinized over and I will make a decision, but I will wait for a clear one as none seem to be as yet.

Sherri

---

### Post by Robynsveil on 2007-05-01
> **delilahjed44 said:**
> ...As of now, I may just wait, I can see the dual boot is going to be another issue I wish not to deal with.  It is complicated and unclear, but possible, I would just assume my machine run at full capacity with windows until Ubuntu comes up with a way to run my programs.  The dual boot will have to be scrutinized over and I will make a decision, but I will wait for a clear one as none seem to be as yet. Sherri

Yes, I can see how that would be a show-stopper, not being able to run your Windows programs. There *are* other solutions besides 'Wine', but if you find setting up dual-boot too daunting, we might as well wait until you're ready to tackle it.

Actually, there are only a few steps involved after you've installed Ubuntu on your drive - I assume it *is* still installed on your system:

> **delilahjed44 said:**
> ...used the installation as a plot to get around GRUB, it worked and I am fully back into windows and running my programs with no problems of course...

so when you are ready, I can show you how to set up the whole dual-boot thingie in just a few short steps.

Cheers,
Robyn

---

### Post by delilahjed44 on 2007-05-02
Hey Robyn, thanks for this, dont know how I will be fortunate enouph to cross your path in here again, but no I do not have Ubuntu installed at all, I cleaned the whole disk out and re-installed windows only, so I will have to do the complete process once again.  I have seen other options for running my programs but with each there was  a new problem listed.  It was one thing after another and no cure, even on switching the DLL files for those in Linux to duplicate, nothing was victorious, it was all quite time consuming as well.  Ya and I am presently having a bout with tennis elbow, how fun, I already have tendonitis in hands so I have to stay in a position where my machine is easily operated without all the hassle at the moment.  Thank you Robyn you are a doll! and I appreciate your input

Sherri

---

### Post by antoz on 2007-05-02
There are alternative programs in Ubuntu to the windows programs and as you probably have found out others can run under wine BUT if you are used to Windows there are lots of programs you will not be able to use full stop. This is why a lot of people use dualboot you get the best of both worlds.A

---

### Post by delilahjed44 on 2007-05-02
Yes of course, which is why I wanted to dual boot, but without a said way that looks to be the answer it does make it difficult for one to explore especially a newbie caught in the middle of a bad dual boot situation and cant get back into either OS.  Your had unless you have two computers to work with.  There needs to be a step by step procedure for dual booting that should make the experince worth the trying.  But I see there are different routes with different approaches, one sais this, one sais that.  You go with the one, suddenly it changes the number one into possible number 2 or 3 thus creating confusion.  I see its almost there but not quite, not for a newbie anyway.   I tried as many outlets as offered in Ubuntu for my programs it just is not a go, as of yet, maybe someday it will be able to better emulate windows files for programs like mine, but for now it does not.  No biggie, I just would have like to try the dual boot, and the NTFS stated for a walk through in the URL submitted has to many holes in it for a clear understanding for dual booting, especially when something goes wrong and it does not boot.  

Thanks 
Sherri

---

### Post by apunc1 on 2007-05-02
> **delilahjed44 said:**
> Yes of course, which is why I wanted to dual boot, but without a said way that looks to be the answer it does make it difficult for one to explore especially a newbie caught in the middle of a bad dual boot situation and cant get back into either OS.  
Sherri

I'm confused: are you having trouble with a dual boot? I thought you said before you had not attempted an Ubuntu install at all. 
Actually I find the psycocats link to be a very nice step by step tutorial on how to set up a dual boot with a /home and /shared partition.
Either let the Ubuntu installer resize windows for you or manually configure the partitions yourself using the above mentioned tutorial.
What **specific **issues are still giving you a hard time with the dual boot scenario?

---

### Post by thefoolisme on 2007-05-02
I agree with Apunc.  The Psychocats website is great for Linux newbies.  The bottom line is that there are different ways to set up your system, not just one way.  I did SOOOOO much reading of different sites before I installed mine, after deciding how I wanted to set my system up.  Read through the options, pick the one that's right for you, back up your windows important documents in case something happens, then follow the directions for your choice of dual-boot installation.  It really isn't that hard, once you become familiar with what you'll need to do.

---

### Post by delilahjed44 on 2007-05-02
> **apunc1 said:**
> I'm confused: are you having trouble with a dual boot? I thought you said before you had not attempted an Ubuntu install at all. 
Actually I find the psycocats link to be a very nice step by step tutorial on how to set up a dual boot with a /home and /shared partition.
Either let the Ubuntu installer resize windows for you or manually configure the partitions yourself using the above mentioned tutorial.
What **specific **issues are still giving you a hard time with the dual boot scenario?

Hello, well I found on the site which out of the 3 to dual boot from it said to do.  First let me clear the air, I had Ubuntu Edgy Eft, fully installed, had to go back to windowsm wiped out the hard-drive clean then re-installed windows only.  But the dual boot is my desire, the URL submitted has 3 choices, mine is in the middle, NTFS, not Fat 32, immedietly following these directions lower down the game changes, now its a possible Fat 32.  On the page you go to follow pictorial drawings it gives you that choice.  But if the first one does not work then there is a new set of rules, mainly command line info.  Also it installs grub.  Now its my understanding that I should not install grub.  Grub either sees both or not, so it has become confusing exactly what to choose, and I dont have a clue how much space to use as either.  I only have 256 MB ram, so I dont want the bare bones of both OS.  Well hope I answered your question, its a matter of what i want to put myself through is how I see it, but it is stil difficult for a newbie.

Sherri

---

### Post by apunc1 on 2007-05-02
> **delilahjed44 said:**
>  the URL submitted has 3 choices, mine is in the middle, NTFS, not Fat 32, immedietly following these directions lower down the game changes, now its a possible Fat 32.  On the page you go to follow pictorial drawings it gives you that choice.  But if the first one does not work then there is a new set of rules, mainly command line info. 

the windows partition is in ntfs format. the partition that you will share will be formatted fat32 (unless you want to use FS-Drive to let windows read from and write to ext3 and is explained in the psyhocats link). the partition ubuntu is installed on (/) will be ext3. as show here [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
They all reside on the same hd. I'm not sure which command line info you're referring to.

 > **delilahjed44 said:**
>  Also it installs grub.  Now its my understanding that I should not install grub.  Grub either sees both or not, so it has become confusing exactly what to choose

grub is the bootloader that will neatly and easily show the operating systems installed on your computer (in your case ubuntu and windows) and allow you to choose which to load at start up.


 > **delilahjed44 said:**
>  and I dont have a clue how much space to use as either.  I only have 256 MB ram, so I dont want the bare bones of both OS.

how much hard drive space do you have? the amount of hard drive space will determine how much space to give to each partiton. there are many tutorials online that explain this.
such as [http://www.linuxjournal.com/article/8761](http://www.linuxjournal.com/article/8761)
if you only have 256 mb of ram you might want to consider using xubuntu edgy instead of ubuntu as xubuntu is for lower end machines.

---

### Post by antoz on 2007-05-02
Hi Sherri
 If you installed Ubuntu before it should not be that hard to try again. As far as partitions the Fat 32 partition is mainly because it makes it easier to share files between the 2 operating systems. There are other ways you can install programs so that Windows can read and write to ext3 it boils down to a matter of preference.
Since you have the Widows XP CD I would not worry about Grub in fact you need it to give you a choice at boot. If you decide after a while you don't want Ubuntu anymore use the XP CD to restore your MBR (master boot record) grub will be gone and it will boot into Windows again.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE](http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE)

The link gives you advice how to do it; some people like to get Super Grub you can put it on a floppy and it makes restoring the MBR very easy.

Partitions that you need for an install: " / "  and  "swap" this is what you get if you let Ubuntu install 
 you should create a "home" partition though because then it makes it easier later if you reinstall you keep all your files and settings that way it is a bit like My Documents in Windows.

To give you an idea I attach a screen shot of my partition table.
IN Ubuntu it is very easy to take a screen shot just go to aplications then screen shot and it will take a picture it might come handy if you have a problem and you want to show what is on your screen to get some help.
Cheers for now, A

---

### Post by antoz on 2007-05-02
oops forgot the screeshot

---

### Post by delilahjed44 on 2007-05-03
> **apunc1 said:**
> the windows partition is in ntfs format. the partition that you will share will be formatted fat32 (unless you want to use FS-Drive to let windows read from and write to ext3 and is explained in the psyhocats link). the partition ubuntu is installed on (/) will be ext3. as show here [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
They all reside on the same hd. I'm not sure which command line info you're referring to.

 

grub is the bootloader that will neatly and easily show the operating systems installed on your computer (in your case ubuntu and windows) and allow you to choose which to load at start up.


 

how much hard drive space do you have? the amount of hard drive space will determine how much space to give to each partiton. there are many tutorials online that explain this.
such as [http://www.linuxjournal.com/article/8761](http://www.linuxjournal.com/article/8761)
if you only have 256 mb of ram you might want to consider using xubuntu edgy instead of ubuntu as xubuntu is for lower end machines.

Hey Thank you on this, why? because it truly clears the air on the FAT 32 and the NTFS, Big Difference, now I understand this much more clearly, logically and sensibly.  This was my issue of seeing both then reverting to one over the other, this I could not understand.  Thank you.

Sherri

---

### Post by delilahjed44 on 2007-05-03
> **antoz said:**
> Hi Sherri
 If you installed Ubuntu before it should not be that hard to try again. As far as partitions the Fat 32 partition is mainly because it makes it easier to share files between the 2 operating systems. There are other ways you can install programs so that Windows can read and write to ext3 it boils down to a matter of preference.
Since you have the Widows XP CD I would not worry about Grub in fact you need it to give you a choice at boot. If you decide after a while you don't want Ubuntu anymore use the XP CD to restore your MBR (master boot record) grub will be gone and it will boot into Windows again.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE](http://www.users.bigpond.net.au/hermanzone/p18.htm#STEP_ONE)

The link gives you advice how to do it; some people like to get Super Grub you can put it on a floppy and it makes restoring the MBR very easy.

Partitions that you need for an install: " / "  and  "swap" this is what you get if you let Ubuntu install 
 you should create a "home" partition though because then it makes it easier later if you reinstall you keep all your files and settings that way it is a bit like My Documents in Windows.

To give you an idea I attach a screen shot of my partition table.
IN Ubuntu it is very easy to take a screen shot just go to aplications then screen shot and it will take a picture it might come handy if you have a problem and you want to show what is on your screen to get some help.
Cheers for now, A

Hi, and thank you for this.  Well I did install Ubuntu for 2 months, went back to windows, had to for my progams to run, as stated they would not run with Wine.  Now, if Grub is there, you cannot get back into windows CD or not.  It will boot automatically into Ubuntu no matter what you use, F1-F2-F12.  I had Ubuntu, then an attempt to get past grub, so I re-installed Ubuntu, choosing the clean up hard-drive, erase all files, moments after this choice, I shut my system down.  Restarted with windows CD, finally it worked, see cuz I could not get past Grub before, this worked, I erased Ubunut and the CD kicked in.  Now I will have to do some work on the ( how much space I can use thing ) I am wondering to buy some more ram, so I can enjoy both.  I have XUbuntu, on a CD but I prefer Feisty Fawn now.  Well this will be a chore, I will need a day to dedicate in case of problems.  I miss my Ubuntu, the ease of use, my sticky notes, all my goodies I built up, but until Wine can make and emulate windows DLL files and quicktime set up its on hold. I did everyting possible to the extent of help granted to make my programs run but no victory.  Its coming, Ubuntu will win.  I did have issues with disapearing scroll bar in Ubuntu, that was aggravating, fixed it in the Fire Fox browser, but it would only work for ahwile.  Well Ok now I will scrutinize all info and see about getting more ram.

Sherri, thanks for all the excellent help, thank goodness for open scource communtiy,

---

### Post by apunc1 on 2007-05-03
you're welcome
Planning the partitions is the toughest part of a dual boot. The installer does all the work once you are certain on your partition sizes and mount points.
good luck

---

### Post by delilahjed44 on 2007-05-04
> **apunc1 said:**
> you're welcome
Planning the partitions is the toughest part of a dual boot. The installer does all the work once you are certain on your partition sizes and mount points.
good luck


Hey hi, here is my plan, I am to get more ram from a pc of ours where the hard-drive crashed and use the ram to give me the space I  need, at least I think I can do this.  I guess if the hard-drive is dead it has nothing to do with the ram.  That is my hope.  Well it is 512 MB, so I can keep the 256 MB on my windows XP and use the other for Ubuntu, 6.10 as I do not care for Fiesty at the moment, but I will school myself as much as possible on the total dual thing and when I botch it all up, he-he I will be back.  I have two pc's so this is needed as to keep a contact with my progress so open scource can cure this ail.  Not to mention, mark my path in case others want to use if they too have XP.  Ok off to work, oh the fun part, work.

Sherri everyone have a great day!!!

---

