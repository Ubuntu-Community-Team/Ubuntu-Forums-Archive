---
title: "Multiple Booting Linux Distro's w/Ubuntu"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Kazna on 2006-12-14
Hi all!

I've read the sticky's, read a few tutorials and also got some help off a few other Linux users. I'm still a little unsure and confused.

**Background: **I have many Windows and Mac installations but I don't have a Linux :(
Haha, anyway, I heard what all the craze was about and my associates/friends recommended me to use Linux. I'd love to use it but I'm totally unfamiliar with it and that can be scary combined with ample foolishness.

I've got 4 different spec systems to try on. The one I'm mainly installing on will be the oldest; an AMD Duron 1.3Ghz with 1.5GHz RAM and 160GB HDD with a LAN connection, an Epson printer and a LG CD-RW. Thats it and all of the equipment is of 2002/3. I don't think I'll have any hardware compatibility issues but its not a concern for me anyway.

Right. I have 2 HDD's @ 80GB each connected. 
HDD 0 has the main XP installation on it along with 2 other partitions.
HDD 1 has the backup of Drive 1 on it along with 3 other partitions.

I'm wanting to install 4 Linux Distro's on the partitions. 2 on the HDD0 and 2 on HDD1.
HDD0 will have Fedora Core 5 on it and Ubuntu 6.06 LTS.

I've tried FC and was stuck. Now onto **Ubuntu** [COLOR="Blue"]**I'm inquiring on how to get the system to dual boot and not affect the XP installation at all.**[/COLOR] I'm very familiar with XP and the command line. However I've took a long break from computer technology, since '86 and not returned till the start of this year. Back then I was a programmer. Now my profession is unrelated and I know very little about technical matters apart from engineering, security & Windows.

*To make sure: Is it only one CD as ISO in total?
*How long does installation take?
*Where I get stuck is on how to choose the partition where Ubuntu is to be installed. Its a 20GB partition.
*Am I supposed to leave it unpartitioned or partitioned, or formatted or unformatted?
*Will I be shown a screen with all my partitions or is that a more advanced customization?
*I also want it to not be the default OS on bootup.

Thats about all I need help with at the moment.
I am basically experimenting and trying to learn about it; something I like doing.

I'd appreciate any help although as being on many forums myself I realize that you might be completely sick of questions answered endless times and so identical. I thought mine was a little more specific.

Thanks.

---

### Post by confused57 on 2006-12-14
You might consider this for your system with 2 hard drives:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

This method won't affect your Windows installation mbr, but you'd need the Ubuntu drive as master to be able to boot your Linux partitions on the slave Windows drive.

Use the Ubuntu grub to boot all your other Linux OS, by installing grub of each Linux OS to it's root partition and add entries to your Ubuntu to boot the OS using chainloading...entering an entry similar to this:

title   Linux OS
rootnoverify (hd0,1)
chainloader +1

You can set up one swap partition that can be used by all 4 Linux OS...if you happen to install a Linux OS that doesn't allow  you to select where to install grub you can always restore your Ubuntu mbr and add the Linux OS grub to it's root partition, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If all this sounds feasible, first thing would be to set up your system as mentioned in the first link above...then go from there.   It's a summary explanation of how I would set it up, but you might want to wait to see if someone else has a better setup for you.

I'm currently booting 9 different Linux OS(a little overkill, I know) on 2 hard drives(IDE + SATA) using chainloading in Dapper's grub.  It's an all Linux box, but the principle is still the same.

You definitely need to do some reading, before beginning your installations...you'd need to opt for "manual partitioning" to select which partition to format(ext3) & install on and be sure to create one swap partition.   Installation shouldn't take more than 30-45 minutes, the Ubuntu desktop live cd doesn't allow you to select where to install grub(the alternate cd does)...this shouldn't matter setting up the initial install of Ubuntu.

Here's a couple of excellent sites for installing:
Desktop:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You might want to defragment your Windows partition before you do any partitioning on your Wincows drive.
All this should get you started.

Add: Speaking of using the live cd to install grub, I recently installed Sabayon Linux, which automatically installed grub to the mbr of the boot drive(containing Ubuntu's grub)...I was able(using the live cd) to reinstall Dapper's grub to the mbr, the Sabayon's grub to it's root partition...handy little tool to know.

The Gparted Live CD(30 mb) is an excellent partitioning tool:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by Kazna on 2006-12-14
Many thanks confused57.

Yes, I'm thinking of having 8 distro's on an empty HDD once I can get used to this stage of basic testing and experimenting.

I'll be a little while now reading those links. Still on the first and will give it a try and then see how it goes.

---

### Post by Kazna on 2006-12-15
OK. Before I can proceed I don't understand the basics here. The terms for a beginner are very confusing. I'm not one who proceeds with anything until I know firmly the ins and out of some matter, usually.

Ive read through all that and there's too much room for error and too much I don't understand. So many commands/options that I don't know what they mean either. I've decided not to have the hassle of risking my main XP and Vista installations and choose to install all this on a new 80GB HDD with 6 partitions devoted only to Linux! With this I intend to experiment and play about with it, mess about with it to try and create faults, recover and see alternate methods, problems until I know what Linux is for myself.


Firstly, why is there mention of Alternate CD, Live CD and some standard ISO on CD to install?

I've asked 9 experienced (3 year plus) users: 4 have said I need the regular CD, 3 that I need the live CD and 2 that I need the Alternate!!??


Can you help here please. :(

I think I'll take it one at a time.

---

### Post by steve.horsley on 2006-12-15
There is no regular CD any more. There is only the "desktop" CD and the "alternate" CD. 

The Desktop CD is a full live CD. It boots a full Ubuntu OS from the CD. You can use it to check for hardware compatibility, use it as a rescue CD etc. It also has an install icon on the desktop once you are logged in, and you can launch the installer to install to the hard disk. This installer has fewer options than the alternate CD installer, and is of course reliant on getting the graphical interface working straight off, with all the hardware and memory requirements that entails.

The alternate CD is a text mode installer for Ubuntu. It has more options than the graphical installer, and seems to be more reliable too, maybe because it is less demanding on hardware and memory. 

One of the extra options on the alernate installer, under the guided partitioning, is the option of installing the bootloader GRUB to the system partition instead of to the MBR. This allows you to have a different bootloader as your initial bootloader. Unfortunately, this has never worked for me and I have always had to finish the bootloader install by hand, using the rescue mode of the alternate installer CD. 


The Ubuntu installer is only one CD because the rest of the packages available (after a good install) are available on the Internet. There are 20-30 CDs worth of extra packages! That said, they pack enough into the first CD to make a very useable install straight off.


The install takes less than an hour, even allowing for time going slow and thinking about the installer questions. Most of that time is having a cuppa waiting for the installer to copy off the CD. It only asks questions right at the beginning and right at the end

---

### Post by xpod on 2006-12-15
Hi Kanza,welcome to ubuntu

Mabey you could just think about the one distro at the moment rather than 8 m8;) ....and if you have 4 pc`s then install ubuntu onto one of those spare ones so theres no added risks of you doing any damage to all you windows installs....then you can cause all the problems you want without concern.
This is definetly the best bet to start out with me thinks

The alternate cd is just a text based installer which is really handy for those older systems(and some not so old)...as it dosent have the live session and all the gui`s to run that go with one.

You can actually do quite a bit more with an alternate cd than you can with a live cd but unless your having troubles with a live cd then it`s mabey best to just stick with that for now to save yourself any added confusion....

These guys will soon have you up and running im sure but as long as you give it a little patience and take it "one" step at a time you should be fine...

Good luck pal...you just got youself the best xmas pressie you could ever hope for:mrgreen:

---

### Post by Kazna on 2006-12-15
Thanks steve.horsley.

While you read/typed I read some more too doing a search on the forum.

I have to confirm there is some weird problem with burning Linux ISO's to CD, using any utility when the CD-RW/HDD/ISO is perfect. I know very well about hardware problems and troubleshooting and am still getting CD TEST : FAILED!

Anyway. Now thats made it all clearer for me (one worked). I have one CD ISO burned. Now that must be the install CD as when I boot from it it gives me the installation options.
 
So the Desktop CD lets me try Ubuntu fully working on my current XP OS without doing anything to it!?
It also allows alternate install options and installation options!?
I need to install Grub (bootloader) as well through the Alternate CD if I use the one install CD!?

Thats my current understanding.

Now if I don't have Grub and Dapper Drake is installed on a dual boot, will it still boot to Linux or not?

I'm also stuck on partitioning... do I have to format it as FAT32 beforehand or leave it unpartitioned and unformatted, or partition it and leave it as free space and how do I partition it: as logical drive, a separate drive or an extended drive?

This is all due to reading too many variable afflicted threads, opinions and tutorials. :roll:

Thanks.

---

### Post by Kazna on 2006-12-15
I was typing and missed your post xpod :D

Thanks BTW. I'll do one first yes. Dapper Drake onto a clean new HDD.

I'll download the Live CD and see where I get.

One more question: is there any way to exit/abort a running setup?

I never found an option as such.

---

### Post by xpod on 2006-12-15
>  	I was typing and missed your post xpod 

I miss more than the posts mate so dont worry about it:D 

Not sure what you mean by "anyway to abort a running setup"???
If you mean abort a running live cd session then it`s just a case of hitting the shutdown icon the same as any installed os....and removing the cd when it tells you to.

Aborting any install would mabey be a different case...especialy if you had other stuff on the drive and the partitioning stage had begun.....not a good idea then.

Personally those first weeks i just left any space\hd ubuntu was going onto "unallocated" and once i began the install procedure i would just point ubuntu to the relevant space\drive and let it do the rest itself.......

You got all the time in the world to learn the many different ways of setting up and installing  so just do things the easiest way possible to start out and it should be a walk in the park

---

### Post by Kazna on 2006-12-15
> **xpod said:**
> I miss more than the posts mate so dont worry about it:D 

Not sure what you mean by "anyway to abort a running setup"???
If you mean abort a running live cd session then it`s just a case of hitting the shutdown icon the same as any installed os....and removing the cd when it tells you to.It didn't prompt me to remove the CD so I shutdown after 10 minutes.

> Aborting any install would mabey be a different case...especialy if you had other stuff on the drive and the partitioning stage had begun.....not a good idea then.Before the partitioning stage. @ the languages stage I needed to get out as I got stuck after that and there was no option but to press the power switch.

> Personally those first weeks i just left any space\hd ubuntu was going onto "unallocated" and once i began the install procedure i would just point ubuntu to the relevant space\drive and let it do the rest itself.......Thats a perfect idea. Very simple. I'll be doing that myself thanks ;)

> You got all the time in the world to learn the many different ways of setting up and installing  so just do things the easiest way possible to start out and it should be a walk in the park

[COLOR=Blue]The first thing anyone should do when wanting to test/experience a particular Linux distro is try the Live CD or otherwise maybe called Desktop CD (ask for more)[/COLOR]

I've just ran Edgy (Ubuntu 6.10) and Dapper (Ubuntu 6.06) and both are excellent! Believe me, everything I was missing in Mac and Win is on there!!

I'll be doing a Bordeaux/Dapper Drake/Edgy Eft install, today on a new HDD hopefully. We'll see how it goes when trying to dual boot them. :mrgreen:

[B][COLOR=DarkRed]BTW, how do I check how much RAM Linux OS is using and where do I find all the system files/folders... are they in /lib?
[/COLOR][/B][COLOR=DarkRed][COLOR=Black]
Thanks!
[/COLOR][/COLOR]

---

### Post by steve.horsley on 2006-12-15
As xpod says, the easiest approach to partitioning is to make totally unallocated un-partitioned disk space by deleting or shrinking existing partitions, and then telling the installer to use the unallocated space - beware that the default choice is to erase and re-use the entire disk! I recommend partition magic for removing and shrinking existing partitions, partly because if you screw up at that stage, you cannot blame Ubuntu. There is always a tendency to blame Ubuntu when you screw up the partitioning, and to be fair, the Ubuntu partitioning tool is not as user friendly as PM so the chances of a mistake are higher.

You will need to use the Ubuntu partitioning tool if you want to install more than one distro though, because the default install uses all the free disk space.

The command to see how much RAM is being used is **free**, but don't worry if it says it's all in use because Linux uses spare RAM as disk cache - it's more relevant to see if swap is being used.

System files and folders are all over the place. 
[http://tldp.org/LDP/intro-linux/html/chap_03.html](http://tldp.org/LDP/intro-linux/html/chap_03.html)
tldp.org is well worth spending some time at.

---

### Post by confused57 on 2006-12-15
> **Kazna said:**
> OK. Before I can proceed I don't understand the basics here. The terms for a beginner are very confusing. I'm not one who proceeds with anything until I know firmly the ins and out of some matter, usually.

Ive read through all that and there's too much room for error and too much I don't understand. So many commands/options that I don't know what they mean either. I've decided not to have the hassle of risking my main XP and Vista installations and choose to install all this on a new 80GB HDD with 6 partitions devoted only to Linux! With this I intend to experiment and play about with it, mess about with it to try and create faults, recover and see alternate methods, problems until I know what Linux is for myself.


Firstly, why is there mention of Alternate CD, Live CD and some standard ISO on CD to install?

I've asked 9 experienced (3 year plus) users: 4 have said I need the regular CD, 3 that I need the live CD and 2 that I need the Alternate!!??


Can you help here please. :(

I think I'll take it one at a time.

It's wise to take it slow, I was mainly wanting to give you an overview of how I set up my mutli-boot Linux system...steve.horsley & xpod have explained things very well...don't hesitate to ask any questions after you formulate your game plan & before you actually begin installing.  

For your new hard drive, you might want to set it as the drive to boot first...you can add the entry to boot Windws to grub, as described in the first link I gave you.  Didn't really expect you to actually be able to jump right in and start installing multiple OS, I've been using Ubuntu for almost a year and I'm just now getting the confidence to experiment & actually be able to repair my mistakes(sometimes not).

I've had excellent results partitioning with the Gparted Live CD, however, I've never used PM.

---

### Post by Kazna on 2006-12-15
Thank you confused57 :D

OK. [U][COLOR=Blue][B]LATEST UPDATE:

[/B][/COLOR][/U][COLOR=Blue][COLOR=Black]I've downloaded Dapper Drake, Edgy Eft, Mandriva 2007 and FC Bordeaux.
Two are Live CD's and two are straight install CD's.
I've played around on the Live CD's with the Terminal etc to get a hang of things.
I've deleted 4 x FAT32 partitions on my HDD - 80GB
The HDD is solely for Linux now :D
The first install is to be Dapper Drake starting in around 6 hours.
I want this HDD to be dual boot with 3 other Linux distro's mentioned above (later).
I will Master the HDD when installing and disconnect the other one just to make sure all goes right.

[/COLOR]*What aspects shall I keep in mind for this dual boot feature to work well later?
*Where will I install Grub and will it have to be installed manually later?
*How do I create partitions now: 
[LIST]
[*]using Windows now (Disk Manager)
[*]a separate utility beforehand (PTD, GP, PM)
[*]off the Live or install CD (setup)
[*][img]http://img374.imageshack.us/img374/7813/123gifs0136fr.gif[/img]
[/LIST]
*How many partitions do I create (i.e. now for the later installs or only one for first one?
*Any special configurations I need to make before setting off on the rollercoaster to the first Ubuntu installation, bearing in mind I want to dual boot it later or not?

[B][COLOR=Red]I have no worries for data because there isn't any on the HDD![/COLOR] [COLOR=Black]So I'm willing to try anything. ;)

[/COLOR][/B][COLOR=Black]Thank you for being so decent BTW. I was told I'll be faced with a disgruntled group but after reading 15+ threads and my own experience, its been quite the contrary [img]http://camou.net/udg/smilie/e021.gif[/img]

I'll await your replies guys before continuing. These are the only aspects holding me back now.
[/COLOR]
[/COLOR]

---

### Post by Kazna on 2006-12-15
HAHA!!! What a beauty! I've been playing about with it and have managed to create 8 partitions on the 80GB HDD, 4 under an extended partition as logical drives, set /dev/hda1 as the /root HDD with /boot and /Grub and set a 2GB swap file and now I've installed all updates and a few programs from Synaptic Packet Manager perfectly with Ubuntu Edgy Eft 6.10 fully working!!! :mrgreen:

Thanks guys, this is awesome. :cool:

There the fun stops :|

Some more questions. 
I used GNOME partition to setup my HDD partitions while using the Live CD. What a beautiful tool, love it.
See my screenshot attached for my HDD setup. 

Firstly why are they basically all over instead of numerically in order?
Even in the partitioning and installation mounting section, they were all over the shore, hda1, then hda3, then hda6 etc. I had to change it around manually.

Secondly, where can I access hda1 and the swap file from? (its not showing there)

Thirdly, whats the 'Desktop' folder and where is it stored? Can I move it?
Whats the 'Home' folder and where is it stored to access?

Home is my username BTW.

*Next, where can I stop the using the login username/password screen?
*Also how does the workspaces function work.. where are they both held?
*Erm, yes and why are the colors a little vague and light rather than sharp? *The writing especially is kinda blurry and it is certainly hard to see. Any settings for this?
*More, how can I shrink my menu and font size?
*In the screenshot, why are hda1 (root) and hda3 (swap) not shown?
*What is Floppy1 when I only have one floppy drive?
*Why is internet upload/download extremely fast with Linux and creepy slow with Win?

Thats all fro now. Sorry for asking so much.. I'm interested and like to learn about Linux as long as someone will explain :mrgreen:

NOTE: I'm surprised how fast my net connection and page flickering with Linux is in comparison to Win. What could this possibly mean.... ?

---

### Post by steve.horsley on 2006-12-15
> Firstly why are they basically all over instead of numerically in order?
Even in the partitioning and installation mounting section, they were all over the shore, hda1, then hda3, then hda6 etc. I had to change it around manually.

Maybe because they are listed in alphabetical order and the size is the first part of the name? That is certainly true of the nautilus file browser.

> Secondly, where can I access hda1 and the swap file from? (its not showing there)
I guess that hda1 is your filesystem root, so that / is your access to hda1. You can't not have access to it.
Swap is a partition, not a file, and you cannot access it as a file any more than you can access system memory as a file. The command **free** will show how much swap is being used.

> Thirdly, whats the 'Desktop' folder and where is it stored? Can I move it?
Whats the 'Home' folder and where is it stored to access?

Home is my username BTW.
The directory /home is where all the user's home directories are located. Since your username is Home, your home directory will be /home/Home. This is like the windows My Documents, and is where all your user info, documents and configuration files will go. A directory Deshtop exists in your home directory, and anything you place in there will be visible on your desktop as an icon. Confusingly, some things (like the partition icons) appear on your desktop even though there is no corresponding file in /home/username/Desktop.

> *Next, where can I stop the using the login username/password screen?
System->Administration->Login Window, Security tab adn enable automatic login.
> *Also how does the workspaces function work.. where are they both held?
Not sure what this means. There are several virtual desktops that you can switch between ny clicking the desktop switcher or Alt-Ctrl-Left/Right-arrow.
> *Erm, yes and why are the colors a little vague and light rather than sharp? *The writing especially is kinda blurry and it is certainly hard to see. Any settings for this?
Because it looks so much better than that awful dated and jaggy Microsoft look. Stick with it for a week and then look at windows again - you too will go Ugh! If you really must have the jaggies, go System->Preferences->Font and set the font rendering to monochrome. Ugh.
 
> *More, how can I shrink my menu and font size?
System->Preferences->Font
*> In the screenshot, why are hda1 (root) and hda3 (swap) not shown?
hda1 is / so is always there. Called Filesystem.
Swap is not part of the filesystem, it is just memory. An icon for it would be useless.
> *What is Floppy1 when I only have one floppy drive?
A buglet in the installer. It's non-functional. I seem to remember there is a line in /etc/fstab that you can comment out to get rid of it, but unless you're sure what you're doing, just ignore it.
> *Why is internet upload/download extremely fast with Linux and creepy slow with Win?
Better networking stack perhaps? I really don't know.

---

### Post by Kazna on 2006-12-15
[B]Eggscellent [COLOR=Blue]steve.horsley!!!! [IMG]http://users.pandora.be/eforum/emoticons4u/happy/1074.gif[/IMG]

[/COLOR][/B][COLOR=Blue][COLOR=Black]You answered all my queries, even the wrongly worded ones. Thank you so much.[/COLOR] [IMG]http://i2.photobucket.com/albums/y43/christianchr/Emoticons_2/worthy.gif[/IMG]
[/COLOR]
> **steve.horsley said:**
> Maybe because they are listed in alphabetical order and the size is the first part of the name? That is certainly true of the nautilus file browser.They were not. They were listed randomly and there was no correlation between size or name. Its something of a trouble using GParted there as I had to manually type in the drive and the folder to install.

> I guess that hda1 is your filesystem root, so that / is your access to hda1. You can't not have access to it.
Swap is a partition, not a file, and you cannot access it as a file any more than you can access system memory as a file. The command **free** will show how much swap is being used.Yes. Thank you. I knew about the hda1 but wanted to see the size of the swap thats all. Have checked and it works as you have told.

> The directory /home is where all the user's home directories are located. Since your username is Home, your home directory will be /home/Home. This is like the windows My Documents, and is where all your user info, documents and configuration files will go. A directory Deshtop exists in your home directory, and anything you place in there will be visible on your desktop as an icon. Confusingly, some things (like the partition icons) appear on your desktop even though there is no corresponding file in /home/username/Desktop.This is what I needed and was confused about mostly!

> Because it looks so much better than that awful dated and jaggy Microsoft look. Stick with it for a week and then look at windows again - you too will go Ugh! If you really must have the jaggies, go System->Preferences->Font and set the font rendering to monochrome. Ugh.Haha, I'll see how that goes. I think I had resolution problems that were making it seem weird. I've chosen one now that seems fit.
 
> Better networking stack perhaps? I really don't know.The upload/download and general surfing speed with Linux was very very quick in comparison to Win. I have no idea why that was so but having an 18MB connection I was only getting maximum 570Kbps d/l and 100Kbps upload while I've done everything there is to change this behavior. Wow, but I love the speed of 8Mbps upload I saw with Linux :mrgreen:


[B]One more thing: in which folder are programs installed when going through SPM?

[/B]Thanks!

---

### Post by Kazna on 2006-12-16
Anyone awake?

---

### Post by confused57 on 2006-12-16
Here's where programs downloaded by SPM are stored:
[http://www.ubuntuforums.org/showthread.php?t=259075&highlight=archives](http://www.ubuntuforums.org/showthread.php?t=259075&highlight=archives)

---

### Post by steve.horsley on 2006-12-16
I don't know what spm is.

It occurs to me on the subject of anti-aliased fonts... the acts of looking at a font and of reading text are very different activities that use different parts of the brain. Sure, if you look at an antialiased font, it looks a little blurred. But when you read text, you are using recognition of word shapes, and I believe that this is easier with antialiased fonts where there is less high frequency noise from the jaggies. At the moment you are doing a lot of looking at the font because it is strange and unusual. As you get used to it and begin just reading what it says, I think you will find it easier on the eye and easier and quicker to read.

I finally found how to enable antialiasing in XP - they call it Microsoft ClearType (TM) Technology, and it actually makes windows a lot less objectionable to me.

---

### Post by Kazna on 2006-12-16
> **confused57 said:**
> Here's where programs downloaded by SPM are stored:
[http://www.ubuntuforums.org/showthread.php?t=259075&highlight=archives](http://www.ubuntuforums.org/showthread.php?t=259075&highlight=archives)
Quality. Thanks!
> **steve.horsley said:**
> I don't know what spm is.OK. I referred to Synaptic Package Manager as the SPM. I thought it'd be a common term in usage.

> It occurs to me on the subject of anti-aliased fonts... the acts of looking at a font and of reading text are very different activities that use different parts of the brain. Sure, if you look at an antialiased font, it looks a little blurred. But when you read text, you are using recognition of word shapes, and I believe that this is easier with antialiased fonts where there is less high frequency noise from the jaggies. At the moment you are doing a lot of looking at the font because it is strange and unusual. As you get used to it and begin just reading what it says, I think you will find it easier on the eye and easier and quicker to read.

I finally found how to enable antialiasing in XP - they call it Microsoft ClearType (TM) Technology, and it actually makes windows a lot less objectionable to me.Wow. Didn't know. Well I'm obviously used to Mac and Win so it'll take time for the brain and eyes to become accustomed. 
Thanks for the brill answers all of you!
I can't think of any other queries I have at the moment.. so until next time :mrgreen:

---

### Post by cleverselfreferentialname on 2006-12-28
Slow connection in Windows XP is due to Microsoft intentionally limiting the number of connections Windows XP can make, with SP2 I believe.

[QUOTE=Microsuck_luser]Windows XP is designed from the ground up to be a secure OS. In order to prevent the propagation of worms, Microsoft has limited the number of outgoing connections Windows can make at any one time to 10....this is for your safety....Microsoft is looking out for you...you are getting sleepy...[/QUOTE]

Of course, that's not the case. 10 connections at once still means a worm will propagate at an exponential rate. They just want you to 'upgrade' to Windows Server.

---

### Post by Kazna on 2006-12-29
Yes, SP2 restricted that option, but its only for maximum multiple connections at any one time allowed by a single piece of software such as P2P apps thats been restricted.
 
I don't have that restriction as due to the hack I did :D

The restriction means nothing tp security as it'll only take a few more seconds and you'll still be infected with the same worm, but that its a pain to users and they'd like you to upgrade and feed them money.. which is well documented.

---

### Post by randiroo76073 on 2006-12-29
Hi Kazna, I've just been in Linux for 4 mos. and am multibooted w/ 14 distros + 98se.  They've all pointed you in the right direction so all thats left now is to have fun.  Once you find where things are located you'll be overjoyed at the simplicity of it all, you'll find yourself sitting at your computer laughing, typing code in a terminal, and actually enjoying yourself!

Why 14 distros?  Cause I can!  Welcome to Linux, no boundaries, no rules except "Respect your fellow man"

---

### Post by Christopher on 2006-12-29
> **randiroo76073 said:**
> Hi Kazna, I've just been in Linux for 4 mos. and am multibooted w/ 14 distros + 98se.  They've all pointed you in the right direction so all thats left now is to have fun.  Once you find where things are located you'll be overjoyed at the simplicity of it all, you'll find yourself sitting at your computer laughing, typing code in a terminal, and actually enjoying yourself!

Why 14 distros?  Cause I can!  Welcome to Linux, no boundaries, no rules except "Respect your fellow man"


14 , Nice!   I typed free in terminal and i get this:


christopher@christopher-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        775584     762940      12644          0      74784     490160
-/+ buffers/cache:     197996     577588
Swap:      1735012          0    1735012
christopher@christopher-desktop:~$ 

Does it look like my swap is working properly? Thank you in advance.

---

### Post by randiroo76073 on 2006-12-29
Looks fine to me, the 0 under "used" means your not needing to use "swap" at present :)

---

### Post by Christopher on 2006-12-29
> **randiroo76073 said:**
> Looks fine to me, the 0 under "used" means your not needing to use "swap" at present :)

THank you

---

