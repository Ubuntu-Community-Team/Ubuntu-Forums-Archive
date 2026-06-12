---
title: "Live CD 6.10 installation fail on sony laptop"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by scottnoakes on 2007-03-06
Hi,

I've got a Sony Vaio Laptop PCG-FX103 which I have replaced the HD on and the Windows ME  recovery disk will no longer work due to this change.

I would like to install Ubuntu however am having no luck so far. I've tried most things mentioned on the basic CD boot intro help screen. It looks like the installer is failing to detect the graphics card correctly, stopping after 30secs with a multi coloured 'snow' display on the screen.

I've tried booting from the boot: command prompt as mentioned:

boot: live vga=771 noapic nplapic  

But again no success. I have found a page which indicates that installing linux on this model is possible [http://cwrose.de/vaio/fx101.html](http://cwrose.de/vaio/fx101.html) 

How do I specify it to boot using the Intel i815EM i810 (X11) graphics chipset? What should I do now?

Help! Thanks Scott.

---

### Post by xyz on 2007-03-06
Hi,
Not sure this will be of any help but what's your HD brand? Because, following your link, I read this: (see bold)
> ntel Celeron (Coppermine) 600MHz
Intel i815EM
64 MB RAM (Samsung), upgraded to 128 MB
**10 GB HDD (Futjitsu), exchanged to Hitachi due to failure**
24x CD-Rom (QSI)
25 mAh Li-Ion Accu (max 2h)

---

### Post by proalan on 2007-03-06
try configuring the graphics card manually before install

open a terminal and type

sudo dpkg-reconfigure xserver-xorg

once done restart the xserver by 

control+alt+backspace

I've got the i810 on my laptop and it definitely works

---

### Post by scottnoakes on 2007-03-06
Hi,

The replacement HD is a Hitachi 2.5" 80GB, 5400rpm, 8M Cache, ATA-100. Ive installed, patitioned and formatted it, no problems. 

THe laptop has also been upgraded to 256MB ram.

Cheers Scott.

---

### Post by scottnoakes on 2007-03-06
Ok,

Now Im getting confused. I thought to open a terminal you first need to install the OS? Or are you saying do this from the command prompt option available from the Live CD splash screen? The things you mention seem to me that I would need the OS installed first in order to get this far.

I've downloaded the alternate CD and will try using this tonight. Are you saying I can use the Live CD to perform your selected actions?

Cheers Scott.

---

### Post by xyz on 2007-03-07
Yes Live Cd's can do just sooo many things even clone your Windows!
Just to give you an idea, have a look at [The LiveCD List]("http://www.frozentech.com/content/livecd.php")
Also read our excellent [Psychocats]("http://www.psychocats.net/essays/index.php")
Let us know how you get along.

---

### Post by scottnoakes on 2007-03-07
Hi Xyz,

I'll read through the links you suggested and see what happens. I've scanned the and essay it seems to ring true with me. I've been a software engineer for 10 years and am now a product manager. When you're used to OS's like windows which (in my experience) _just_install_ attempting to install Linux feels like you've come up against a brick wall. 

If Ubuntu is Linux for Human Beings then I have been left feeling decidedly human (mortal, small and insignificant!). Im sure it installs just fine on a desktop system so the laptop problem is where its falling down, fair enough. Anyways I shall push on and overcome. I'll give this a week of effort and see what happens. My requirements are minimal:

- I only use the laptop for wireless internet and yahoo email.
- I'll need USB support.
- I want a stable, virus free system.
- I dont use it for anything else, no games, apps, etc.

I also expect theres alot of people like me out there, open to using linux, with a working (albeit old) laptop that they can't restore windows to, and just want to use it for basic stuff rather than retiring it.

So far I'm very impressed with the Ubuntu community, which is why I shall persevere. I have found the documentation to be reasonably unhelpful so far, maybe I'm looking in the wrong place. I'll give this a week of effort before I put in in the too hard basket and install XP.

Wish me luck! Cheers Scott.

---

### Post by scottnoakes on 2007-03-08
Back again.

I have now burnt the Alternate CD, and verified its integrity on my work toshiba laptop, so the CD looks to be ok.

The CD boots ok on the sony laptop and I get the 'Install In Text Mode' option. Selecting this produces a blank screen with a text cursor flashing at the top left. After that nothing happens. At least the live CD made lots of CD noises for about 30 seconds before locking up and showing the pretty multicoloured snow!

I've tried the OEM option with the same result. The 'check CD for defects' option again displays a blank screen but at least makes lots of CD noises.

In fact the only option I've tried that seems to work is the memory test. This shows me a nice VGA text screen as it does its thing.

Sooo my question is: If the text installer does not work what should I try now?

Thanks Scott.

---

### Post by xyz on 2007-03-08
Hi Scott,

Well I have a laptop, a Toshiba Satellite A 40 with Ubuntu and it works fine. I'm no gamer either.
I mean, Ubuntu works fine on laptops; don't get the idea that it is reserved for desktops somehow.
Also:
[HW Compatibility]("http://www.ubuntuforums.org/showthread.php?t=361236")
[More on the subject]("http://www.ubuntuforums.org/showthread.php?t=182834")
[ Incompatibility List.]("http://www.ubuntuforums.org/showthread.php?t=361237")
The threads are often labelled "Desktop HW..." but there's lots on laptops.
Finally...[About wireless]("http://ubuntuforums.org/showthread.php?t=185174")
I don't know what card you have or or plan on buying but here's one.
Hang in there and good luck.

---

### Post by scottnoakes on 2007-03-08
Hi,

Im sure that linux can work on this laptop cause a friend of mine installed Red Hat on it about 2 years ago as a dual boot, but windows crashed and to recover I had to remove the partition to get the recovery CDs to work.

My problem is that even the text installer on the alternate CD does nothing except show a blank screen. So I cant even start to figure out what could be wrong.

I was starting to wonder if the HD was failing but I've booted of a DOS system disk and test copied some files to C: without problem. So Im sure its not that.

What should I do now? This seems to be a dead end. Should I try another Distro? Is Mandriva any good? That distro was the other reccommendation from the online linux quiz. 

Cheers Scott.

---

### Post by Kateikyoushi on 2007-03-08
You could try some of these one at a time.
Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by xyz on 2007-03-08
These are your needs:
> - I only use the laptop for wireless internet and yahoo email.
- I'll need USB support.
- I want a stable, virus free system.
- I dont use it for anything else, no games, apps, etc.

So why not try a 'lighter' distro like Slax, DSL...see the link about available distros in one of my previous posts.
After all, it's not like you have to go out and buy an OS evey time you want to
try it.  See what works for you and...be patient!
Your specs are not the problem:
>  	Hi,

The replacement HD is a Hitachi 2.5" 80GB, 5400rpm, 8M Cache, ATA-100. Ive installed, patitioned and formatted it, no problems.

THe laptop has also been upgraded to 256MB ram.

Cheers Scott.
...and what Kateikyoushi says sounds like something to try for sure.

---

### Post by scottnoakes on 2007-03-08
Hi,

Choosing the option 'Install a command line system' actually does display something, it stops after displaying the following:

...
[17179572.412000] Setting up standard PCI resources.

So it may be getting hung up on the PCI bus, I'll try some of the command options suggested and see what happens.

Thanks.

---

### Post by Kateikyoushi on 2007-03-08
Press F6 at the menu and add them to the end of the line without linux and boot.
Like this:

noapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
nolapic
framebuffer=false
linux irqpoll

---

### Post by Carnavan7 on 2007-03-08
Might I suggest you see if the 6.06 cd installs? I have all sorts of problems with 6.10 (x86 and 64bit) on my desktop but 6.06 is flawless everytime.

---

### Post by scottnoakes on 2007-03-08
Here are the results:

Boot: linux noapic
Starts and after two display lines shows a blank screen, nothing more

Boot: linux pci=irqroute
Stops showing the following message
[...] PCI: Unknown option irqroute

Boot: linux pci=noacpi
Starts and after two display lines shows a blank screen, nothing more

Boot: linux acpi=off
Holy **** batman! I now get to the language selection screen, we're cooking with gas!

Arigato gozaimasu Kateikyoushi-san.

---

### Post by scottnoakes on 2007-03-08
Ok,

Just re-read your email and did not do what you said. Its working through the config process but is coming up with all sorts of 'Debootstrap warnings' saying file xxx was corrupt. I'll reboot and add switches to the command line prompt as requested and see what happens.

---

### Post by scottnoakes on 2007-03-08
Ok,

Install progresses until the following error occurs:
'Debootstrap warning'
warning: file:///cdrom/pool/main/o/openssl/libss10.9.8_0.9.8b-2ubuntu2_i386.deb was corrupt.

then:
'Debootstrap warning'
warning: Couldn't download package libss10.9.8

then loads of simular errors.

Whats happening here? The CD image has been verified as good. If I use the same switches on the live CD is it likely I may have more success?

Cheers Scott.

---

### Post by Kateikyoushi on 2007-03-08
Worth to give it a shot, is the system reliable ? Could try the memory test on the disc.

---

### Post by scottnoakes on 2007-03-08
Hi,

The system is reliable, I've run the memory test, no problems there.

I've now put the live CD (this arrived in the mail should be reliable) in and run the install with the suggested switches on the 'safe graphics mode' install, however the screen is again blank. Im sure I heard is make some intro noise through the speakers and it responds to keyboard input so the install is progressing and waiting for input. So live CD is not much use here.

I have a second copy of the Alternate CD so I'll try that now.

---

### Post by Kateikyoushi on 2007-03-08
At least we know that you can boot the live CD only the vga has problem.

Try to do what he recommends but instead of ati add i810 as driver. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by scottnoakes on 2007-03-08
Hi,

Have tried the second Alternate CD and same problems, lots of bootstrap warnings etc. I assume that selecting <continue> through all these errors wont help. Is this true?

So where to from here? Should I download the 6.06 (?) release and try to install this instead?

Its far too late, Im off to bed. thanks everyone for your help, its good to get to the point where the installer progress is actually visible.

---

### Post by scottnoakes on 2007-03-08
hi,

okay got as far as editing config file, had to boot from live CD, using switches and break option, this only works in safe graphics mode. The driver listed by default is "i810". I've replaced this with "radeon".

Booting continued, brought up screen saying "Failed to start the X server", writes more stuff to the screen, and then installation halts, and am back on the command prompt. last thing displayed before prompt is: 
* Starting hardware abstraction layer hald

I'll try to use the vesa driver now.

---

### Post by scottnoakes on 2007-03-08
Oh joy,

right, using the vesa driver does not work. Xserver fails again and looking at its output it says 'Fatal server error: Caught signal 11. server aborting'

and thats the end of story. The last displayed action is:
'14: /usr/x11r6/bin/x(fontfilecompleteXLFD+0xa1) [0x806da51]'

Back at the command prompt the last message displayed is:
*Starting Bluetooth services.

Wow, this whole thing is just a doddle! What confuses me is the the link and config files for a simular laptop [http://cwrose.de/vaio/fx101.html](http://cwrose.de/vaio/fx101.html) does not mention any changes to the xorg.conf file, instead making changes to a XF86Config file. Is this just a difference between where config info is stored between distros?

Anyways, stuck again, Help!!!

---

### Post by scottnoakes on 2007-03-08
From looking at the simular laptop link my guess is that there is some sort of conflict between the video chipset and the OS relating to memory access, apparently the graphics uses the system memory as it does not have its own:

> 
Since XFree 4.0 the i810 is well supported. Because the chipset cannot scale the picture, the only usable resolution is 1024x768 pt. You need agp-support compiled (as module or in kernel) in order to use higher resolutions. The graphics chipset is build in into the MCH (memory controller hub) and uses the main memory for video ram. I use the notebook for 'on the way' development, so graphic-speed is not important for me.

 
The other info in his post that seems important is:
> 
kernel boot parameter (eg. append in lilo.conf)
video=i810fb:vram=4:hsync2=49:xres=1024:yres=768:mtrr:accel:ext_vga:hwcur

Should a similar setting be used for Ubuntu?

Also is the graphics identifier important, does this need to be specified as well as the driver?

---

### Post by richardjennings on 2008-04-09
as luck would have it, i purchased a fx103 2 days ago with the sole intention of using it purely for an offline version of xp for a java course I am on.

As always, I buckled to pressure, and had a go at an ubuntu install.

I am writting this from a far from perfect 7.10 custom server install. I thought I should let you know how I got to where I am, before I continue to make refinements.

typing startx after installing relivent packages has given me a 640 x 480 resolution. I havnt checked but this is almost certainly vesa.

here is what I have done, step by step.

download, burn 7.10 server iso

boot cd, press f6 at menu, delete splash and quiet from kernel and append linux acpi=off

follow installation instructions. It is usefull to attach an ethernet network connection when the installer gets to automatic network setup. Saves doing it manually later.

The installation should finish without issue, and leave you with a command line system.

firstly, the basic gnome install package is in a repository that is not enabled by default.

sudo nano /etc/apt/sources.list

uncomment, delete the # before the two parter repositories
ctrlx, y, enter, to save the modification.

update apt with newly available packages, (depends on internet connection).

sudo apt-get update

* a usefull command for finding packages is sudo apt-cache search string

adding | more is usefull if there are alot of results. an example search:

sudo apt-cache search gnome-core


right onwards and upwards.

next install xserver gdm and gnome to get the base graphical enviroment#

sudo apt-get install xserver-xorg-core gdm gnome-base

then you need xserver fonts, and also compiz. (seems crazy right) :)

sudo apt-get install xfonts-base compiz


now reboot the system, sudo reboot

you SHOULD now boot into gnome with a 640x480 resolution.

you will get an error about the human theme not being present(havnt installed it yet). you will also get two errors for taskbar items that are not available. 

Once you have ignored those errors, you have a very basic gnome install from which you can build in whichever direction you want.


there are many packages you will need from here on in. if you are unfamiliar with ubuntu packages, you will probably want to install synaptic (a graphical package manager)

sudo apt-get install synaptic

also gnome-system-monitor gnome-system-tools gnome-utils

so there you have it. I'll update the thread when I have looked at the resolution and battery monitoring issues, + any others i find on my travels.

Happy adventures!

---

