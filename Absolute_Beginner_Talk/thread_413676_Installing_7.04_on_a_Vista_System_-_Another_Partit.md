---
title: "Installing 7.04 on a Vista System - Another Partition Question"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by bodean on 2007-04-19
Ok. I just burned the 7.04 cd 

My laptop has 1 harddrive, currently broken into two partitions, each 50 gig.  I have vista on, and want to dual boot ubuntu.  I'm reading that I need to repartition in vista prior to installing.

Any ideas how to do this?  What type of size partition do I want for ubuntu? 10gig?
I have to leave vista on as I do play games on it.

---

### Post by LaRoza on 2007-04-19
Here's the deal with Vista.

You cannot use Ubuntu to resize the Vista partition, Vista must do it.

So:
1. Boot Vista
2. Defrag hard disk
3. Resize the partition IN VISTA, for help, press F1 and type in Partition.
4. Make a partition for Ubuntu, the sizes required are quite small, but 10 Gig is enough. It really depends on the size of your HD. I would make a bigger partition, (20 Gig).
5. Install Ubuntu, in the correct partition, if you install it in the wrong partition, you'll loose everything in that partition. 

Depending on what games you want to play, you can probably play them in Linux. Search the forum or check out 

[http://appdb.winehq.org/](http://appdb.winehq.org/)

this is for wine, other apps may be better or worse.

---

### Post by bodean on 2007-04-19
Thanks.
I also read that it's wise to run the live cd first prior to full install? Advantages of this? Does this not install the OS to the harddrive?

---

### Post by freebird54 on 2007-04-19
While on the live CD, your hard drives are not even mounted - thus you can have no effect on your existing installation.  It allows you to see what the system can do, and to check that your hardware is recognized/supported adequately prior to installing.  You can then install directly from a running CD session - and even surf the net, play games, ask for help or whatever WHILE installing...

Hope that clarifies it for you.

BTW - resize or move Vista partitions only with Vista tools - as stated in the previous post...

---

### Post by xanikseo on 2007-04-19
The live CD does nothing to your computer at all. You have to install Ubuntu from it anyway. So being wise is nothing about running the live CD first. You have to do it anyway.

---

### Post by bodean on 2007-04-19
I noticed that My 1 hard drive has two partitions. A 60gig C and a 40gig (logical) D.
Following a guide on here, it is recommend in vista to use the "Shrink" feature.  Upon looking at that in vista, it says "Total Size before shrink in MB 57302", Size of available shrink space in MB "26"

If I need 10-20 gig of that, i dont know why its telling me 26

---

### Post by freebird54 on 2007-04-19
Probably it has put the page file near the end of the available space, leaving the middle open for other things.  If you turn off the page file, then defrag, THEN resize, you should see a big difference in the available change.

---

### Post by bodean on 2007-04-19
I turned off the page file, defragging now with perfectdisk. See if this works. Will let you know

---

### Post by graigsmith on 2007-04-19
definately back up first!  as doing dual boot with 2 os's is almost always a good way to loose your data.

---

### Post by freebird54 on 2007-04-19
Forgot to mention - sometimes there's a Hibernation file (depending on your setup) which can also be near the end of your space.  I *THINK* it defaults to your data partition though.... (heard that somewhere - no personal experience)

---

### Post by az on 2007-04-19
> **graigsmith said:**
> definately back up first!  as doing dual boot with 2 os's is almost always a good way to loose your data.

The Ubuntu installer is very reliable and safe.  While it is smart to back things up, things rarely go wrong.

---

### Post by bodean on 2007-04-19
Why would you lose you data with a dual boot? they are on seperate partitions.

---

### Post by freebird54 on 2007-04-19
How about a power outage while resizing your partition?  The best use of a backup is to make it less likely that problems will happen! (See Murphy's law)

---

### Post by bodean on 2007-04-19
I managed to get the partition tool working in vista.
I now have 15gig of free space. I started up the live cd, now stuck on the step 4
and it says "No root file system is defined"

How do I fix this and continue the install?

I choose "Manual" over the guided partition disk options.  Was this not the right one to chose?

---

### Post by az on 2007-04-19
> **bodean said:**
> I managed to get the partition tool working in vista.
I now have 15gig of free space. I started up the live cd, now stuck on the step 4
and it says "No root file system is defined"

How do I fix this and continue the install?

Are you picking the manual partitioning or just going with using the FREE SPACE?

---

### Post by az on 2007-04-19
> **freebird54 said:**
> How about a power outage while resizing your partition?  The best use of a backup is to make it less likely that problems will happen! (See Murphy's law)

Actually, the partitionner should not fail during a power outage.  It will copy data, then change the pointers for it.  It does this in steps.  You can't perform tasks that overwrite data on-the-fly.  That'S why you can change the endpoint of a partition, but not the start.

---

### Post by bodean on 2007-04-19
> **az said:**
> Are you picking the manual partitioning or just going with using the FREE SPACE?

manual

---

### Post by livingtarget on 2007-04-19
Just quickly: you need to have a partition which contain "/" i.e.: your root partition it needs to be mounted as /, just pick maximum minus your swap partition, _unless_ you want a /home/ partition than give that the most space. Think carefully before proceeding and good luck.

---

### Post by bodean on 2007-04-19
SO I need to have 2 partitions for ubuntu?  A Home and another?

Still unsure what option to select on step 4.

---

### Post by az on 2007-04-19
> **bodean said:**
> manual

I suggest guided partitioning.  It will calculate the needed sizes and create a root and swap partition.  It iwll assign mount points to them.  You need to do this by hand if you pick the manual partitioning option.

---

### Post by bodean on 2007-04-19
> **az said:**
> I suggest guided partitioning.  It will calculate the needed sizes and create a root and swap partition.  It iwll assign mount points to them.  You need to do this by hand if you pick the manual partitioning option.

So Guided - Use largest free space. That shouldnt mess up my windows ntfs partitions?
Thanks for the guidance.

---

### Post by az on 2007-04-19
> **bodean said:**
> SO I need to have 2 partitions for ubuntu?  A Home and another?

Still unsure what option to select on step 4.

A home partiton will just complicate things unneccesarily.  The default guided partitoining scheme will put your home folder in the / (root) partition and you will not run the risk of running out of space.  It is also far less complicated.   

Some find a seperate home partition useful when they want to install multiple versions of a linux operating system on their drive over time.  I find it a lot easier to just back things up the regular way.

---

### Post by freebird54 on 2007-04-19
You should have a list of all the partitions in front of you.  They will have identifiers  ( /media/windows/  OR  swap  OR whatever ).  They should have their number/names - and they should have a checkbox under a heading FORMAT beside each one.

Assuming that you made 2 partitiions for Ubuntu - mark the little one (1 Gb, right) as Swap (if it hasn't already) from the drop down list, and the big one as /  (meaning root).  If you made three, then small=swap, medium=/ and large = /home.

If this isn't clear enough - let us know!  Format should only be ticked on swap and root for sure, and /home if it is there. DO NOT TICK the WINDOWS partitions :)

OK?

---

### Post by INFERNO2K on 2007-04-19
Im in ther same boat as the thread starter. I'll let him be my guinea pig.

Let me know how it goes.

I have the same laptop, same vista, and 15 gigs allocated to a seperate NTFS partition for Ubuntu.

---

### Post by Sengar on 2007-04-19
Are you already running the installer ?

---

### Post by andrewabc on 2007-04-19
I have same problem installing feisty i386 live cd.
I go to manual partition because I have 4 partitions. 1 is windows xp, other is ntfs partition for windows I am unable to merge back to windows partition. Another is windows backup recovery partition. Other is dapper drake which I want to format/install feisty.
When I select the dapper drake partition and select format for it, then hit next on step 4 of 7, I get no root file system defined. please correct this from the partitioning menu.

How do I install feisty over my dapper drake installation?
I don't want to format my windows partition (which is what the guided install looks like it is gonna do)!

EDIT:
In step 4 of 7, I deleted dapper drake partition, then I got free space. Then I created new partition with free space, made it root / ext3

For some reason though it is not recognizing the swap space for dapper drake I had?? It was about 500 mb. gparted live cd isn't booting for me (panicking) so I couldnt see if it was there. It wasn't showing up in disk drives in dapper though.

EDIT:
No idea to make swap logical or not, so i made it logical.

Now installing Feisty!

---

### Post by Sengar on 2007-04-19
No root file system defined means that you have not selected a mount point for your 
root directory ( / ).
In your case that would be the partition you used for dapper drake.
You also need a swap partition which you should actually have ( because of dapper ).


edit: k... i was a bit too late... :-)

---

### Post by bodean on 2007-04-19
Ok.
After numerous headaches with my nvidia graphics card, and ubuntu not loading the gdi, i had a buddy run me through a config to reset the refresh and resolution so I can get into graphical ubuntu.  Didn't think I would have issues after popping out the live cd, but I did.

How do I make sure I have to latest compatible nvidia drivers, and where do I change the display settings in ubuntu?

ALSO: Vista will no longer boot up.  When the boot menu comes up, i select Vista, and it just reboots the computer, and back to the boot loader. Any ideas how to fix this?

---

### Post by az on 2007-04-20
> **bodean said:**
> 
ALSO: Vista will no longer boot up.  When the boot menu comes up, i select Vista, and it just reboots the computer, and back to the boot loader. Any ideas how to fix this?

Apparently, you can use the vista disk to fix the windows bootloader.  But you will then have to reinstall grub to be able to boot Ubuntu.  I don't know what the fix is.

---

### Post by Sengar on 2007-04-20
I don't know which driver is installed by default if you have a nvidia graphics card but 
to install the nvidia driver you can use synaptic ( alt+f2 and type: gksudo synaptic   or use the panel and look for synaptic under administration) and install nvidia-glx or, if you have a graphics card which is newer than a geforce 4 , you can install nvidia-glx-new. 

Another way is to open a terminal (---> applications ) and type:

sudo apt-get install nvidia-glx  or sudo apt-get install nvidia-glx-new 


To enable the driver open a terminal and type   sudo nvidia-glx-config enable

You could also download the driver from nvidia.com and but installing it is a bit more complicated.
You are propably served best with the method described above.

I think that's it....

---

### Post by Milt888 on 2007-04-20
I found this howto to be the simplest  method I've seen.
Check it out.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by Madmoose on 2007-04-20
Okie. This is good to know. I tried to install 6.10 on my laptop the other day, and it had vista. I used the LiveCD to shrink Vista, and then installed Edgy. Everything was working great while I was in Ubuntu, but then I wanted to do something on the Vista Partition and it wouldn't load up. It just froze. 

Is this why? If I follow these instructions: 

> 1. Boot Vista
2. Defrag hard disk
3. Resize the partition IN VISTA, for help, press F1 and type in Partition.
4. Make a partition for Ubuntu, the sizes required are quite small, but 10 Gig is enough. It really depends on the size of your HD. I would make a bigger partition, (20 Gig).
5. Install Ubuntu, in the correct partition, if you install it in the wrong partition, you'll loose everything in that partition. 

Will my laptop behave like it did when I had an XP/ Ubuntu Edgy boot?

Thanks, 

Moose

---

### Post by Milt888 on 2007-04-20
You don't want to resize your Vista partition with the live cd. It must be done with Vista.
Go to start > computer management then click on Disk Management, rt click on your disk and choose shrink volume. You'll have an option of how much to shrink.
Then install ubuntu on the newly created disk space.
Be careful not to bother the Vista volume when you install.
This worked for me.

---

