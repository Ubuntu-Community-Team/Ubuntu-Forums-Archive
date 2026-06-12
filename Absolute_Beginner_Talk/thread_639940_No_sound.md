---
title: "No sound?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Want A Pie on 2007-12-13
Hey, I am new to Ubuntu,and I have been having a lot of problems
I finally got YouTube working, but then I found out that my sound isnt working!
I looked in the settings, but I don't know where to begin.
Hope someone can help :D

---

### Post by Pumalite on 2007-12-13
Type in your Terminal:
alsamixer
And post the results.

---

### Post by Want A Pie on 2007-12-13
[[IMG]http://img90.imageshack.us/img90/8075/screenshotdaledalelaptouv1.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshotdaledalelaptouv1.png)

Hope that helps

---

### Post by Pumalite on 2007-12-13
Make sure everything is 'on' and up to 100%, then try your sound

---

### Post by Want A Pie on 2007-12-13
Where do I turn everything on?

---

### Post by Pumalite on 2007-12-13
At the graphical interface you showed me.

---

### Post by Want A Pie on 2007-12-13
I don't know how to do anything with it...

---

### Post by stchman on 2007-12-13
> **Want A Pie said:**
> I don't know how to do anything with it...

Use the cursor keys when you have the alsamixer up and running.

---

### Post by Want A Pie on 2007-12-13
I put everything on 100, but still no sound
Then I changed the sound device and turned everything to 100, but still no sound!

---

### Post by RomeReactor on 2007-12-13
Hi. Do you get sound from playing files in Totem or Rhythmbox? if so, the make sure you don't have PulseAudio installed. From the terminal, run:
```
sudo apt-get remove pulseaudio pulseaudio-esound-compat
```

---

### Post by Want A Pie on 2007-12-13
I tried playing a song in Rhythmbox, but it doesnt play mp3s...
so I don't know if it works in there
I'll try that code anyway

EDIT: Tried the code, said I don't have it installed, so I can't remove it

---

### Post by ZipoTe on 2007-12-13
what sound card have you got?

---

### Post by Want A Pie on 2007-12-13
I have no idea

---

### Post by ZipoTe on 2007-12-13
...

**EDIT**

ok, have a look at your computer's documents or something, it should tell you what sound card are you using

---

### Post by dustyken on 2007-12-13
I'm experiencing a similar problem.  It was working fine when I first installed 7.10, but after I ran the updates, the sound stopped working.  Any ideas?

---

### Post by deadgobby on 2007-12-13
OK lets go this route please...
 Do you have a sound card or use the on board sound device. If you are not sure. Please type in the terminal this command

  aplay --list-devices 

This will tell you what sound card you have. 

Gobby

---

### Post by RomeReactor on 2007-12-13
What sound card do you have? if you're unsure, run:
```
sudo lshw -C multimedia
```

Do you have more than one sound card in the system? if so, to list them run:
```
aplay -l
```

Please post the output of both commands. Also right-click on the volume control applet in the top panel, select "Open Volume Control", go to "Preferences, check all the channels there, and play with the sound levels of the different channels; maybe the sound card's control channel is different from the default, as is the case with the SoundBlaster Audigy LS.

---

### Post by Want A Pie on 2007-12-13
dale@dale-laptop:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
dale@dale-laptop:~$

dale@dale-laptop:~$ aplay -1
aplay: invalid option -- 1
Try `aplay --help' for more information.
dale@dale-laptop:~$

---

### Post by Pumalite on 2007-12-13
It's small L, not 1. As for the rest: your card is recognized and the module loaded. You might have to compile a new alsa-driver:
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-intel model=3stack

Save the file, close it, reboot, and CROSS YOUR FINGERS!

---

### Post by Want A Pie on 2007-12-13
do I type all of that into the Terminal at once?

---

### Post by Pumalite on 2007-12-13
One line at a time and pressing 'Enter' after each line.

---

### Post by RomeReactor on 2007-12-13
Also try posting the output of:
```
aplay -l
```
Remember, that's a lower case "L".

---

### Post by sixftsix on 2007-12-13
Go to System
          Administration
           Synaptic Package Manager *( put in your Password)*
           Settings
           Repositories

Select the Update Tab
Click to put a check in the box in front of "Unsupported Updates (gutsy-backports)
Close The Repositories Windows
Close Syanaptic

Now select Applications
                   Accessories
                   Terminal

In the Terminal Window Type    **sudo apt-get update** and press Enter
*( put in your Password)*

When the update finishes Type  **sudo apt-get upgrade** and press Enter

Agree to the Updates it offers **Y**

When it finishes updating Close the Terminal.....

Bet you have sound now!   :guitar:

---

### Post by Want A Pie on 2007-12-13
I'm gonna try sixftsix's, then the full code one
I'll post if it works

---

### Post by Want A Pie on 2007-12-13
Neither of them worked...

---

### Post by anewguy on 2007-12-13
Came here from your thread for wireless.  Please do the following:

click "applications" then scroll your mouse to "accessories" then over and down to "terminal" and click.  When that terminal opens up, type the following then cut/paste the output back here and we'll go from there.

lspci  and press enter

:)

---

### Post by anewguy on 2007-12-13
Getting some supper - be back to check in about an hour.:)

---

### Post by magicman5421 on 2007-12-13
What brand of laptop are you using? Because I had a problem like yours with my hp laptop  and i had to install the newest version of alsa, 1.0.15(?), and then sound worked. Also, does your sound work with headphones as opposed to built in speakers?

---

### Post by anewguy on 2007-12-13
Found this thread that may be of interest:

[http://ubuntuforums.org/archive/index.php/t-239995.html]("http://ubuntuforums.org/archive/index.php/t-239995.html")

What it boils down to in that thread is there are problems with alsa support for the HPA MCP51 nVidia.  First and foremost try the instructions posted by Pumalite a few posts ago.  If you have questions on that please post back for more help.  Since you are a newbie, and we've all been there, a lot of this stuff can sound like gobblie-gook, so please ask any questions.  We will reply at the simplest level needed for you to follow.

Also worth noting from the thread I posted above, some people have gone to the OSS sound drivers to get this to work.:)

---

### Post by Want A Pie on 2007-12-14
Sorry, I was away
I have a HP Compaq Presario V3000
Turion 64 X2 
512Mb RAM
80Gb HDD

I went to the link someone posted, and I downloaded Alsa 1.0.15 but I don't know how to install it. lol I clicked the install file, but it opened a text document...

---

### Post by Want A Pie on 2007-12-14
I still need help....

---

### Post by anewguy on 2007-12-14
Open up a terminal window again, then do each of these commands and copy/paste their output back here.  Thanks!

cat /proc/asound/cards     and press enter

dmesg      and press enter



This can help us a little.  Also, could you either explain what you did for alsa 1.0.15 or point me to the link you followed?  I would need to look at that to get an idea what you did and what you need to do.:)

BTW - depending on your screen resolution, you may not be able to see some distinctions on PumaLite  previous post:  look carefully as some of what appear to be a single dash "-" are actually 2 dashes "--", and it's important to get those right or things won't be recognized as they need to in the script.  The line in particular I am referring to is:

sudo ./configure --with-cards=hda-intel     <----- note that there are 2 dashes in front of "with-cards="

I really believe if you follow their instructions you should get 1.0.15 installed.  There may be somethings with other switches or aliases after you have done that that may still need to be done, but try that first then report back here.  Good luck!!

---

### Post by Want A Pie on 2007-12-14
It returned:

dale@dale-laptop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 22

I followed a link I read somewhere in the forums, but I don't know what it was anymore.

---

### Post by emitchlpd on 2007-12-14
I'm going to chime in here to say that I'm having the exact same problem with my new Compaq F730US, with the nVidia Corporation MCP51 High Definition Audio. It looks like it's loaded, but I get no sound.

I've tried alsa-driver-1.0.15, lib, and utils with no luck.

This is the output from my lspci:

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 10
        Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

On this bug report on the ALSA site it looks like there's a patch that might offer some hope:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

Look about 3 quarters of the way down at a patch by this guy:
(0016822)
jwdonze
09-09-07 23:21

I'll be trying that this weekend and will follow up on whether it's successful.

---

### Post by Want A Pie on 2007-12-14
OK, I'm glad it isn't just me that's having the problem then!
Could someone could show me the code or something to download the alsa driver 1.0.15?
and I also need the IcedTea thing (icedtea-java7-jdk_7~b23-1.5~20071124-4_amd64.deb), but I don't know much about the terminal.

Thanks

---

### Post by Pumalite on 2007-12-14
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
(cross your fingers)

---

### Post by anewguy on 2007-12-14
> **Want A Pie said:**
> OK, I'm glad it isn't just me that's having the problem then!
Could someone could show me the code or something to download the alsa driver 1.0.15?
and I also need the IcedTea thing (icedtea-java7-jdk_7~b23-1.5~20071124-4_amd64.deb), but I don't know much about the terminal.

Thanks

Pumalite's reply a page or 2 back gives you step by step for that.  Also, as mentioned above, it's not just you - this is a widespread problem.  There are ways to get it to work, but they involve some detailed things I don't know if you know enough about Ubuntu yet to do or not.  There are several alias's and things that can get set to help out.  I believe I posted a link to one of those threads a little ways back in this post.  I know it seems like a hassle that things don't just go in easy and work - some people say it's the price for free open software, some blame manufacturers for not providing Linux support.  Some of us actually have no problems with our sound, etc., but I guess we are the lucky ones.  So, keep in mind you will probably have to do a lot of reading in other posts as well, because there really isn't a "just do this" answer.  You'll need to read, interpret, read another, meld it with other stuff you've read, etc..

If you want an idea on what to look for, just do this search in Yahoo! or the search engine of your choice:

ubuntu HDA MCP51


It will return a LOT of things for you to go through.  I've been reading a lot of those since yesterday.  You will see a lot of "it don't work" things, but keep reading as there are little tid-bits interspersed with those.

I really do wish you the best of luck.  I know it's a pain to have to hunt around on your own and try things - believe me - I used to have a Gateway laptop when I was brand new to Ubuntu, and it took a long time and can get frustrating.  Using Linux of any sort can have a learning curve different of that for Windows, and you will probably find yourself "deeper" into things than might be needed to use Windows, but at least I feel that even with the frustrations it is a fun learning experience.  We've all been where you are at one time or another, so hang in there!

After reading some of the other posts, links, etc., if you have more questions please post back here so we can try to help.  Sometimes the help may not be a speedy as one would like, but it's free and made of a bunch of people who have been where you are and just want to try to help.  I still come up with tons of things I look to here for help on, but I've also learned enough, almost by accident, that at least those things aren't quite a newbie "ish" as they were at first.:)

---

### Post by Want A Pie on 2007-12-14
I'll try Pumalite's again
last time it said it was invalid code or something
if it doesn't work, i'll search the net for something
thanks

---

### Post by Want A Pie on 2007-12-14
Didn't work:

dale@dale-laptop:~$ sudo apt-get install build-essential ncurses-dec gettext
[sudo] password for dale:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package ncurses-dec
dale@dale-laptop:~$ 
dale@dale-laptop:~$ dale@dale-laptop:~$ sudo apt-get install build-essential ncurses-dec gettext

bash: dale@dale-laptop:~$: command not found
dale@dale-laptop:~$ [sudo] password for dale:
bash: [sudo]: command not found
dale@dale-laptop:~$ Reading package lists... Done
bash: Reading: command not found
dale@dale-laptop:~$ Building dependency tree       
bash: Building: command not found
dale@dale-laptop:~$ Reading state information... Done
bash: Reading: command not found
dale@dale-laptop:~$ build-essential is already the newest version.
bash: build-essential: command not found
dale@dale-laptop:~$ E: Couldn't find package ncurses-dec
> 
> dale@dale-laptop:~$ sudo apt-get install build-essential ncurses-dec gettext
> [sudo] password for dale:
> Reading package lists... Done
> Building dependency tree       
> Reading state information... Done
> build-essential is already the newest version.
> E: Couldn't find package ncurses-dec
bash: E:: command not found
dale@dale-laptop:~$ sudo apt-get install build-essential ncurses-dev gettext
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
gettext is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dale@dale-laptop:~$ sudo apt-get install linux-headers-'uname-r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname-r
dale@dale-laptop:~$ mkdir ~/alsa-src && cd ~/alsa-src
mkdir: cannot create directory `/home/dale/alsa-src': File exists
dale@dale-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2)
--09:55:27--  [ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.15.tar.bz2)
           => `drive...1.0.15.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive...1.0.15.tar.bz2 ... 
No such file `drive...1.0.15.tar.bz2'.

dale@dale-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/lib/a...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/a...1.0.15.tar.bz2)
--09:55:46--  [ftp://ftp.alsa-project.org/pub/lib/a...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/a...1.0.15.tar.bz2)
           => `a...1.0.15.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/lib ... done.
==> PASV ... done.    ==> RETR a...1.0.15.tar.bz2 ... 
No such file `a...1.0.15.tar.bz2'.

dale@dale-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/utils...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils...1.0.15.tar.bz2)
--09:55:59--  [ftp://ftp.alsa-project.org/pub/utils...1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils...1.0.15.tar.bz2)
           => `utils...1.0.15.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR utils...1.0.15.tar.bz2 ... 
No such file `utils...1.0.15.tar.bz2'.

dale@dale-laptop:~$ sudo tar xjf alsa-driver-1.0.15.tar.bz2
tar: alsa-driver-1.0.15.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dale@dale-laptop:~$ sudo tar xjf alsa-lib-1.0.15.tar.bz2
tar: alsa-lib-1.0.15.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dale@dale-laptop:~$ sudo tar xjf alsa-utils-1.0.15.tar.bz2
tar: alsa-utils-1.0.15.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dale@dale-laptop:~$ cd alsa-driver-1.0.15
bash: cd: alsa-driver-1.0.15: No such file or directory
dale@dale-laptop:~$ sudo ./configure --with-cards=hda-intel
sudo: ./configure: command not found
dale@dale-laptop:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
dale@dale-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
dale@dale-laptop:~$ cd ../alsa-lib-1.0.15
bash: cd: ../alsa-lib-1.0.15: No such file or directory
dale@dale-laptop:~$ sudo ./configure
sudo: ./configure: command not found
dale@dale-laptop:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
dale@dale-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
dale@dale-laptop:~$ cd ../alsa-utils-1.0.15
bash: cd: ../alsa-utils-1.0.15: No such file or directory
dale@dale-laptop:~$ sudo ./configure
sudo: ./configure: command not found
dale@dale-laptop:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
dale@dale-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.

anyone know where I went wrong?

---

### Post by Want A Pie on 2007-12-14
Someone with the same problem as me fixed theirs by downloading the alsa driver
I downloaded it, but I have no idea how to install it :D

---

### Post by Pumalite on 2007-12-14
Where did your alsa-driver end up? You have to put the path to the driver after sudo.

---

### Post by RomeReactor on 2007-12-14
> **Want A Pie said:**
> E: Couldn't find package ncurses-dec

Try copy/pasting the commands to avoid typos.

---

### Post by Riffer on 2007-12-14
OK going out on a limb here.  I have a nVidia MB which sounds like is what you have. And I too had trouble getting sound to work.   Its my understanding that the onboard audio is an USB device and how I fixed it is by 

In the terminal put in

sudo nano /etc/modprobe.d/alsa-base

in that file down at the bottom is this

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

Hash out the line "snd-usb-audio index=-2
So it looks like

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# options snd-usb-audio index=-2
options snd-usb-usx2y index=-2


save and exit and reboot. Thats it!!!

I hope this helps.

---

### Post by emitchlpd on 2007-12-14
> **Riffer said:**
> OK going out on a limb here.  I have a nVidia MB which sounds like is what you have. And I too had trouble getting sound to work.   Its my understanding that the onboard audio is an USB device and how I fixed it is by 

In the terminal put in

sudo nano /etc/modprobe.d/alsa-base

in that file down at the bottom is this

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

Hash out the line "snd-usb-audio index=-2
So it looks like

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# options snd-usb-audio index=-2
options snd-usb-usx2y index=-2


save and exit and reboot. Thats it!!!

I hope this helps.

I tried it, but no luck for me...

---

### Post by Want A Pie on 2007-12-14
OK that didn't fix my sound
it did make everything on my computer larger
so now I have another problem
how do i make everything smaller again?

---

### Post by RomeReactor on 2007-12-14
Do you mean that the icons are larger, or that it changed your screen's resolution?

---

### Post by Want A Pie on 2007-12-14
Everything on my screen is larger, the panels are bigger, icons are bigger.
Also the top of my firefox page is blue, whereas it used to be orange, and my help, log off, sound and back to desktop icons have all changed...

---

### Post by Want A Pie on 2007-12-14
could someone tell me what is supposed to be in the:
 sudo nano /etc/modprobe.d/alsa-base
because Riffer's code completely changed my computer...
it is almost impossible to do anything any many of the icons are overlapping eachother

P.S  I STILL HAVE NO SOUND!

---

### Post by RomeReactor on 2007-12-15
Seems those instructions somehow changed your theme and resolution; go to "System->Preferences->Appearance" and on the "Theme" tab, select **Human**. Then go to "System->Preferences->Screen Resolution" and change that to your previous one.

I'm sorry you're having so much trouble getting sound to work, but nVidia sound chipsets are very problematic, as a search of these forums has showed me; too many people are in the same boat.

---

### Post by Riffer on 2007-12-15
I'm sorry. I didn't want you to copy my whole code, just to hash out the one line for usb sound.  I thought my instructions were pretty clear.  Did you erase the rest of the file?

---

### Post by emitchlpd on 2007-12-15
I gave the situation some thought, and I think I've figured out what's going on (in my case anyway, and I have sound working now).

Couple of things. To start the installer's Live CD for Gutsy, I had to add the "noapic" and "irqpoll" boot options to the kernel line in grub. Apparently Ubuntu figured that these are necessary for my computer during the install process, because the default boot option in /boot/grub/menu.lst contained those options.

I went into /boot/grub/menu.lst and removed the "noapic" and "irqpoll" options from my default boot menu item. NB: You shouldn't necessarily do this! This is what worked for me, bringing me back to a "stock" ubuntu kernel.

By searching Google for my chipset name (MCP51), my codec (Conexant CX20549), and my driver (snd-hda-intel), I came across a Chinese page with some debug information on a working configuration. This page indicated that the option "model=laptop-hp" was passed to the snd-hda-intel driver (this is one of the items you'll find in the Alsa "Configuration.txt" file. I edited /etc/modprobe.d/alsa-base and /etc/modprobe.d/snd-hda-intel.modprobe to contain the line:

options snd-hda-intel model=laptop-hp

My understanding is that this line tells the driver how to route sound output for the speaker and the microphone. "laptop-hp" is what works for my Compaq laptop. Yours may be different.

Anyway, "noapic" and "irqpoll" are related to how the kernel handles inturrupts, and I suspect that passing those options was part of the reason the sound card wasn't working. The "laptop-hp" option was required to tell the snd-hda-intel driver where to direct the output for the speakers and headphone jack.

I'm definitely not a hardware engineer, but I know a few so that's why I'm venturing these guesses.

Hopefully others will benefit from this information. Please follow up if you'd like me to post more detailed information.

---

### Post by Want A Pie on 2007-12-15
There is only one screen resolution (640x800) in the options
and I did copy your instructions how you had them
Emitchlpd, your info seems good, but I have no idea how to do it

---

### Post by emitchlpd on 2007-12-15
Want a Pie, my initial thoughts are that your screen resolution problems are separate from your sound problems. The common NVidia theme might make one think that they're related but I think you should attack them separately.

I'm not sure how many individual chips are on our motherboards. Nvidia should be associated with graphics more than anything else. I think the connection to the "chipset" for sound/network/IO etc... is more of a marketing thing than an engineering thing.

Without cracking open my new laptop, my speculation is that there are fewer "chips" on here than your average laptop, as silicon has a lesser marginal cost than printed circuit boards. I think for consumer-level hardware the tendency is to integrate numerous functions onto one chip (piece of silicon) and slap the strongest brand name on it (NVidia).

So, I think there's some integrated processor in my system that uses the Conexant design, and it happens to be branded as NVidia.

As far as graphics, I think you should get that back to normal before worrying about sound. Is 640x480 the only option you're given in System->Administration->Screens and Graphics?

---

### Post by emitchlpd on 2007-12-15
> **Want A Pie said:**
> There is only one screen resolution (640x800) in the options
and I did copy your instructions how you had them
Emitchlpd, your info seems good, but I have no idea how to do it

Ok, I didn't read this carefully enough. I think your first goal should be to restore the "alsa-base" file to what it was originally, because whatever changes happened seemed to screw up your video.

Can you post the contents of your /etc/modprobe.d/alsa-base at this moment?

---

### Post by Want A Pie on 2007-12-15
yes, 640x480 is the only one in my screens and graphics, it used to have more before tho

what is /etc/modprobe.d/alsa-base

---

### Post by Want A Pie on 2007-12-15
I think I found it:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by emitchlpd on 2007-12-15
That looks like the default. So I wouldn't worry about that particular file for now.

[edited to remove email address -- should have used private message]

---

### Post by Pumalite on 2007-12-15
Make sure you are running -14-generic and not -i386
uname -a
Also I found this:
1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.

---

### Post by Want A Pie on 2007-12-15
I can't make a new account, because everything is so huge, I can't see all the way down the form...
EDIT: managed to make one :D will test now

---

### Post by Want A Pie on 2007-12-15
Tested it, and no sound :(
and I don't know what you mean by running -14 generic
I will email u now emitchpld
EDIT: Emailed you, but because of screen problems I couldn't get to the box to write anything, so I just sent a blank email, maybe if you just PM'ed me on here it would be easier?

---

### Post by crazyfish666 on 2007-12-15
> **Pumalite said:**
> sudo apt-get install build-essential ncurses-dev gettext
*snip*
(cross your fingers)

This looks very similar to the first step of the code here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) that caused me to lose my audio. I was attempting to get a microphone to be recognized by and work on my computer and carried out the first step of the code on that link and then rebooted. When I logged back on I had no sound and when I tried to do the second step and inputted
> cat /proc/asound/card0/codec#* | grep Codec
it came back with
> cat: /proc/asound/card0/codec#*: No such file or directory
And when I decided I would figure out what my sound card model was some other way and inputted the next command
> /usr/src/2.6.22/Documentation/sound/alsa/A LSA-Configuration.txt
I get back
> bash: /usr/src/2.6.22/Documentation/sound/alsa/ALSA-Configuration.txt: No such file or directory

I seem to have somehow put myself in the possition of the OP as I now have no sound and do not seem to be able to get it back no matter how much I fiddle. I tried re-imputting the code as it was in your post Pumalite, but that didn't help.

---

### Post by Want A Pie on 2007-12-15
Well my Ubuntu came with no sound, and when I was trying to fix it, my screen resolution has become large, and I can't fix it...

---

### Post by crazyfish666 on 2007-12-15
> **Want A Pie said:**
> Well my Ubuntu came with no sound, and when I was trying to fix it, my screen resolution has become large, and I can't fix it...

I am rather hoping that whatever works for you to fix it will work for me because frankly I can't seem to find any other way to fix it.

---

### Post by Pumalite on 2007-12-15
> **crazyfish666 said:**
> This looks very similar to the first step of the code here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) that caused me to lose my audio. I was attempting to get a microphone to be recognized by and work on my computer and carried out the first step of the code on that link and then rebooted. When I logged back on I had no sound and when I tried to do the second step and inputted

it came back with

And when I decided I would figure out what my sound card model was some other way and inputted the next command

I get back


I seem to have somehow put myself in the possition of the OP as I now have no sound and do not seem to be able to get it back no matter how much I fiddle. I tried re-imputting the code as it was in your post Pumalite, but that didn't help.
Sorry to hear that. Sometimes it works. Sometimes it doesn't.

---

### Post by crazyfish666 on 2007-12-15
> **Pumalite said:**
> Sorry to hear that. Sometimes it works. Sometimes it doesn't.

Any way to get my sound back? :) Or am I stuck without it forever? :icon_frown: Or do I just try the same things Want A Pie does?

---

### Post by Want A Pie on 2007-12-15
nothing i've tried has worked so far, and I seem to be worse now then I was when I first tried to fix the sound

---

### Post by Pumalite on 2007-12-15
I've seen a lot of people having success compiling latest alsa-driver. See one of my posts.

---

### Post by emitchlpd on 2007-12-15
Ok, Want a Pie, the screen resolution problem is related to whichever driver XWindows is using. Did you do anything related to "restricted" drivers? Assuming you have an Nvidia chip, you want your system to go ahead and use the "restricted" Nvidia drivers.

---

### Post by emitchlpd on 2007-12-15
> **Pumalite said:**
> I've seen a lot of people having success compiling latest alsa-driver. See one of my posts.

For me the vintage of the driver wasn't the problem. It was just a matter of getting "noapic" and "irqpoll" out of my kernel options, and passing "laptop-hp" as an option to the "snd-hpa-intel" driver.

---

### Post by foppeh on 2007-12-15
I have sound.

I am reading this thread with similar problems on an Acer Aspire 7520 laptop without sound in Ubuntu. I found this thread: [http://ubuntuforums.org/showthread.php?t=615649&highlight=alsa](http://ubuntuforums.org/showthread.php?t=615649&highlight=alsa) that solved my problem. It looks hopeful for you guys also, but this is a warning: I am a newby also :)

---

### Post by Want A Pie on 2007-12-15
My display went dodgy after doing pumalite's instructions (although I don't know if I did them correctly) on page 4
Other than that, I don't think I did anything with "restricted" drivers

---

### Post by emitchlpd on 2007-12-15
That was an assumption on my part. I'm wanting to get your video problem solved before your audio problem. There are two drivers for your video "card". There's the "nv" driver, which is the open source driver which does not support 3d and advanced acceleration for 2d (somebody correct me if I'm wrong). Then there's the nvidia driver, which is produced by NVidia, is not open-source, but is provided by Ubuntu through the "restricted" channel because it's useful but not open.

Anyway, I wonder if X is using a useful driver for you. Video cards tend to default to a certain level, often 640x480 if they can't find something better. 

I'm conscious of the amount of time you're spending here. Keep in mind the amount of time it would take you to start from scratch with a clean Gutsy Gibbon install. 

Hang in there. You and I have the same chipset (NVidia MCP51) and same codec (Conexant CX20549). I'm listening to Steve Earle on the Intarwebs, who might as well be an Aussie. We're going to get it figured out.

---

### Post by Want A Pie on 2007-12-15
I don't want to re-install because the sound might not work anyway, since it didnt when I first installed Ubuntu. Should I try running from a live CD to see if the sound will work?

---

### Post by RomeReactor on 2007-12-15
If running the Live CD gets your sound working, see how alsa is configured:
```
cat /etc/modprobe.d/alsa-base
```

Maybe you could email yourself a copy of the file, or make a copy in a USB drive, and use that in your installed system. Just a thought.

---

### Post by cwmaxson on 2007-12-15
Want A Pie,

I'm sorry, but this sounds like the most heinous post/advice I've seen.  I'm sorry to say it, but a clean install is probably your best option.  You've tried so many things on top of each other that untangling the knot will take more time than it's worth.  Once you've done that, I think this will fix it:

type:
**sudo gedit /etc/modprobe.d/alsa-base**
in a terminal

this opens a text file which you should add 
**options snd-hda-intel model=3stack**
to the end.

You will then have to reboot.

---

### Post by Want A Pie on 2007-12-15
ok, i'll run the Live CD, and post if my sound is fixed or not

---

### Post by emitchlpd on 2007-12-15
> **cwmaxson said:**
> Want A Pie,

type:
**sudo gedit /etc/modprobe.d/alsa-base**
in a terminal

this opens a text file which you should add 
**options snd-hda-intel model=3stack**
to the end.

I'm not 100% sure. I think cwmaxon is right that it's hard to say how far you are from a "default" install, so starting from scratch is probably the shortest path to a blank slate that you have.

model=3stack may or may not be the right configuration for your particular system. My configuration proved to be model=laptop-hp. As mentioned, these are defined in that Alsa Configuration file. Whether you have the Alsa drivers that came with your default Ubuntu install, or you downloaded them separately, they're still going to dance to the tune you call in /etc/modprobe.d/alsa-base

When you edit that file, you want to edit it for the exact configuration you have. For me, it was adding a line as follows:

options snd-hda-intel model=laptop-hp

That told the "snd-hda-intel" driver that I have a system wired according to the "laptop-hp" pattern. Yours may or may not be wired the same way. 

It's hard for me to say what the current state of your system is, I want a pie. I want to you to be good-to-go in as little time as possible, and you might be at a spot where re-installing from scratch would get you there quicker than undoing what attempt's you've done so far.

The video issue is a mystery. I'm not sure why that's happening. If you've done anything in /etc/X11 you should let us know.

Seriously though it seems your shortest path at this point is to reinstall.

---

### Post by Want A Pie on 2007-12-15
I'm running from Live CD now, no sound still though
I'll try Cwmaxon's code though

and the video issue is from the code on page 4 that Pumalite said

EDIT: Can I do Cwmaxon's code if I'm on Live CD?

I don't want to reinstall because of how many downloads I had to do (updates etc.) for my previous one, my download limit is looking a bit tight

---

### Post by emitchlpd on 2007-12-15
Ok, if you have a download cap, then hold back for a sec. I didn't take that into account -- I was trying to save you time but if you have a bandwidth limitation then that's another thing to consider.

Try rebooting into your original system, without doing the reinstall. If I were you, I would treat the video resolution problem as a separate issue from your sound issue. I would attempt to solve the video resolution problem first. Once that's solved, then you should work on the audio issue. 

You might consider starting a new thread to solve the video issue. Try to think of what you might have done to change the video situation. Any changes to files in /etc/X11 could be responsible for that change.

Sorry it's working out to be a trial for you. You get points for perseverance.

---

### Post by Want A Pie on 2007-12-15
Lol, I think I'll get the video working then stop for a while
I can live without sound, I do have an iPod and speakers so I won't miss out on music :D

Thanks btw for helping me so much!

I'll reboot Ubuntu from my harddrive

While I'm on Live CD, is there any settings I could find to use with my installed version?

---

### Post by Want A Pie on 2007-12-15
I read somewhere that this file helps your sound:
[http://packages.ubuntu.com/gutsy/sound/asoundconf-gtk](http://packages.ubuntu.com/gutsy/sound/asoundconf-gtk)
I don't know how to download or install it, but can you check it out to see if its any good?

---

### Post by emitchlpd on 2007-12-15
There may be, if sound is working with the live CD. I don't know the exact commands to run to know what the configuration is with the Live CD, though. Maybe others can post with those answers.

The page that let me on the right path was this one:

[http://ja.pastebin.ca/790310](http://ja.pastebin.ca/790310)

I'm pretty sure that's Japanese. Anyway the output is the universal language of computer-speak, aka English. (I'm just a dumb American). 

The "laptop-hp" was a solid lead for me, and I gave it a try without the "noapic" or "irqpoll" options passed to the kernel at boot time, and it worked.

I hope you can get it figured out. Remember, if you're confused, that means you're learning.

Good luck!

---

### Post by Want A Pie on 2007-12-15
Lol, it was Japanese, here is the english one [http://pastebin.ca/790310](http://pastebin.ca/790310)
I don't know what I'm supposed to do with that though

---

### Post by tekwerx on 2007-12-15
I havent seen anyone offer to tell them to run alsaconf...usually works for me, anyhow....


Just a thought.





*edit* Apparently I cant spell.

---

### Post by Want A Pie on 2007-12-15
How do I run "alsaconf"?
Also, my resolution settings are now broken, anyone know how I can fix?

---

### Post by Want A Pie on 2007-12-15
I think I'll start a new post asking if anyone knows how to fix my resolution. Thanks everyone that has helped me with my sound problem, but I don't need sound right now.

---

### Post by tekwerx on 2007-12-15
> **Want A Pie said:**
> How do I run "alsaconf"?
Also, my resolution settings are now broken, anyone know how I can fix?

alsaconf = ALSA (Advanced Linux Sound Architecture) configurator.  

I just tried messing with it in my Gutsy 7.10 here, and it seems it's not installed.  Hm.  Im guessing that its been removed by the devs?  Its there with my Debian install.  

*after some searching*

Ah, my bad.  I'm so sorry.  It appears the devs did indeed remove alsaconf from Ubuntu.  So much for an easy fix.  

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)   might be a good place to start to see how to fix your sound issue.  I see theres a link there for an upgraded version of the help, but unfortunately for me, it appears to be a dead link.  Click on search up top here in the forums and search around for some other helps that might be able to help you more with your sound.  

As for your esolution, go to System, then Preferences, then Screen Resolution and see if you can change it there.

---

### Post by RomeReactor on 2007-12-15
Want A Pie, to restore the resolution you can try this: press CTRL+ALT+BACKSPACE to switch to a terminal, and enter:
```
sudo /etc/init.d/gdm stop
```
followed by:
```
sudo dpkg-reconfigure xserver-xorg
```

Accept all the defaults, unless you know that a setting is different from what it suggests you; in case of a nVidia video card, select **nvidia** as the driver. If the display doesn't start automatically afterwards, enter:
```
sudo /etc/init.d/gdm start
```

---

### Post by Want A Pie on 2007-12-16
thanks, I got the resolution fixed, but not the sound...
atm i'm trying to get Java working tho lol

---

### Post by trimethoxy on 2007-12-16
I am having a similar problem, but I am getting sound of my headphone jack, but not my laptop speakers.  

I tried to install the updated alsa drivers but i get the following error:
~/alsa-src/alsa-driver-1.0.15$ sudo ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by trimethoxy on 2007-12-16
> **Pumalite said:**
> sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
(cross your fingers)

when i get to the compiling step, the following error occurs:

The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

what do i need to do now?

---

### Post by Pumalite on 2007-12-16
Make sure you have build-essential:
sudo apt-get install build-essential
If after that you still have problems, try:
sudo apt-get install linux-headers-`uname -r`

---

### Post by crazyfish666 on 2007-12-16


Okay! Progress! Now I am only stuck on one little thing which shows my complete lack of ubuntu knowledge. I have followed all the steps in [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") link and I am now trying to close /etc/modprobe.d/alsa-base I can't get it to work (this would be because I don't know how :) ). At the bottom of the terminal window it says
>  ^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

but I don't know how to input ^X as if I simply type it and hit enter I just go to another line of the document and have to backspace it out again, and I am not inventive enough to think of any other ideas :). Help! 
After this I can reboot and tell y'all if it works, if it does maybe it will help Want A Pie.

---

### Post by crazyfish666 on 2007-12-16


Ooo, I figured it out by myself. I really am an idiot. ^=hold down Ctrl. I never claimed to be any good at this computer stuff :) .

---

### Post by crazyfish666 on 2007-12-16


Dang! No help there.

---

### Post by trimethoxy on 2007-12-16
> **Pumalite said:**
> Make sure you have build-essential:
sudo apt-get install build-essential
If after that you still have problems, try:
sudo apt-get install linux-headers-`uname -r`

Alright, the next error i got was:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

---

### Post by crazyfish666 on 2007-12-17
> **trimethoxy said:**
> Alright, the next error i got was:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

That is exactly the same as what I am getting. But what is odd is that if I try to exit a document without saving it still beeps at me, or if I backspace too far in certain places. These were two things that were originally never controlled by the volume control (they still beeped when it was on mute) so I am beginning to think that the problem is not in the system communicating with the speakers, but in the volume control not recognizing that it can communicate with them. Do you also get these beeping sounds or have you completely lost sound??

---

### Post by trimethoxy on 2007-12-17
As far as I can tell, I've completely lost sound.  Before, I could get it through speakers, but now I've got nothing.  It may be possible that I did this when I included the hda-intel string in "sudo ./configure --with-cards=hda-intel".  Would that be specific to a particular sound card, is that a generic value?  How can I found out which values there are, and if I chose the wrong one, undo it, and start over again?

---

### Post by crazyfish666 on 2007-12-17
> **crazyfish666 said:**
> That is exactly the same as what I am getting.

Also, I just tried going into Alsamixer and it looked like this
[IMG]http://i129.photobucket.com/albums/p206/crazyfish666/Alsamixer1.png[/IMG]

And when I go to "Edit" and place my mouse over "Sound Card Properties" the bottom bar says "configure the current sound card" and if I click then the Alsamixer closes and nothing else happens.

---

### Post by trimethoxy on 2007-12-17
How do you get your Alsamixer to come up like that? I typed it into the terminal and all I got was "alsamixer: function snd_ctl_open failed for default: No such device."

---

### Post by crazyfish666 on 2007-12-17
> **trimethoxy said:**
> How do you get your Alsamixer to come up like that? I typed it into the terminal and all I got was "alsamixer: function snd_ctl_open failed for default: No such device."

Since your system does not seem to be registering it as a device this may not work, but I suppose it is worth a try. In the top bar click "Applications", move your mouse down to hover over "Sound & Video" and look in the drop down menu that appears, there will hopefully be one that reads "GNOME ALSA Mixer" if you click on that then it will open Alsamixer. Best of luck.

---

### Post by trimethoxy on 2007-12-17
> **crazyfish666 said:**
> That is exactly the same as what I am getting. But what is odd is that if I try to exit a document without saving it still beeps at me, or if I backspace too far in certain places. These were two things that were originally never controlled by the volume control (they still beeped when it was on mute) so I am beginning to think that the problem is not in the system communicating with the speakers, but in the volume control not recognizing that it can communicate with them. Do you also get these beeping sounds or have you completely lost sound??

Ok, I get the system speaker beeping, but nothing else.  

And I don't see the ALSA mixer in the applications pull-down.

---

### Post by crazyfish666 on 2007-12-18
> **trimethoxy said:**
> Ok, I get the system speaker beeping, but nothing else.  

And I don't see the ALSA mixer in the applications pull-down.

*Does a little jig* :) I have sound!! :). What I would recommend you do (this comes with a disclaimer that I know very little about ubuntu) is go to "System" in the top bar and then "Administration" and then "Synaptic Package Manager". Search "Alsa" and look down the list that it creates for the packages called "alsa-base", "alsa-utils", "gnome-alsamixer" and "libasound2" and either mark them for installation or mark them for reinstalation depending on whether or not they are already installed (you do either by right clicking on them and going down the drop down menu). Hit apply and go through the download process. 

Hopefully you will then see GNOME ALSA Mixer in your "Applications" menu. If not, or if you are unable to complete any of those steps then go to this [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) page and follow this instructions given. Reboot your computer at the very end. When you log back on hopefully GNOME ALSA Mixer will be in your "Applications" menu. If not then I can't help you, if yes then move onto the next step if you still do not have sound.

Go into "Terminal" and type in

find /lib/modules/ -name *hda-intel*

hopefully you will then get these two hits plus maybe one or two others;

/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko

The second one is the one alsa installs, the first one is a bugfix update from ubuntu.

Remove the first one by typing in

sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

and then type in

sudo depmod -a

and then

sudo modprobe snd-hda-intel

then reboot and hopefully you have sound.

Credit for the last set of instructions goes to m94mni who helped me fix my computer.

---

### Post by agerg on 2007-12-18
Just so those who are having sound problems don't feel alone...I too am having sound problems and have installed the latest version of alsa (using the link to that script [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)) with no avail...I only get sound through my headphones. In volume control I only have headphones in the switches panel :(
The result I get from running "sudo lshw -C multimedia" is:
```
*-multimedia            
       description: Audio device
       product: SB450 HDA Audio
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

```
and from running "aplay -l" is
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by emitchlpd on 2007-12-19
> **emitchlpd said:**
> 

Couple of things. To start the installer's Live CD for Gutsy, I had to add the "noapic" and "irqpoll" boot options to the kernel line in grub. Apparently Ubuntu figured that these are necessary for my computer during the install process, because the default boot option in /boot/grub/menu.lst contained those options.

I went into /boot/grub/menu.lst and removed the "noapic" and "irqpoll" options from my default boot menu item. NB: You shouldn't necessarily do this! This is what worked for me, bringing me back to a "stock" ubuntu kernel.



I thought I'd follow up on this today, as the kernel update that came through undid this fix that worked for me, leaving me without sound again. When the system updated the kernel, it wrote over /boot/grub/menu.lst with the original kernel options from install (noapic & irqpoll).

I had to remove these from the list and reboot in order for the audio drivers to load correctly again.

I'm going to try to figure out how the system knows to add those two options when it updates the grub menu, and see if I can't keep the behavior from happening.

---

### Post by Want A Pie on 2007-12-20
My sound is working, I thought I should post it on here incase someone was looking through here
What is funny is that my 12 year old brother that has never used Ubuntu fixed it! He was trying to look at Youtube on my laptop, and installed something that got it working :D
Thanks again to everyone that helped.

---

### Post by artrimbaud on 2007-12-20
> **Pumalite said:**
> It's small L, not 1. As for the rest: your card is recognized and the module loaded. You might have to compile a new alsa-driver:
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
mkdir ~/alsa-src && cd ~/alsa-src
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

Reboot
Code:

sudo gedit /etc/modprobe.d/alsa-base

Add this line at the end of the file:
Code:

options snd-hda-intel model=3stack

Save the file, close it, reboot, and CROSS YOUR FINGERS!

Hello all,

First post in the forums.  I just wanted to say thank you to Pumalite for the above information.  I've been working on this sound thing all morning, and this solution worked for me.  And thanks to everyone who posted info in this thread.  I think I read through it 3 times.  :)

-b.

---

### Post by gumpontheweb on 2007-12-20
I am the original user on the computer and I don't get any sound through the totem player?
Vlc works and plays movies. Just the totem player with NO sound, No audio??? The speaker looking volume control is grey and the menu volume controls are also inactive?

the video is fine.
Is there anything I can do?

---

### Post by searchesend on 2007-12-20
I tried your magic code that you posted early on in this forum and after rebooting (and having my fingers crossed) I've ended up with :

aplay -l
aplay: device_list:205: no soundcards found...

When I click the volume control icon in the tray it says:

No volume control GStreamer plugins and/or devices found


You seem to know what you're about and I don't have a monkeys so any help is appreciated!

---

### Post by artrimbaud on 2007-12-21
> **artrimbaud said:**
> Hello all,

First post in the forums.  I just wanted to say thank you to Pumalite for the above information.  I've been working on this sound thing all morning, and this solution worked for me.  And thanks to everyone who posted info in this thread.  I think I read through it 3 times.  :)

-b.

Ok, well, I had to reinstall Ubuntu, and when I first installed it, my sound was working.  I started updating the install, and afterwards my sound stopped working.  I tried the same solution as before, and now my Audigy sound card is not recognized.  I don't know how to get the system to reconfigure my sound devices so it will be recognized.  Any help would be appreciated.

-b.

---

