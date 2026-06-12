---
title: "installing 8.10 on ibook g4"
date: 2009-01-24
forum: Apple Hardware Users
---

### Post by devrele on 2009-01-24
I am just getting started with Ubuntu and  I would like to install  8.10 (as part of a dual boot with OS X) on my iBook G4.

 I have recently installed Unbuntu as part of a dual boot on a PC system running Vista. That was a breeze. But I have the impression things are not quite so simple and straightforward for Mac users!

The first thing I did was to download the "alternate" version of 8.10. I was able to boot this disc on my iBook G4, whereupon I received a command prompt. I did not know what to do then.

Anyway, from what I have read I gather only the Ubuntu live disc for PC systems can create partitions, the disc for Mac cannot.  So I'm assuming the first thing I need to do is use iPartition to make a second partition on my system, before I even boot the ubuntu disc. But iPartition gives me a long list of "types" to choose from when I go to make a partition--everything from HFS to various forms of Linux. So my first question is: what type is best to use for an installation of Ubuntu? And do I check or leave unchecked the option for "format partition"?

Then the next thing I hope to find out is what I need to type at the command prompt when I boot the 8.10 alternate disc, in order to get the Ubuntu installer to load.

I'm hoping from there everything will be self-explanatory, but if anyone who has done this before has any useful information to add, please do: I'd appreciate it!

Thanks in advance for your help.

---

### Post by devrele on 2009-01-24
^^

---

### Post by pxwpxw on 2009-01-24
> **devrele said:**
> ^^

For ppc, you get a different start - with a yaboot prompt to select from options, looks like

boot:

Is that what you got?

---

### Post by mkvnmtr on 2009-01-24
I am running 8.10 on a G4 Ibook. I tried to boot both the alt. disk and the live disk but had no luck. It had become my normal manner of upgrade to just do a clean install. 8.04 had been easy to install but in reading the forum the workarounds to install 8.10 seemed like a lot of trouble so I waited. This week I decided to see if I could do an upgrade from 8.04. It was the first of three distro upgrades that worked smoothly. The workarounds are kind of daunting for someone that does not have a lot of experience.You might find it easier to install 8.04 and then upgrade. There are several threads that will help you install 8.10.It is your choice but I found the upgrade easier.
As for partitioning. The live disk will do everything you need. Don't use the installer. When you boot the live disk go to system/admin/partition editor to find Gparted. It is the same as on the other disks.
When I first installed 6.06 I used Apiece of software called Drive Genius to defragment my mac os. Then the live disk to resize and give myself the free space to install Ubuntu.
The rest was easy. I have reinstalled and changed my partitions at least 30 times and never lost anything I didn't want to loose.
There are several posters here that can help you through what ever install you decide to use.

---

### Post by devrele on 2009-01-24
Thanks to those of you who replied.

Pxpw: Yes that is what happened I got the prompt "boot:"


Mkvn:

Thanks for sharing your installation experiences with me. After reading what you wrote, I think I will indeed install 8.04; then upgrade from there. So, if I understand you right, I just need to burn 8.04 to disc and boot that up on my ibook G4. Run Gparted. And then install Ubuntu. Sounds like something I can handle!

Is there also an "alternate" disc for 8.04 or can I just use the regular live disc also used on a PC? I will go in search of it now...

---

### Post by mkvnmtr on 2009-01-24
You have it right boot the live disk and use the partition editor to resize then go on to the install. Leave the space as free space, don't make a partition. Then in the install you can choose to use the largest free space. It will make the partitions you need for yaboot , swap and the install. Yes there is an alt install disk but you don't get the partition editor to use off of the desktop. It is a lot easier to explain how to do it all before the install. If you have no experience using the installer it is easier to mess up during the install. As luck would have it I am doing the same thing today. I messed up my so bad thet I have to reinstall. I am downloading the updates for 8.04 right now. Then I am going to upgrade again. At least I get a little better at it each time. The only thing I have to save is my addresses from Thunderbird and abooout 10 GB of music. The addresses are business but the music is not too important.
When you go to install 8.04 as you restart with the disk as the firsts words come on the screen press the tab key. Then type in "live-nosplash-powerpc". Then hit the enter key. Then it will finish booting.

---

### Post by devrele on 2009-01-24
I just downloaded 8.04 from the Ubuntu site and burned it to disc, but the disc will not boot on my iBook for some reason?

The one I downloaded is:

"Ubuntu 8.04 LTS Desktop: Released April 2008 and maintained until April 2011 – ideal for large deployments"

Is that correct or do I need another version? And if so, do you have a link? Thanks.

---

### Post by devrele on 2009-01-24
Ok I think I found the right one?

8.0.4.1-alternate-PowerPC ....

downloading now

---

### Post by DrFarnsworth on 2009-01-25
I just installed Ubuntu 8. on my Ibook g4 900mhz it starts up fine but for some reason i can not connect to any wifi but i can see my network. it is also using around 70% to 80% of the processor for the OS. That just seems really odd and really high. any tips for getting it to run better?

---

### Post by mkvnmtr on 2009-01-25
For the wifi in system/administration look for hardware drivers. Enable it. I install htop to view cpu and memory usage. It should go up and down a lot but just setting on a web page it should be pretty low. Maybe with Htop you can see where your usage is.

---

### Post by DrFarnsworth on 2009-01-25
> **mkvnmtr said:**
> For the wifi in system/administration look for hardware drivers. Enable it. I install htop to view cpu and memory usage. It should go up and down a lot but just setting on a web page it should be pretty low. Maybe with Htop you can see where your usage is.

thanks for the help, I was wondering if it is possible to have a bad install or something since when i try to got  system/admin hardware drivers it asks for my password then closes down and does nothing. 

also every time i restart it wants me to change my password for some reason.

---

### Post by mkvnmtr on 2009-01-25
When I click on hardware drivers it just opens the window. When you click on enable it will probably ask for a password. It should then download it and you should see in the window it is enabled. You are connnected to the internet by cable? As for asking you to change your password I have never seen that. You probably clicked on something about changing passwords.

---

### Post by devrele on 2009-01-26
Ok I got 8.04 alternate and boot it up, but it puts me in the same palce as the 8.10 disc:

I get a prompt with "boot"

What do I do then? I tried typing "live-nosplash-powerpc" But I get the msg "unable to open the file/invalid device"

I am also wondering if it isn't safest for me to make a second partition using iPartition before I even think about installing Ubuntu, so that I don't risk losing my OS X installation if I make a mistake my first time using the Ubuntu installer? 

I know how to make a second partition on my HDD using iPartition, I just don't know what "type" is best to select for a partition that is going to house Ubuntu.

---

### Post by pxwpxw on 2009-01-26
> **devrele said:**
> Ok I got 8.04 alternate and boot it up, but it puts me in the same palce as the 8.10 disc:

I get a prompt with "boot"

What do I do then? I tried typing "live-nosplash-powerpc" But I get the msg "unable to open the file/invalid device"

I am also wondering if it isn't safest for me to make a second partition using iPartition before I even think about installing Ubuntu, so that I don't risk losing my OS X installation if I make a mistake my first time using the Ubuntu installer? 

I know how to make a second partition on my HDD using iPartition, I just don't know what "type" is best to select for a partition that is going to house Ubuntu.

For the PPC version Alternate CD or the Live CD

boot:

Press the TAB key and it will show you all the options.
If you just hit Enter it will boot with no special options - should be ok for the Alternate CD, it was on my ibookg4.

There should be a 'nosplash' option for the live cd, but I dont think you need it for the Alternate CD.

 **mkvnmtr** has the partitioning covered.

With the 810 Alternate CD, there was a bug with the installer failing to mount the CD.
A fix is here if you use that -
PowerPC - Installing Intrepid (8.10) - No common CD-ROM drive was detected (**tiresia**)
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by mkvnmtr on 2009-01-26
The thing is you have to hit the tab key as soon as the first words come up after starting. It is sometimes very quickly. If you wait typing in the live nosplash doesn't work. 
If you form a partition then you have to do a manual install and form all that you need. If you just resize your mac partition and leave free space unformated then you can choose to use the largest free space to install in and it won't touch your mac install. It is much easier for some one new to mess up the manual install.

---

### Post by devrele on 2009-01-26
Thanks for your continued help.

I tried "tab" a few more times, but it seems I can't catch it quickly enough?
Anyway, "enter" worked! got things going...

So here's what I'm at now: I get to the "Partition Disk" and I choose "Guided - use largest continuous freespace"

But I then get the message: "Failed" and a message that is probably because I don't have enough free space to make another partition. But I have 15 gigs free on my drive...

Any ideas?

---

### Post by pxwpxw on 2009-01-27
> **devrele said:**
> Thanks for your continued help.

I tried "tab" a few more times, but it seems I can't catch it quickly enough?
Anyway, "enter" worked! got things going...

So here's what I'm at now: I get to the "Partition Disk" and I choose "Guided - use largest continuous freespace"

But I then get the message: "Failed" and a message that is probably because I don't have enough free space to make another partition. But I have 15 gigs free on my drive...

Any ideas?

You need to actually resize the MacOS partition so there is an 'empty' partition. - not just space on the  Mac volume.

---

### Post by devrele on 2009-01-27
Yes, this is the place I'm stuck. I don't seem to be able to create a new partition. I keep getting the message "not enough space on the device." I read that this might be caused by having a file over 1 GB on the drive or having a highly fragmented drive, but I have no files over 1 GB and I've run a defragmenter, yet still get the message "not enough space." 

So it looks like I may have to backup and reformat before I can even get to the point of installing Ubuntu. My God, things shouldn't be this complicated! It took me all of a few minutes to install Ubuntu in a dualboot with Vista!

---

### Post by pxwpxw on 2009-01-27
> **devrele said:**
> Yes, this is the place I'm stuck. I don't seem to be able to create a new partition. I keep getting the message "not enough space on the device." I read that this might be caused by having a file over 1 GB on the drive or having a highly fragmented drive, but I have no files over 1 GB and I've run a defragmenter, yet still get the message "not enough space." 

So it looks like I may have to backup and reformat before I can even get to the point of installing Ubuntu. My God, things shouldn't be this complicated! It took me all of a few minutes to install Ubuntu in a dualboot with Vista!

Life is interesting for Mac users.

Are you getting the "not enough space" message from iPartition before the install, or the ubunu installer? 

Have you tried verifying and repairing the Macos volume in MacOS - can sometimes cause problems if not done.

---

### Post by devrele on 2009-01-27
Good news: I was able to get the drive partitioned. For anybody reading this who is stuck in the same place I was: I did this by running iDefragmenter on the "compact" setting. It appears that only the "compact" setting will be effective for making enough contiguous space to allow for a partition.  All of the other defragmenting algorithms are useless for this! After this I made a second partition and then installed Ubuntu.

I verified my OS X installation is still working; and I am getting a dual boot option.

So, slowly progress is being made! 

The place I'm at now is when I boot Ubuntu, I'm not getting Ubuntu, instead I'm getting a black screen with lots of purple dots moving around. Keyboard and mouse are unresponsive.

---

### Post by mkvnmtr on 2009-01-27
If you installed 8.04 I never encountered this problem. You might try rebooting and pressing the tab key to try a nosplash option. If you got 8.10 installed I believe there are some x org problems and you have to edit a file. I never did it just upgraded from 8.04. There are some threads in the forum about it.

---

### Post by devrele on 2009-01-27
I installed 8.04 (using the PPC alt disc) and was going to upgrade later, per your advice.

I'm trying "tab" but can't seem to get any result rom it.

---

### Post by devrele on 2009-01-27
I found the following advice, which I tried out: "When you get to the second stage boot: prompt, hit TAB to stop the countdown. Then issue: Linuxvideo=ofonly nosplash."

But when I do this I get the message "no such file or directory"

---

### Post by mkvnmtr on 2009-01-27
When you hit tab at the boot prompt there is a list of options. The one that worked for the disk was live-nosplash-powerpc. Use the options you se on the screen. Of course you don't need to try one that says something like powerpc 64bit. Use them one at a time until you find the one that works. These are options in the way the kernel boots to fit your machine.

---

### Post by devrele on 2009-01-27
When I hit "tab" at the boot prompt all I get back is text like this:


Linux                old



No list of options appears.

---

### Post by mkvnmtr on 2009-01-27
I just rebooted a few times to see. When you get to the type help for a list of boot options  instead of typing help press enter. If that doesn't do it when you type help and get to the old linux deal press enter.

---

### Post by devrele on 2009-01-27
I read a thread where it was suggested that one should use the "desktop-ppc" ISO rather than the "alternate-ppc" ISO, unless one really knows what one is doing. Could reinstalling using the desktop-ppc image perhaps fix my problem?

Another person says he wasn't able to get Ubuntu to boot on his system except by going back to 7.10.

Maybe I will just try the desktop 8.04 first, and see what happens.

If I reinstall is there anything I need to know?  I am guessing I won't use "guided -- use largest free space" anymore, since I already have an Ubuntu installation. What will I need to select? Or will Ubuntu automatically know to install on the right partition?

---

### Post by devrele on 2009-01-27
If I press "enter" after the "old linux" msg, it proceeds to try and boot Ubuntu and I'm at the black screen again. 

"Enter" at the boot prompt always boots Ubuntu.

What happens for me when I boot is first I get the message "Stage 1 boot" : l for linux, x for OS X. 

So I choose "l" --

Then I get another boot prompt.  At this boot prompt if I type "tab" I get the message "old linux."

If I press "enter" Ubuntu tries to boot and I get a black screen.

and the message I get before the screen goes black and purple dots start appearing is something like "Region 0: cannot allocate device"

---

### Post by mkvnmtr on 2009-01-27
If you press l then yhou have to press enter or it will just wait for you. If you don't press l then in a few seconds it will go ahead and boot. I think you have a good install .

---

### Post by devrele on 2009-01-27
The install might be good. But it's not doing me much good, until I can find a way to get past the black screen and get Ubuntu to boot!

I wrote down the precise message I am getting before the screen begins blacking out, after I select to boot Ubuntu, in case this can help anyone in identifying the problem:

"PCI cannot allocate resource region 0 of device 0001.10.18.0"
"PCI cannot allocate resource region 0 of device 0001.10.19.0"

I don't know if that message is an explanation for the reason I'm getting the black screen or not. But I can't get into Ubuntu, and I'm not able to get an options menu when I press "tab" at the boot prompt, so I'm really not sure what I can do next, aside from trying to use a different installer.

---

### Post by mkvnmtr on 2009-01-27
Thaaaaaaat is exactly whaaat mine says every time it boots up since 6.06. After that how long do you wait. It should go ahead and boot. Mine never took more than a minute or two but give it some time the first time.

---

### Post by devrele on 2009-01-28
I have waited quite awhile. Just to make sure, I let it sit there for 30 minutes after booting. No luck.

It begins with dark purple pixels moving on a black screen... Then the screen becomes completely black... And nothing after that.

By the way my iBook is a 14" screen, not a 12"... don't know if that could be relevant to the problem ,but thought I'd mention it... since whatever the problem is I get the impression it is related somehow to video/video drivers???

---

### Post by mkvnmtr on 2009-01-28
I think you have the same machine I have. I have had no problems that were machine related since I installed 6.06. Plenty of problems but they were all self induced by the operator. I can't imagine what the problem is.Try searching for threads on installing on that Ibook. You will find that google gives better results for threads on this forum than the forum search feature.

---

### Post by marconeuro on 2009-02-26
And then, the solution? I have exactly the same problem on an ibook G3. The fact is that I had to do a network install. Then there is no way to came out of this problem? I should reinstall everything? no way to start even in text mode? remember me windows...

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by avtolle on 2009-02-26
Try this; at the second prompt, hit the Tab button; then type in ```
Linux video=ofonly
```and press the return key to see whether that helps.

There are two options presented once installed at the second prompt; Linux and old. One must add the boot parameter manually as above'.

EDIT: Let me clarify that; if only Ubuntu, e.g., is installed, the above two options are those which appear. If one is dual booting with OSX, then there will be three options, one for OSX, Linux and old.

---

