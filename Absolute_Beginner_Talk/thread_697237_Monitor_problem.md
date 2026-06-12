---
title: "Monitor problem"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by TaylorMarieXXX on 2008-02-14
I just wanted to drop in and introduce myself to the community as I think I will be around here a full time.  I'm a Florida boy, I love saltwater fishing, just got my Juris Doctor, and I've currently started a couple of internet based business, so I need a good reliable operating system.

My first computer was a 286 with 512kb ram, and a 20meg hard drive.  It ran Dos 3.2.  After having it for two weeks my father came home one day in a panic as I had the top off the case off installing at the time, a blazing fast 9600 baud modem.  I've been into computers since.  Like a few people here I was kind of disturbed with the rise of windows.  Why did I need this stuff?  I'm a DOS wizard, it just makes my computer run slow for some pretty graphics.  I was absolutely beside myself when windows became the operating system in exchange for a fake little command prompt.  So I've always hated windows.

So when I learned about Linux (via a backtrack 2 CD my buddy gave me) I was really stoked when I got Ubuntu and I feel happy to be going back to my roots.  I couldn't get a good install on a very old desktop I had so I bit the bullet and put it on my Dell D610 laptop and couldn't be happier.  The problem is that I'm still learning from the begining the command line based linux language.  And the fact that Ubuntu trys to make everything doable without it kind of hampers the learning process of people like me who want to understand how everything works.  If it weren't for the software repositories (possibly the best idea of the decade) I don't think I would've gotten off the ground.

Anyways, just wanted to introduce myself as I'm sure I'll be around on my linux learning journey.  I've got a problem getting my laptop monitor back to its original configuration because I'm trying to install my new Acer 22" flat panel as my main monitor but run it off my laptop (I have wireless keyboard etc.).  But I will post those in the relevant forum.  If anyone feels me with how I got here and could drop by and tell me what to do to get everything working (like i said I'm a command line retard so I hope I can do it through the GUI until I leanr that stuff) I would really appreciate it.

---

### Post by tgalati4 on 2008-02-14
Welcome to the community.  Post the output of the following (from a command line of course):

lspci -vv

and

lsmod

---

### Post by stevejesus on 2008-02-14
Your not gonna try and sell something are you?

---

### Post by TaylorMarieXXX on 2008-02-14
Cool, well it looks like I will get the help I need with the problem in this forum.  If it ends up being the wrong forum could someone move it to the right forum.  I've got 5 hours of work to do tonight and it's something I need to get cleared up.  This is my first big configuration problem and curing this will hopefully allow me to keep my faith in Ubuntu as being use friendly.  Here's the deal.

Like I said I installed Ubuntu on my dell D610 laptop.  When I installed everything went fine and my display installed perfectly.  The display and resolution was nice and high so my icons and everything was nice and small how I liked it.  I was really stoked because despite the fact that my laptop is almost two years old it ran superfast and even did the compiz thing great (more to show off my friends how much cooler this is than windows) and everything ran great.

So, Dell D610 laptop, installed perfect, resolution was nice and high.  I have a wireless keyboard and mouse that detected and installed and runs perfect so I figure all I needed was a nice big monitor and I could use this like my desktop now that I had a big monitor.

The monitor is an Acer AL2216W.  So I went to System>Administration>Screens and graphics and I was able to get the new monitor which is pluged into the monitor port in the back of my laptop to work fine as a secondary monitor.  Where its just like a big desktop on two screens.  But thats not what I wanted, I want it to be the man monitor and just show everything the same on both monitors.  As I was messing with the configuration, something messed up and the Acer monitor stopped working alltogether and my computer only restarts in graphic safe mode thing.  Now I can't get my leptop monitor to go back to the normal resolution and size regardless of whatever I try to change the settings too.  I've tried the generic settings and it restarts the same every time.  When I click on detect It detects as plug n play monitor at 800x600 resolution which is  not what it originally was after my install. 

 First I'd lick to get my laptop monitor back to its normal setting so if I go mobile it works right.  Second I'd like to be able to use my new monitor and have it so when it plubs in it's the sole monitor I use.  I will post that log in just a second

---

### Post by TaylorMarieXXX on 2008-02-14
lspic -w came back with invalid and just listed all the options and proper usage.

the other came back with:

john@john-laptop:~$ lsmod
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  1 
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
video                  18060  0 
ac                      6148  0 
battery                11012  0 
bay                     6912  0 
dock                   10656  1 bay
button                  8976  0 
sbs                    19592  0 
container               5504  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
joydev                 11328  0 
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
ipw3945               119840  1 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
usbhid                 29536  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
usblp                  15104  0 
i2c_core               26112  0 
serio_raw               8068  0 
hid                    28928  1 usbhid
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 41388  0 
pcspkr                  4224  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
psmouse                39952  0 
intel_agp              25620  0 
agpgart                35016  1 intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  7 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_piix               17540  3 
tg3                   110980  0 
ehci_hcd               36492  0 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
uhci_hcd               26640  0 
usbcore               138632  5 usbhid,usblp,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
john@john-laptop:~$

---

### Post by TaylorMarieXXX on 2008-02-14
Hey guys, I came here because I am having a problem getting my dell D610 laptop to go back to the monitor setting after installation.  I dropped a quick post to say hello and I think they were trying to help me there, but I realized this would be the best forum.  If you want to know my background you can check out
[http://ubuntuforums.org/showthread.php?p=4334003#post4334003]("http://ubuntuforums.org/showthread.php?p=4334003#post4334003")

Here's the deal, I bit the bullet and installed Ubuntu on my best laptop and I am so stoked by how well it's running.  The laptop is almost 2 years old but it runs laser fast.  I don't understand why anyone would ever run Winblows.

So here's the problem.  I installed Ubuntu on my Dell D610 notebook and everything runs flawlessly, my display and resolution was nice and crisp and all my icons were like I liked.  I have a logitex wireless mouse and keyboard so I bought a nice big monitor to plug into the blue monitor port in the back of my laptop so at home I could have a nice big monitor.  It's an AcerAL2216W.

So when I hooked the monitor up I could get it to work fine as a secondary monitor.  Where it just like expands the desktop over two monitors.  But thats not what I wanted, I just wanted the Acer to show the same as my lapto monitor so I could just se the laptop to the side and use my new monitor.  Somewhere in the process of getting it working I messed up my Dell monitor setting and now it keeps restarting in Graphics safe mode and all the icons are too big now and I can't get it back to how it was.  When I click the detect thing under screens and graphics under administration it says plug n play at 800x600 and restarts in the same goofy big desktop mode thing.

So the first thing I want done is my laptop to just go back to the resolution settings it had after my initial install.  Second I would like to set it up soe that my new monitor is likemy main monitor so I can just set my laptop aside and use the big monitor and wireless keyboard and mouse.

Thank you for any help.

---

### Post by jespdj on 2008-02-15
Instead of complaining, explain exactly what you did (step by step) and explain exactly what / how / why it did not work. Did you get any error messages? If so, post them.

What is the problem? Are you not getting anything on your new monitor? Are you sure it's a problem with Ubuntu? Does the monitor work properly when you run Windows? Which display driver are you using? How are you connecting the computer to the monitor (VGA or DVI)? Are you sure that the video card in your laptop can handle the monitor?

There's a great Ubuntu community here ready to help you.

---

### Post by TaylorMarieXXX on 2008-02-15
I've certainly atleast done my homework, I've put about 14 hours into trying to solve this at this point.  I've found a bunch of threads on the subject matter and since I'm not too confident about just going in and messing with my x.conf I figured I'd see if I could find someone with the same set up and they could let me know what they do.  I figure I'll post here and see if someone can save my faith in Ubuntu before I give up.  I really want it to work, I just don't have 20 work hours to put into this thing when I need to be getting work done.

I have a Dell D620 Laptop, with the NVidia 110M graphics card.  I just bought a 22" Acer Monitor AL2216W.

Ubuntu installed with zero problems.  I was able to run and utilize Compiz no problem.  After the install my resolution worked fine, icons and everything was nice and small like I like them.

When I first hooked up the new monitor with System>Administration>Screens and Graphics  I was able to get it work as a secondary monitor (where it's like you just have one big desktop on two screens).  While trying to adjust the settings, the settings of my laptop's monitor got messed up and now everytime it restarts it starts it does so in Graphic Safe mode.  In the same settings as described above it detects my laptop monitor as 800x600 plug n play, even if I completely disconnect the new monitor I bought.  Nothing I have done has made me able to restore my laptop screen to the size it was before all this.  RIght now all the icons are huge and bulky.  

So first I would just like to get my laptop monitor back to the correct resolution so I can actually get some work done.  I'd just like to return to how it was.

Second if i'm going to continue using Ubuntu I need to get my new monitor to work, and I need it not to be a secondary monitor thing, but to Mirror the default monitor.  It is hooked up to the laptop via the vga plug in the back.

---

### Post by Spenzer4Hire on 2008-02-15
I've done dual monitor setups with nvidia cards, and I'm currently using the AL2216w on a GF 6150.  I haven't tried a dual monitor setup since the "screens and graphics" addition in 7.10 but I always had really good luck with the nvidia utility.  If you have the proprietary nvidia drivers installed run ```
sudo nvidia-settings
``` and configure things through there.

Good Luck!

---

### Post by TaylorMarieXXX on 2008-02-15
Wow, I guess whatever I did last night at 5am right before bed worked (uninstalled a bunch of drivers and reinstalled the Nvidia driver).  I was able to adjust my resolution for my laptop screen under Preferences>Screen Resolution which i had tried a bunch of times but this time it finally worked.  Lowest I could get was 1024x7** but that will work.  And then out of no where I was able to set up the new monitor and all of a sudden the 'mirror default' button lit up for the first time.  But now I have a new set of problems.

First is whenever I try to shut down or run anything in System>administration it acts like its launching but no window comes up.  I would think its sending it to the screen which isnt there (my laptop screen is black which is actually what I want) but all my tool bars and everything else is loading on my external screen fine.  Same deal when I click Turn off, it doesn't come up with the six options.  I'm pleased though becuase atleast I can do work.  And Compiz started working fine again.  Let me tell you, compiz is pretty sick on a 22".

The other problem is since I have such a big monitor I want to crank the resolution way down (up?) so I have smaller Icons, right now the resolution it is at is fine, but I could go smaller but since I cant get any administration windows up I dont know what to do.

I'm just taken aback that after 14 hours all I had to do was reinstall the drivers.

---

### Post by posburn on 2008-02-15
I'm a bit of a Linux noob, but my suggestion is to become friends with xrandr.  I also initially had some problems with my dual monitor setup (I'm using an intel card though), but the xrandr commands really simplified things.  For example, let's say I  boot up my laptop (1024x768 ) and then connect it to the external monitor (1440x900).  By typing the following in a terminal:

```

xrandr --output VGA --mode 1440x900
```

I direct my gfx card to output a signal to the monitor (an Acer BTW) at its native resolution.  Works perfectly.  The laptop is still at 1024x768 and the screens are mirrors of one another, not an "extended desktop".

There are lots of other things that can be done with xrandr, but maybe give this a try and see if it helps.  By the way, I've found that the "Screens and Graphics" dialog under System->Administration really didn't work that well for me when it came to setting up the dual monitors.

---

### Post by tgalati4 on 2008-02-15
That's lspci -VEEVEE (not double-u) :  lspci -v  or lspci -vv  (extra verbose)

It looks like you have on-board, Intel graphics (intel_agp).

You will need to get familiar with your /etc/X11/xorg.conf file.  First make a backup of it:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
[B]
Without[/B] the second monitor attached:

sudo dpkg-reconfigure -phigh xserver-xorg

Reboot.  

You should now have full resolution on your laptop.  You should now have a working xorg.conf.  Let's make a backup of it:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.working

Now is the time to search the forums for *dual monitor*.  Windows handles dual monitor well.  Dual monitor can be made to work in Linux, but it requires some work on your part.  It is not plug-and-play.

Print out a copy of xorg.conf so you have a copy to refer to as you take notes on how to set up.  You will probably have to edit xorg.conf manually to get the configuration that you want.

---

### Post by freebeer on 2008-02-15
> **TaylorMarieXXX said:**
> 

First is whenever I try to shut down or run anything in System>administration it acts like its launching but no window comes up.  

Just a guess here, but whenever you launch one of those programs, you're going to be prompted for a password.  (Administration stuff usually needs sudo privileges.) I suspect that the password dialog window is launched, awaiting your input, but due to your screen configuration, you're not seeing that prompt.  It may be hidden behind another window, or perhaps minimized somewhere on the task bar.  Once you answer the password prompt you should then see the application launch.

---

### Post by TaylorMarieXXX on 2008-02-15
Wow lots of great stuff, thanks guys I'll try it out.  I actually got it kind of working. 

I switched my bios which was from Docked, to whatever the other option was.  Now my Acer is working and my laptop is dark which is what I want.  Let me try that stuff.

---

### Post by TaylorMarieXXX on 2008-02-15
Here is my .conf file.  I tried making some of the changes you guys suggested and the Acer just stopped working and it would boot with the laptop monitor.  So I just replaced the .conf with my backup and now it's back to working with the acer but the resolution is still 1024x768.   At this point the only thing I really need to get taken care of is the resolution.  Native resolution on my monitor is 1600x1050@50.

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"TwinView"	"on"
	Option		"TwinViewOrientation"	"clone"
	Option		"SecondMonitorHorizSync"	"28.0-33.0"
	Option		"SecondMonitorVertRefresh"	"43-72"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"640x480@60"	"800x600@56"	"800x600@60"	"1024x768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" #     
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
	Option		"TwinView"	"on"
	Option		"TwinViewOrientation"	"clone"
	Option		"SecondMonitorHorizSync"	"28.0-33.0"
	Option		"SecondMonitorVertRefresh"	"43-72"
EndSection
Section "screen" #     
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #     
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by TaylorMarieXXX on 2008-02-15
Bump

Still trying to get my resolution down

---

### Post by TaylorMarieXXX on 2008-02-16
An Admin can change the heading to Solved!

I took the time to type this because I got a good amount of help from you guys, and while no one gave me 'the answer' enough of you contributed enough good stuff I was able to figure it out on my own.  So I took and now I'm giving because I see tons of questions on this.

Ok, so I got everything worked out and I'm back to loving Linux, and I learned something important about Linux and I will discuss that at the end.

Right now my Acer 22" is basically completely mirroring my laptop screen but it is doing so at 1920x1200 which is great.  The only thing is the laptop monitor remains on, it turns off when I manually put into my xorg 1600x1050 which is the native resolution of my monitor but that cuts off some of the bars. 

 Here is how I got to where I got.  Basically at first I could only get the external monitor working when I had that goofy program under admin "Screen and something..."  so I copied that xorg.conf.  Then I removed that program, reset everything "dpkg -reconfigure -phiph xserver-xorg" and that gave me a nice clean  xorg.conf and my laptops resolution returned to normal.  Then I can't believe how lucky I got on my first try and just added 2 lines and changed the resolution.  Basically the two lines I added to my xorg were the two below beginning with Twinview...  Then I just changed the resolution in the one place I saw it in Xorg. and BAM it worked.

Section "Device"
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"TwinView"	"on"
	Option		"TwinViewOrientation"	"clone"
	Option		"NoLogo"	"True"
EndSection

That's all I had to do.  Also make sure that the Nvidia is enabled under restricted driver management.   I can't believe how easy it was.  The only thing left is to find out the command to turn my laptop monitor off once my external is on.  Like I said when I run it in 1680 it does so but I lose part of the toolbar.  So I have 1920 running even though it automatically changes it to 1680 without messing up the toolbars. 

So if anyone knows the command to add to my xorg to shutoff my laptop monitor while using my external let me know.  I'm not sure I can do it the way I'm set up because basically my xternal is reproducing my Laptop directly, resolution and all.

Here is what I learned about Ubuntu.  Ubuntu tries very hard to have as many GUI's for just about everything you need so if you aren't good at line commands you can get most things working.  The culprit with my problem though was the GUI "screen configuer.  I've noticed that while the GUI's will help the majority of people, they aren't as heavily tested and debugged as one might thing.  Basically if you don't know the line commands (which also makes you understand what happening, the GUI might save your butt, but equally it could be the cause of your problems.  I spent 18 hours trying to fix a problem that I could've figured out using xrandr and editing my xorg.conf in less than an hour.  And this is still my concern with Ubuntu.  I don't have the time to learn all this at once, I can't afford the down time it costs me.  Though if you can stay functional and learn as you go you will have unprecidented control and understanding of exactly what your computer is doing.  The lesson I learned is that the GUI file did nothing but clutter up and mess up xorg, and it failed to sense my monitor or the external monitor.  As an aside when I ran xrandr it didn't detect the external monitor under any circumstances.  I just plugged in the twin view and it worked.

---

### Post by jespdj on 2008-02-18
> **TaylorMarieXXX said:**
> An Admin can change the heading to Solved!

No, you can set the thread to Solved yourself. Do you see the "Thread Tools" link near the top of the page? There's a link there where you can set your thread to Solved.

Good that you got the problem fixed. :)

---

