---
title: "Frustrated Newbie"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Ralf_CT on 2008-03-03
Two years later and I've once again made an attempt to change over to Linux.  I've just installed (attempted) Ubuntu Linux 7.10.  All went well, until time came to reboot... SYSTEM DISK ERROR etc.  I'm only able to boot into Linux if I leave the Installation CD in and choose 'Boot from 1st hard disk'.  I've done a few Linux installations in the past, none ever gave as much problems as this one.  Why is there no boot loader as in previous versions of Linux (Suse)?  
 
For someone who has supported Windows systems since 1999 I still find the transition to Linux somewhat frustrating.  It doesn't boot, and once it does I still have to get the PCI USB card, soundcard, network card and parallel printer card to work.  
 
Any quick tips, or should I wait another few years?  I lack the time to spend weeks or months becoming conversant with Linux.  I was hoping by now that it would just work... like Windows.

---

### Post by northern lights on 2008-03-03
After the Ubuntu installation it sets up a bootloader (GRUB) which should have three Ubuntu entries and a Windows one. Are you saying that's not present?

---

### Post by ugm6hr on 2008-03-03
Something is not right with that.

Try giving more info:

Is this dual-boot with Windows or single OS?  If dual-boot, can you still access Windows?

How did you install?

What boot priority have you set in BIOS?

---

### Post by twright on 2008-03-03
hi,

can you try the command
```
sudo grub-install hda1 (or whichever partition ubuntu is on)
```

---

### Post by Ralf_CT on 2008-03-05
Thanks for the tips thus far.  This is a new installation on a machine I intend giving away.  Ubuntu is the only OS on the hard drive.  I thought this may be an Ubuntu problem and loaded SUSE Linux 9.3.  The same problem!  I can only boot if I leave the CD in the drive and then choose 'Boot from hard disk'.

Twright, where must I enter the code you recommend?  SUSE has a Boot Loader section, I'm not too sure about Ubuntu.

---

### Post by Ralf_CT on 2008-03-05
Boot priority in BIOS is CDROM, HD0.  Even if I set it up as HD0, CDROM I get the same error.  I've even tried setting it up as HD1.  No luck!

---

### Post by Ianman on 2008-03-05
forgive me if this is a totally n00b (and very Windows oriented) answer but with Windows you have make sure that the partition Windows is installed on is set to "active" with FDisk or some other partition tool. 

Is this the same for Linux partitions?

---

### Post by Paqman on 2008-03-05
> **Ralf_CT said:**
> 
Twright, where must I enter the code you recommend?  SUSE has a Boot Loader section, I'm not too sure about Ubuntu.

Into the terminal. Applications > Accesories > Terminal.

As for stuff "just working" with Windows, it really depends on your hardware, just like Linux. My motherboard doesn't really work at all with a default XP install. You need a ton of drivers on separate disks to get sound, networking, graphics, etc. The difference is that you get the Windows drivers with your hardware. That's something that only widespread adoption of Linux would fix. Catch-22 situation, really.

---

### Post by sanddgroper on 2008-03-05
Hi Ralf_CT
Could you tell us you computer specs.
I know this is of no help but I have four versions of Ubuntu from 6.06 to 8.04
mostly off live CD's and all installed in about 25 mins with full net access.
Where did you get you copy from and what version is it

Cheers
Sandy

---

### Post by punong_bisyonaryo on 2008-03-05
Bootloader doesn't work in both Gutsy and Suse...Hmmm...too much of a coincidence if you ask me. System disk error on both... Sounds like this is a hardware problem, probably couldn't write to the boot record properly.

Is it possible for you to give it a try on a different hard disk?

---

### Post by Ralf_CT on 2008-03-05
Hi Sandy,

The specs are as follows: 40GB IDE HDD, Epox EP-8K3AE MB, 512MB RAM, Athlon 1700 CPU.  There could be a problem with the disk as it was one of my old 'faulty' disks which I formatted.  However, the installation runs without any problems.

I downloaded the Ubuntu 7.10 ISO image last week, wrote a CD and installed.

I've just tried installing the latest (Linux) version of Thunderbird.  It doesn't seem to be a case of simply copying the folder to the Desktop and running the thunderbird.bin file (the only executable I found).  Linux is still a long way from being as 'user-friendly' as Windows.  I've been supporting Windows machines since 1999 and planned to give this Ubuntu machine to my brother (a complete Windows and Linux novice).  He would be totally lost and frustrated.

In my opinion, issues such as those above and several remaining program incompatibilities are preventing the mass implementation of Linux PCs.

---

### Post by VoodooLoveDog on 2008-03-05
> **Ralf_CT said:**
> Hi Sandy,

The specs are as follows: 40GB IDE HDD, Epox EP-8K3AE MB, 512MB RAM, Athlon 1700 CPU.  There could be a problem with the disk as it was one of my old 'faulty' disks which I formatted.  However, the installation runs without any problems.

I downloaded the Ubuntu 7.10 ISO image last week, wrote a CD and installed.

I've just tried installing the latest (Linux) version of Thunderbird.  It doesn't seem to be a case of simply copying the folder to the Desktop and running the thunderbird.bin file (the only executable I found).  Linux is still a long way from being as 'user-friendly' as Windows.  I've been supporting Windows machines since 1999 and planned to give this Ubuntu machine to my brother (a complete Windows and Linux novice).  He would be totally lost and frustrated.

In my opinion, issues such as those above and several remaining program incompatibilities are preventing the mass implementation of Linux PCs.

As a previous poster said, Windows has it's own subset of problems when installing as well. I know from my experience using Windows, if it's not an IDE ATA drive then you will need to load 3rd-party drivers for Windows to even "see" the physical drive.

I think the problem here is that Ubuntu is not Windows. You are trying to install and manage the OS in the same fashion as you would Windows. Coming from Windows myself, I find the management of applications on a machine much much easier in Ubuntu than in Windows. 

If you want Thunderbird installed, you simply go to the Package Manager and search for it. The software downloads and installs in the appropriate location. I do not have to spend time searching the net for software. Almost everything I need is in the repositories. 

Sorry you are having such a hard time installing the OS to the machine. I know that in the past, I have spent hours trying to get Windows on a computer. Ubuntu definitely will take you out of your comfort zone, especially if Windows is all that you have dealt with in the past. Best thing to do is to lurk the these boards and follow the links to get a better understanding of how the OS works. I spent months lurking these boards for tips/tricks and general installation/management posts. It helped me tremendously.

---

### Post by CasPol on 2008-03-05
Hi there;

I recognise your problem, and your frustration !! I struggled with the same problem for a while untill I decided to download the Ubuntu 7.10 iso again and burn the ISO to a fresh  DVD (!!!!) I did the following:

1. On a computer with Windoze, download and install "XP Burner"

2. Download the Ubuntu 7.10 ISO ( do not use bittorrent)

3. Burn the ISO file on a brandnew DVD using XP Burner.

4. Boot the system where you want to install Ubuntu on from the DVD and wait untill the live cd has loaded completely.

5. Connect the system to a modem or to a adsl access point with a ethernet cable.

6. Now install Ubuntu, answer the questions like language, country etc ..

7. When you get to the partitioner choice ( assuming you want only Ubuntu on your system) choose "guided, use entire disk".

8. Leave it alone untill install is completed, when prompted remove the DVD, system will restart and boot. Leave ethernet/modem connected !!

9. Allow to install restricted drivers if so requested

10. Yous hould now be ready to go !!

Good luck.

---

### Post by Ralf_CT on 2008-03-05
The Ubuntu PC does not have access to the Internet yet.  I downloaded Thunderbird (for Linux) on a Windows machine, extracted it, copied the extracted directory to a USB stick and then to the Desktop of the Ubuntu machine.  Launching the Thunderbird application from there didn't work.  Then I tried copying it to the /home directory.  No luck.  I then started Yast, entered the root password and searched for the directory containing the Thunderbird installation files.  I was then told the destination didn't contain any installation files (or something to that effect).

My frustration levels are steadily rising even though I'm usually quite patient.

---

### Post by dstew on 2008-03-05
> I downloaded Thunderbird (for Linux) on a Windows machine, extracted it, copied the extracted directory to a USB stick and then to the Desktop of the Ubuntu machine.That is not the way to install software on an Ubuntu machine. If you are offline, you download an [Ubuntu Debian package]("http://packages.ubuntu.com/"). Transfer it to your Ubuntu desktop, and double-click it. Or, from the command line, do ```
sudo dpkg -i *package-name*
```

Often, when installing off-line, you will have problems with dependencies (other packages that the main program depends on). This is taken care of automatically on-line, but it can be frustrating off-line. There is a service called [nonetdebs]("http://nonetdebs.homeip.net/") that you sign up for (free) and they will let you download packages with all the dependencies. Check it out.

---

### Post by Ralf_CT on 2008-03-05
Those packages are huge!  I'm sharing a 3GB capped broadband connection with two others, I can't use up the bandwidth on Ubuntu packages.  Surely one can install one piece of software from a USB stick and then search for updates once one is online (as in Windows)!

My fondness for Linux is rapidly diminishing, as is my patience level.  No doubt Bill Gates smiles quietly to himself when he reads these forums.

---

### Post by dstew on 2008-03-05
> Surely one can install one piece of software from a USB stick and then search for updates once one is online (as in Windows)!Yes, you can do that from nonetdebs. If your software has dependencies, that service will include them in your download. That is the same as Windows. A Windows program has tons of dependencies. The Windows plan is to put all those dependencies onto the disk at install time, so they are already there. However, they take up a ton of disk space (all those .dll files). The Ubuntu strategy is to have only the dependencies needed for the software that is installed, or is being installed. That is why you can install Ubuntu in 5 Gb, but Windows needs 20 Gb or more.

Which way is better? That is for you to decide. Both ways work, and have different strengths and weaknesses. Ubuntu is just different from Windows, thats all.

EDIT: Are you trying to do a full update, or just for Thunderbird? I would not think that updating Thunderbird alone would be huge, but updating the whole system might be.

---

### Post by jseiser on 2008-03-05
i think the problem is an ignorant end user who hasnt taken the time to research the differences between windows and linux.  This is all done for free, it works for thousands and thousands of people just fine, you are the minority.  Not trying to sound mean, but i think if you relaxed, did a google, read a wiki, and then went about your problems you would do  better.  You know windows because you have used it for a long time, your a linux user, you need to adjust to how to manage a linux system.  If you cant get online, insert your ubuntu disc, open up synaptic, tell it to download thunderbird, it will look to the CD first, and pull the packages off there.

---

### Post by hungryOrb on 2008-03-05
Ralf, I feel for you. 
One fast thing I noticed, Thunderbird is a small program so wont affect your line cap really. Even if it did, you could simply be happy with Evolution Mail which comes installed with Ubuntu. You dont really need to update anything after a standard install, assuming you want the computer for net access, mails, surfing, office work, and media playing. So after that download of Ubuntu, you should be ready to go.

Having said that, the recommended updates that you can download will be around 250mg. Installing additional stuff in 'Synaptic Package Manager' will start drawing on your resource fast ;] So I'd leave that for now.

As for your install. Try the exact combination that CasPol suggested. If that fails, please report back :)
Personally, I'd love for you to love Ubuntu, because I installed it 2 weeks ago, (dual boot) and I love it!

P.S. BTW, This has been said already, sort of, but Linux is a different operating system. So all those file extensions that you are used to in Windows, don't exist in Linux. Except in the Windows Emulator. Try to forget windows, and then just mess with Ubuntu, your messing will be your greatest education,.. probably :)

---

### Post by VoodooLoveDog on 2008-03-05
> **Ralf_CT said:**
> The Ubuntu PC does not have access to the Internet yet.  I downloaded Thunderbird (for Linux) on a Windows machine, extracted it, copied the extracted directory to a USB stick and then to the Desktop of the Ubuntu machine.  Launching the Thunderbird application from there didn't work.  Then I tried copying it to the /home directory.  No luck.  I then started Yast, entered the root password and searched for the directory containing the Thunderbird installation files.  I was then told the destination didn't contain any installation files (or something to that effect).

My frustration levels are steadily rising even though I'm usually quite patient.

I don't know, but clicking 'Applications' ->'Add/Remove...', then typing 'Thunderbird', clicking the check box next to it and then clicking the 'Apply Changes' button seems about as simple as something can get.

Call me crazy.

I'm not trying to be crass either, but I do agree with the above poster. This OS is not Windows, there will be a learning curve.

---

### Post by ugm6hr on 2008-03-05
> **Ralf_CT said:**
> Surely one can install one piece of software from a USB stick and then search for updates once one is online (as in Windows)!
Yes one can.  One just needs to know how to do it in Ubuntu (which is different than in Windows).

Unfortunately, Ubuntu is very much designed to work with an active internet connection - hence VoodooLoveDog's statement (which assumes you have internet on Ubuntu).  There are ways around this, but they are less pretty.

2 methods:
1. [nonetdebs]("http://nonetdebs.homeip.net/") (as linked by dstew) - this is probably your best bet for doing it without getting confused.
2. [http://packages.ubuntu.com/gutsy/thunderbird](http://packages.ubuntu.com/gutsy/thunderbird) - you need to select your "architecture" - presumably i386 from the table bottom left to download the package.  This will allow you to download the Ubuntu-specific Thunderbird package (as a .deb file), which can be double-clicked to install.  However, Ubuntu packages have "dependencies" which need to be installed before this package can be installed.  They are listed on the linked page, so if it complains about certain dependencies, you will have to manually download them as well (although I suspect that most of them will be installed as default).

> I still have to get the PCI USB card, soundcard, network card and parallel printer card to work.  
I suspect that the PCI-USB card, soundcard and PCI network card should all just work (i.e. Ubuntu should have loaded drivers automatically at installation).  There are some exceptions, but it would be unusual for all your hardware not to work (PS: I am not sure what a parallel printer card is).

> Any quick tips, or should I wait another few years? I lack the time to spend weeks or months becoming conversant with Linux. I was hoping by now that it would just work... like Windows.
If you are not prepared to learn, then I wouldn't waste any more time with Ubuntu / Linux.  If you are waiting for it to *just work like Windows*, you will be waiting forever.  Ubuntu is not Windows.

> My fondness for Linux is rapidly diminishing, as is my patience level.  No doubt Bill Gates smiles quietly to himself when he reads these forums.

Remember your brother will be asking you for support if things go wrong with this new computer, and if you are not prepared to spend time becoming accustomed to the Linux way of doing things yourself, you will not be able to support him.

I would ask you to consider these points before asking for any more help, simply because we as a community are always happy to assist people in the transfer from Windows to Linux (for whatever reason you make that choice), but don't particularly want to waste our time if you are looking for Ubuntu to be Windows.

This is a worthwhile read: [http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

Either way, thanks for visiting.

---

### Post by xeth_delta on 2008-03-05
> **Ralf_CT said:**
> Those packages are huge!  I'm sharing a 3GB capped broadband connection with two others, I can't use up the bandwidth on Ubuntu packages.  Surely one can install one piece of software from a USB stick and then search for updates once one is online (as in Windows)!

My fondness for Linux is rapidly diminishing, as is my patience level.  No doubt Bill Gates smiles quietly to himself when he reads these forums.

The packages for just a program like Thunderbird can not be "huge", to be honest. There might be some more libraries needed, but I seriously doubt the amount would be that big.
I have to share the view of a previous user, I also prefer the package management system in diferent Linux distributions (apt in the case of Ubuntu) much better than the way you do program administration in Windows. Installations and updates are made transparent fast and secure. Updates are performed to the entire software library at once and not programs and system one by one.

That said, I guess it is a matter of personal preference, but remember that because something is or works differently, doesn't mean it is bad. It is just that, different.

In any case, I agree with ugm6hr in general terms. Whatever you decide to do, I wish you good luck!

---

### Post by Ralf_CT on 2008-03-07
Okay, after reading some of your posts and also the links to other Windows/Linux articles I've decided to clear my mind of everything relating to Windows and start afresh... with an open mind.  As one Poster aptly stated, when starting with Linux it's better to be a novice PC user than a clued-up Windows user.  Sometimes the best people for a job are those who haven't had their minds 'corrupted' by formal teachings.  They come to the table with clear ideas, based on intuition rather than years of formal studies.

Anyway, I  successfully installed Ubuntu 7.10 on another hard drive... and it now boots.  The other drive must've had a faulty boot sector.  I'm now working with it and treating it as an alternative OS, rather than a substitute for Windows.  I've also been using Firefox for years and must say, I would never go back to IE (however, sometimes one is forced to, as when updating Windows).  Before installing Ubuntu I also installed SUSE 9.3 Professional (just to see if the system would boot).  Each Linux version has it's own unique features.  I don't know what the latest version of SUSE is like but Ubuntu is small and compact in comparison.

I'll give Ubuntu a chance ... there's light at the end of the tunnel.  Thanks to all for the tips and advice.:)

---

### Post by mangurt on 2008-03-07
Congrats on the installation!  Sometimes trying to do a multitude of things at one times makes things very unclear (ie, a faulty hard drive and trying to learn a new OS).

A few suggestions (and these are suggestions), depending on what you plan on doing with the computer, I might suggest trying linux mint.  Granted, you just got ubuntu up and running, but linux mint is a polished version of ubuntu, and a lot of people say that it works "out of the box".  For me, when I was weaning my family off of windows, I had to run PSlinuxOS on my "kids" computer it "looked" like windows, and for my children, that was the biggest factor for them.  As you stated before, you have to come into linux completely differently than "oh, I use to do this in windows" mind set, once you get past that hurdle, you may come to find out that linux is great.

---

### Post by xeth_delta on 2008-03-07
I'm glad the installation went fine. Enjoy Ubuntu and do not hesitate to write if you have questions. Good luck!

---

### Post by steveneddy on 2008-03-07
> **jseiser said:**
> i think the problem is an ignorant end user who hasnt taken the time to research the differences between windows and linux.

:shock:

---

### Post by ugm6hr on 2008-03-07
> **Ralf_CT said:**
> I'll give Ubuntu a chance ... there's light at the end of the tunnel.  Thanks to all for the tips and advice.:)

Glad to see you've got your first installation sorted.  It really is easy from here!

If you have any further specific problems, feel free to start a new thread for each.

To get you started for necessary stuff on Ubuntu, I will direct you to this multimedia thread that works to get all youyr audio and video sorted (the one thing that Ubuntu doesn't do out-of-the-box):
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Good luck with the rest of the journey...

---

