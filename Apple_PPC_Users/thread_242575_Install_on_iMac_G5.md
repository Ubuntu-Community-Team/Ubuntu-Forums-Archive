---
title: "Install on iMac G5?"
date: 2006-08-23
forum: Apple PPC Users
---

### Post by mike_hore on 2006-08-23
Hi folks,
I'm a raw newbie, and want to run off the CD to give ubuntu a try before I do any repartioning etc.  
I downloaded the CD image last night and burned a CD as instructed.

But I can't boot -- I get the yaboot boot: prompt, hit return, and it goes through the initial stuff with no apparent problem, but then the screen goes black, I get a white arrow then everything freezes.  Help??

--  Mike.

---

### Post by mike_hore on 2006-08-23
Further to my post:

I've been trying all the different options at the boot: prompt, but get exactly the same problem.  The initial checks all look OK, but when it tries to go to the next stage which looks like the graphical interface, the screen goes black, the arrow appears in white, and I can move it around for about a minute, then there's a total freeze with the fans running flat out.  I never get the language prompt which I think is supposed to come next.

I'm really stuck here -- please help before I ditch ubuntu and look elsewhere!!

--  Mike.

---

### Post by TomA on 2006-08-24
Just to say I've downloaded 6.0.6 for use on my iMac G5 (ALS) and I'm having the same issue described above. The CD I burned works fine on my iBook G4, so I guess it's unlikely to be the CD.

Can anyone help?

Tom

---

### Post by mike_hore on 2006-08-24
Hi Tom,

Just looked this morning (Australian time) and see that while I downloaded ubuntu-6.06-desktop-powerpc.iso, the current download is ubuntu-6.06.1-desktop-powerpc.iso.

So there's been an update.  I might give it a try later but will be out for a while this morning.

Could SOMEBODY please enlighten us as to whether this is a known issue which is fixed by the update, or should I file a bug?  I thought it couldn't be the same issue as the bad update that happened a few days ago, since I wasn't getting the error screen, but the hang could be in video initialization, so it could be the same.  Any enlightenment, please??

Cheers,  Mike.

---

### Post by avtolle on 2006-08-24
There are some threads on the forum dealing with the same or similar problem. In some cases, an upgrade to the kernel solved the problem. As 6.06.1 has the latest kernel, the only way to find out is to download it and try. No, it's not the same problem as the bad update; btw, that affected certain Intel chipsets on certain computers, judging from the various threads/posts that I have read.

---

### Post by mike_hore on 2006-08-25
> **avtolle said:**
> There are some threads on the forum dealing with the same or similar problem. In some cases, an upgrade to the kernel solved the problem. As 6.06.1 has the latest kernel, the only way to find out is to download it and try. No, it's not the same problem as the bad update; btw, that affected certain Intel chipsets on certain computers, judging from the various threads/posts that I have read.

Thanks for that -- obviously I can't upgrade the kernel myself since I can't install anything to start with!  But I have downloaded 6.06.1 and will give it a try today.

--  Mike.

---

### Post by mike_hore on 2006-08-25
> **mike_hore said:**
> Thanks for that -- obviously I can't upgrade the kernel myself since I can't install anything to start with!  But I have downloaded 6.06.1 and will give it a try today.

--  Mike.

The problem still isn't fixed.  I'm getting exactly the same hang about a minute into the initial boot.

I can only assume that 6.06.1 is incompatible with iMac G5s of about 2 years ago.  As nobody seems to know what's going on, I'll file a bug (once I work out how to).  

Basically I'm pretty disappointed at this point.  This is a pretty common Mac model and a fundamental incompatibility like this that nobody seems to be aware of is a bit of a worry.  I'm going to give Gentoo a try.

Cheers,  Mike.

---

### Post by mike_hore on 2006-08-25
OK, next inatalment:

I sussed out how to file a bug, and did the right thing and read through the open bugs.

Then lo and behold, I found that this bug has been known about since October last year, and still not fixed!!!  To say I was underwhelmed would be a bit of an understatement.  I realise that developers can't be expected to have every kind of hardware at their disposal, but with a show-stopper like this there should be a warning on the ubuntu home page that dapper is currently incompatible with iMac G5s, so other people won't waste time and blank CDs like I did.

Anyway I'm too new with all of this to try recompiling kernels etc -- I'm going to try Gentoo and if I have trouble there too I'll just leave it for a couple of months before I come back.

Cheers,  Mike.

---

### Post by Torrance on 2006-08-25
Yep, this bug has been known for a while. It's been filed on Launchpad at [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/23445](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/23445)

It looks as though we might finally get some attention as one of maintainers/bug-fixers is has just recently started working to fix it.

---

### Post by sirrahn on 2006-08-29
Hi Mike,

Your right this is pretty underwhelming. I've been watching these forums for a while to see if a solution comes up - there are quite a few threads posted. Unforunately the Ubuntu community or developers think that it is reasonable to put out a release for mac that doesn't work on most recent machines - and still claim that Ubuntu works on different architectures  - its really strange and I'm yet to hear any justification or explanation.

---

### Post by mike_hore on 2006-08-30
Hi folks -- just an update.  There's been an ongoing discussion in the bug #23446 thread.

Edgy Eft will fix this bug (finally!).  I've installed Edgy knot-1 and everything's running fine -- I had some excitement getting a dual boot set up but it's all running now.  I still can't get on the internet via ADSL but hopefully that will be all fixed when Edgy goes final.

Cheers,  Mike

---

### Post by carontis on 2006-08-30
With a friend of mine (he has a G5) we tried but at the end the distro was searching for jaboot and for a partition to install it. The partion was there but it wasn't able to find it. After time we understood that was necessary have a partition dedicated. The only difference from your installations is that this friend of mine pretended to install it on an external hdd. So you can imagine what troubles, 'cause the bootloader needs to be installed in a boot sector (partition) and that must reside on the original first hdd. We ahven't ended the all 'cause he was afraid to di in that way, so now is simply using the Live CC. If someone can have suggestions for this kind of installation, is welcome.
Thanks to all

---

### Post by Torrance on 2006-08-30
Yup, I've had Edgy Eft working - but, as with any testing software, it's pretty unstable and the fans are on full speed (but the sound works!).

**I've also got Dapper working, with fan control, but no sound.** 

1. Install it as per normal (using the alternative/text based installer). If you start it up and let X Windows load it'll hang at the log-in screen.
2. Stop X-Windows from loading. Just before the log in screen appears during start up, the mouse will appear in front of a black screen. Quickly press control-alt-backspace to quit x-windows. It will try to load again - 6 times in fact (taking slightly longer each time) - until the 6th time it will notify you that it is going to wait 2 minutes before trying to load again.
3. Quickly log in using the terminal and then type "sudo /etc/init.d/gdm stop". This will stop X Windows from loading up at all this session and give you a fully operational terminal to play with (just don't do anythign that will generate a pc beep - such as backspacing when there's nothing to backspace... everything will freeze).
4. Follow the instructions at [http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657) to complile a kernel. Please note that you may need to install "libncurses5-dev" in addition to those mentioned in step 1. Most importantly, change step 7 to "sudo make g5_defconfig && sudo make menuconfig".

The Dapper kernel has sound but no fan control, while this new g5-defconfig kernel has fan control but no sound. I've been comparing the two but have yet come up with a kernel that covers both. I would welcome other people's attempts!

I have the deb packages for this new kernel too, which I can email to people who can't compile a kernel - as long as you can stop X Windows loading you can install these kernel packages and have Dapper up and running. Email - torrance123 -> AT <- gmail DOT com

---

### Post by carontis on 2006-08-30
Mmmmhh... I'm afraid my friend will not do this. He's terribly paranoid to touch the kernel or simply touch the normal system disk. For this he was installing Ubuntu on an external USB hdd. But as I told him Ubuntu needs to boot up from first hdd, he started to say he doesn't want delete all he has on the hdd. So, I will propose him your way, but I don't think he will accept (he bolt the USB external drive only for Ubuntu...).
One question I have to ask to you all, Mac users: why the Mac-line say that their sofware is an OpenSource when it's not? Do you know how much costs the last OS for Mac? How can they say is OpeSource when there are closed programs, closed system and about all expansives? Why they too, don't give drivers for all architecture? Only 'cause is not OpenSource, but they show it as it is! Only houses that give open drivers are to be meant OpenSource. But this is in relation also to those laptop pc are around with windows... So, don't forget to buy something one future day can install also Linux, or you'll have a proprietary machine (is it yours at all?).
Thanks for answer and believe: after researches done, I came to that conclusion. Don't trust them when they say they are giving you the Yin/Yang 'cause it's all about what they need to sell; they don't care if it will cost to much and will not work as told! This is the actual policy used by many houses (companies), and I don't approuve them!

---

### Post by mike_hore on 2006-08-30
This bug is fixed in the current Edgy Knot 1 -- it was filed as bug 23445.  The screen resolution needs in terminal:
sudo dpkg-reconfigure -phigh xserver-xorg

but I haven't figured out how to actually use it yet.  The fan isn't fixed yet.

But at least some progress is being made (with a bit of agitation from several of us  :-)

Cheers,  Mike.

---

### Post by Torrance on 2006-08-30
Sweet! - I now have a fully working iMacG5 running Dapper, with both fan control and sound. All it took a compile of the 2.6.18 kernel with the configuration "g5_defconfig".

I'm happy to write a how-to if anyone would like to know. :)

---

### Post by DylanRE on 2006-08-30
So... to get sound working, all you did was compile the kernel as g5_defconfig, or did you need any extra drivers or anything?

---

### Post by Torrance on 2006-08-30
The drivers have been built into the 2.6.18 kernel. I was originally compiling based on the 2.6.17.11 kernel, which only has fan control. Of course, the 2.6.18 kernel is still a release candidate, so you'll need to do some patching. Besides that, it was a straight g5_defconfig.

The only issue I have noticed so far is that video is rather sluggish. The Dapper kernel had quite good video, so it's something to do with the kernel and not the hardware or anything else in the system. Be nice if anyone works this one out.

---

### Post by 3rdalbum on 2006-08-31
I don't think anyone claims that OS X is open-source. The kernel it uses is open-source, but in a different way to Linux; the kernel isn't the whole operating system anyway. Claiming that OS X is open-source because of its kernel is like claiming that Windows is open-source because of its FTP program.

---

### Post by rbroen on 2006-08-31
> **3rdalbum said:**
> I don't think anyone claims that OS X is open-source. The kernel it uses is open-source, but in a different way to Linux; the kernel isn't the whole operating system anyway. Claiming that OS X is open-source because of its kernel is like claiming that Windows is open-source because of its FTP program.

Apple Mac OS X is built on top of Apples open source kernel, which they call Darwin.
[read about Darwin on the Apple site]("http://developer.apple.com/opensource/index.html")
[read about Darwin on Wikipedia]("http://en.wikipedia.org/wiki/Darwin_%28operating_system%29")

Ontopic: The solution for the iMac G5 problem is comming, we just have to be patient.

---

### Post by estebandido on 2006-09-03
> **Torrance said:**
> Sweet! - I now have a fully working iMacG5 running Dapper, with both fan control and sound. All it took a compile of the 2.6.18 kernel with the configuration "g5_defconfig".

I'm happy to write a how-to if anyone would like to know. :)

Yes, for crying out loud! Please write one! I keep telling everyone around me how cool Ubuntu is, but then I have to explain why I can't seem to install it on my iMac.

---

### Post by Torrance on 2006-09-03
My 'How To' is here: [http://ubuntuforums.org/showthread.php?t=248238](http://ubuntuforums.org/showthread.php?t=248238)

Please post on that thread any problems (or sucesses!). :D

---

### Post by ACoolie on 2006-09-03
Mhmm, I downloaded Edgy Knot 2 PPC Desktop and I just get a gray screen on bootup. Did I do something wrong?

---

### Post by Torrance on 2006-09-03
Does it load up and then go grey? Or do absolutely nothing, just grey? If it's the latter, you're probably missing the yaboot bootloader - you'll have to reinstall and make sure you include it. Unfortunately, the graphical installer does not make installing the bootloader very easy, so I recommend the text based alternative installer.

---

### Post by ACoolie on 2006-09-04
I hadn't even installed yet, just tried to bootup and it almost instantly went gray. I am trying the alternate version but a lot of the checksums don't check out. Not that the files don't match the checksums, but the files do not have the proper location. (Hundreds of files under /pool/ do not end in .deb as they should).

I haven't tried booting from alternate yet though.

---

