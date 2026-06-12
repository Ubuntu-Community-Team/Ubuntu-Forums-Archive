---
title: "Failed making sound work, had to reinstall, now what?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-02-16
I am up against the seemingly common Realtek ALC655 barrier.  What is most unfortunate is, despite how many threads I have found regarding this, there is no 'Beginner Friendly' HowTo that I have found.  I attempted to deal with it the best I could with my lack of understanding, and failed so miserably that I was unable to log back into GNOME. Accessing the Failsafe Terminal did me no good as I've no idea WHAT would need to be done to have fixed whatever went wrong. 

Hardware:
CPU: AMD64 3400+
Mobo: BIostar GeForce 6100-M9 
Sound: Onboard Realtek ALC655 6-channel AC97
1GB RAM
40 GB HDD

The most helpful thread I had found was this: [http://www.ubuntuforums.org/showthread.php?t=341219&highlight=realtek+alc655](http://www.ubuntuforums.org/showthread.php?t=341219&highlight=realtek+alc655)

However, this is as far as I'd gotten, as much as I can recall, anyway:

Downloaded the file referenced in the last post of the above thread.  
Not knowing where the file needed to be, it went to the Desktop and extracted there. 
Tried clicking "Install" in the GUI, but that failed.
Opened Terminal, cd to Desktop and tried ./install
Noticed that it wanted gcc installed. 
Used Synaptic to install gcc.
I remember it saying that it couldn't find a C compiler in $PATH after I'd installed gcc. 

I closed Terminal to try to do more reading.  Upon trying to restart Terminal, I found that it would not, in fact, restart.  Hm.  I shut the machine down and wander off.  When I returned, as far as I could get was the login page. 

A lovely message greeted me telling me how my session lasted less than 10 seconds and that I should attempt using a Failsafe mode. 

There was an option to view errors, I believe, and the last line is what I took note of:
x-session-manager: error while loading shared libraries: libasound.so.2  cannot opne shared object file: No such file or directory.

Well, Failsafe GNOME wouldn't even work, and  after getting into Failsafe Terminal, I realized I didn't know what I was doing, and that it'd be pointless to stay in there, and decided to cut my losses and reinstall.  VERY disappointing. 

So, what does it take to get a warm and fuzzy hand-holding explanation of what needs to be done in order to use the available driver download to do what it is meant to do and have this box make some noise?  If there is one somewhere and I've missed it, feel free to scold me so long as you point me in the direction of this wond'rous document.  

I have used Synaptic to install gcc, in anticipation of what might come, but have done NOTHING else so far. 

Thank you in advance for any help you can give.

---

### Post by duality on 2007-02-17
I dont know how to solve it but to compile stuff you need "build_essential" and the headers.
you can download them like this:

sudo apt-get install build_essential linux-headers-$(uname -r)

gl

---

### Post by logos34 on 2007-02-17
I have that same board (actually TForce), and everything should work out of the box.

Audio works with **snd_intel8x0** module/driver included with Ubuntu.  I'm on Edgy 6.10 so maybe that's the difference. (32-bit version)

This link should get you sorted:
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by Wartooth on 2007-02-17
I appreciate your responses. 

I've made some progress, will report in a few.

---

### Post by logos34 on 2007-02-17
> Here is what I have done so far:
I tried getting the headers, was met with this:
sudo apt-get install build_essential linux-headers-$(uname -r)

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build_essential

I didn't look too closely at that guy's post...It has errors and wasn't clear...The packages are 
> build-essential 
linux-headers-2.6.**xx-xx-arch** (add the ouput from 'uname -r' to the end)

And to get the right linux-headers you do:
uname -r 
to show your kernel
(for instance on mine it returns '**2.6.17-10-generic'**

Then do sudo apt-get install...

> I then went to the ALSA site as per step 3. Realtek was not available, so I chose Intel, as that is how Ubuntu is detecting it, and saw the above mentioned snd_intel8x0

So, I go back to the instructions to try following along again...
sudo modprobe snd-

FATAL: Module snd_ not found.

No, put in 
**sudo modprobe snd-intel8x0**

Then add it to /etc/modules file so it will load at boot.  

Make sure your sound preferences in alsamixer and in system>prefs>sound are set for 'Intel ICH' (Alsa) or 'Autodetect,' system sounds boxes are ticked, and that nothing is muted.   

Try that before compiling the official driver.

Forgive me, it's been a while since I did any sound troubleshooting, so I'm not whether any of that will solve your problems.

---

### Post by Wartooth on 2007-02-17
logos34:  Thank you very much for being so willing to help.  I deleted my post upon having the following happen, in hopes that I had actually done something right and was on the verge of a breakthrough.  Not so sure about that now, though I do have the post saved elsewhere. 

Argh.  Now I have an interesting twist. 

I cranked up the speakers and attempted to get one of the system sounds to make some noise.  I had EVERYTHING in alsamixer cranked up.  EVERYTHING.  I heard this tiny little tinkling through the speakers.  Okay, that means something, somewhere is TRYING to work. 

I was using the front panel audio at the time.  My husband suggested disabling that (the mobo I have allows you to only use the front OR the back, not both) and plugging in on the rear panel.  I've done that, and now don't even have a tinkling. 

Am I now looking at a hardware issue since I at least got some, albeit faint, sound out of a speaker?  At what point do I find that it is necessary to buy an add-on soundcard?

---

### Post by Wartooth on 2007-02-17
Well, I have managed to hear a faint whisper of sound out of the speaker by pressing it into my flippin' ear.  I've found others have had this problem and have tried

sudo nano /etc/modprobe.d/alsa-base

and adding this: 
options snd-intel8x0 ac97_quirk=3 

Which was said to have helped [http://www.linuxforum.com/forums/index.php/topic,178761.new/topicseen.html](http://www.linuxforum.com/forums/index.php/topic,178761.new/topicseen.html) in there, however, I don't know what is meant by restarting the sound device.  It also says to try other numbers if 3 doesn't work.

---

### Post by logos34 on 2007-02-17
> Am I now looking at a hardware issue since I at least got some, albeit faint, sound out of a speaker? At what point do I find that it is necessary to buy an add-on soundcard?

Anything is possible, but I don't think it's a hardware problem...Sound problems often turn out to have simple causes.  I get the same output from 'aplay -l' you do, by the way...Onboard audio is enabled you say in the bios, so that's not the issue.  If you had an S/PDIF cable or analog cable with RCA plugs I'd say try piping your audio out to a stereo receiver to see if THAT works...On second thought it could be a problem with the jacks: I notice on mine that I have to play with the position of the plug in the jack to get sound just right so it's full stereo; sometimes I don't hear anything at first until I pull it out and push it back in but not all the way...In other words, just jiggle the thingamabob!

Your next post just popped up...lemme read that

---

### Post by logos34 on 2007-02-17
Here's my /etc/modprobe.d/alsa-base in case you're interested:

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2


---

### Post by logos34 on 2007-02-17
And I ran some audio probe commands just to give you an idea what they look like for this board:

> logos@logos-desktop:~$ cat /etc/group | grep audio
audio:x:29:user

logos@logos-desktop:~$ lspci | grep -i audio
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)

logos@logos-desktop:~$ lsmod | grep snd
snd_intel8x0           34844  3 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd                    58372  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

logos@logos-desktop:~$ cat /proc/modules
...
snd_intel8x0 34844 3 - Live 0xdfa47000
snd_ac97_codec 97696 1 snd_intel8x0, Live 0xdfa67000
snd_ac97_bus 3456 1 snd_ac97_codec, Live 0xdf94f000
tsdev 9152 0 - Live 0xdf9c7000
snd_pcm_oss 47360 0 - Live 0xdfa3a000
snd_mixer_oss 19584 1 snd_pcm_oss, Live 0xdf9fd000
usbhid 45152 0 - Live 0xdfa2d000
snd_pcm 84612 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xdfa17000
snd_timer 25348 2 snd_pcm, Live 0xdf9d0000
snd 58372 10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xdf9ed000
...
soundcore 11232 1 snd, Live 0xdf958000
snd_page_alloc 11400 2 snd_intel8x0,snd_pcm, Live 0xdf954000
...


logos@logos-desktop:~$ lsof | grep /dev/dsp
logos@logos-desktop:~$ ls -l /dev/dsp* /dev/mixer
crw-rw---- 1 root audio 14, 3 2007-02-17 12:03 /dev/dsp
crw-rw---- 1 root audio 14, 0 2007-02-17 12:03 /dev/mixer
 


---

### Post by houstonbofh on 2007-02-17
I got a motherboard with the 6100 chipset thinking support would be easy.  **HA!**  Seems the southbridge can be one of 2 chips, and only one of them works.  I eventually put in a $5 nic, and old soundblaster, and just used "nv" graphics.  It might work better in a year...  Since it is a business PC, it is no big deal, but it is the last "integrated" motherboard I buy.

---

### Post by logos34 on 2007-02-17
I have to go now. I'll look into this more tomorrow because, frankly, I'm curious why mine works and yours doesn't (unless it's a problem specific to dapper).

---

### Post by Wartooth on 2007-02-17
I stole your last two lines in alsa-base out of desperation.  No change. 

Here's my stuff for comparison.  FIrst glance, it appears to be the same or very similar to yours. 

cat /etc/group | grep audio 
audio:x:29:user

lspci | grep -i audio
0000:00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)

lsmod | grep snd
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

cat /proc/modules

snd_intel8x0 33692 1 - Live 0xf8a71000
snd_ac97_codec 93088 1 snd_intel8x0, Live 0xf8a8f000
snd_ac97_bus 2304 1 snd_ac97_codec, Live 0xf89a2000
snd_pcm_oss 53664 0 - Live 0xf8a62000
snd_mixer_oss 18688 1 snd_pcm_oss, Live 0xf8a4b000
parport_pc 35780 1 - Live 0xf8a19000
parport 36296 3 ppdev,lp,parport_pc, Live 0xf8a25000
snd_pcm 89864 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xf8a34000
snd_timer 25220 1 snd_pcm, Live 0xf89ab000
snd 55268 8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xf8a0a000
soundcore 10208 1 snd, Live 0xf895b000
nvidia 4550772 12 - Live 0xf8eb9000
agpgart 34888 1 nvidia, Live 0xf8974000
snd_page_alloc 10632 2 snd_intel8x0,snd_pcm, Live 0xf8957000

ls -l /dev/dsp* /dev/mixer
crw-rw---- 1 root audio 14, 3 2007-02-17 14:40 /dev/dsp
crw-rw---- 1 root audio 14, 0 2007-02-17 14:40 /dev/mixer

---

### Post by Wartooth on 2007-02-17
Haha, well, I certainly thank you for your curiosity.  I'm going to try to keep plugging away at it until I get irked enough to go work on one of my cars or something.  At which point I'm likely to get irked enough to come back here!  Ha! 

Thanks again. :)

---

### Post by Wartooth on 2007-02-17
> **houstonbofh said:**
> I got a motherboard with the 6100 chipset thinking support would be easy.  **HA!**  Seems the southbridge can be one of 2 chips, and only one of them works.  I eventually put in a $5 nic, and old soundblaster, and just used "nv" graphics.  It might work better in a year...  Since it is a business PC, it is no big deal, but it is the last "integrated" motherboard I buy.

I bought this (barebones system) as I had a free machine with parts I could scavenge and wanted to build a hobby box of sorts on a budget.  Other than installing Ubuntu on another free machine just to see if it worked, this is my only real experience with Linux.  This will be my permanent machine for it, and if I have to buy a soundcard eventually, so be it.  I'm going to dig through our closet computer museum and see if we have any spare soundcards, but somehow I don't think we do, or if we have any, I don't know that they'll fit.  

The video was a breeze for me, whereas that's something I struggled with on the other machine.  Wound up being that the video was far too old and weak to push a 24" widescreen.  No biggie.  dpkg-reconfigure cured all this time around, at least.  Funny that I was so concerned with video, and it wasn't an issue, but I had ZERO thought at all about sound, and now look at where I am. 

I suppose I can't complain too much for an ~$85.00 rig.

---

### Post by Wartooth on 2007-02-18
Not much to report overnight. However, this morning, I woke up to find that my computer had not shut down as I had told it to before bed.  Apparently, it hung up during shutdown.  Mind you, had I had my coffee, I'd have been smart enough to note what was on the screen where it got snagged in case that was indicative of something, but, yeah...

So, I powered it off and started back up, with no issues.  No sound, either, but that was to be expected, I suppose.

Decided to go through the items on that Comprehensive Sound Problems thread one more time.  

sudo modprobe snd-

FATAL: Module snd_ not found.

Would this have some bearing on what is going on?  After all that I did yesterday, there is no sound module?

And, would attempting the download from the Realtek site be a worthwhile (I mean, what the heck, right?) option?

Here is the readme from what I downloaded off of Realtek's site:

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
Installation notice:
1.It must have GCC compiler in your OS.
2.Kernel source code is the necessary for driver compile.

For driver installation, please follow below steps. 

Automatic install:
execute

  ./install

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code and install the driver
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. ./snddevices

Step 4. Install ALSA Lib
        a. tar jxvpf alsa-lib-1.0.xx.tar.bz2
        b. cd alsa-lib-1.0.xx
        c. ./configure 
        d. make
        e. make install

Step 5. Install ALSA Utility
        a. tar jxvpf alsa-utils-1.0.xx.tar.bz2
        b. cd alsa-utils-1.0.xx
        c. ./configure
        d. make
        e. make install

Step 6. Run ALSA auto configuration
        ./alsaconf

Step 7. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already installed)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package.

---

### Post by logos34 on 2007-02-18
> Decided to go through the items on that Comprehensive Sound Problems thread one more time.

sudo modprobe snd-

FATAL: Module snd_ not found.

Would this have some bearing on what is going on? After all that I did yesterday, there is no sound module?

Read post #5 above.

---

### Post by Wartooth on 2007-02-18
D'oh!  Coffee is now making it through my system.  I should never start this sort of thing first thing in the morning.

---

### Post by logos34 on 2007-02-18
while you're doing that, i have a list here somewhere of the alsa-related pkgs installed on my system.  I'll post it as soon as I can find it.  You can use it to see if you have the dapper equivalents installed (just use Synaptic).

---

### Post by Wartooth on 2007-02-18
sudo apt-get install build_essential linux-headers-2.6.15-26-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build_essential

Have I typed something incorrectly?

sudo modprobe snd-intel8x0 seems to make it happy.  However, when you say to put it in /etc/modules, do I just cd /etc/modules and type that in, or how lost am I?

Sorry for being a bumbling idiot. :/  Thanks for your patience.

---

### Post by logos34 on 2007-02-18
I corrected all that in post #5. 

It's **build-essential** (hyphen, not underline)

You have to be root to edit a file:
> gksudo gedit /etc/modules

insert **snd-intel8x0** 

Reboot after that and see if you get audio.

---

### Post by Wartooth on 2007-02-18
Okay, got build-essential just fine now. 

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.0 libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
Suggested packages:
  debian-keyring gcc-4.0-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 8060kB of archives.
After unpacking 34.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main linux-kernel-headers 2.6.11.2-0ubuntu18 [1039kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libc6-dev 2.3.6-0ubuntu20.4 [2822kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5 [1471kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main g++-4.0 4.0.3-1ubuntu5 [2271kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main g++ 4:4.0.3-1 [1386B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main make 3.80+3.81.b4-1 [286kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main dpkg-dev 1.13.11ubuntu7 [163kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main build-essential 11.1 [6826B]
Fetched 8060kB in 59s (136kB/s)
Selecting previously deselected package linux-kernel-headers.
(Reading database ... 71223 files and directories currently installed.)
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20.4_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20.4) ...
Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu7) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...


I noticed it said it was also selecting linux-kernel-headers, and 
sudo apt-get install linux-headers-2.6.15-26-386     gives me
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-26-386

Which is probably another case of my ineptitude at work. 

Also, in Terminal:
gksudo gedit /etc/modules

(gedit:8636): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Something to ignore, I hope?

gedit opened up and contained:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse

added snd-intel8x0 and am rebooting.

---

### Post by Wartooth on 2007-02-18
No sound, although I'm doubting that I did everything correctly. :/

---

### Post by logos34 on 2007-02-18
edit: nevermind

---

### Post by logos34 on 2007-02-18
Just disregard that warning. (see above edit)

So, at this point I'm not sure why you're not getting sound.  Here's my list of alsa related pkgs.  Just open up Synaptic and search 'alsa' and go through and find the dapper equivalents.  Not sure it'll help though.

> E: Couldn't find package linux-headers-2.6.15-26-386

I checked the dapper package repository and that kernel is listed.  Don't know why apt-get is having problems.  Try to get it using synaptic.

#############

alsa-base
alsa-oss
alsa-source
alsa-utils
gnome-alsamixer
libasound2
libasound2-dev
libesd-alsa0
gstreamer0.10-alsa
linux-sound-base
libsdl1.2debian-alsa

linux-source-(your kernel) *you need this if you compile driver from source

---

### Post by Wartooth on 2007-02-18
Hrm.  Synaptic gives me the following options when searching for linux-headers:

linux-headers-2.6.15-23
linux-headers-2.6.15-23-386
linux-headers-2.6.15-23-686
linux-headers-2.6.15-23-k7
linux-headers-2.6.15-23-server
linux-headers-386
linux-headers-686
linux-headers-k7
linux-headers-server
linux-headers-server-bigiron
linux-source-2.6.15

Now, searching for alsa, it gives lots of options and says that I have these installed:
alsa-base
alsa-utils 
gstreamer0.10-alsa
libasound2
libesd-alsa0
libpt-plugins-alsa
libsdl1.2debian-alsa
linux-sound-base

I'll select the ones from your list that I do not show as having had installed in the meantime.

---

### Post by logos34 on 2007-02-18
> linux-headers-2.6.15-23
linux-headers-2.6.15-23-386
linux-headers-2.6.15-23-686
linux-headers-2.6.15-23-k7
linux-headers-2.6.15-23-server
linux-headers-386

Not sure why there's no linux-header pkg for your kernel returned by 'uname -r'...Mine is.
But you might want to get 'linux-headers-386'.  
> 
alsa-base
alsa-utils
gstreamer0.10-alsa
libasound2
libesd-alsa0
libpt-plugins-alsa
libsdl1.2debian-alsa
linux-sound-base

Those are the main ones.  alsa-oss is just a wrapper for oss audio, gnome-alsamixer a gui for alsamixer (but easier to configure), and libasound2-dev just the development pkg.

---

### Post by Wartooth on 2007-02-18
Ooookay. ALSA stuff all downloaded nicely, same with linux-headers-386.

So...where to now? Start over again somewhere?

---

### Post by logos34 on 2007-02-18
Recheck Volume control by right-clicking on speaker icon in sys tray (lower right).  Under File>Change Device '0 Intel ICH (alsa mixer)' should be enabled (not alc655).  Under Edit>Preferences you have checked at a minimum Master, PCM, CD, Capture and Channelmode (set for 2 channel).  Master and PCM sliders locked together and up.  No red x's through little speaker icons.  

Go to Applications>Sound&Video>Gnome alsa mixer.  If it's not there right-click on Applications>Edit menus.  Go to sound and volume and check it.

The two most important sliders are master and PCM.  And none of the 'mute' boxes should be ticked. 

Under System>Prefs>Sound>Devices tab, settings should be set for 'autodetect' except for last which should say 'Alsa.'  On Sounds tab, Esd and Sys sounds should be ticked, and at the bottom should be set for Intel ICH.  

Try your favorite media player.  Go into preferences and make sure it's se to use alsa output.  

I know you've probably done all that and missed nothing, but I can tell you from using the sound system (particularly for recording) the settings can change for no apparent reason.

---

### Post by Wartooth on 2007-02-18
Channel mode was not checked on the first one.  It is now. It also was on 6 channel, now set to 2.

In ALSA mixer, surround was muted as was mic. Capture slider was down.  

However, under System > Prefs > Sound .... I have no Devices.  All it does is open 'Sound Preferences' which has two tabs: Sound and System Beep.

---

### Post by logos34 on 2007-02-18
I think I know the reason for this:
> E: Couldn't find package linux-headers-2.6.15-26-386

You don't have all the repos enabled.  Go to Synaptic>Settings>Software sources>Ubuntu 6.06 tab.  Tick all the boxes including source code.  Then click on Internet Updates.  security updates and 'recomended updates' should be ticked.  Now hit the Reload button.  Search for 'linux-headers-2.6.15-26-386' and linux-source-2.6.15-26 and linux-source-2.6.15-26-386.

---

### Post by logos34 on 2007-02-18
> **Wartooth said:**
> Channel mode was not checked on the first one.  It is now. It also was on 6 channel, now set to 2.

In ALSA mixer, surround was muted as was mic. Capture slider was down.

Channel mode might make a difference, but the others are for recording.  Master and PCM are the most important for playback.

> However, under System > Prefs > Sound .... I have no Devices.  All it does is open 'Sound Preferences' which has two tabs: Sound and System Beep. 

Dapper may be a little different. Just check everything as best you can and try playing something in a media player. (streaming audio, mp3, etc).  Reboot and try again.  If nothign works then do what I suggested in above post and then you can try compiling the alsa driver. (you need the right  linux-headerr pkg)

---

### Post by Wartooth on 2007-02-18
Perhaps the difference is running Dapper.  I went Synaptic > Settings > Repositories and was met with a whole lotta 6.06 stuff, quite a few of which were not checked, but are now. 

Reloaded and, ta-daaaah.  There's the elusive 26-386.  Clicked and installed.

---

### Post by logos34 on 2007-02-18
> **Wartooth said:**
> Perhaps the difference is running Dapper.  I went Synaptic > Settings > Repositories and was met with a whole lotta 6.06 stuff, quite a few of which were not checked, but are now. 

Reloaded and, ta-daaaah.  There's the elusive 26-386.  Clicked and installed.

Ok, so at this point your card is being detected, you've done modprobe routine to enable snd-intel8x0, put it in /etc/modules, checked all the volume and output settings and still no sound, right?

Then I'd go ahead with sudo dpkg-reconfigure alsa-source.  Follow the section 'ALSA Driver compilation' in the Comprehensive sound guide.

---

### Post by Wartooth on 2007-02-18
Rebooted, sound still barely audible.  It's making sound (put in a CD, can recognize the song, but it sounds like it's about a mile away).

Now, just to double check something, sudo modprobe snd-intel8x0 is it supposed to output something or no? Because I did not get an error, but I also did not get any output.

---

### Post by logos34 on 2007-02-18
sudo modprobe just loads the module--it doesn't output anything. (would ne nice for it to confirm).  

Stupid question #14: you're getting a faint signal--playing wiht the jack doesn't do anything? Could you have a faulty cord/short? You're using headphones or speakers?

---

### Post by logos34 on 2007-02-18
Why don't you just go ahead and try the alsa driver compilation.

---

### Post by Wartooth on 2007-02-18
I've tried two sets of speakers, one set of headphones, and just did lots of wigglin' of the plug to no avail.

Should I try that which is mentioned in the thread, or the ALSA driver available through Realtek?  Or does that work out the same either way?

On Edit:  Gonna try the compilation first.  What the heck.

---

### Post by Wartooth on 2007-02-18
Outputs: 

sudo apt-get install build-essential linux-headers-2.6.15-26-386 module-assistant alsa-source
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
linux-headers-2.6.15-26-386 is already the newest version.
alsa-source is already the newest version.
Suggested packages:
  dialog
The following NEW packages will be installed:
  module-assistant
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 73.9kB of archives.
After unpacking 377kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe module-assistant 0.10.2 [73.9kB]Fetched 73.9kB in 1s (57.2kB/s)
Selecting previously deselected package module-assistant.
(Reading database ... 124349 files and directories currently installed.)
Unpacking module-assistant (from .../module-assistant_0.10.2_all.deb) ...
Setting up module-assistant (0.10.2) ...

 sudo module-assistant a-i alsa-source
Reading package lists... Done
Building dependency tree... Done
alsa-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
Done with /usr/src/alsa-modules-2.6.15-28-386_1.0.10-4ubuntu4+2.6.15-28.51_i386.deb .
Selecting previously deselected package alsa-modules-2.6.15-28-386.
(Reading database ... 124390 files and directories currently installed.)
Unpacking alsa-modules-2.6.15-28-386 (from .../alsa-modules-2.6.15-28-386_1.0.10-4ubuntu4+2.6.15-28.51_i386.deb) ...
Setting up alsa-modules-2.6.15-28-386 (1.0.10-4ubuntu4+2.6.15-28.51) ...
You should now stop all applications using sound devices
and reload all ALSA sound modules.

---

### Post by Wartooth on 2007-02-18
Rebooted after all that. 

Here's a new twist:

Error pop-up warning box saying:

The volume control module did not find any elements and/or devices to control.  This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured. 


O_o

---

### Post by Wartooth on 2007-02-18
ALSA Mixer is BLANK when opened up via GUI, and is said not to exist when attempting to open it up in Terminal.

---

### Post by logos34 on 2007-02-18
wait, didn't you skip a step?

> #
Type the following to shell: (note: module-assistant is optional, it will compile the package for you)
Code:

sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

#
Code:

**sudo dpkg-reconfigure alsa-source**

#
[B]You now have a big blue dialog box (left and right keys to choose 'Yes' and 'No', Enter key proceed). Answer yes (for ISA-PNP - recommended by package maintainers), then yes again (for debugging - recommended by package maintainers).
#
Now you must pick which driver you want to install. Use space to select and deselect modules, and up and down to navigate.
#
From General Help step 3, you should know the name of your driver. Deselect 'all' (the * will go away), and select your driver. In my case, I deselected 'all' then selected 'via82xx'. Hit Enter. Almost home free![/B]
#

    *
      If you chose module-assistant
      Code:

      sudo module-assistant a-i alsa-source

      If the progress bar reaches 100% with no errors, you will have installed the drivers successfully. Resume this guide from General Help step 4.



The part in bold will start a interactive configuration process.

---

### Post by Wartooth on 2007-02-18
I did all that,sorry for spacing on it in the post, got the big blue box, deselected all, selected the intel8x0, it seemed to complete the process without any errors, checked out everything on ALSA mixer.  Rebooted to find that error.

---

### Post by logos34 on 2007-02-18
Oh, alright.

Not sure what's up with the errors and funky gui bit.  You configured it with dpkg-reconfigure.  Not sure why it's saying
> The volume control module did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

It says in the guide to go back to step 4 and do sudo modprobe snd-intel8x0 to load the module, but I don;t think that's gonna solve the problems here.  Just do it.  Then try reinstalling gnome-alsamixer using synaptic.

---

### Post by logos34 on 2007-02-18
WAIT--open up gnome alsa mixer and hit File>prefs and check the box

---

### Post by Wartooth on 2007-02-18
Opening up File > Prefs in ALSA mixer gives:

Mixer Names and Visibility

-there's nothing there-

Slider Style
Slider Toggle Style. 

It's as though most everything ALSA related is now gone.

---

### Post by logos34 on 2007-02-18
Question: Did you just install dapper last month?  Would you care to backup whatever files you've save since and install Edgy 6.10?  Because there's a good chance it'll work out of the box.  Frankly, that's what I'd suggest.   Of course, you could try manually compiling the driver as the guide outlines it.

---

### Post by Wartooth on 2007-02-18
I just put this thing together the other day.  I haven't loaded a single thing on it yet. :)

The reason I went with Dapper is due to LTS and it being recommended for newbs, and the whole warning at the top of this forum about kind of being on your own if you head to Edgy.  That's really about the only thing that would make me hesitant about it.  

Would running an Edgy LiveCD be as likely to work as an install to try it out?  

Either way, I'd probably give Edgy a shot so long as I can actually get help when I'm lost (which may well be often...).

---

### Post by logos34 on 2007-02-18
Yeah, try the livecd!  I was just going to say I thought you may have chosen it for LTS.  But I can tell you Edgy is very stable (been running it since it came out last fall), and I'm just thinking that it's got to work for you as for me since we have the same boards--they;re identical down to last chip except for minor things like BIOS options. If you use the generic (vs. the 386) kernel then I can't think of any reason why it won't work.  I haven't customized the configuration much.

---

### Post by Wartooth on 2007-02-18
Okay, I've already started downloading ubuntu-6.10-desktop-i386.iso and have a blank cd waiting.  I'm going to try it on this machine first, if that doesn't work, then I'll fire up my XP box.

To what are you referring when you say "If you use the generic (vs. the 386) kernel"?

---

### Post by logos34 on 2007-02-18
> **Wartooth said:**
> I just put this thing together the other day.  I haven't loaded a single thing on it yet. :)

The reason I went with Dapper is due to LTS and it being recommended for newbs, and the whole warning at the top of this forum about kind of being on your own if you head to Edgy.  That's really about the only thing that would make me hesitant about it.  

Would running an Edgy LiveCD be as likely to work as an install to try it out?  

Either way, I'd probably give Edgy a shot so long as I can actually get help when I'm lost (which may well be often...).

Yes. It will detect all your hardware and if it works on the livecd it should work when installed.

And the Ubuntu forums are great--best around.  I used to use Suse and I found answers to some important questions here.

> To what are you referring when you say "If you use the generic (vs. the 386) kernel"
When I first installed it included both.  But I had some problems with the 386 (mainly in relation to nvidia graphics driver), and after a while it disappeared from Grub.  Just as well.

As you no doubt already know, check the md5sums before you burn the image to cd, do the burn 4x or slower and do the cd integrity test if and when you decide to install.

By the way, I could never get the latest official nvidia graphics driver to stay in, so ended up using the 8776 glx driver in the repos.  Use automatix2 to install it or follow the Nvidia HOWTO.

If you install, there's a kernel update.  Do the update first thing before putting in the video driver, otherwesie you'll have to reinstall the driver. 

Good luck and post back with your results.  Curious as to how it turns out.

---

### Post by Wartooth on 2007-02-18
Looks like I have about twenty minutes to go on the download. 

The forums here are one of the reasons why I figured I'd give Ubuntu a shot.  I'd been toying with the idea of Linux for years, and finally got the opportunity to test the waters when given a couple of old emachines minus HDDs some weeks ago.  I'd certainly like to make a Linux machine my main machine and only have to deal with my buggy XP when absolutely necessary. 

I may be coming back for video help, though, by the sound of it.  All it took with this was dpkg-reconfigure, choosing nvidia and I was done.  

Hm, down to about 11 minutes now.   Biiiiiig download.

---

### Post by logos34 on 2007-02-18
> and finally got the opportunity to test the waters when given a couple of old emachines minus HDDs some weeks ago. 

Wish someone would give me some computers, old or whatever, better than buying them...But it's precisely a extra hard drive I need. 

I was going to suggest that you consider a reinstall of dapper if you really would prefer LTS, doesn't take that long, but there's no guarantee that a fresh install will solve your audio woes.  There is a slight possibility that something went wrong during your first install.  I did a search of the forums this morning for posts on this chipset and mobo all the way back to late 2005, and some had trouble while for others it worked out of the box...

---

### Post by Wartooth on 2007-02-18
Posting from the Edgy Live CD 

:(  Not a peep.  Edgy sure does look nice, though.  This may sound weird, but the text looks much crisper.  ? 

I guess that's pushing me a bit closer to buying a sound card that is listed as being Ubuntu-friendly.  Actually looked at one on Newegg a little earlier today. 

Here's a fun thing I noticed:

Upon starting up my machine, the first screen where it lists BIOS information, the flippin' thing says "Engineering Release - Not for Production Use." !?!?!?! 

Also, this is my second install of Dapper on this machine.

Of the freebie machines, one worked beautifully with Ubuntu, and will be going to a friend.  The second was good only for parts, but allowed me to put this together for very little money.  Though, it is looking like it might be a few bucks more if I buy a sound card.  Ha!  Ah, well, like I said before, I can't complain too much.

---

### Post by Wartooth on 2007-02-18
Last ditch effort.  Going to go through it all ONE last time before ordering a sound card. 

```
 aplay -l
aplay: device_list:221: no soundcards found...
```

That's worse than before!

```

lspci -v
0000:00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
        Subsystem: Biostar Microtech Int'l Corp: Unknown device 8213
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=256]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

Well, at least there's that, eh?
```

sudo modprobe snd-intel8x0
```

No output, which is apparently good. 

```
 sudo nano /etc/modules
```

And I get:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
snd-intel8x0

```

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
```

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Looks like something's really, really not right. 

I'm abandoning this install and trying once more, if for no other reason than the fact that I feel a bit uncomfortable with an install that is this problematic.  :/

---

### Post by logos34 on 2007-02-18
Well it looks like I've led you down the proverbial primrose path...thought for sure edgy would work for you...(re the font rendering: maybe its a little better, but it's still one of Ubuntu's weak spots because you still need to do a couple of tweaks to get it to look decent)...Maybe this is a hardware problem after all, or my board works by some miracle...i give up...go for a sound card, whatever works.

---

### Post by Wartooth on 2007-02-18
Bah, don't feel too let down, now.  Look about in this thread, if it weren't for you, who would have been helping me out?  You kept me from giving up a lot earlier, and therefore kept me *learning* which is vitally important when doing something like trying a new OS.  To be honest, the more problems I have to work through, the more I will become comfortable with Terminal, the more knowledge of commands and how they work will be retained. 

I'm reinstalled and hangin' out reading the boards and will throw in a sound card and give it a whirl. 

I take on masochistic learning experiences and hobbies for fun (cars, cactus, learning German, computers, etc.).  Builds character, or so they say.  ;)

---

### Post by houstonbofh on 2007-02-19
> **Wartooth said:**
> Upon starting up my machine, the first screen where it lists BIOS information, the flippin' thing says "Engineering Release - Not for Production Use." !?!?!?! 

I too loved that bit on mine.  I guess I will take it to heart the next time I buy a motherboard. :)  I haven't tried Feisty on it yet, but it does have some updated stuff.  However, it does still have some issues...

---

### Post by Wartooth on 2007-02-19
I get a chuckle out of it when I see it.  Adventures in budget computing!

---

### Post by logos34 on 2007-02-21
Just stumbled on this in the wiki (should have looked there before):
[https://wiki.ubuntu.com/Biostar_Geforce_6100-M9?highlight=%28geforce%29%7C%286100%29](https://wiki.ubuntu.com/Biostar_Geforce_6100-M9?highlight=%28geforce%29%7C%286100%29)

> "This Board works perfectly under Edgy Eft. Everything was detected, sound quality was excellent..."

Except, that is, if it's an "engineering release"!

Happy sound card shopping!

---

### Post by Wartooth on 2007-02-21
Wow.  I'm shaking my head at that.  I simply must be cursed.  LOL!  I do have to wonder what the deal is with the 'Engineering Release.'  

I'd be more tempted to try to update the BIOS if I had a floppy in this thing.  I've no idea if I could use a USB stick instead of a floppy.  I read through the always interesting broken English on the Biostar site about flashing the BIOS and only floppies were mentioned.  With my current run of luck, I'd screw something up beyond all hope, I am sure.

---

### Post by logos34 on 2007-02-21
looks like a floppy is the only route if you want to try bios update.  Never tried thumb drive...have to admit I don't even know if usb is possible (on the other hand it should be because they have usb floppy drives).

But it looks like you're just gonna have to fork over some dineros for a card.

good luck

---

### Post by Wartooth on 2007-02-22
I have sound!!!

Bought a Sound Blaster Audigy SE due to seeing it listed as working in Ubuntu, and having read reviews of it 'just working'.  Ripped it out of the box, threw it in, plugged speakers in, turned on the machine, disabled onboard in the BIOS, and VOILA!  Sound!  :)

Thanks again for the help and motivation, though.  Gotta treat all of this as a learning experience and file it for future use.  :)

---

### Post by houstonbofh on 2007-02-22
I know it works, but some things to add.

There are 2 n6100 systems.  The different southbridge is the killer.  One works, and one doesn't.

BIOS upgrades...  Burn the BIOS and util to CD.  Download and burn the UBCD. [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)  Boot it to a command prompt. [F6]  Swap CDs, and flash.  Works very well.

Never take hardware shortcuts.  I get burned every time.

---

