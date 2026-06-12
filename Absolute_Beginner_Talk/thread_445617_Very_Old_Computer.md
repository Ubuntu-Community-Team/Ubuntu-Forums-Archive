---
title: "Very Old Computer"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-05-16
I have a very old computer which was made in 1995. It has a 100 Mhz processor and I am trying very hard to get Linux to boot on it. It has an 8X CD Drive but it will not load any of the live CD's I try. I have tried Damn Small, and Puppy. The computer I have actually has Windows 98 installed on it. I would greatly appreciate if you could walk me through the steps about how I might get a Linux CD to boot onto the computer and install a Linux distribution. The computer probably has about 64 MB of RAM. The computer also has a floppy drive, but I would prefer not to boot Linux via floppy drive. Also, please leave any other additional advice.

Thank you

:guitar:

---

### Post by jbro on 2007-05-16
Hello there,

When you say that the computer cannot "load" any of the LiveCDs that you've tried, what exactly do you mean? Can you not boot from the LiveCD? An older computer like that may not be able to boot from CD, or possibly the BIOS needs to be configured to boot from CD before the hard drive. If you are in Windows, can you put in the CD and browse the contents of the CD? If you can then probably you have one of the problems I just mentioned. If you cannot browse the CD from Windows, then it may be that your CD reader is not working.

Regards,
Jay

---

### Post by tompickles on 2007-05-16
Hey,

Download the [Alternate CD of Xubuntu]("http://www.xubuntu.org/get"). This is a fantastic distro built for older PCs. As you only have 64MB of RAM, you need to unsure you download and then burn and boot from the Alternate CD. This means that you don't have a pretty graphic installer, but the install is very similar to that of installing Windows.

Hope this helps!

---

### Post by jprb85 on 2007-05-16
Thanks

---

### Post by whitefort on 2007-05-16
I had an antique PC that sounds a bit like yours.

I found it absolutely impossible to install Xbuntu Feisty on it, even using the 'Alternate' CD, I got a message about the machine failing the 'bios cut off point' of the year 2000.  After that, installation was unbelievably slow - I left the PC running for about 24 hours, and found that it always totally stalled before installation was complete.

However, I DID find that Dapper Xubuntu installed just fine from the alternate disk, and it works perfectly.  In fact it works like a dream and gave the machine a whole new lease of life.

Just one other observation which may or may not affect you:  I discovered that even Dapper wouldn't install over a failed Feisty installation, even though I told it to reformat and use the entire hard drive.  Oddly enough, I had to reinstall Windows 95, THEN allow Xubuntu Dapper to reformat the drive, and it worked perfectly.  I've no idea why this is the case, but it was 100% repeatable.  Xubuntu always failed to nstall properly over another Xubuntu, but it had no problems installing over Windows!

---

### Post by ginestre on 2007-05-16
I'm just posting a quick reply so I can subscribe to this thread: maybe there's a better way to do this without cluttering the thread itself, but I'm afraid I don't know it

---

### Post by overdrank on 2007-05-16
> **ginestre said:**
> I'm just posting a quick reply so I can subscribe to this thread: maybe there's a better way to do this without cluttering the thread itself, but I'm afraid I don't know it

Hi there is, its in the thread tools at the top of the page and just subscribe to thread. :)

---

### Post by alienexplorers on 2007-05-16
I have a old 300Mhz PC that runs Damn Small Linux thou very very slow.

---

### Post by seshomaru samma on 2007-05-16
Puppy and DSL should be your main options

with 64 MB ,I wouldn't even try Xubuntu....

Another option is to do a server install and then maybe try to run Fluxbox on top of it (or [UbuntuLite ]("http://ubuntuforums.org/showthread.php?t=98233&highlight=minimal") =icewm)
But I would try DSL first

---

### Post by Terl on 2007-05-16
jprb85:  When you say the live version does not load what exactly do you mean?  Is the cd booting?  Or when you boot with the cd does windows start instead?

Puppy or DSL are two I can think of that would work Deli might also.  If you cannot boot from the cd you can make a boot floppy that will help you do a cd install.  Once it is installed you would be able to boot from the hard drive.

You never really answered the question earlier though, which is same that I asked:  What do you mean when you say it does not load?

---

### Post by IainT on 2007-05-16
I run Puppy on a laptop with a 433mhz celeron processor and 96mb ram. It's still pretty slow.

---

### Post by Terl on 2007-05-16
I would give DeLi Linux a try.  Per their web site it is a distro for 486 on up.  It is designed for old pc's such as this.

Go here:  [DeLi Linux]("http://delili.lens.hl-users.com/")

---

### Post by tompickles on 2007-05-16
how did you get on with the different distros mentioned?

The Ubuntu [Wiki]("https://help.ubuntu.com/community/Installation/LowMemorySystems") has something to think about whne installing on a PC with such a tiny amount of RAM. You are basically installing a system with no graphical interface, and then installing a graphical interface which is less resource heavy than Gnome. Any use?

---

### Post by stalkingwolf on 2007-05-16
Have you tried using wakepup floppy to boot the live CD?

---

### Post by Chetamonye on 2007-05-17
I am using an IBM Thinkpad 600E.  It's a 366 mhz machine with 296 megs of ram.  I can't run most of the live CDs.  I also get the same bios message.  I can get xubuntu live to run, but it also throws up the bios error before continuing.  

I Installed Xubuntu from the alternate CD.  Then I installed fluxbox.  It's pretty quick now.  Slackware was faster, but I really like apt for program, maintenance.  

You might want to see if you can install Xubuntu from the alt CD.  Running after an install seems to be much easier than trying to get the live Cds to run.


Chet

---

### Post by derred on 2007-05-17
You could try doing a server install from a alternate CD and then add X, and TWM maybe Window Maker or Ion. That's what I'd recommend if you really want an Ubuntu system. Also you might want to try doing this with the 6.06 LTS version since it seamed to work better for me, at least with older PCs.

Just one more thing: Linux is the only OS with a CLUE(Command Line User Environment ) so install the text based system and see how much X functionality you really need. I use a AMD K6-2 with 64 MB of RAM to read my e-mail, listen to MP3s and so on. I only start X to watch a movie or two.

---

### Post by prince_alfie on 2007-05-17
Thanks guys for your advice as I will be looking at getting some old school ultraportables so that I can carry one around easier than my macbook :)

---

### Post by st33med on 2007-05-17
I'm assuming you have a floppy drive on your computer(s). First click on the below link IN WINDOWS to get rawwritewin.exe
[ftp://141.30.228.4/pub/mirrors/redhat/redhat/9/en/os/i386/dosutils/rawritewin/rawwritewin.exe]("ftp://141.30.228.4/pub/mirrors/redhat/redhat/9/en/os/i386/dosutils/rawritewin/rawwritewin.exe")
Next, download the Smart Boot Manager on your computer. File is below.
[http://downloads.sourceforge.net/btmgr/sbminst.exe?modtime=983203200&big_mirror=0]("http://downloads.sourceforge.net/btmgr/sbminst.exe?modtime=983203200&big_mirror=0")
Now, locate open rawwritewin and browse for the smbminst.exe file. Use rawwritewin to burn that .exe file onto a floppy. Now, make sure your BIOS is set to boot off a floppy before anything else. Insert your floppy, and, at the menu that comes up, select CD-ROM. It should now boot off of it.

---

### Post by RedSquirrel on 2007-05-18
> **seshomaru samma said:**
> Puppy and DSL should be your main options

with 64 MB ,I wouldn't even try Xubuntu....

Another option is to do a server install and then maybe try to run Fluxbox on top of it (or [UbuntuLite ]("http://ubuntuforums.org/showthread.php?t=98233&highlight=minimal") =icewm)
But I would try DSL first

I believe UbuntuLite is defunct.

You can install a lightweight Ubuntu with the following guide, which uses the net installer:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

or you could download the server edition CD from [www.ubuntu.com]("http://www.ubuntu.com") and add a WM and apps on top of that.



> **whitefort said:**
> Just one other observation which may or may not affect you:  I discovered that even Dapper wouldn't install over a failed Feisty installation, even though I told it to reformat and use the entire hard drive.  Oddly enough, I had to reinstall Windows 95, THEN allow Xubuntu Dapper to reformat the drive, and it worked perfectly.  I've no idea why this is the case, but it was 100% repeatable.  Xubuntu always failed to nstall properly over another Xubuntu, but it had no problems installing over Windows!

You might try [KillDisk]("http://www.killdisk.com/downloadfree.htm") next time.

---

### Post by Deathshead on 2007-05-18
im running a toshiba tecra 8100, (pIII 700 256 mb ram) and ubuntu with gdesklets running runs very good for a machine this old, im VERY surprised. Gimp is fast,.. Overall this is the first linux distro im excited about.

---

### Post by Lord Illidan on 2007-05-18
I would use DSL rather than Ubuntu..

tried it on a pentium 1 with 16 MB RAM it actually worked and we could play tetris on it :)

---

