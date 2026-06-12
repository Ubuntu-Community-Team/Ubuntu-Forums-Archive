---
title: "hanging on &quot;mount root file system&quot;"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by tstockma on 2007-04-16
I am trying to install for the very first time.  I've successfully downloaded the .ISO, verified it with MD5, and examining the top-level folder of the CD shows the proper files & folders.  This is Dapper Drake desktop for i386.

As soon as I boot with it, I get the opening menu.  Usually I pick the "Start Or Install Ubuntu" item...all other items get the same result...

Which is, the "Loading Linux Kernel" pop-up appears...then all activity stops.  Lights show no activity on the CD or the HD, and no noises are present other than the fan.  I've left it sitting for 30 minutes.

Any suggestions?  Thanks for any help!

---

### Post by ramjet_1953 on 2007-04-16
What speed did you burn the iso at?

Anything faster than 4 X for ANY iso is asking for trouble.

Also, if you have used budget media, it often causes problems with iso's.

Regards,
Roger :cool:

---

### Post by tstockma on 2007-04-16
I burned at 16x, so I'll try 4x now...thanks, we'll see how it goes!

---

### Post by tstockma on 2007-04-16
No difference whatsoever.  I'd appreciate any other suggestions...also, is there some optional parms at loading time I can add to the command that cause a log file to be written?

My system is an Athlon 2000+ with 256MB memory, more RAM will be added very soon to this system.

Thanks for any & all help...

---

### Post by tstockma on 2007-04-16
I got no help on this question, but found a "next step" on my own by Googling and searching on other web sites.  Here's how I identified where my specific problems occurs:

When the initial splash screen sppers, I hit "F6" for other advanced options.  This displays the parameters passed to the kernel loader.

Using the backspace key, I deleted the "--", typed in "acpi=OFF". Then used the right-arrow to get to the end of "quiet" on that same line...backspaced to get rid of it...then "BOOT_DEBUG=2|3" (that "|" is the shift-backslash on the keyboard).

Then I hit ENTER.  Lots of text flew by, it's the actual output from the kernel load.  My hang-up is on mounting the root file system.  I'll work with that for a bit, then if I can't resolve it I'll open a new thread with more specific info and a request for help.

---

### Post by tstockma on 2007-04-16
I'm trying to install Dapper Drake, my first Ubuntu install.  I have a new 160 GB HD.  I have written the "Windows 2000 signature" to the drive, formatted an NTFS partition, then deleted that partition.  My LiveCDs are "hanging" during installation.

I'm using the F6 option during the initial splash screen, to load the kernel in a debug mode.  I've gotten rid of the QUIET parm, replacing it with BOOT_DEBUG=2|3, I also added ACPI=OFF.

The load hangs on the "Begin: Mounting root file system... ..." command.

I've done some research, but I'm not finding anything that looks helpful so far...I want to get far enough into the install to create three "ext3" partitions, for the root, swap, & home file systems.

Any & all help appreciated, thanks!

AMD Athlon 2000+, 256MB RAM, 160GB HD

---

### Post by speeves on 2007-04-16
Can you add the errors which you are receiving?  That will help us to pinpoint the issue.  Also, what type of hard drives do you have (IDE, SATA)? Are you using RAID (hardware RAID)?

thanks,

---

### Post by dckrinke on 2007-04-16
I get the same problem on my first try at ubuntu? 

I have tried 10 times, but all tries are the same, I don't get to the installation program. 
I have verified CD, and tried different VGA options. 
When I select VGA, I get a message that the xserver didn't start. 

AMD sempron2800, 1.5Gb ram, sata harddrive, ATI radeon X700. 

I currently have two other versions of Linux loaded and have installed others.  

Does ubuntu have a text console installation program? 
Do I need to specify a boot option for the sata harddrive? 
Is this a bug in version 6.10? 

Thanks, 
dckrinke

---

### Post by tstockma on 2007-04-16
I've been working on this for hours, with no real progress.  I've also found many, many other posts of this same problem...one article with 256 posts, many reporting the same problem...here's what I now know:

There are many causes, most of which cause this problem <i>after the install complete</i> and people are trying to boot into their system.  Many of those probably relate to problems in the Ubuntu (or *nix) hardware configuration files.

That's not what we have here...this current issue is, trying to initially load the Ubuntu kernel from the Install CD into memory for our initial install.

My current status:

- One time earliler today, I got my kernel load to give me a "log" of its progress, and it visibly hung on on mounting the root file system.  All I have on my system are a couple NTFS partitions for my old WIndows 2000 system, with plenty of spare space on one of those drives where I want to place the Ubuntu "ext3" partitions.

- I am giving up on the Desktop ISO image for Dapper Drake Install; instead, I am downloading the "alternative" ISO install image for Dapper, which I believe gives me a better shot at both seeing the "log" output of the kernel load, and also a better shot at successful installation.  That image is at [http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso](http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso) --and I found it very, very difficult to locate that image on Ubuntu's download pages.

SO ...I will post updates on my progress as it comes.  There are two other new users struggling with this that I know of, coollibrarian and dckrinke.  I'll keep you two posted...please also let me know how you are doing!

And any & all help is appreciated.  I'll post again, but it will be several hours or more from now, first that download has to complete, then I have to cut the CD & experiment for a while.  This process is turning out to be much more painful than I had feared, in my worst thoughts about it.

Thanks, all!  Tom

---

### Post by tstockma on 2007-04-16
Thanks for asking, Speeves, and sorry to be so long replying...I've been continuing to experiment all afternoon.

I just added a .sig, so my hardware will be more apparent!  It's an IDE, no RAID.  I have 2 drives, a primary IDE master/slave combo.  The secondary master is the DVD-RW that functions as well as my CD drive.

Earlier today, I got the load command to act like a "verbose" command, I got plenty of text scrolling by to tell me results of the actual commands.  I saw output from several commands that seemed to complete successfully, then that message "Begin: Mounting root file system... ..."  But I haven't been able to get that verbose output again, don't know why.

At the moment, I am downloading the "alternative" ISO install image, I believe I've seen several posts indicating that it's kernel is less problematic, and that it is not a GUI driven install...so it's easier to really know what's happening, and get more verbose output.

Thanks for checking in, that's my latest status, I'll followup again in a few more hours.  

Tom

---

### Post by tstockma on 2007-04-16
OK.  Right now it sucks to be me.

Spent a couple hours downloading the alternate Dapper Drake CD.  Cut the CD.  Executed half-dozen times looking for a better outcome.

All of its options, including "Install In Text Mode", still require it to load the kernel.  "Loading Linux Kernel" pop-up consistently appears, and just as consistently, nothing ever happens after that.

I'm out of ideas, very discouraged.  I'm running a very standard Athlon 2000+ processor, I've upped my RAM to 1GB, I've added a 160 GB IDE drive to this system, and have a new Sony DVD RW.  I've spent hours going thru the forums and documents, hours trying different otions.

All to no avail.

PLEASE will someone with a lot of experience comment?  Something's going on that the LiveCDs aren't properly handling, on what I thought was Ubuntu's most stable release, Dapper.

Thanks for any help.

---

### Post by tstockma on 2007-04-16
bump

---

### Post by stmiller on 2007-04-16
Try this:

[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by tstockma on 2007-04-16
Well, I have my "final answer".

Chuck Dapper Drake.  Go to Edgy, or better yet, wait until Feisty production is released.

Much painful research leads me to conclude there's just no upside to trying to make Dapper work, even though it's officially the release with the longest support offered.

So to anyone who reads this, who is having the same issue on Dapper...the fight to install Dapper ain't worth it.  Edgy reportedly is much better about this issue, and Feisty will be even better.

---

### Post by tstockma on 2007-04-17
I've been struggling with this for about 50 hours out of the last 72..so any help would be much appreciated.

I'm trying to install for the 1st time.  I've tried Dapper-desktop, Dapper-alternate, Edgy-desktop, Feisty-desktop...they all have the same issue.  (Yes, I md5'd most of the downloads, yes I wrote the CDs at the slowest speeds possible from burnatonce.)

As soon as I choose _any_ option from the initial menu that comes up, whether it's the Install, Text-Based Install, Check-CD, F6'd options, I get the initial "loading linux kernel" pop-up...then nothing happens.

I've tried many variations on F6 of deleting "quiet splash", of adding "acpi=off nolapic ide=nodma DEBCONF_DEBUG=5 BOOT_DEBUG=2|3 verbose".  

Thrice I got text flying by, one time hanging on the "loading root file system", two other times it proceeded far enough to give me a command line in linux, but I didn't (still don't) know how to run GRUB or the Install from there.

SO...I've got an Athlon 2000+, 1GB RAM, my primary master IDE drive (80GB) has W2K on it, and I have a new Seagate 160GB drive as the primary slave.

I'd love to find decent documentation on those boot options, I think there's a way for me to get more verbose output from that load.  I'd much appreciate any suggestions or information.  

Thanks!

---

### Post by dckrinke on 2007-04-18
For tstockman from dckrinke: 

OK, I was able to get 6.10 to work. 
The problem was that the installation program selected an xserver (driver) for xorg that didn't work. The installation program 'hung' because it couldn't switch video modes.  

I don't know which video card you have, but the problem sounds similar - the selected xserver probably doesn't work with your card. 

I selected F4 VGA 1024x768x16 and that got me slightly further to the 'no xserver' message. Interestingly, the install program didn't actually 'hang' at this point, it was still running, but it was stopped. 

I switched to a console with CNTL+ALT+F2 (or F1, F3, F4, F5, F6) and typed: 

sudo dpkg-reconfigure xserver-xorg

to reconfigure the xserver. This asks many questions, it's probably best to let as many as possible be preanswered. In my case, the installation program correctly identified my ATI X700 video card and selected the 'ati' xserver. I have no idea why the 'ati' xserver doesn't work with my ATI X700 video card... 

You need to select another xserver that will work with your video card. In my case that was 'vesa'. I answered the questions and typed: 

startx
CNTL+ALT+F7

to start xorg and switch to the graphical display. Then the ubuntu liveCD loaded (took a few minutes) and I was running ubuntu in ram. 

Hope this helps, 
Dennis Krinke

---

