---
title: "Problems getting LiveCD to load"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by harminoff on 2007-10-26
Well I just got done reading the stickies and couldn't find an answer, maybe I am just blind though.  Anyways, I'm sick of windows and I'm ready for the switch.  My system specs are as follows:

abit ic7-g motherboard
P4 dual 2.40ghz processor
1.5gb ram
ati 9600 pro video card
sound blaster live! 24 bit sound card
40gb ide hdd with winxp partition
75gb ide hdd freshly formated
300gb sata hdd with just some music and movies


When I run the LiveCd, I can choose to start live cd/install but then it will just hang at the prompt, not allowing any input

I hit f6 and put break=top so that I could catch the error and it is

pci:cannot allocate resource region 0
pci:failed to allocate mem resource

I always f6ed and removed splach from the startup command, and tried to boot in safe graphics mode.  This did seem to try and load, and I did get what I believe to be the startup noise for ubuntu, but still the display stayed frozen.


Anyone got any ideas for me to try?  If you need any more info, just ask aswell.  I really want to get off of windows and try some Ubuntu.

thanks

---

### Post by swoll1980 on 2007-10-26
choose check cd for errors see if that helps

---

### Post by sneezymelon on 2007-10-26
Open your boot settings on system startup
n change your visual memory to max..
maybe that shud do it

---

### Post by harminoff on 2007-10-26
> **sneezymelon said:**
> Open your boot settings on system startup
n change your visual memory to max..
maybe that shud do it

how would I do this?

Sorry, but like I said, I've never touched linux of anykind.

do you mean f6 when the cd load, and change a setting in that?

---

### Post by harminoff on 2007-10-26
so I just went and tried to do the install again

this is exactly what happens


I choose safe graphics mode, it will goto the loading screen, and once the loading bar go's full my screen shuts off.  I can then hit ctrl+alt+f5 and get a cmd prompt.

So I am guessing that I need to install from the alternate cd then?

Is there anyway that I can install from this command prompt?

thanks

---

### Post by molly_001 on 2007-10-26
Install 7.10 from the Alternate Install CD.
However, before installing the AI CD, do an integrity check on the burn of the CD.
I am not convinced you have had a good burn on that Live CD.

You can perform an integrity check on the CD burn from the main Ubuntu window that appears upon booting your machine with the CD.

(Also, if you are using DVD media right now, switch to CD media.)

Secondly, after installation you may need to reconfigure your X-server to work with your graphics adapter.
For that, you hit CTRL + ALT + F1 a couple of minutes after a blank or non-readable screen appears.
Then type:

sudo dpkg-reconfigure xserver-xorg

---

### Post by harminoff on 2007-10-27
> **molly_001 said:**
> Install 7.10 from the Alternate Install CD.
However, before installing the AI CD, do an integrity check on the burn of the CD.
I am not convinced you have had a good burn on that Live CD.

You can perform an integrity check on the CD burn from the main Ubuntu window that appears upon booting your machine with the CD.

(Also, if you are using DVD media right now, switch to CD media.)

Secondly, after installation you may need to reconfigure your X-server to work with your graphics adapter.
For that, you hit CTRL + ALT + F1 a couple of minutes after a blank or non-readable screen appears.
Then type:

sudo dpkg-reconfigure xserver-xorg

ok so I burned the alt cd from a cd (i burned the normal image on a dvd, and although it did clear the check, that still might have been the problem)

anyway, after a long install, i still have a problem.

the ubuntu loading screen goes, and once the progress bar completes my monitor shuts off.  I turned on my pc, went and took a shower, and when i got back I hit ctrl alt f1 and then "sudo dpkg-reconfigure xserver-xorg" but nothing happened, my monitor stays off.

What should I do at this point?

---

### Post by mdpalow on 2007-10-27
hi,

I had a similar problem and you wouldn't believe the fix... move your mouse. :)

For me it loaded and I heard the boot-up .wav file and had blank screen. I didn't realize the screen had simply shut off and moving the mouse brought it back up.

That only worked for me though in Safe Graphics Mode option at boot.

Hope that works.

I also had some initial install problems once and finally had the sense to look at the disk and sure enough there were 4 nice smudge marks on it from my fingers. Cleaned it up and it installed fine.

Last thing - if these don't work for you - check compatibility with your ATI card. I read somewhere in the forum or Ubuntu help that some ATI cards either don't work or have some issues. Sorry I can't be more specific, but I don't have an ATI card, so I didn't really put it to memory.

Wait.....

I may not have put it to memory, but I did save a link I found concerning compatibility! ;)

[https://wiki.ubuntu.com/HardwareSupportComponentsV%20ideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsV%20ideoCards)

Hope you make it 'cause Ubuntu 7.10 is much better than Window$ as I have recently learned. :)

Good luck..

---

### Post by harminoff on 2007-10-27
ok so i tried that and still nothing.  I then tried recovery mode just to see if that would help

It output a bunch of text, and ended with this.  

/buid/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at766503.c : 2522 : assertion dev ->istate == INIT FAILED

/buid/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at766503.c : 2429 : assertion dev->istate == scanning failed


but then it allows me to input commands, so I do the xserver-xorg and set that up, and reboot to normal ubuntu, and the same thing, it hangs after the progress bar loads.

Any other ideas?

---

### Post by molly_001 on 2007-10-27
Is this on a laptop?
 
If it is not (and it instead a desktop) are you able to remove the PCI wireless card (if in fact it is available as a PCI card and not on the motherboard itself)?  Please let me know.
 
Thanks.

---

### Post by harminoff on 2007-10-28
> **molly_001 said:**
> Is this on a laptop?
 
If it is not (and it instead a desktop) are you able to remove the PCI wireless card (if in fact it is available as a PCI card and not on the motherboard itself)?  Please let me know.
 
Thanks.

heh I should have figured that out.  Anyway, now the recovery console finishes fine and stops at the input like it should, but normal mode still turns my monitor off.  I ran through xserver a few times now, and still the same thing.

Should I try anything else before I give up?

---

### Post by molly_001 on 2007-10-28
You are really close now.  If you get to the end and now the monitor seems to shut off -- this is because it is not receiving a signal at the correct frequency and resolution required for the monitor.  I would say this step is needed for easily half of the X11-based linux installations that I do.
 
Now you have only to find the correct xserver-xorg settings and you will see a desktop once you do.
 
The best move you can make right now is to list here in this thread everything you can about your machine:  esp. motherboard name, make/model of machine, graphics adapter name ("gfx card"), chipset, etc.  Anything you can find is very helpful, and then we can surely get the correct xorg settings for you.
 
to help you along, I am including below three recent responses that I've given to other people.  You can read these and you'll see lots of helpful suggestions for configuring the xserver.  You should indeed read all of this, however, the most important thing now is to get the info above about your machine (or anything you can provide us!!)  Thanks!!
 

[PHP] 
After Ubuntu has loaded (again, I recommend a fresh install using the Alternate Install CD, with safe mode, and with the extra commands above) ... you can always get a command line interface at root level. Do do this, after Ubuntu appears to have loaded and you have an orange screen, press simultaneously ALT + CTRL + F1 . This will take you to the text-based command line interface. Now type:

Code:
 
sudo dpkg-reconfigure xserver-xorg
This will allow you to enter a dialogue with the xserver where you can control the refresh rates of the adapter as it speaks to your monitor, and color depth, resolution, etc. I strongly suggest looking below before entering into the xxorg dialogue.
copied from http://tinyurl.com/35v4zc
Preparation
To use this tool you will need to do a little preparation to ensure you have the info needed by dpkg-reconfigure xserver-xorg as you will be asked a series of questions about your setup and hardware - read carefully these questions - often it is ok to leave the answer box blank (where it is suggested) or choose auto. 
Graphics Card - ensure you have the correct drivers installed for your hardware before using this tool. Generic vesa/nv type drivers have limited capabillities and cannot do openGL/3D graphics 
Your Keyboard type - often PC104 
Mouse port connection - commonly /dev/psaux 
Server Modules to load - when using the official nvidia driver "nvidia" it is important to not load the module/section "Dri" 
Monitor Display Resolutions to be used 
Horizontal and Vertical Resolutions (-if you select Advanced when prompted in monitor setup section) - search the web if you don't have the manual/spec of your monitor 
Colour Bit Depth to use - 24 bit for most newer hardware 
It can be a lot to assemble blindly, so I would suggest that you choose nv for driver/adapter type, 1024x768 for resolution, and 16-bit color. There are many other choices along the way, and it's best to just hit enter/next.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
[/PHP]
 
.
.
.
 
[PHP] 
All comments below are for using sudo dpkg-reconfigure xserver-xorg
i810 is the adapter interface, it is on the same selection screen as 'nv' and 'nvidia' and 'ati' and 'vesa' ... there are about 30 choices, and i810 is one choice.
pci bus is the numbered bus on which your graphics adapter is sitting. The graphics is almost always 1:0:0 . Should you change it? No, I would not do so, yet.

for asterick ... looks like this --> *
on the screen for selecting resolution, 
you want asterick ( * ) only next to 1024x768 and lower, such as 800 x 600
please choose 'simple' for monitor selection. Then simply choose appropriate size, for instance choose 19-20 inch if you have 19-inch monitor.
definitely choose 16-bit for color (and not 24) because the basic support in 32-bit machines is for 16-bit color (still gives you millions of shades) ... 24 often will not work when configuring/using X Window manager
^^^^^^^^^^^^^^^^^^^^^^^^^^^
[/PHP]
 
.
.
.
 
[PHP] 
The proper configuration of xorg.conf doesn't depend on the model number, but instead on the type of graphics adapter in the machine and the way that the motherboard talks to that adapter.
Often, you just have to make a guess as to what is most successful while setting up xserver-xorg. I have found the most often the following will work:
i810
check to make sure video card bus is PCI:1:0:0 (if not, then very unusual)
select (asterick) only with 1024x768 and Lower
"Simple" selection for monitor type (not Medium, not Advanced)
16-bit color (not 24)
The above almost always gets me to a viewable 1024x768 screen.

[/PHP]

---

### Post by harminoff on 2007-10-28
abit ic7-g motherboard
P4 dual 2.40ghz processor
1.5gb ram
ati 9600 pro video card
sound blaster live! 24 bit sound card
40gb ide hdd with winxp partition
75gb ide hdd freshly formated
300gb sata hdd with just some music and movies
usb mouse w/ scroll wheel
normal keyboard layout with windows key and whatnot
samsung syncmaster 793mb monitor

if any other info is needed let me know, and I'll try and find out. I really want to get windows off of this machine.

---

### Post by harminoff on 2007-10-28
also, I tried some of your suggestions above, that I thought might help (I did have 24bit selected) but still the same.

Do know though that I can only access xserver in recovery mode, if I just load up ubuntu like normal, and wait for my screen to turn off, then ctrl+alt+f2 nothing happens.

---

### Post by molly_001 on 2007-10-28
24-bit is a bad choice to make, it will almost always cause the xserver to fail to start if there is adapter problems (which there obviously is, in this case).
 
I'll check out your hardware specs and see if I can find any hints from others with like hardware, who have successfully installed and used Ubuntu.

---

### Post by harminoff on 2007-10-29
> **molly_001 said:**
> 24-bit is a bad choice to make, it will almost always cause the xserver to fail to start if there is adapter problems (which there obviously is, in this case).
 
I'll check out your hardware specs and see if I can find any hints from others with like hardware, who have successfully installed and used Ubuntu.

Just wanted to know if you or anyone else had any new ideas for me to try out.

Should I just try the entire install again, and this time just not worry about the updates?  When I installed it the first time, it took about 3 hours to do so.  Is that normal?

Should I try a different distro?

Sorry to be such a bother, but like I said before, I am really sick of windows and can't stand to look at it every day.

---

### Post by molly_001 on 2007-10-30
Three hours for the install using the Alternate Install CD?
With your specs, it should take about 20 minutes.
 
We should try to do the alternate install CD by phone.  I'm really curious what you are running into now.

---

### Post by harminoff on 2007-10-30
well I got it to load using this

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sed -r 's/("fglrx")|("radeon")|("ati")/"vesa"/'< /etc/X11/xorg.conf.backup > /etc/X11/xorg.conf


though booting normal the screen is still all screwy and unreadable, atleast now I can hit ctrl+alt+f1 and get to the logon prompt.

What is the next step to getting a readable screen?

---

### Post by harminoff on 2007-10-31
So I decided to mess with trying to get this to work again. I tried starting ubuntu (both normal and recovery) but both would just kick me to the Terminal.
So I figured I'd try to just reinstall and start from scratch. First I tried the livecd, and it does the same, just kicks me to the Terminal. Same with the alt cd.

Even if I choose "check cd for errors", it tries to load ubuntu (progress bar goes back and forth) and then kicks me to the Terminal.


What is up with this? 


I even disconnected everything but my mouse/keyboard/monitor and still no go.

---

