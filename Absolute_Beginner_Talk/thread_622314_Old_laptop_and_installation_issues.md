---
title: "Old laptop and installation issues"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Justus Alerio on 2007-11-24
Hello all,
Here is the problem. I have an 8 year old Compaq Presario 1670 laptop. I have wiped the hard drive and attempted to install Ubuntu 7.1 with zero luck. Is the laptop just too old? If so, can you recommend a version that would be apprpriate, or at least another version of Linix? My needs are strictly basic- web surfing, looking at photos etc.

---

### Post by jken146 on 2007-11-24
Depends on your specs.  Try Xubuntu, or if that fails you might want to look at Damn Small Linux or Puppy Linux.

---

### Post by serencavalier on 2007-11-24
I am having the same issue with a Compaq Presario 1200 laptop...this computer is also old (intel celeron with 128 mb ram and windows ME).

Is there any way to install Ubutu or am I stuck with windows?

I was attempting to install Ubuntu on a Sony Vaio computer with similar specs as above with no results.

I am excited about ubuntu and would love to get it working on these computers!

---

### Post by odinb on 2007-11-24
Sounds weird, but I had the same issue on 2 different Laptops...
I wanted to install Gutsy (7.10) fresh. 

Both worked with Feisty (7.04). So I ended up reinstalling Feisty, and then I tried running the upgrade wizard, which failed/died on me, ofcourse!

I ended up having to fix it running "sudo dpkg --configure -a" after the wizard failed. Follow the error messages when I got them, and after that Gutsy is now running on both these systems. Might be worth a try.

By the way, the oldest system I have has 384MB RAM. With 128 you need a RAM-upgrade or different version of Linux, see jken146 recommendations.

Good luck!

//Odin

---

### Post by slipperhead on 2007-11-24
i couldnt install 7.04 or 7.10 (including the xubuntu versions) on my old dell cpt with 128 ram. after a long wait, i got dapper 6.01 to install (the wait was because the cd drive kept having hdc not ready errors).

i think 128 ram is probably too low (my experience anyway) for the latest ubuntu so for now i am happy with the 6.01 version. (beats the xp i tried to put on it :) )

i used the alternate install disc as it works best for low memory computers.

---

### Post by serencavalier on 2007-11-24
What linux versions does everyone recommend that can get me close to ubuntu functionality? I need to be able to run OpenOffice and Firefox browsing. I am trying to use my laptop for these tasks and can't stand windows 98 any longer. 

I would appreciate any insight!

---

### Post by slipperhead on 2007-11-24
i can use open office (although it takes a while to open!) and surf happily using firefox firefox on ubuntu dapper. it should be ok for you too.

i had the same ubuntu running on an old toshiba laptop ( 233mhz/96 ram) 

i tried xubuntu but it didnt feel as complete to me as ubuntu (just my opinion)

---

### Post by gn2 on 2007-11-24
I would strongly suggest using Xubuntu 7.04 and installing from the "Alternate CD" available here: [http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/7.04/release/xubuntu-7.04-alternate-i386.iso](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/7.04/release/xubuntu-7.04-alternate-i386.iso)

Burn to CD as an image then boot with the CD  in the drive, select "Install a command line system" from the splash menu and install.

Once it's done, re-boot, lots of text will appear. 
Wait till it finishes and press Enter. 
Log-in, then at the command prompt type: sudo aptitude install xubuntu-desktop 

This installs the GUI and various other programs. 
Re-boot and you're done.

---

### Post by bobpur on 2007-11-24
I had Xubuntu  v6.06 LTS running on an old IBM Thinkpad 390E. It run acceptably well. Newer versions slowed it down some. If you're determined to stay with Ubuntu I'd try Xubuntu v6.06 LTS. You could also try LinuxMint 3.0 or 3.1 XFCE. I have that running on an old desktop with a PII cpu and 128 mb RAM.

---

### Post by Taboo Mirage on 2007-11-24
Slackware with one of the lighter weight WMs such as Xfce, Blackbox or Fluxbox is what you're looking for.  It's a world away from Ubuntu though so you may need to do a little research on how Slackware accomplishes things and how to manually configure things.  It's not as forgiving on users unfamiliar with Linux.

---

### Post by verraeter on 2007-11-24
I am trying to install that very version on my Toshiba Satellite 1620 CDS

> **gn2 said:**
> I would strongly suggest using Xubuntu 7.04 and installing from the "Alternate CD" available here: [http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/7.04/release/xubuntu-7.04-alternate-i386.iso](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/7.04/release/xubuntu-7.04-alternate-i386.iso)

Burn to CD as an image then boot with the CD  in the drive, select "Install a command line system" from the splash menu and install.

Once it's done, re-boot, lots of text will appear. 
Wait till it finishes and press Enter. 
Log-in, then at the command prompt type: sudo aptitude install xubuntu-desktop 

This installs the GUI and various other programs. 
Re-boot and you're done.

But where is the option "Install a command line system"?

Kai

---

### Post by gn2 on 2007-11-24
> **verraeter said:**
> 
But where is the option "Install a command line system"?



It is an option when you boot the 7.04 Alternate CD, which is different from the standard 7.04 Live CD.

---

### Post by verraeter on 2007-11-24
Strange, the iso is definitely called 'alternate', but I am downloading it again now and burn a new cd.

Now my screen has really large writing on -  that was never there before.

Kai

---

### Post by serencavalier on 2007-11-25
Thank you all for the quick and helpful replies.
I have downloaded the Desktop CD of Xubuntu 7.10 already but will be downloading the Alternate CD version right now and give that a chance first.

I hope this works out well and I am happy to be a new member of the Linux community :o)

---

### Post by serencavalier on 2007-11-25
So after rebooting and going through all the installation steps, the result is myname@vaio:~$ 
I guess it wants me to enter a command, but I dont know which one. Should I just reboot and take the CD out of the drive?

I am not sure if setup is completely finished...although it seems I have gone through all the steps posted by member gn2.

Please help me out!
Thank you

---

### Post by Paulmd on 2007-11-25
> **Justus Alerio said:**
> Hello all,
Here is the problem. I have an 8 year old Compaq Presario 1670 laptop. I have wiped the hard drive and attempted to install Ubuntu 7.1 with zero luck. Is the laptop just too old? If so, can you recommend a version that would be apprpriate, or at least another version of Linix? My needs are strictly basic- web surfing, looking at photos etc.

The factory version came with a k6-2 350, which is fine, and 64MB ram, which is not sufficient to run Ubuntu. You should have 256 or more.

Damn Small linux, is probably your best bet.

---

### Post by pinbrook on 2007-11-25
i also want to install ubuntu on an old Dell Lattitude.  I can get a Live CD to work OK, but i really want to install ubuntu - i've got 256 memory.

My question really is how do i get rid of the XP install on the machine prior to trying to install ubuntu.

---

### Post by gn2 on 2007-11-25
> **serencavalier said:**
> So after rebooting and going through all the installation steps, the result is myname@vaio:~$ 
I guess it wants me to enter a command, but I dont know which one. Should I just reboot and take the CD out of the drive?

I am not sure if setup is completely finished...although it seems I have gone through all the steps posted by member gn2.


When you get to that command prompt, put the CD back in and if it's the Xubunntu Alternate CD type: "sudo aptitude install xubuntu-desktop" (without the quotes) and press Enter.
You will be asked for your password, type it in and press enter.

If you have the Ubuntu Alternate CD type: "sudo aptitude install ubuntu-desktop" (without the quotes) and press Enter. 

What happens next is the GUI and various programs are installed from the CD.
Re-boot after it's finished.
I don't know the command to switch off, I just press and hold the power button....
Maybe someone with more CLI knowledge can post the power off command.......?

Next step after re-booting to the working desktop is to open a terminal and run this command:
sudo apt-get install ubuntu-restricted-extras

That will install a whole bunch of useful extras.

---

### Post by gn2 on 2007-11-25
> **pinbrook said:**
> My question really is how do i get rid of the XP install on the machine prior to trying to install ubuntu.

Very simply, you don't have to. 
During the installation process there is an option to let the partitioner use the entire hard drive.
Take this option and all data on the drive will be wiped completely off, so if there's anything you need to keep, back it up  to removeable media first.

---

### Post by serencavalier on 2007-11-26
> **gn2 said:**
> When you get to that command prompt, put the CD back in and if it's the Xubunntu Alternate CD type: "sudo aptitude install xubuntu-desktop" (without the quotes) and press Enter.
You will be asked for your password, type it in and press enter.

If you have the Ubuntu Alternate CD type: "sudo aptitude install ubuntu-desktop" (without the quotes) and press Enter. 

What happens next is the GUI and various programs are installed from the CD.
Re-boot after it's finished.
I don't know the command to switch off, I just press and hold the power button....
Maybe someone with more CLI knowledge can post the power off command.......?

Next step after re-booting to the working desktop is to open a terminal and run this command:
sudo apt-get install ubuntu-restricted-extras

That will install a whole bunch of useful extras.


Thank you for the thorough explanation!

I have a few more quirks to iron out though:

--during the GUI setup, I was asked about internet config and postfix...I choose to not change configurations at this time and the setup continued. Does this mean I will not be able to setup a wireless network connection?

--the entire setup seems to have taken 3.0 GB out of my hard drive...is that normal? The xubuntu website states that I only need 1.5 GB!! I went through the second portion of the installation twice so maybe that is my problem.

--I have a PC card for my wireless internet that uses software and drivers to work properly. Is there a way to make it work on Xubuntu or am I stuck with no wifi?

If I need to start from scratch, please let me know.

So far the Xubuntu is much slower than the windows 98 I had installed on this computer...which is really unfortunate because I was hoping the computer would run better with Linux!
I am patient and willing to give this a shot.

---

### Post by gn2 on 2007-11-26
> **serencavalier said:**
> 
So far the Xubuntu is much slower than the windows 98 I had installed on this computer...

7.04 would perhaps have been a better bet.......

This may help with the slow booting in 7.10:
[http://ubuntuforums.org/showpost.php?p=3567220&postcount=1](http://ubuntuforums.org/showpost.php?p=3567220&postcount=1)

Wireless info: [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

3gb seems quite a lot.  :confused:

---

### Post by serencavalier on 2007-11-26
Thanks for the reply.

I did install 7.04 as you recommended!

After spending an entire day playing and toying with the system, I decided to take a step back and go back to windows 98...it was fun and worth a try though.

Thank again for all the help!

---

### Post by Afkpuz on 2007-11-26
Yea guys, make sure you use the ALTERNATE INSTALL discs.  They are text based and do not require loading up a live boot environment to install.  I know that the live CDs use alot of ram and many people have trouble with em.  Older comps might not make it to the live boot environment.  Also, have you tried fluxbuntu?

---

