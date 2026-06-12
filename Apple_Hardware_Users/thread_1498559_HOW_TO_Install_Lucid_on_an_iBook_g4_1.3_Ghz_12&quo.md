---
title: "HOW TO: Install Lucid on an iBook g4 1.3 Ghz 12&quot;"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by sha.goyjo on 2010-05-31
MAJOR EDIT:

Sorry folks. I no longer have this iBook (it exploded) so I really can't field any further questions about it. If you have updates that you would like included in the howto please PM me and I'll make certain that they go in at the top.

/EDIT

Hello folks. Sorry this took me so long, but I was fiddling with trying to get KMS working for about a week till I realized that it was probably broken and decided to drop it and use userspace DRI. Lo and behold, it was faster than I think I've ever gotten out of this model before. I'm aware that KMS supposedly supports the Mobility Radeon chip in this machine, but until I can find an easy way to get it to work, I'm probably going to stick with UMS. That being said, if anybody can get KMS working, I'd LOVE to change the tutorial around a bit.

    That being said, I'd like to take a moment to address a few things. This is not a tutorial for all iBooks, or all PPC Macs for Lucid. I cannot stress enough that your mileage may vary, and you should not hold me responsible for your individual situation. That being said, I have tried to be careful not to make any mistakes in my command strings, and if there are any mistakes or questions, I would be happy to deal with them quickly and efficiently.

 So, here we go. Enjoy.

EDITED 6/3/2010:
Added a few new lines in the xorg.conf section. Also commented on the removable disk drive bug.
EDITED 8/13/2010:
Fixed a typo in the last apt-get line.

[B][U][SIZE="4"]
1. Install the system.[/SIZE]
[/U][/B]
[INDENT]
First things first, press the power button, and then insert the Ubuntu 10.04 PowerPC Desktop Live CD. Hold down the "C" key as you do this. Holding down the "C" key causes the system to boot from the inserted disk. If you miss it the first time, you can always shut off the computer and try it again. Regardless, you should hold down the button until you get to a prompt that asks you to input the boot options. I very much advise you to boot with the options
```
live video=radeonfb:1024x768-24@60 radeon.modeset=0
```
Because when you install the system this will be automatically added to the yaboot.conf. Not a huge issue, since we're going to have to change that file later anyways, but it'll save you about 12 seconds of typing and about a week of confusion if you are as stupid as I am.

Other than that, this part is fairly standard for PPC systems. Select your language and time zone. Select use entire disk, choose user options, let run. Make sure to leave "install boot loader" in the advanced options checked. When you are done, reboot the system using the live cd (do not hard reboot with the power button), and after it ejects the cd, press the enter key to finish rebooting the system.
[/INDENT]
[B][U][SIZE="4"]
2. Clean up after the installer.[/SIZE][/U][/B]

[INDENT]First things first. Before the system explodes from overheating, go into the terminal and code the following
```

$sudo modprobe therm_adt746x
$sudo apt-get update
$sudo apt-get install cpudyn

```
(Thanks to dmillard10 for reminding me to update repos ::slaps own hand::) 
Contrary to the ubuntu powerpc known issues page, cpudyn works just fine on this machine, scaling the processor well with no additional configuration. Maybe it's a little heavier than powernowd, but i still can't get that program to work as well as cpudyn. If someone can give me confirmed working instructions for using powernowd in this situation, I'd be happy to put it here as an alternative.

Now that you have prevented immediate overheating, you should prevent it in the future. In order to do so you need to make sure that the fan module is loaded during boot.
```

$sudo gedit /etc/modules

```
In the file that opens, at the end add the line
```

therm_adt746x

```
And, while you are at it, remove the erroneous duplicate line
```

snd-powermac

```
Which is just silly. snd-powermac will be re-written by modprobe as snd_powermac, so there is no point to having it twice in the file. Save the file and close up.

Now that you have prevented the imminent and future heat death of your system, it is time to move on.[/INDENT]
[B][U][SIZE="4"]
3. Installing Wireless drivers.[/SIZE][/U][/B]
[INDENT]
I advise doing this in the terminal, as I've had jockey wuss out on me a couple of times now. Use this command.
```

#sudo apt-get install b43-fwcutter

```
Should do the trick just fine. Make sure to say yes when it asks you the important question. You know, the question the program was designed for. The question about whether or not you want it to fetch the firmware. 

Yes, I'm an ***. I just don't know anyone who uses b43-fwcutter to cut firmware locally. Okay, I promise, I'm done with my rant now.
Please note that I've attached a 7z of the firmware folders. The uncompressed folders can be placed in /lib/firmware for the same effect.[/INDENT]
[B][U][SIZE="4"]
4. Compiling a new kernel.[/SIZE][/U][/B]

[INDENT]Why compile a new kernel, you ask? Well, a number of reasons. First off, because I want the best support for everything. Second of all, this system gets loads better performance if you install the PostFactum Kernel patch set. Although it takes a little work, it's worth it.

first, you need an up to date 2.6.34 kernel from kernel.org. Second, you need the PostFactum patch set 2.6.34-1 (as of now), which you can get from the postfactum site, or on softpedia. Get superuser rights, and copy them both into /usr/src. Then open a terminal and CD into that directory

Now, follow my lead
```

$sudo su
#apt-get install patch kernel-package libncurses5-dev
#tar -xjf linux-2.6.34.tar.bz2
#bunzip2 patch-2.6.34-pf1.bz2
#ln -s linux-2.6.34 Linux
#cd Linux
#patch -p1 < ../patch-2.6.34-pf1
#cp /boot/config-'uname -r' ./.config
#make oldconfig

```
(Thanks to crazyphysicist and jbwilliams for finding my typo in the patch command! )
Now, this last command will unleash a flurry of options and choices. Accept the defaults on all of them. We'll deal with fine tuning in a moment. If you want to skip all of this, I've included a pre-tuned config that you can use.

Moving on...
```

#make menuconfig

```
Now, you need to change two settings and remove two parts of the kernel. Go into kernel options and set the timer to 1000hz and the desktop to low-latency. Battery life will suffer, but speed will be snappy. Now, for the important parts. Go into device drivers-->scsi drivers-->low level scsi drivers--> and remove ALL support for the IBM Power Raid adapter. This will completely bork your kernel compile if you don't remove it.

You also need to go into device drivers-->sound and remove ALL support for the open sound system (oss), including OSS preclaim. Save yourself a lot of time and just disable the tree from the top. It doesn't hurt anything important, unless you have very special reasons for needing it.

Now, leave menuconfig, making sure to save your config file when you leave (you will be prompted, do not choose "save alternate config"). Now...
```

#make-kpkg clean
#make-kpkg kernel_image kernel_headers

```
Now, take a nap. This will take quite some time. Also, while we are here, a note. Some of you may be wondering why I didn't choose to add --initrd to the make-kpkg line. I tried. For some reason, it never got made. Ever. So I'm going to show you how to use update-initramfs instead.

Once your kernel has finished compiling, you'll need to do the following..
```

#dpkg -i linux-image-2.6.34-pf1_2.6.34-pf1-10.00.Custom_powerpc.deb
#dpkg -i linux-headers-2.6.34-pf1_2.6.34-pf1-10.00.Custom_powerpc.deb
#update-initramfs -c -k 2.6.34-pf1

```

You have now installed your custom kernel and created a new initrd.img.
Now we are ready too....[/INDENT]

**_[SIZE="4"]5. Edit /etc/yaboot.conf.[/SIZE]_**

[INDENT]Please note that I've attached a yaboot.conf, which you can use instead of editing, if you like. I recommend learning how to edit your own.

We begin..
```

#sudo gedit /etc/yaboot.conf

```
You need to create a new stanza above the old stanzas, which will read like this.
```

image=/boot/vmlinux-2.6.34-pf1
	label=PostFactum
	read-only
	initrd=/boot/initrd.img-2.6.34-pf1
	append="quiet splash video=radeonfb:1024x768-24@60 radeon.modeset=0"

```
While you are at it, you might want to add
```

enableofboot
enablenetboot
fgcolor=black
bgcolor=white

```
to the configuration options at the top, if you so desire. These will max out your boot options at the first boot splash screen, and give you a nifty white yaboot. Save the /etc/yaboot.conf, and
```

#sudo ybin -v

```
And, if you've never run this command before, proceed to laugh your *** off. I don't need to tell you why. You'll see.[/INDENT]
[B][U][SIZE="4"]
6. xorg.conf[/SIZE][/U][/B]

[INDENT]I have attached a pretty damn verbose xorg.conf to the bottom of this post. I'd advise using it. Kudos to the ArchLinux folks. You guys rock. To use it, just download, decompress, and code
```

$sudo cp {path to xorg.conf} /etc/X11/xorg.conf

```

And it should be working when you restart X. If, for some reason the xorg.conf I've attached gives you trouble, use the command..
```

$sudo dpkg-reconfigure xserver-xorg

```
To auto-rebuild your xorg.conf. (And thanks to Praxicoide for the contrib)

Please post any rebuilt xorg.conf (that works) along with the output of 
```

$lspci

```
And we can help fix the problem for anyone else.

[/INDENT]
**_[SIZE="4"]7. All the little things.[/SIZE]_**

[INDENT]Now for the small things. Run
```

$sudo apt-get install hdapsd gpmudmon-applet

```
(Shout out to j_anthony for spotting my typo)
in order to get yourself inertial dis
k-parking and a working battery monitor. hdapsd (disk parking) should run by default,  Also, for those of you that don't know, Medibuntu is done actively supporting PowerPC as of Lucid, but the packages for libdvdcss2 and ppc-codecs are still available from the website. You have to get libstdc++5 from the debian package site though, although I've attached all three files for convenience. 
d 
```

$sudo dpkg -i {path to file}

```
To install those packages.[/INDENT]


**_[COLOR="Black"][SIZE="3"]AND YOU'RE DONE![/SIZE][/COLOR]_**

As far as I know, everything works, but I know as soon as people start using this I'll be editing, so please, don't hesitate to ask me to correct things.

**EDIT FOR MAJOR BUG:**
I hate to do this to everybody, but there is still one major bug in lucid (which I cannot figure out). Lucid (and karmic before it) do not automount the CD's and DVD's properly via gnome-mount. You can still mount them manually (by editing your /etc/fstab and using sudo mount), or you can boot with the CD or DVD in in order to mount it. Please note this does not affect CD or DVD playback, as both totem and vlc can run without mounting the disks.

Jason

---

### Post by Praxicoide on 2010-06-02
I just installed Lucid in an iBook G4 using your How-to. I can't thank you enough, especially for including the necessary packages.

The xorg was blurry using the parameters given here, but performing dpkg-reconfigure xserver-xorg fixed it. I don't know if this is a different G4 or what.

Thank you once again.

---

### Post by sha.goyjo on 2010-06-03
> **Praxicoide said:**
> I just installed Lucid in an iBook G4 using your How-to. I can't thank you enough, especially for including the necessary packages.

The xorg was blurry using the parameters given here, but performing dpkg-reconfigure xserver-xorg fixed it. I don't know if this is a different G4 or what.

Thank you once again.

Please do me a favor and make a post with your new xorg.conf attached. Also, can you explain how it was blurry? That might be helpful. If there is something definite I can work with I'd be happy to make a change to the faq.

Also, the output from 
```

#lspci

```
Would let us know whether or not you have a different video card.

Thanks.

---

### Post by coolcourt on 2010-06-03
Hey thanks for this article, i am trying to install 10.04 on my G3 ibook, i d/l the alternative iso from the site. i was gonna post a thread asking for help. but im sure if i cant at least get it somewhat working from this. i can ask here or start a thread.

in a nutshell from what u wrote so far. the only thing i cant do is get to boot it in 1024 and once i install it a lot of the terminal commands end up being a pain. let alone trying to copy some files to the system and upgrading things through the shell in such a hectic enviornment lol.

have a good day and thanks for the article im off to work on it

---

### Post by sha.goyjo on 2010-06-03
> **coolcourt said:**
> Hey thanks for this article, i am trying to install 10.04 on my G3 ibook, i d/l the alternative iso from the site. i was gonna post a thread asking for help. but im sure if i cant at least get it somewhat working from this. i can ask here or start a thread.

in a nutshell from what u wrote so far. the only thing i cant do is get to boot it in 1024 and once i install it a lot of the terminal commands end up being a pain. let alone trying to copy some files to the system and upgrading things through the shell in such a hectic enviornment lol.

have a good day and thanks for the article im off to work on it

Okay, the g3 is a FUNDAMENTALLY different beast. Different video cards, so you can't use the boot options I gave. I recommend that if you want to do that you start a new thread and ask a lot of questions, and then write a new howto from that for people to use. This tutorial won't be that much help for you, beyond the very basic similarities.

---

### Post by coolcourt on 2010-06-03
Yes I plan on doing that, ill use your write up as a skeleton to maybe make a tutorial. thanks

---

### Post by dmillard10 on 2010-06-11
Thanks for this!

Just as a note, I needed a

```
sudo aptitude update && sudo aptitude safe-upgrade
```

before installing anything.

I was wondering why cpudyn wasn't found anywhere and then it hit me.

Easy (at least for me) to forget after a new system install.

---

### Post by crazyphysicist on 2010-07-01
Hi, on running #patch p1 < ../patch-2.6.34-pf1
I get nothing but "HUNK Failed at..." for each entry is this supposed to happen?

---

### Post by svtguy88 on 2010-07-02
> **sha.goyjo said:**
> 
Now, you need to change two settings and remove two parts of the kernel. Go into kernel options and set the timer to 1000hz and the desktop to low-latency. Battery life will suffer, but speed will be snappy.

Jason

I'm in the process of compiling my first custom kernel as I type this, and I just got done researching (and selecting) the options I wanted.  The only thing that caught my eye with your setup was the low-latency desktop.  Just wondering what made you enable that...everything I've read says that it is more for machines running one/few dedicated processes.

[QUOTE=tgalati4]
Low-latency guarantees 95% of the CPU cycles will go to your primary application. If you are running Audacity for mixing or recording music, then 95% of the CPU cycles will go to Audacity. This is helpful if you are recording a 2-hour concert directly to disk and you don't want any interrupts in recording.

The downside is that the mouse is sluggish and any other application that doesn't hook into the real-time kernel will only only get 5% of the CPU, so low-latency is not good for general desktop use. That is why you need to boot into it separate from a regular kernel.

It works well. If you run 'top' you can clearly see that 95% of the CPU goes to your primary application. Everything else gets postponed until the primary appliation is finished doing what it needs to do.

If you are doing anything "Live" such as recording, streaming to the web, or just want better video or audio editing performance then low-latency can help out. Don't expect a responsive machine otherwise for desktop use.

*from [http://ubuntuforums.org/archive/index.php/t-445198.html]("http://ubuntuforums.org/archive/index.php/t-445198.html") *
[/QUOTE]

---

### Post by linuxopjemac on 2010-07-02
If you are in the process of compiling kernels, maybe you could help a brother in need:

[http://ubuntuforums.org/showthread.php?t=1519878](http://ubuntuforums.org/showthread.php?t=1519878)

It's probably only editing one line in the source code and recompiling with the same conf file as the stock Ubuntu kernel.

---

### Post by derciojr on 2010-07-04
Good morning.

 I have a G4 800, early 2004. I've used Kubuntu 7.04, no problems. Now, when I try install 10.04, it can't format HD. With 8.04 is the same problem. The HD is fine (both 7.04 and original OSX can format it easyly). I tryed format with 7.04 before install 10.04 with no results. I think the problem is with the s.m.a.r.t. instructions that HD don't support, but I can't disable them in the installer.
Can you help me?

Thanks in advance.

---

### Post by JBWilliams on 2010-07-05
> **crazyphysicist said:**
> Hi, on running #patch p1 < ../patch-2.6.34-pf1
I get nothing but "HUNK Failed at..." for each entry is this supposed to happen?
I lost a couple newbie hours on this issue myself.  I wrongly assumed the 'p1' was related to the file's name; finally I looked up the patch command.  As 'p*num*' is a command option, there is a critical missing dash in sha.goyjo's instructions:

```
#patch -p1 < ../patch-2.6.34-pf1
```The above should work.

---

### Post by JBWilliams on 2010-07-10
**sha.goyjo:** Now that my machine is fully functional, I wanted to let you know that this guide was absolutely indispensable.  I compiled the kernel with 2.6.34-pf6, which appears to work great.   I used the system for a couple days before bothering with your xorg.conf; the change when I started using it was pleasantly dramatic.

I had only 2 major problems.  One was the typo described above.  The other was rather more annoying--I used update manager after having compiled the custom kernel, and the damn thing installed its own kernel updates.  I didn't catch the problem, and my boot sequence got caught in some kind of never-ending loop.  I ended up starting from scratch with a new Ubuntu installation (there may be a simpler fix for that, but I didn't have alternate internet access to look one up).  In a sense the problem still exists as I forgot to run update manager before my second kernel compile--I was careful once I did run it to uncheck the kernel-related files, but they're still listed, waiting for this dumb newbie to make a mistake.  Is there a way to make them disappear from the list so I won't accidentally install them later?

Many thanks again for your excellent guide.

---

### Post by coolman98 on 2010-07-11
Does it work  with a 1.2 ghz ppc g4 ?

---

### Post by JBWilliams on 2010-07-12
That's what I'm using; I'm very happy with it so far.

---

### Post by sha.goyjo on 2010-07-12
Alright ya'll, sorry for the lapse in posting (and adding your points of clarity/fixin to the guide). I'll get those in as quick as I can.

DMillard10, I'm a little confused at your need for the safe-upgrade. Was there anything odd about your update? apt-get update command updates the repository lists, so after that you should be able to install cpudyn without the need for the safe-upgrade.

pkmgarf, as to your question about the low latency choice, it's mostly a personal choice thing. Since I used the laptop for primarily single operation at a time situations, I rarely find I need to be running multiple services with a great deal of cpu cycles. Add to this the fact that most macs run with very low latency in OSX and I thought it would be a good idea. My first inclusion of the 1000hz clock into my powerpc mac kernels was at somebody else's advisement, and I have had great luck with them.

---

### Post by sha.goyjo on 2010-07-12
> **JBWilliams said:**
> **sha.goyjo:** Now that my machine is fully functional, I wanted to let you know that this guide was absolutely indispensable.  I compiled the kernel with 2.6.34-pf6, which appears to work great.   I used the system for a couple days before bothering with your xorg.conf; the change when I started using it was pleasantly dramatic.

I had only 2 major problems.  One was the typo described above.  The other was rather more annoying--I used update manager after having compiled the custom kernel, and the damn thing installed its own kernel updates.  I didn't catch the problem, and my boot sequence got caught in some kind of never-ending loop.  I ended up starting from scratch with a new Ubuntu installation (there may be a simpler fix for that, but I didn't have alternate internet access to look one up).  In a sense the problem still exists as I forgot to run update manager before my second kernel compile--I was careful once I did run it to uncheck the kernel-related files, but they're still listed, waiting for this dumb newbie to make a mistake.  Is there a way to make them disappear from the list so I won't accidentally install them later?

Many thanks again for your excellent guide.

You can do what I do. Go into synaptic and just uninstall the default kernel packages. That way they won't update. I find the PF kernel to be stable enough for production use.

---

### Post by coolman98 on 2010-07-12
I can't get the wireless to work help?

---

### Post by coolman98 on 2010-07-12
I can't get the wireless to work help!

---

### Post by coolman98 on 2010-07-12
never mind thanks for the tutorial I bought an ibook just for getting ubuntu on it 125$ ebay !

---

### Post by coolman98 on 2010-07-12
everything is kind of blue.

---

### Post by coolman98 on 2010-07-13
help!

---

### Post by sha.goyjo on 2010-07-13
Coolman98, please delete a few of those posts and condense them into a single post. In an IRC one liners are acceptable, but in a forum they fill up a page REALLY quick and it becomes difficult to navigate.

First off, I'm glad you got your wifi working sucdessfully. b43-fwcutter is a brilliant hack. As for the blue-ness, I could use some more information. I'm not precisely familiar with that problem, but maybe we could solve it with some more verbose info.

---

### Post by luvgirl12345 on 2010-07-15
Does this work with a 1.4ghz 14" g4?? does suspend work??

---

### Post by coolman98 on 2010-07-16
the bottom panel and some of the icons are blueish maybe x.org?
yes suspend works.

---

### Post by linuxopjemac on 2010-07-16
> the bottom panel and some of the icons are blueish maybe x.org?
yes suspend works. 

likely

what machine exactly? (everymac.com)

---

### Post by coolman98 on 2010-07-16
ibook g4 1.2 ghz 30 gig hd

---

### Post by linuxopjemac on 2010-07-16
14 inch or 12 inch ?

can you give me the output of:
```
cvt 1024 768
cvt 800 600
cvt 640 480
```

---

### Post by coolman98 on 2010-07-16
12 inch cannot copy from term.

---

### Post by linuxopjemac on 2010-07-16
then I can't help you.

---

### Post by coolman98 on 2010-07-16
okay I will try will screenshot work for you?

---

### Post by linuxopjemac on 2010-07-16
why can't you do a copy paste of the terminal ? You have X right ?

---

### Post by coolman98 on 2010-07-16
```
christopheer@christopheribook-laptop:~$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
christopheer@christopheribook-laptop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
christopheer@christopheribook-laptop:~$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
christopheer@christopheribook-laptop:~$ cvt 640 480
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
christopheer@christopheribook-laptop:~$ gnome-panel-screenshot

```

---

### Post by linuxopjemac on 2010-07-16
Try the following xorg.conf file:

```
Section "Device"
   Identifier   "Radeon9600"
   Driver      "radeon"
   BusID      "PCI:0:16:0"
EndSection

Section "Monitor"
   Identifier   "StandardMonitor"
   Option      "DPMS"
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
Option "PreferredMode" "1024x768_60.00"
EndSection

Section "Screen"
   Identifier   "StandardScreen"
   Device      "Radeon9600"
   Monitor      "StandardMonitor"
   DefaultDepth   24

   SubSection      "Display"
      Depth      8
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection      "Display"
      Depth      15
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection "Display"
      Depth		16
      Modes	"1024x768" "800x600" "640x480"
   EndSubSection
   SubSection   "Display"
      Depth      24
      Modes      "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

Section      "ServerLayout"
   Identifier   "Default Layout"
   Screen "StandardScreen"
EndSection

Section "DRI"
   Mode      0666
EndSection
```

---

### Post by coolman98 on 2010-07-16
thanks It worked. THANKS * 10000000000000000000000

---

### Post by linuxopjemac on 2010-07-16
NICE. I will put this xorg.conf on my website as well.

---

### Post by rjmusto on 2010-07-30
<PowerBook G4 12">

Thanks sha.goyjo for a great post.

Can I ask maybe a dumb question?  I'd read elsewhere about overheating problems with Ubuntu running on a PowerBook - which lead me to your post in fact.

As instructed, I first off used the "$sudo modprobe therm_adt746x" command.  Now on my system the cooling fan was running, but at this point it stopped and I haven't heard it since. So am a bit bothered that I've made things worse and not better.

Any suggestions/comments?

Thanks.

---

### Post by sha.goyjo on 2010-07-30
> **rjmusto said:**
> <PowerBook G4 12">

Thanks sha.goyjo for a great post.

Can I ask maybe a dumb question?  I'd read elsewhere about overheating problems with Ubuntu running on a PowerBook - which lead me to your post in fact.

As instructed, I first off used the "$sudo modprobe therm_adt746x" command.  Now on my system the cooling fan was running, but at this point it stopped and I haven't heard it since. So am a bit bothered that I've made things worse and not better.

Any suggestions/comments?

Thanks.

Did you put the therm_adt746x line into /etc/modules? If not, the fan won't start on boot. Otherwise, I'd be worried about a mechanical failure of the fan. I may have a few spares lying around which I could send to you for shipping though :-). If you can give us some more detailed info on the problem I think we could be of more help.

---

### Post by rjmusto on 2010-07-30
Yes, I did initially include it in /etc/modules, but I have taken it out again. Set like this, the fan does seem to run ok, so it seems 10.04 works ok for me unaided. No idea why.

Happy to provide more detail if it would be useful - just let me know what.

Know a good CPU temp monitor applet? Might be wise for me to keep an eye on it.

---

### Post by j_anthony on 2010-08-12
Thanks to this how-to, I've compiled my first kernel (from 2.6.35), and I'm impressed with how fast Lucid runs on my iBook G4. I followed all the instructions successfully down to the last step, where I hit a couple of problems. When I try to run hdapsd, I get the following error:

```
anthony@exmac:~$ hdapsd
Thu Aug 12 17:10:13 2010: Starting hdapsd
Thu Aug 12 17:10:13 2010: WARNING: You did not supply any devices to protect, trying autodetection.
Thu Aug 12 17:10:13 2010: Could not read from /sys/block/hda/device/unload_heads: Operation not supported
Thu Aug 12 17:10:13 2010: Could not detect any devices.
```

Also, apt says "package not found" when I try to install gpmudmon.

I already have pmu_battery working; does gpmudmon do something different that I need? And how important is hard disk parking? I've been running the standard ppc install of Lucid for a month or two, and I assume I didn't have that feature. I only need that if I drop my computer while the disk is spinning, right?

There are several errors showing in TTY1 but I don't know how to copy them. They include the following:
Invalid ROM contents

unable to open rtc device (rtc0)

init: ureadahead main process (232) terminated with status 5 (I'm not sure if it's supposed to do that or not)

not starting hdapsd: neither /sys/block/sda/queue/protect nor /sys/block/sda/device/unload_heads do exist, please read /usr/share/doc/hdapsd/README.Debian (I did, but I still couldn't figure out what was wrong)


Also, the computer hangs on shutdown and the fan starts going like crazy. I have to hold down the power button to power it off.

Finally, the F11 key no longer works to go fullscreen in a picture viewer or browser window. As far as I can tell, everything else on the keyboard is normal, but I could be missing something. On a 12" screen, I use this feature all the time, and I'm hating opening a menu every time I need fullscreen.

Can someone point me in the right direction here? I'll be glad to provide more info if you need it.

---

### Post by Arkasai on 2010-08-12
I'm running into a little trouble, I'm able to launch the LiveCD but on my first install it hung after I told it to reboot.  So I hard booted and reinstalled Lucid.  I was able to get it to reboot after the install (had to pull the CD out with some needle nose pliers, cause it was hopelessly stuck.)  But now when booting the system, I see the Ubuntu 10.04 splash screen for a few seconds before it goes dark.  So it doesn't load GNOME, but I'm able to login through the command line.  

I'm on an iBook G4 1.4Ghz, 1GB RAM, 32MB ATI FireGL T2e, Broadcom network card etc.  Pretty sure those specs are very close to yours so I'm not sure why I'm running into this issue.  I did encounter some wirmware errors when booting the LiveCD but I expected those and they didn't halt the install.  Maybe a faulty burn(didn't check MD5)?  I made sure the CD burned at 4X rather than 24X, so errors are unlikely right?

---

### Post by sha.goyjo on 2010-08-12
> **j_anthony said:**
> Thanks to this how-to, I've compiled my first kernel (from 2.6.35), and I'm impressed with how fast Lucid runs on my iBook G4. I followed all the instructions successfully down to the last step, where I hit a couple of problems. When I try to run hdapsd, I get the following error:

```
anthony@exmac:~$ hdapsd
Thu Aug 12 17:10:13 2010: Starting hdapsd
Thu Aug 12 17:10:13 2010: WARNING: You did not supply any devices to protect, trying autodetection.
Thu Aug 12 17:10:13 2010: Could not read from /sys/block/hda/device/unload_heads: Operation not supported
Thu Aug 12 17:10:13 2010: Could not detect any devices.
```

Also, apt says "package not found" when I try to install gpmudmon.

I already have pmu_battery working; does gpmudmon do something different that I need? And how important is hard disk parking? I've been running the standard ppc install of Lucid for a month or two, and I assume I didn't have that feature. I only need that if I drop my computer while the disk is spinning, right?

There are several errors showing in TTY1 but I don't know how to copy them. They include the following:
Invalid ROM contents

unable to open rtc device (rtc0)

init: ureadahead main process (232) terminated with status 5 (I'm not sure if it's supposed to do that or not)

not starting hdapsd: neither /sys/block/sda/queue/protect nor /sys/block/sda/device/unload_heads do exist, please read /usr/share/doc/hdapsd/README.Debian (I did, but I still couldn't figure out what was wrong)


Also, the computer hangs on shutdown and the fan starts going like crazy. I have to hold down the power button to power it off.

Finally, the F11 key no longer works to go fullscreen in a picture viewer or browser window. As far as I can tell, everything else on the keyboard is normal, but I could be missing something. On a 12" screen, I use this feature all the time, and I'm hating opening a menu every time I need fullscreen.

Can someone point me in the right direction here? I'll be glad to provide more info if you need it.

I have no idea about the hdapsd error. That's odd to me. Hard disk parking is not a necessary feature, but the howto's purpose was to get as functional of an install as physically possible. If you can't install it, you won't die or anything.

For the f11 thing, have you tried fn+f11? I've had trouble sometimes with the default being that the f keys have typical mac button functions instead of their numbered standard functions. If that fn+f11 works, there are ways to switch it to the other way.

Unfortunately, I no longer have my ppc ibook to test on, as my fiancee has it with her in Burkina Faso, and will have it with her for the next 24 months. So I cannot check and see if those startup errors are abnormal. Somebody else will have to weigh in on this.

As for gpmudmon, I've never had any luck getting pmu-battery to display the battery for the g4. If it works for you, I'm glad! I would be willing to admit that I can be a bit dense sometimes.

The shutdown thing bothers me a bit. Can I ask, does it still happen with the standard kernel?

---

### Post by sha.goyjo on 2010-08-12
> **rjmusto said:**
> Yes, I did initially include it in /etc/modules, but I have taken it out again. Set like this, the fan does seem to run ok, so it seems 10.04 works ok for me unaided. No idea why.

Happy to provide more detail if it would be useful - just let me know what.

Know a good CPU temp monitor applet? Might be wise for me to keep an eye on it.

Very unusual. I remember that every time I ran the live cd, the fan would work, but after install it wouldn't till I started up the kernel module, and the only way to keep it running was to put it in /etc/modules. It seems your situation was the exact inverse of mine.

Welcome to powerpc ubuntu, where we accept the unexplainable as commonplace, as long as we can get it to f-ing work.

---

### Post by j_anthony on 2010-08-13
Thanks again for this thread and for the great advice. Here's what's happening with my install now.

> Hard disk parking is not a necessary feature, but the howto's purpose was to get as functional of an install as physically possible. If you can't install it, you won't die or anything.

I just removed hdapsd so I don't have to see the errors anymore.

> For the f11 thing, have you tried fn+f11? I've had trouble sometimes with the default being that the f keys have typical mac button functions instead of their numbered standard functions. If that fn+f11 works, there are ways to switch it to the other way.

Before posting, I had tried every combination I could think of with f11. The only thing f11 will do is open a photo in the image viewer, but it won't full-screen it once open. If you know how to restore the function, please do instruct me.

> As for gpmudmon, I've never had any luck getting pmu-battery to display the battery for the g4. If it works for you, I'm glad! I would be willing to admit that I can be a bit dense sometimes.

Since my earlier post, I've discovered that pmu_battery doesn't work reliably. Sometimes it refuses to recognize when the battery is discharging. A quick Google search cleared up my trouble with installing gpmudmon (For the ignorant among us, you might clarify in the how-to that the package is gpmudmon-applet). Unfortunately, gpmudmon doesn't seem to be doing anything other than displaying a "thunderbolt" icon on the panel; it doesn't seem to know the battery exists, and the Battery tab is gone from the power manager. Is there a module or something that needs to be loaded first?

> The shutdown thing bothers me a bit. Can I ask, does it still happen with the standard kernel?

It's shutting down okay now with either kernel. I don't know what changed. 

Some weird bluish colors show up on the desktop when I boot with the old kernel, I suppose as a result of the new xorg.conf, but if I ever want to use that kernel regularly, I'm sure I can figure out how to rebuild the file.

To sum up, I'm not worried about hard drive parking, but I need a working battery monitor and I need to know how to restore normal functionality to the f11 key. Any help is appreciated.

---

### Post by sha.goyjo on 2010-08-13
> **j_anthony said:**
> Thanks again for this thread and for the great advice. Here's what's happening with my install now.

Before posting, I had tried every combination I could think of with f11. The only thing f11 will do is open a photo in the image viewer, but it won't full-screen it once open. If you know how to restore the function, please do instruct me.

Since my earlier post, I've discovered that pmu_battery doesn't work reliably. Sometimes it refuses to recognize when the battery is discharging. A quick Google search cleared up my trouble with installing gpmudmon (For the ignorant among us, you might clarify in the how-to that the package is gpmudmon-applet). Unfortunately, gpmudmon doesn't seem to be doing anything other than displaying a "thunderbolt" icon on the panel; it doesn't seem to know the battery exists, and the Battery tab is gone from the power manager. Is there a module or something that needs to be loaded first?

Some weird bluish colors show up on the desktop when I boot with the old kernel, I suppose as a result of the new xorg.conf, but if I ever want to use that kernel regularly, I'm sure I can figure out how to rebuild the file.

.
1. The weird bluishness is caused by the alterations to your yaboot.conf, not the xorg.conf. X hasn't started yet by that point, and yaboot doesn't pull anything from xorg.conf

2. How-to edited for clarity. Thanks for pointing that out.

3. Okay, I'm beginning to think that there is something wrong system-wide with your pmu integration. pmu support should be making your f-keys work properly, giving you battery info, and pushing your fan's regulation to therm_adt746x (I think). These problems are beginning to look rather linked. That you see them in both kernels means probably not a kernel build error. So I'm beginning to question actual packages. Can you install powerprefs (I think that's the name of it) and see if you can change any of your settings in there, or see if it even recognizes a running pbbuttonsd.

---

### Post by j_anthony on 2010-08-23
> **sha.goyjo said:**
> 1. The weird bluishness is caused by the alterations to your yaboot.conf, not the xorg.conf. X hasn't started yet by that point, and yaboot doesn't pull anything from xorg.conf

2. How-to edited for clarity. Thanks for pointing that out.

3. Okay, I'm beginning to think that there is something wrong system-wide with your pmu integration. pmu support should be making your f-keys work properly, giving you battery info, and pushing your fan's regulation to therm_adt746x (I think). These problems are beginning to look rather linked. That you see them in both kernels means probably not a kernel build error. So I'm beginning to question actual packages. Can you install powerprefs (I think that's the name of it) and see if you can change any of your settings in there, or see if it even recognizes a running pbbuttonsd.

1. I should have said I see bluish colors on the desktop AFTER I boot with the old kernel. The color problems are on the Gnome desktop. That would be X, wouldn't it?

3. Nope, the problem with pmu_battery and the F11 key only exists with the custom kernel. I double-checked just now. When I boot with the old kernel they work as expected. But I'll try installing powerprefs and see if I learn anything.

Also, it's hanging on shutdown again, but only if I'm logged in when I shut down. If I shutdown from the login screen with nobody logged in, it shuts down properly, as far as I can tell. Don't know if that tells you anything.

---

### Post by sha.goyjo on 2010-08-23
> **j_anthony said:**
> 1. I should have said I see bluish colors on the desktop AFTER I boot with the old kernel. The color problems are on the Gnome desktop. That would be X, wouldn't it?

3. Nope, the problem with pmu_battery and the F11 key only exists with the custom kernel. I double-checked just now. When I boot with the old kernel they work as expected. But I'll try installing powerprefs and see if I learn anything.

Also, it's hanging on shutdown again, but only if I'm logged in when I shut down. If I shutdown from the login screen with nobody logged in, it shuts down properly, as far as I can tell. Don't know if that tells you anything.

OHHH oooh oooh,

Okay, THOSE errors I've seen before. Are you using my xorg.conf and setting KMS off in yaboot? I used to get things similar to what you are saying before I fixed those two things. With the glitchy blue graphics and weird function keys. BTW is it JUST f11, or do you get trouble with the other function keys as well?

---

### Post by j_anthony on 2010-08-24
> **sha.goyjo said:**
> Are you using my xorg.conf and setting KMS off in yaboot? 

I'm using your xorg.conf but I don't know about KMS. How do I do that?

> BTW is it JUST f11, or do you get trouble with the other function keys as well?

All the other function keys seem to work as expected in ubuntu, and fn+f-key gives them the original iBook functions, volume/brightness controls, numlock and eject.

To clarify, below I'll list each new issue I'm having since following all steps on the how-to, grouped according to whether they occur when I'm running the old kernel or the custom one I compiled per your instructions.

PostFactum:

[LIST]
[*]Non-working f11 key
[*]hdapsd won't run and gpmudmon-applet doesn't recognize a battery (Neither is currently installed)
[*]Erratic function of pmu_battery
[*]If any user is logged in, hangs on shutdown but not on restart
[*]Displays the following messages during second-stage boot:
radeonfb 0000:00:10:0 Invalid ROM contents
drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[/LIST]

Old Kernel
[LIST]
[*]Since installing your xorg.conf, funny bluish colors on some desktop elements
[/LIST]

---

### Post by Wesleytf on 2010-08-24
I got ubuntu installed and working, but I'm a bit nervous about executing that entire protocol, but I'd like the battery monitor.  I tried running just that line and it looked like it worked, but I don't see a monitor anywhere.  Do I have to run the whole thing just to get the battery monitor?

---

### Post by j_anthony on 2010-08-26
> **Wesleytf said:**
> I got ubuntu installed and working, but I'm a bit nervous about executing that entire protocol, but I'd like the battery monitor.  I tried running just that line and it looked like it worked, but I don't see a monitor anywhere.  Do I have to run the whole thing just to get the battery monitor?
For some reason it didn't work for me either. Instead, try loading the pmu_battery module:
```
sudo modprobe pmu_battery
```
If you like it and want it to run every time you reboot, you'll need to add it to /etc/modules
```
gksudo gedit /etc/modules

```
and add a new line:
```
pmu_battery
```
Save the file and close. Now the battery monitor should always load by default.

If that all works great, you could finish up by removing gpmudmon-applet:
```
sudo apt-get remove gpmudmon-applet
```

---

### Post by Wesleytf on 2010-08-27
hey, that worked like a charm!  Thanks mega!

---

### Post by JDFIght on 2010-09-26
Thanks sha.goyjo!  

I have been running debian and ubuntu on my 17in powerbook g4 for about a year now.  Your thread helped me compile my first working kernel! Anyway,  I had some issues initially with the 2.6.35 kernel - After booting into the new kernel the Powerbook touchpad was completely borked.  So,  I went in and disabled all of the ps/2 mouse support options that i could find and now my touchpad is working :D

Also,  i am glad I found this thread because I didn't know about the therm_adt746x -  My powerbook is much cooler now :P

I am currently running lucid on a 17in 1.67ghz powerbook.  Kernel version: 2.6.35-pf8

Now if I could only get suspend/hibernate to work - I have never had any luck with suspend on any of the various linux builds (debian Lenny, ubuntu karmic, lucid, etc...) I have run on this machine...  It just always wakes to blank screen... nothing...

---

### Post by rkevsmith on 2011-04-16
sha.goyjo, 

Thanks for all this.

As of April 2011, is this still good info?

The reason I ask is in getting up-to-date 2.6.34 kernel from kernel.org ( inux-2.6.34.8 ) and the PostFactum patch (2.6.34-pf7) as of now to compile a new kernel, I'm running into problems.

#patch -p1 < ../patch-2.6.34-pf7

is telling me

Reversed (or previously applied) patch detected! Assume -R? [n]


Thanks for any advice, 
K

---

### Post by aquilainferna on 2011-11-20
Hi Sha.goyjo i send you one hi from México, i decide to turn  my ibook into Ubook after seeing your How to, i didnt have any trouble with it, but while i was testing the system i realize that, when i open my windows live email, it doesnt open as normally it do, it open in a mobile version of it and i dont know if i commit a mistake when i was installing the system or it is another issue with ibooks.

And finally thanks for all, this is and will be one of my more read port on this blog. 
If anyone knows whats happen please helpme

---

### Post by coolman98 on 2012-03-01
whahaha i miss my ibook  with ubuntu

---

### Post by sha.goyjo on 2012-03-01
I have to apologize for not being on here to check on this thread more often. Work, the completion of college, and an incoming wedding have held me off of many social responsibilities.

Regrettably, I no longer have an iBook (it puffed the last of it's magic smoke) so I really can't offer reliable advice any more. I'm going to leave the howto up for legacy purposes, and anybody who wants to post updates can PM me and I'll include them in the header message.

Again, sorry for my absence.

---

