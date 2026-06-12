---
title: "New to this thing called Ubuntu"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by cw1925 on 2006-12-08
Well, I just burnt the ISO to disk and booted with it.  Is there any reason to install the image on the system?  I noticed that I can save to the hard disk, but does it stay when I go back into Windows and then come back again?  Also, here's a screenshot of my desktop:
[img]http://img85.imageshack.us/img85/9356/screenshotqb2.png[/img]
Is there any way to make the pixels smaller to where I can see the whole window, like reduce the screen size (if that makes sense)?  Notice that there is no visible "Forward" button.

---

### Post by Tarvok on 2006-12-08
What graphics card/chipset are you using? I had a Dell 2400 or something with on-board graphics that used regular RAM rather than having it's own, and all I had to do to get the resolution up to where I could actually see the whole install window was get into the BIOS and increase my video memory to 8 MB, rather than the default 1 MB. You might look into that.

As to why to install, it makes it run significantly faster, since it can access programs from hard disk, rather than the CD. However, you mention you are running Windows. Do you already know how to set up dual-boot? If not, I'm sure we can help you with that.

---

### Post by cw1925 on 2006-12-08
> **Tarvok said:**
> What graphics card/chipset are you using? I had a Dell 2400 or something with on-board graphics that used regular RAM rather than having it's own, and all I had to do to get the resolution up to where I could actually see the whole install window was get into the BIOS and increase my video memory to 8 MB, rather than the default 1 MB. You might look into that.I have no earthly idea of knowing that.  Is it in the BIOS?> However, you mention you are running Windows. Do you already know how to set up dual-boot? If not, I'm sure we can help you with that.Nope, don't know how to do that.
BTW, I'm installing it as I type.
Also, I didn't notice any anti-virus proggies working in the background (or even a firewall).  Should I worry about that?  Is there any firewall proggies for Linux?  I'm pretty sure there are.

---

### Post by cw1925 on 2006-12-09
****, it just formatted it. :(

---

### Post by riven0 on 2006-12-09
> **cw1925 said:**
> ****, it just formatted it. :(

Oh boy. The correct way to do it was to partition the harddrive. That way you can dual boot. If you still want windows, my advice is to reformat the entire hd, install windows, and then partition the drive with Ubuntu and install it in the partitioned space. 

As for anti-virus and firewalls. Anti-virus is not really needed, but it is up to you if want to run one. However, the majority of Linux users don't run anti-virus. 

As for a firewall, Ubuntu already has one built in. The only reason you'll need it is if you're running a server.

---

### Post by seijuro on 2006-12-09
> **cw1925 said:**
> Also, I didn't notice any anti-virus proggies working in the background (or even a firewall).  Should I worry about that?  Is there any firewall proggies for Linux?  I'm pretty sure there are.

Antivirus software isn't really needed with Linux, however if you want one you can install ClamAV from the repository. IPtables firewall is installed by default if you want a GUI to help configure it check out Firestarter in the repo.

About the window size I had an issue like that with my wife's computer all it needed was the nvidia driver if you have an nvidia card and have not set up a driver for it you might want to start there.

---

### Post by Famicommie on 2006-12-09
Sorry to hear that you formatted your entire hard drive >.< During the install there's an option which will allow you to set up partitions...

But, now that you have Ubuntu installed, why not try using it exclusively for a week? I only boot into Windows when there's a Windows-exclusive application I want to use that doesn't have a suitable Linux counterpart.

Now, after lurking for quite some time in this community, I've noticed that lots of people like to give newbies the "hard way" to do things. For instance, before you go editing your BIOS settings, why don't you tell us what video card you're using.

I have a Radeon X800 pro, and until I installed the necessary proprietary libraries (libraries are the Linux version of Windows drivers so far as a I can tell) I couldn't get a resolution above 800x600. Once I did the ati-library install dance I went right up to 1600x1200. See, the guys who release Ubuntu only include opensource software and libraries. Nvidia and ATI have proprietary closed source libraries. So, you have to install the stuff manually. Do a google search on how to install the necessary components for your video card!

Yes, there are firewalls available for Ubuntu. One of the things that I love about Linux is that it contains a database of opensource programs, with an application that will automatically install them for you. To download the Firestarter firewall all you have to do is open up the Synaptice Product Manager and tell it that you want it. There are tons of video/mp3 players available through your product managers, programming tools, office tools, etc. All of them accessible through one coherent and organized system.

If you're absolutely new to Linux (I'm pretty new myself), I strongly recommend reading through as many of the help files as you feel comfortable with. They can be accessed by clicking "System->Help->System Documentation". It helped me get tons of information to help me work in Linux as fluently as I do in Windows, with a couple of other neat options. Also, the forums are extremely helpful.

So far as having Windows and Linux on your computer at the same time: when you install Ubuntu it will replace your mbr file with something called the GRUB loader, which will allow you to select which partition/OS of your drive you want to boot into.

---

### Post by cw1925 on 2006-12-09
I just got back from formatting my hard disk.  I'm now using Windows again and noticed I lost Ubuntu.  I still have the CD though, so I'm fortunate for that.  This *had* to happen before finals too, didn't it?  Just my luck.> **riven0 said:**
> Oh boy. The correct way to do it was to partition the harddrive. That way you can dual boot.How do you do that the free way?  I've searched and I saw that Norton PartitionMagic is good, but don't have the money to do it (college, nuff said).> If you still want windows, my advice is to reformat the entire hd, install windows, and then partition the drive with Ubuntu and install it in the partitioned space.Problem:  I have that system recovery option that does it for me in like 20 minutes, so I didn't get the chance to see a partition option.> As for anti-virus and firewalls. Anti-virus is not really needed, but it is up to you if want to run one. However, the majority of Linux users don't run anti-virus.

As for a firewall, Ubuntu already has one built in. The only reason you'll need it is if you're running a server.That is so sweet.
And I just sleep better at night with an antivirus proggy, so I think I'll go with> **seijuro said:**
> ClamAVI'll also check out> Firestarter> About the window size I had an issue like that with my wife's computer all it needed was the nvidia driver if you have an nvidia card and have not set up a driver for it you might want to start there.No, mine is ATI (Radeon Xpress 200, dunno if that helps, dunno if that's good either).> **Famicommie said:**
> But, now that you have Ubuntu installed, why not try using it exclusively for a week? I only boot into Windows when there's a Windows-exclusive application I want to use that doesn't have a suitable Linux counterpart.And wouldn't you just know that I had to boot back into Windows, just to find out I couldn't escape the system recovery?> Now, after lurking for quite some time in this community, I've noticed that lots of people like to give newbies the "hard way" to do things. For instance, before you go editing your BIOS settings, why don't you tell us what video card you're using.I have no idea what my video card is.  Is there any easy way to find out, like in Windows, or something?  There's not a sticker on the front of my computer, so there's no way I can tell unless I take it to the computer store or something.> I have a Radeon X800 proWait, maybe the card is ATI Radeon Xpress 200?> and until I installed the necessary proprietary libraries (libraries are the Linux version of Windows drivers so far as a I can tell) I couldn't get a resolution above 800x600. Once I did the ati-library install dance I went right up to 1600x1200. See, the guys who release Ubuntu only include opensource software and libraries. Nvidia and ATI have proprietary closed source libraries. So, you have to install the stuff manually. Do a google search on how to install the necessary components for your video card!Okay, I'll see where I can get to.> If you're absolutely new to Linux (I'm pretty new myself), I strongly recommend reading through as many of the help files as you feel comfortable with. They can be accessed by clicking "System->Help->System Documentation". It helped me get tons of information to help me work in Linux as fluently as I do in Windows, with a couple of other neat options. Also, the forums are extremely helpful.That's what I love about forums.> So far as having Windows and Linux on your computer at the same time: when you install Ubuntu it will replace your mbr file with something called the GRUB loader, which will allow you to select which partition/OS of your drive you want to boot into.Until I can be absolutely sure I won't format my computer by doing something without researching first, I won't install any version of Linux.  I'll just use it from the CD.

---

### Post by Famicommie on 2006-12-09
> How do you do that the free way? I've searched and I saw that Norton PartitionMagic is good, but don't have the money to do it (college, nuff said).

IIRC the installation of Ubuntu gives you the option to set up a partition. No need to use any program in Windows to do it. When you go to install Ubuntu it should give you a dialogue asking whether or not you want to make a partition. I'm not sure how you would go about it, since I simply used my secondary HD

> Wait, maybe the card is ATI Radeon Xpress 200?

That sounds like it :D Try reading this thread:

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

> 
Until I can be absolutely sure I won't format my computer by doing something without researching first, I won't install any version of Linux. I'll just use it from the CD.

I wish I could help more, but it's been a while since I installed and I don't have a Live CD handy. With all of that said, I would suggest going through the install dialogues up to the point where you have to actually install. That should give you an idea of what options are available in the process.

Ubuntu is wicked sexy when it's actually installed, as it runs much faster.

---

### Post by riven0 on 2006-12-09
> **cw1925 said:**
> How do you do that the free way?  I've searched and I saw that Norton PartitionMagic is good, but don't have the money to do it (college, nuff said).
Actually, Ubuntu comes with a built in partitioner. The installer should give you the option to either completely erase your hd, resize it, or custom partition it. 

> No, mine is ATI (Radeon Xpress 200, dunno if that helps, dunno if that's good either).And wouldn't you just know that I had to boot back into Windows, just to find out I couldn't escape the system recovery?I have no idea what my video card is.  Is there any easy way to find out, like in Windows, or something?[QUOTE]
In windows the way to do it is click Start >> Run >> type in 'dxdiag' with the quotes and it should bring up a box with your hardware info.


[QUOTE] I won't format my computer by doing something without researching first, I won't install any version of Linux.  I'll just use it from the CD.

Sometimes you gotta take the plunge. When I first tried Ubuntu I partitioned it with Windows, so I was able to dual-boot between them. After a week, though, I realized I was no longer using windows and I just wiped it out. Your results may vary ;) 

Tell us if you need help partitioning.

---

### Post by riven0 on 2006-12-09
> **Famicommie said:**
> 
Ubuntu is wicked sexy when it's actually installed, as it runs much faster.

Gotta agree. You're not going to get the full power of Ubuntu if you don't install. At least try a dual-boot.

---

### Post by cw1925 on 2006-12-09
> **riven0 said:**
> Actually, Ubuntu comes with a built in partitioner. The installer should give you the option to either completely erase your hd, resize it, or custom partition it.I did that, didn't know which one to install.  Do you think I should go ahead and boot up from Ubuntu and let you guys talk me through it?> In windows the way to do it is click Start >> Run >> type in 'dxdiag' with the quotes and it should bring up a box with your hardware info.I was correct in the ATI graphix card anyways.> Sometimes you gotta take the plunge. When I first tried Ubuntu I partitioned it with Windows, so I was able to dual-boot between them. After a week, though, I realized I was no longer using windows and I just wiped it out. Your results may vary ;) 

Tell us if you need help partitioning.I'm not planning on wiping out Windows, because I never know when I'll need it.  School demands Windows.

I've booted into Ubuntu.  It hit the install icon.  First, before I do anything other than getting this far:
[img]http://img82.imageshack.us/img82/6599/screenshotuv0.png[/img]
do I *absolutely* need to install Linux onto the system?  Does it give me any extra features?  I'm perfectly fine with running this software off of the CD, because I've been working with Portable Apps for Windows for a year, and I know that while it may be slower access time to open and close a program on a flash drive, it's tolerable.  Do I get to save settings to the hard drive without worrying about it being wiped out (didn't get to test it out last time because I had the little incident trying to access windows)?

Another question:  is there any way to transfer my Windows version of Firefox's bookmarks over to my Linux version?

---

### Post by houstonbofh on 2006-12-09
> **cw1925 said:**
> I did that, didn't know which one to install.  Do you think I should go ahead and boot up from Ubuntu and let you guys talk me through it?I was correct in the ATI graphix card anyways.I'm not planning on wiping out Windows, because I never know when I'll need it.  School demands Windows.

By the way...  Why are you doing this durring finals? <mother-voice>You should be studying!</mother-voice>

That said, you can do this, but it will take some time.
> **cw1925 said:**
> I've booted into Ubuntu.  It hit the install icon.  First, before I do anything other than getting this far:
[img]http://img82.imageshack.us/img82/6599/screenshotuv0.png[/img]
do I *absolutely* need to install Linux onto the system?  Does it give me any extra features?  I'm perfectly fine with running this software off of the CD, because I've been working with Portable Apps for Windows for a year, and I know that while it may be slower access time to open and close a program on a flash drive, it's tolerable.  Do I get to save settings to the hard drive without worrying about it being wiped out (didn't get to test it out last time because I had the little incident trying to access windows)?
If you want to save anything, install programs, or fix your graphics driver, Yes.  You are on the right track.  Repartition and install.  Then from the GRUB boot menu, you can choose Ubuntu or Windows.  I have my systems duel boot.  And I am never in Windows.
> **cw1925 said:**
> Another question:  is there any way to transfer my Windows version of Firefox's bookmarks over to my Linux version?
Yes, if you install.  Once you do, you can install NTFS support and read and write with your Windows partition.  There is also a Linux file system driver for Windows.  And while we are on the subject...  Ubuntu has a good firewall.  You do not need a virus scanner.  No Windows virus can run in Linux.  Just save yourself the trouble for now.

Last thing...  You will need to go into Windows and look up all the things you don't seem to want to remember.  You will need to know your graphics card.  Model and size!  You may also need to know your network card.

---

### Post by cw1925 on 2006-12-09
> **houstonbofh said:**
> By the way...  Why are you doing this durring finals? <mother-voice>You should be studying!</mother-voice>It's next week, and today is Friday, so I'm enjoying the calm before the storm of studying.> If you want to save anything, install programs, or fix your graphics driver, Yes.  You are on the right track.  Repartition and install.  Then from the GRUB boot menu, you can choose Ubuntu or Windows.  I have my systems duel boot.  And I am never in Windows.Cool, didn't think it was possible.> Yes, if you install.  Once you do, you can install NTFS support and read and write with your Windows partition.  There is also a Linux file system driver for Windows.  And while we are on the subject...  Ubuntu has a good firewall.  You do not need a virus scanner.  No Windows virus can run in Linux.  Just save yourself the trouble for now.Just for my thirst for knowledge, what is it about Linux that makes it harder for viruses to do damage?  Different setup, or what?> Last thing...  You will need to go into Windows and look up all the things you don't seem to want to remember.  You will need to know your graphics card.  Model and size!  You may also need to know your network card.First thing after finals.  I'll try and set it up now, and go hard core during the month off we get.

---

### Post by 3rdalbum on 2006-12-09
I would definately recommend installing Ubuntu. Running the Live CD is like a little shot glass of lemonade - running a fully-installed system is like a full bottle of whiskey!

Your changes on the live CD aren't saved onto hard disk, so the next time you boot up the Live CD your menubar will be at the top again, all the settings will be back to normal and any files you have saved into the home directory will be gone. Any programs you install will disappear after reboot.

When you decide to install Ubuntu for good :-)  make sure you use Windows to defragment your hard disk first.

When you get to that screen in the installer, drag the slider so that it shows a good size for the new Ubuntu partition. (looks like you can spare some room - I've got 30 gigabytes on mine, you'll probably want 20 gigs)

---

### Post by compwiz18 on 2006-12-09
> Just for my thirst for knowledge, what is it about Linux that makes it harder for viruses to do damage? Different setup, or what?

First reason: You may have noticed that whenever you try to run an adminstrative program, it asks for your password.  This means that if a virus tries to wipe your drive, its gonna need that password (which it won't have ;))

Second reason: Only about 1% of the people in the world run Linux - why spend time devloping viruses? (please don't flame me for this - you know it's true)  Although, on the other hand, Linux is run on a higher percentage of servers then Windows, yet more viruses are written for Windows servers.  Therefore, Linux is more secure.

Third reason: The virus writers use Linux.

Fourth reason: You should (in theory, anyway) never have to install programs from unknown sources - so less chance of accidentally picking up a virus.

Fifth reason: All software is avaliable for anyone to edit - this means that anyone who finds a hole can fix it, and it will be included in the next release - unlike Microsoft, where they have to go through the whole deal of finding, fixing, testing.  Linux does this, but much faster.

---

### Post by cw1925 on 2006-12-09
> **compwiz18 said:**
> First reason: You may have noticed that whenever you try to run an adminstrative program, it asks for your password.  This means that if a virus tries to wipe your drive, its gonna need that password (which it won't have ;))Something that Microsoft ripped off of Linux with Vista (but it's for a good purpose).> Second reason: Only about 1% of the people in the world run Linux - why spend time devloping viruses? (please don't flame me for this - you know it's true)  Although, on the other hand, Linux is run on a higher percentage of servers then Windows, yet more viruses are written for Windows servers.  Therefore, Linux is more secure.I haven't had a flame war in over 3 years, no need to start now.  It's childish and it solves nothing.> Third reason: The virus writers use Linux.LMAO!> Fifth reason: All software is avaliable for anyone to edit - this means that anyone who finds a hole can fix it, and it will be included in the next release - unlike Microsoft, where they have to go through the whole deal of finding, fixing, testing.  Linux does this, but much faster.If I had the time, patience, skill and/or ability to edit the software, I'd do it a couple of Windows proggies, but alas, I'm not, and I frankly don't care to edit software.
I'll have more questions tomorrow, or in a couple of weeks.  For now, I'm off to bed.

---

### Post by cw1925 on 2006-12-09
OK, here's another question.  Since I have yet to install Microsoft updates since this last format, should I go ahead and go with Microsoft updates?  Will that affect Linux in any way?

---

### Post by riven0 on 2006-12-09
> **cw1925 said:**
> OK, here's another question.  Since I have yet to install Microsoft updates since this last format, should I go ahead and go with Microsoft updates?  Will that affect Linux in any way?

I don't see why. When I first tried Ubuntu, I had winxp, service pack 2, with all the updates installed and Ubuntu installed fine. Just make sure to de-fragment the hard drive before partitioning.

---

### Post by cw1925 on 2006-12-09
Will do.

---

### Post by sailor2001 on 2006-12-09
to audit your windows so you know make, serial etc of everything on the windows hard drive download belarc.com

---

### Post by seijuro on 2006-12-09
And yes the ATI needs you to install the dirvers yourself to get your full screen res. I think someone posted a link to a walkthrough earlier if not just post that you need directions for installing the ATI drivers when you get Ubuntu installed.

---

### Post by cw1925 on 2006-12-10
Is there a Linux download site?  You know like where you can only download Linux software?  There are a million Windows software download sites, but I was wondering if there were any focused solely on Linux.

---

### Post by riven0 on 2006-12-10
Some good sites:

For Ubuntu downloads: [Ubuntu.com]("http://www.ubuntu.com/")

For *all* the Linux distros: [DistroWatch]("http://distrowatch.com/")

Linux Apps: [Linux App Finder]("http://linuxappfinder.com/")

Anything else about Linux: [Google Linux]("http://www.google.com/linux")

---

### Post by houstonbofh on 2006-12-10
> **cw1925 said:**
> Is there a Linux download site?  You know like where you can only download Linux software?  There are a million Windows software download sites, but I was wondering if there were any focused solely on Linux.
Built into Ubuntu is a program called Synaptic.  It is several thousand programs ready to install.  Try there before you go to a website.  Installs by hand are never as easy as Synaptic.

---

### Post by cw1925 on 2006-12-10
> **houstonbofh said:**
> Built into Ubuntu is a program called Synaptic.  It is several thousand programs ready to install.  Try there before you go to a website.  Installs by hand are never as easy as Synaptic.That is wicked.

---

### Post by lyceum on 2006-12-10
A few things to add to all of the excellent advice you have been given.

1. You install Windows first, because it will hide Ubuntu if you don't. Ubuntu creates this box that lets you pick which OS you want to use.

2. Although Linux does not get viruses it can be a carrier. If someone sends you an e-mail with an attachment and the attachment has a virus, and you move the file with the virus to your (or any other) Windows PC, the Windows PC will get the bug. That is why there are different Linux anti-virus software out there.

That said, Enjoy!

---

### Post by cw1925 on 2006-12-14
Finals are over, and I am about to install Linux.  Am I on the right track to "building" a duel boot system with
[img]http://img82.imageshack.us/img82/6599/screenshotuv0.png[/img]
?
I don't want to mess up my system.
I'll be on here for the rest of the night, so I'm not going anywhere.  I would like to do this the right way, if you know what I mean. :)

---

### Post by cw1925 on 2006-12-14
[LEFT]Is this the screen and formating criterior I want?

[img]http://img215.imageshack.us/img215/1152/screenshotry1.png[/img]
[/LEFT]

---

### Post by JayTee on 2006-12-14
you're on the right track. just make sure you run Disk Defragmenter in Windows FIRST (and you may need to run it more than once) until the graphical display of your hard drive has alot of white space at the end of the drive (right side of drive bar display). Once you've got that done it should be safe to install Ubuntu. Reboot with the LiveCd and get back to the Gparted partition manager utility (the screen shot you posted) and then select the resize option like in your screen shot and continue from there. You should end up with a good install of Ubuntu wit a dual boot menu option in the GRUB bootloader menu. Boot into Ubuntu and play around with it and set some of your preferences then reboot and choose the Windows boot option to make sure Windows still boots properly. If it does you're pretty much good to go except for the fun of choosing what other linux apps to install. The amount of choice is staggering and it doesn't cost anything above what you pay to connect to the internet to your ISP. If you run into any snags just come back to this thread and post your issues and I and others will be happy to help you through them. Enjoy! And welcome to the Ubuntu Community.

---

### Post by cw1925 on 2006-12-14
[LEFT]Thanks.  It worked! :KS

Now, it says I have 47 updates.  I know from Windows experience that not all the updates to an OS are safe.  Is it safe to update all of them?

Oh, and I feel very welcome.
[/LEFT]

---

### Post by dorcssa on 2006-12-14
It's not windows, so it's safe. :mrgreen:

---

### Post by cw1925 on 2006-12-14
New question:  how do I install Beryl?  Or should I worry about installing everything first?  Is there any requirements?

---

### Post by cw1925 on 2006-12-14
[LEFT]Also, should I go ahead and defragment again?
[/LEFT]

---

### Post by pizzutz on 2006-12-14
> New question: how do I install Beryl? Or should I worry about installing everything first? Is there any requirements?

You will want to get your graphic card drivers installed first.  here are some helpful sites

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)


> Also, should I go ahead and defragment again?


if you did it before you installed you are fine.  your OSes are on separate partitions and should not interfere with each other.

---

### Post by cw1925 on 2006-12-14
I didn't get anything useful or down to earth kinda stuff out of that first URL.  But, does> **pizzutz said:**
> [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)automatically install the latest drivers?

ADDED:  Okay, I did everything up to this point:
[img]http://img186.imageshack.us/img186/9514/screenshot1ot0.png[/img]
I didn't find Driver "ati" or Driver "radeon"

---

### Post by pizzutz on 2006-12-14
Actually those were more beryl related.  I'd assumed you gotten your Vid drivers installed already.  I use NVidia not ATI, so I can't tell you the specific packages you need (I'm on my work computer atm)  I'm sure someone here can tell you.

---

### Post by cw1925 on 2006-12-14
[LEFT]No, I didn't get my drivers installed.  They just told me to go to the sites.  Will that site's instructions automatically update my drivers?
[/LEFT]

---

### Post by cw1925 on 2006-12-14
Hmmm... my screen is smaller thanks to the tutorial, but is that all it does?  I thought it would do what those vids over at YouTube do?  Should I try Metisse?

---

### Post by LookTJ on 2006-12-14
> **cw1925 said:**
> Hmmm... my screen is smaller thanks to the tutorial, but is that all it does?  I thought it would do what those vids over at YouTube do?  Should I try Metisse?

To play YouTube, You have to install flash

```
sudo aptitude install flashplugin-nonfree
```

To update flash to latest version for Linux

Download:

```
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz
```

Unpack

```
tar xvzf FP9_plugin_beta_112006.tar.gz
```

Copy the file(flash libaray file)

```
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 

```

Enjoy!

EDIT: You can find most help for installing needed programs [here](http://ubuntuguide.org)

Enjoy Ubuntu Linux!

---

### Post by cw1925 on 2006-12-14
[LEFT]I didn't need help with playing YouTube vids, I can play them just fine.  It's actually using Beryl, that I'm having probs with.  I followed all those instructions with the exception to signing into XGL.  It says to> Note you need to change the XX in the first entry to match your current keymap, uk for united kingdom, dk for denmark etc etc.But I live in the US.  I tried both "xmodmap /usr/share/xmodmap/xmodmap.uk" and "xmodmap /usr/share/xmodmap/xmodmap.us", but neither worked.  It just showed a screen where I had to sign in to a server or something.  It showed no servers (I think that's what they are), and had the selection to add one, but the instructions didn't tell me what to add.  So I just signed in regularly and I noticed that it didn't do anything.  What is the next step after> Second run[INDENT]sudo chmod +x /usr/bin/startxgl
sudo gedit /usr/share/xsessions/xgl.desktop
[/INDENT]And copy the following contens into this file.

*[Desktop Entry]*
*Encoding=UTF-8*
*Name=Xgl*
*Comment=Start an Xgl Session*
*Exec=/usr/bin/startxgl*
*Icon=*
*Type=Application*[I]?  I'm using this site of course:  [http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)


[/I]Edit:  I also tried logging in to the XGL session, and it just gave me a whole mess of errors.  What am I doing wrong?
[/LEFT]

---

### Post by pizzutz on 2006-12-14
Sounds like you didn't get your graphic drivers installed correctally.  can you post your /etc/X11/xorg.conf  file?

---

### Post by cw1925 on 2006-12-14
> **pizzutz said:**
> Sounds like you didn't get your graphic drivers installed correctally.  can you post your /etc/X11/xorg.conf  file?```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath     "/usr/share/X11/fonts/misc"
    FontPath     "/usr/share/X11/fonts/cyrillic"
    FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/Type1"
    FontPath     "/usr/share/X11/fonts/100dpi"
    FontPath     "/usr/share/X11/fonts/75dpi"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "vbe"
EndSection

Section "Extensions"
    Option        "Composite" "0"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
    Option        "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "SyncMaster"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
    Monitor    "SyncMaster"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection


```

---

### Post by riven0 on 2006-12-14
When you type in the terminal:

>  fglrxinfo

What does it bring back?

---

### Post by cw1925 on 2006-12-14
> **riven0 said:**
> When you type in the terminal:> fglrxinfoWhat does it bring back?Just a quick black screen, then it goes away.

---

### Post by riven0 on 2006-12-14
> **cw1925 said:**
> Just a quick black screen, then it goes away.

:confused: That' weird. Alright, when you do:

> glxinfo | grep direct

Does it return **direct rendering: Yes** ?

And are you getting good a good framerate when you do:

> glxgears

---

### Post by cw1925 on 2006-12-15
> **riven0 said:**
> :confused: That' weird. Alright, when you do:> glxinfo | grep directDoes it return **direct rendering: Yes** ?It just does a black screen, and then goes away.  :mad:> And are you getting good a good framerate when you do:[quote]glxgears[/quote]Yes, that works very smoothly.

---

### Post by cw1925 on 2006-12-15
[LEFT]Well, I've got to keep trying, right?  What about Metisse?  Any good straight-forwards guides for that?
[/LEFT]

---

### Post by riven0 on 2006-12-15
> **cw1925 said:**
> [LEFT]Well, I've got to keep trying, right?  What about Metisse?  Any good straight-forwards guides for that?
[/LEFT]

I've seen a youtube video of Metisse, but I've never installed it. You can try it, of course, but I don't know about the success rate on it. 
But first, did you follow [this howto]("http://www.ubuntuforums.org/showthread.php?t=204910&highlight=install+fglrx") on installing the ati drivers? Of course, you'll have to do beryl with xgl if you install the official drivers, but you may have better luck.

---

### Post by cw1925 on 2006-12-15
[LEFT]I think I've done something majorly wrong.  I tried to do those things, but no matter what I type in, the terminal suddenly closes on me.  WTF is going on?

Edit:  Wait, I just disabled the beryl tray icon, and it's working.  I'll update when I need help.

Edit again:  It still abruptly closes on me and the> [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run]("https://www2.ati.com/drivers/linux/ati-driver-installer-8.26.18-x86.run")file doesn't work.  No matter what I try, it won't work. [/LEFT]

---

### Post by TooRight on 2006-12-15
Your ati driver is not set up properly yet hon


I posted some instructions here:
[http://ubuntuforums.org/showthread.php?t=318894](http://ubuntuforums.org/showthread.php?t=318894)

Also, since you have it half installed already when it comes to the "sudo aticonfig --initial" line, then make it "sudo aticonfig --force --initial" instead.

As well, be sure to add 
```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
 to the end of your /etc/X11/xorg.conf file


After you reboot, run "fglrxinfo" to check that it worked.

---

### Post by David Floyd on 2006-12-15
> **lyceum said:**
> A few things to add to all of the excellent advice you have been given.

1. You install Windows first, because it will hide Ubuntu if you don't. Ubuntu creates this box that lets you pick which OS you want to use.



Does this work if I already dual boot?  i.e. I have dual boot into W2K and XPPro - will that facility still be there after I've installed ubuntu

David 
(Very new - 1st post)

---

### Post by cw1925 on 2006-12-15
> **TooRight said:**
> Your ati driver is not set up properly yet hon


I posted some instructions here:
[http://ubuntuforums.org/showthread.php?t=318894](http://ubuntuforums.org/showthread.php?t=318894)I followed those instructions perfectly, and it led me to forcefully shut down my computer. :mad:> Also, since you have it half installed already when it comes to the "sudo aticonfig --initial" line, then make it "sudo aticonfig --force --initial" instead.

As well, be sure to add 
```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection
``` to the end of your /etc/X11/xorg.conf file


After you reboot, run "fglrxinfo" to check that it worked.I don't even want to try Linux anymore.  It's too confusing and it only breaks my computer.  Is there a way to delete Beryl completly?  I just want it off there.

---

### Post by riven0 on 2006-12-15
> **cw1925 said:**
> I followed those instructions perfectly, and it led me to forcefully shut down my computer. :mad:I don't even want to try Linux anymore.  It's too confusing and it only breaks my computer.  Is there a way to delete Beryl completly?  I just want it off there.

Well, if you're not going to use Linux anymore, then don't worry about uninstalling beryl. Just boot back up to windows, use [one of the tools here]("http://www.thefreecountry.com/utilities/partitioneditors.shtml") to delete Ubuntu and resize the partition. No need to make it harder than it has to be.


Good luck!:KS

---

### Post by cw1925 on 2006-12-15
[LEFT]I think I'll put it off until next week.  It's just so confusing and no one I know runs Linux, so there goes any real-life help.
[/LEFT]

---

### Post by mdsmedia on 2006-12-15
My first piece of advice is to take your time. Don't try to jump in too deep too early.

Ask for help on here but read up a bit first before jumping into something.

You were asking for help on Beryl and were told to get your ATI drivers working first, but it seems you jumped into Beryl before getting your ATI drivers.

Read the advice that's given. Don't take everything you read as gospel. But if a couple of people tell you you should get your ATI drivers first you can probably take that seriously.

As for no real life help, I don't know anyone who uses Linux either, but I do know there is plenty of help on here and on the web.

---

### Post by riven0 on 2006-12-15
> **cw1925 said:**
> [LEFT]I think I'll put it off until next week.  It's just so confusing and no one I know runs Linux, so there goes any real-life help.
[/LEFT]

Alright, then. We'll be glad to have you back. :) When you come back, though, you may want to first [look at this page]("http://www.ubuntuforums.org/showthread.php?t=318889"). It may help. 

And don't worry. I didn't know anyone who used Linux either, but with a little patience I got it up and running. If I can do it, anyone can. :mrgreen:

---

### Post by cw1925 on 2006-12-19
[LEFT]New problem:  I was forced once again to format Windows.  But, I've noticed that 150 GBs are missing from Windows.  I guess this means that Linux is still on my machine, just hidden.  How do I delete those partitions (I believe there are 2 due to the first install as well), and get back the space that I need?
Someone posted this link:  [http://www.thefreecountry.com/utilities/partitioneditors.shtml](http://www.thefreecountry.com/utilities/partitioneditors.shtml)
Will that help?
[/LEFT]

---

### Post by macogw on 2006-12-19
Boot from the Ubuntu live cd and go to System, Administration, GParted.  You can edit the partition table there.

---

### Post by cw1925 on 2006-12-19
[LEFT]What do I do then?  Format it to NTFS?  Here's a screenshot of the table.

[IMG]http://img237.imageshack.us/img237/9991/screenshotau9.png[/IMG]

I'm guessing I just format the ones that says Linux swap?  Or....?
[/LEFT]

---

### Post by macogw on 2006-12-19
Anything ext3 or linux-swap is a Linux thing.  Just delete those, then double click on the NTFS one and pull the right-side bar all the way to the right as far as it goes so it'll take up the remaining free space.

---

### Post by cw1925 on 2006-12-19
> **macogw said:**
> Anything ext3 or linux-swap is a Linux thing.  Just delete those, then double click on the NTFS one and pull the right-side bar all the way to the right as far as it goes so it'll take up the remaining free space.Did that, still missing about 85 GB.  The bar is at the max.

---

### Post by macogw on 2006-12-19
Hmm, go back into GParted and post another screenshot.  There has to be something taking up that space, and the Window Restore Partition is only about 6 GB.  Formatting space adds another gig or so....There's 70-something unaccounted for.

---

### Post by cw1925 on 2006-12-19
[IMG]http://img224.imageshack.us/img224/7775/screenshotxs2.png[/IMG]

I believe it's that unallacated space.  I don't see an option to format it.  I'm wanting to ultimately reinstall Linux, so will Linux take up that part?

---

### Post by macogw on 2006-12-19
Oh, you have to delete the extended one where the swap was contained.  THEN yank the NTFS one further right.

---

### Post by houstonbofh on 2006-12-19
> **cw1925 said:**
> [IMG]http://img224.imageshack.us/img224/7775/screenshotxs2.png[/IMG]

I believe it's that unallacated space.  I don't see an option to format it.  I'm wanting to ultimately reinstall Linux, so will Linux take up that part?
That extended partition can be deleted.  If you want to leave it empty, go ahead, but do delete the extended partition.  Once deleted, you can expand NTFS, and just shrink it later when you need to...

---

### Post by cw1925 on 2006-12-19
Thanks a million.

---

### Post by cw1925 on 2006-12-22
Okay, I'm going out on a limb here, but is it possible to install Fedora on my machine too?  Or should I lay off of it?  Would I need to install anything first, or will the process be similar to Ubuntu?

---

### Post by houstonbofh on 2006-12-22
Yes you can.  You can even use the same swap and /home partitions if you set it up correctly. (swap any time.  /home if you settings can be the same.)  But you need a separate / partition for each *nix you have.  And you will have lots of choices in GRUB.

---

### Post by cw1925 on 2006-12-22
> **houstonbofh said:**
> Yes you can.  You can even use the same swap and /home partitions if you set it up correctly. (swap any time.  /home if you settings can be the same.)  But you need a separate / partition for each *nix you have.  And you will have lots of choices in GRUB.Oh, no no no.  This isn't good at all.  I did that, and well, I'm so stupid, it's not funny.  I'm not able to get system recovery to work.  I think it might have deleted that partition or something.  Is there any way of getting that back at all.  I really need to restore Windows.  Not only do I not have Windows, I also don't have Fedora or Ubuntu.  I'm only writing this on the Ubuntu Live CD.  I can just install Ubuntu, but I also really need Windows.  Is there any way at all of getting that partition back?  The Grub menu only shows Fedora command line, that's it.

---

### Post by houstonbofh on 2006-12-22
Take a screen shot of gpartd and post it.  If you overwrote your Windows partition, it is gone.  (Without expensive data recovery)  If you just broke your bootloader, we can fix that.  Show us the screen shot, and tell us what OSs you attempted to install.

---

### Post by cw1925 on 2006-12-22
> **houstonbofh said:**
> Take a screen shot of gpartd and post it.  If you overwrote your Windows partition, it is gone.  (Without expensive data recovery)  If you just broke your bootloader, we can fix that.  Show us the screen shot, and tell us what OSs you attempted to install.Oh, it's gone for sure.  I don't even have gpartd anymore. :(  I just installed Fedora, and it was gone.  Could it be a bug or what?  I'm very sad about this, because I had a lot of encrypted documents on there that I can't access anymore.  And school's out, and I'm in an apartment in a town with no libraries.  Plus school is coming up, so that's even worse.  So, I can't provide a screenshot.  I may just have to save up for another computer, or just save up for Vista.  Here's to hoping Vista doesn't mess up my computer too.  I heard Wine does an excellent job handling Windows stuff, is that true?  I installed it from my repo, but I don't know how to use it.  Is there a short tutorial or something?

---

### Post by riven0 on 2006-12-22
> **cw1925 said:**
> Oh, it's gone for sure.  I don't even have gpartd anymore. :(  I just installed Fedora, and it was gone.  Could it be a bug or what?  I'm very sad about this, because I had a lot of encrypted documents on there that I can't access anymore.  And school's out, and I'm in an apartment in a town with no libraries.  Plus school is coming up, so that's even worse.  So, I can't provide a screenshot.  I may just have to save up for another computer, or just save up for Vista.  Here's to hoping Vista doesn't mess up my computer too.  I heard Wine does an excellent job handling Windows stuff, is that true?  I installed it from my repo, but I don't know how to use it.  Is there a short tutorial or something?

Now that's bad. :( There should have been a partitioner with Fedora. Did you use it to partition the hd? And what about a spare Windows cd? Did your comp come with any backup cd's? I believe you may be able to install windows with those. 

As for Wine, it really depends on what apps you want to install. Check out the [AppDB]("http://appdb.winehq.org/") for more info.

However, I consider VMWare server a better solution. I have some relatives who use VMWare server to access XP within Linux and that works great. I really recommend that over using Wine. But just be aware that you won't be able to play some games if you go with VMWare, since it's running over Linux.

---

### Post by cw1925 on 2006-12-22
> **riven0 said:**
> Now that's bad. :( There should have been a partitioner with Fedora. Did you use it to partition the hd?Nope.> And what about a spare Windows cd? Did your comp come with any backup cd's?It's fairly new with an automatic system recovery (one of those ones where when you first boot your computer you have to hit an F10 key)> I believe you may be able to install windows with those.If only it were that convenient.  I may just have to save up for Vista Home Premium, although I've got a month and a week until that comes out.  Hopefully mom will pitch in half.  I hate Fedora now (I still <3 my Ubuntu :))> As for Wine, it really depends on what apps you want to install. Check out the [AppDB]("http://appdb.winehq.org/") for more info.I have some proggies I have payed money to get for Windows that have a year-long free update service, and I don't want them to go to waste, if you know what I mean.> However, I consider VMWare server a better solution. I have some relatives who use VMWare server to access XP within Linux and that works great. I really recommend that over using Wine. But just be aware that you won't be able to play some games if you go with VMWare, since it's running over Linux.Is it free?  I can't spare much more cash now.

---

### Post by riven0 on 2006-12-22
> **cw1925 said:**
> It's fairly new with an automatic system recovery (one of those ones where when you first boot your computer you have to hit an F10 key)


Then I suppose it's gone for good. :( But at least you have the Ubuntu livecd for backup. :KS 

> Is it free?  I can't spare much more cash now.

Yep! [Here is a good howto]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+with+windowsxp") to get set up and running. It's incredibly easy... except that you don't have an xp cd. Still, it's something to keep in mind until you figure out what to do.

Keep us updated.

---

### Post by cw1925 on 2006-12-23
[LEFT]Okay.  My mom just talked to the Geek Squad, which in my experience, knows little about computers.  They're just idiots IMO.  They said that Windows XP is located in the D drive.  Now my questions are:  how do I access the D drive in order to get back to installing XP?  Is that even possible now?  Does Linux touch the D drive?  Since it completely disallows me to use System Recovery, I'm thinking it's gone for good.  Is that right?
The one thing they did tell me, which confirms my belief they are idiots in uniforms, is that I couldn't have more than one operating system on my computer, which is a complete lie.
If all else fails, I will just have to wait until Jan 30 to get Vista, which is the ultimatum here.
Edit:  BTW, if you are on the Geek Squad, please don't be offended, I'm talking in general, not towards anyone in particular.
[/LEFT]

---

### Post by cw1925 on 2006-12-24
[LEFT]I have WINE installed, and I need Word, because school demands Word.  I have tried OpenOffice, and I like it, but the database has different rulers and stuff from Word, and some of the projects demand a certain amount of width.  I put the Mic. Office CD in, and it wants to install in the C:/ directory, but I don't have one.  Is it possible to install Mic. Office on Linux?  And where should I install it?
[/LEFT]

---

### Post by houstonbofh on 2006-12-27
Boot the ubuntu Live CD, and run Gpartd and post a screenshot from within the live cd.  I bet your "D: Drive" is gone, if fedora wiped your entire system.  Nice of them...

And you can get some versions of Office to run in Wine.  Check the APDP listed above.  You may need to buy Crossover Office, which is a tweaked version of Wine specifically for running Office.  Also, if you decide to run a VM, you may want to look at Win98SE as opposed to XP.  It can run in much less resources.  (But it won't run Office 2003)

---

### Post by macogw on 2006-12-27
> **cw1925 said:**
> [LEFT]I have WINE installed, and I need Word, because school demands Word.  I have tried OpenOffice, and I like it, but the database has different rulers and stuff from Word, and some of the projects demand a certain amount of width.  I put the Mic. Office CD in, and it wants to install in the C:/ directory, but I don't have one.  Is it possible to install Mic. Office on Linux?  And where should I install it?
[/LEFT]

~/.wine/drive_c is C:\

---

### Post by cw1925 on 2006-12-27
Also,> **houstonbofh said:**
> Boot the ubuntu Live CD, and run Gpartd and post a screenshot from within the live cd.  I bet your "D: Drive" is gone, if fedora wiped your entire system.  Nice of them...Yeah, nice of them. :mad:  Anyways, here's my screenshot:
[[IMG]http://img299.imageshack.us/img299/7756/screenshotmw7.th.png[/IMG]](http://img299.imageshack.us/my.php?image=screenshotmw7.png)> And you can get some versions of Office to run in Wine.  Check the APDP listed above.  You may need to buy Crossover Office, which is a tweaked version of Wine specifically for running Office.  Also, if you decide to run a VM, you may want to look at Win98SE as opposed to XP.  It can run in much less resources.  (But it won't run Office 2003)I installed it to> **macogw said:**
> ~/.wine/drive_c is C:\but to no avail.  I'll keep trying.  If all else, I'll just my hallmate's computers.  A couple of more questions:  if I obtain an XP CD from my mom, I just need my own key code, right?  The key code sticker is on my machine.
Also, how do I read and write to an external hard drive and pen drive?  Is there a "safely remove hardware" equivalent for external drives?
Finally, screw Vista.  I've been reading all about the DRM issues, and I don't want to go into those waters.  That's a nightmare waiting to happen.

---

### Post by riven0 on 2006-12-28
> **cw1925 said:**
> I installed it to but to no avail.  I'll keep trying.  If all else, I'll just my hallmate's computers.  

Yeah, wine is a hit and miss. Some programs will work, some not. Some you've got to work on for days to get it working. I've went that route, :rolleyes: , it's jut easier to do vmware.

> A couple of more questions:  if I obtain an XP CD from my mom, I just need my own key code, right?  The key code sticker is on my machine.

Yeah, no reason why it shouldn't work. If you're unlucky, though, you may have to call up microsoft customer service to obtain another activation code.

> Also, how do I read and write to an external hard drive and pen drive?  Is there a "safely remove hardware" equivalent for external drives?


If you plug in the external hd, (or pen drive), Ubuntu will automatically mount it for you and you'll be able to read and write in a few seconds. It's pretty much plug and play. I've got a couple myself and never had a problem.
To remove the hd's just right-click and choose **Unmount Volume**.

> Finally, screw Vista.  I've been reading all about the DRM issues, and I don't want to go into those waters.  That's a nightmare waiting to happen.

Yeah, read more about it [here]("http://www.techworld.com/opsys/news/index.cfm?newsid=7675"). :D

---

### Post by cw1925 on 2006-12-28
> **riven0 said:**
> If you plug in the external hd, (or pen drive), Ubuntu will automatically mount it for you and you'll be able to read and write in a few seconds. It's pretty much plug and play. I've got a couple myself and never had a problem.I did that, and it doesn't work.  Do I need to format the drive first?  Also, how do I format?  Don't remember an option for that.

---

### Post by houstonbofh on 2006-12-29
> **cw1925 said:**
> Also,Yeah, nice of them. :mad:  Anyways, here's my screenshot:
[[IMG]http://img299.imageshack.us/img299/7756/screenshotmw7.th.png[/IMG]](http://img299.imageshack.us/my.php?image=screenshotmw7.png)I installed it tobut to no avail.  I'll keep trying.  If all else, I'll just my hallmate's computers.  A couple of more questions:  if I obtain an XP CD from my mom, I just need my own key code, right?  The key code sticker is on my machine.
Also, how do I read and write to an external hard drive and pen drive?  Is there a "safely remove hardware" equivalent for external drives?
Finally, screw Vista.  I've been reading all about the DRM issues, and I don't want to go into those waters.  That's a nightmare waiting to happen.
Well, you have no partitions to find.  Sorry, but that sucks...

As to Mom's CD, yes if;
Same version (XP Home, vs XP Pro)
Either both are Dells or Neither are Dells. (Dell uses a non-standard Windows disk)
You key is not a "limited install" key.  (Some builders do a VMLK thing and when the key runs out, it runs out.  This is quite rare, but I have seen it.)

Pen drive is easy.  It should just work.  However, an encrypted pen drive, or NTFS formated USB drive can take some tweaking.  What do you have?

---

### Post by cw1925 on 2006-12-29
> **houstonbofh said:**
> Well, you have no partitions to find.  Sorry, but that sucks...

As to Mom's CD, yes if;
Same version (XP Home, vs XP Pro)
Either both are Dells or Neither are Dells. (Dell uses a non-standard Windows disk)Well that just sucks.  My mom's is a Dell, and mine is an HP.  Screw M$ then.  Plus, mine was Media Center and my mom's was Home.  I guess there's no phone # I can call to get a replacement disc (don't even know if a Media Center disc exists)?  WTF is M$ thinking these days?

---

