---
title: "Help installing Xubuntu on a Mac G3 500 ibook..."
date: 2008-06-04
forum: Apple Hardware Users
---

### Post by Michael Carvaggio on 2008-06-04
i've been a mac guy all my life & i wanted to put Xubuntu on my old ibook (G3 500Mhz)
i'm very new to linux (i did install Xubuntu on my parents Compaq & it solved a whole lot of problems & my mother now loves it)

so i went and downloaded Xubuntu for PPC (alternative install) & burned it to disc & tried to install it but when i restart & hold down the "C" key a blinking folder with a question mark in it coms up flashing.  i've searched for instructions online on how to install Xubuntu on an G3 ibook but i think i'm just missing something.?

(i also tried Ubuntu for PPC)

any help (advice) would be appreciated...

---

### Post by Scientia on 2008-06-04
Is your disc drive functioning properly? On an iBook like yours you should be able to hear it whirring..If it's really not working then you might have to check the documentation for alternative install methods.

---

### Post by Michael Carvaggio on 2008-06-04
my disc drive is working.

i just don't know why the question mark folder comes up blinking & it doesn't just go to a install menu like on a PC...

---

### Post by stream303 on 2008-06-04
Make sure you are burning at a very low speed, as an iso image (not just copied over) onto CD-R, not cd-rw.

Some have had issues holding down the "C" key prior to powering up.  Try holding down the "C" key very shortly *after* powering up, and long enough to hear the CD being booted, then release.

Some good tips for burning are here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Michael Carvaggio on 2008-06-05
ok, so i can't use a rewriteable cd?  and i have to burn it as an ISO not just drag it over to the cd folder?

ok i'll give it another try...

thanks.

---

### Post by stream303 on 2008-06-05
Yep, especially those early machines.  Slow speeds like 2x or 4x seems the best for them.

I've had good results with IsoRecorder in Windows, and Apple's disk-utility in OSX, I just open up disk utility, drag the iso file into the left hand pane, highlight it, and hit burn.  Choose a low-speed option if you see it.

---

### Post by blampars on 2008-06-05
not really much help as far as your problem goes, more of a suggestion.. i recently did a server install of ubuntu on a g3 ibook 500mhz and added the xubuntu-desktop afterwards. depending on the amount of ram you have in your little g3 (i only have 192) you're going to be a little tight for memory..

i've since installed fluxbox, and after getting it all set up i've got alot more functionality than i did running xfce.  it might be something you wanna look into. ;)

---

### Post by Michael Carvaggio on 2008-06-05
fluxbox? i will have to take a look at that.

thanks for all the help everyone, i did install ubuntu last night and it has a few problems (it's only using about 3/4 of the screen, it's repeated on the bottom of the screen, no sound)  i then installed xubuntu interface and ran all the updates. (it didn't fix any of those issues)

i'm thinking about reinstalling tiger but i'm going to take a look at fluxbox first.

thanks again.

---

### Post by stream303 on 2008-06-06
You may want to see just what Hardy thinks your video card is by looking around at your /var/log/Xorg.0.log file.

You may want to force recognition of an ATI Rage 128 Mobility card by editing /etc/X11/xorg.conf and adding the r128 driver:

I'm pretty sure your G3 iMac 500 has one.  You can verify it with:
```
lspci
```

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "r128"
EndSection
```

See the section here in the faq for some other good suggestions:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

You may also have to force a native 1024x768 mode by adding a subsection to the screen section:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
    [b]SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection[/b]
EndSection
```

If this doesn't seem to work initially, be sure to go back into your display resolution system preferences and see if you can make the change now in the gui.  If you look at /var/log/Xorg.0.log again, you can see if your changes have been accepted or rejected.

Let's see if this gets you a little further along...

---

### Post by blampars on 2008-06-06
here's a section of my xorg.conf i used to get my screen working, as my initial install was only using 1/4 of the screen as well.. this fixed things for me. of course replace the name of the graphics card with whatever's in your ibook, but i'm guessing its probably the same as mine.

```
Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
Identifier "Color LCD"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
Monitor "Color LCD"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubsection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection
```

---

### Post by Michael Carvaggio on 2008-06-06
i hate to show my lack of coding knowledge but could you back up & tell me where i find the Xorg.conf (i'm guessing in the terminal) to modify.  

thanks.

---

### Post by avtolle on 2008-06-06
> **Michael Carvaggio said:**
> i hate to show my lack of coding knowledge but could you back up & tell me where i find the Xorg.conf (i'm guessing in the terminal) to modify.  

thanks.
Go to the terminal. To read the contents of said file```
cat /etc/X11/xorg.conf
```

To edit same (nano used here as an example)```
sudo nano /etc/X11/xorg.conf
``` using CTRL-O to write it out, <Return> to save, CTRL-x to exit. First, though, you might want to make a backup```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` just in case, so you do have something to revert to.

HTH.

---

### Post by Michael Carvaggio on 2008-06-11
thanks for the details, but i still am not sure about editing code in the terminal.  (let's just say i tried & then had to re-install ubuntu)

if anyone could walk me through like 
1st-open the terminal 
2nd -????

it would be appreciated...

---

### Post by blampars on 2008-06-11
thats really all you have to do is open the terminal then follow avtolle's directions in the post above ;)

start with this in terminal first to make your backup copy
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then type
```
sudo nano /etc/X11/xorg.conf
``` to edit the file..

you may want to use mousepad to edit the file though so you can do it in gui instead of terminal editor so type

```
sudo mousepad /etc/X11/xorg.conf
``` it's easier to copy/paste stuff into there that way

---

### Post by stream303 on 2008-06-11
Blampars is right.  He has shown a text-based (ncurses-based) example that can be used across all versions as well as a gui version with mousepad - although if you can't even get to a gui, a curses-based editor is what you have to use at first.

xorg.conf need to be edited with elevated root priveleges, so you preface the normal commands with sudo, or gksudo / kdesu for the gui editors.

Mousepad is a graphical editor that comes with Xubuntu, so that works if you have it.  If you have Ubuntu, mousepad may not be available unless you installed it, so you can use Ubuntu's default gui editor as well:

```
gksudo gedit /etc/X11/xorg.conf
```

If you are using Kubuntu (kde desktop):
```
kdesu kwrite /etc/X11/xorg.conf
```

Fortunately, you can rely on nano being there no matter what version you use.  Just like the vi editor, but for newcomers vi can have a bit of a learning curve.

---

### Post by avtolle on 2008-06-11
The reason I recommend nano is identified by stream303; if one is not able to get into the graphics first, gedit, mousepad, aren't going to do one any good. Plus, it's easier than vi for a newcomer.

---

### Post by xynamax on 2008-06-11
Michael, i'm having a similar problem on a G3 Imac 600mhz.

Did Burning your install CD at a slower speed do the trick for you?

---

### Post by Michael Carvaggio on 2008-06-11
Thanks everyone, the display is fixed now i'm working on the wireless card.  Does anyone know if there is a good linux-based program that will scan for wireless connections?

thanks again for all your help.

PROBLEM SOLVED!

---

### Post by blampars on 2008-06-11
> **avtolle said:**
> The reason I recommend nano is identified by stream303; if one is not able to get into the graphics first, gedit, mousepad, aren't going to do one any good. Plus, it's easier than vi for a newcomer.

considering michael stated he had a 3/4 screen which repeated on the bottom which was similiar to what i had before i edited my xorg.conf, mousepad would have still been useable which is why i suggested it over using nano from command line due to being easier to use;)

[QUOTE=Michael Carvaggio]Does anyone know if there is a good linux-based program that will scan for wireless connections?[/QUOTE]

i use wifi-radar.. i thought xubuntu came with a network manager? i can't remember now

---

### Post by Michael Carvaggio on 2008-06-12
sorry, i forgot to mention previously that i opted for ubuntu instead. (i may download the xubuntu desktop later)

---

### Post by ssam on 2008-06-12
which version of ubuntu did you install. (System-> about ubuntu should tell you).

thats an old enough mac to have the original airport (assuming it has a wireless card at all). this is the easiest wireless card to make work. however the fancy new auto-configuring networkmanager, did not work much on versions 7.10, and is flaky on old versions as well. If you have ubuntu 8.04 then you should see a little computer icon in the top right corner, left of the clock. if you click on it you should get a drop down list of networks.

---

### Post by Michael Carvaggio on 2008-06-12
my ibook does have an airport card.
i am currently running 7.04 (feisty? i think) 

it doesn't have the computer in the corner. that's one of the reasons i thought about Xubuntu because i'm used to the layout scheme.

(i'm thinking about downloading Xubuntu & doing a clean install because things are a bit messed up right now on the G3 - the wireless isn't working, the bar at the bottom just doesn't do anything, if i minimize a window it just disappears.)  

i was wondering about the other install methods (like are there any?) do i have to burn a disc image or is there some other way of installing? (it's no big deal if i have to burn a disc image but since i wiped the ibook i would be doing it from a PC & i know it's more difficult than just opening up disc utilities like in osX)

---

### Post by blampars on 2008-06-12
i have both a xubuntu live install cd (which i couldnt get to work properly) and the ubuntu 8.04 server install cd (both were downloaded and burned to cd-r).

i recommend the server install. it went great without any problems. i also recommend being "hard wired" into your router though for that as i dont know how well configuring your wireless from CLI will go.  Being wired in was automatic and no hassle.

afterwards you can get xubuntu-desktop from the repos and be running your xubuntu in no time.

either way, you're most likely going to have to reconfigure your xorg.conf i would think.

as far as burning the PPC iso's from a pc (windows), thats what i did and i didnt have any problems with getting them to work on my ibook.

there might also be a net install method but i'm pretty sure you still have to burn an iso but its only like 10mb i believe. i dont know much of anything about that method though.

---

### Post by stream303 on 2008-06-12
> **blampars said:**
> there might also be a net install method but i'm pretty sure you still have to burn an iso but its only like 10mb i believe. i dont know much of anything about that method though.

It is a very good method, akin to the "alternate" install, except that the download image is much smaller, and it picks up the very latest updates during the install procedure itself, rather than having to update all over again after your first reboot with other methods.  Saves a lot of redundant download time and bandwidth.  You can grab them here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It is also a good way to see if you will be met by possible screen issues right up front without having to download the rest of the distro to find out.  That is, the cli-screen that some have issues with - you still may have to manually edit xorg.conf when all is said and done, but this way you've saved yourself a lot of time and bandwidth.

Highly recommended if you have time or bandwidth limitations and of course a working network connection.

---

### Post by Andrew Booth on 2009-08-22
> **blampars said:**
> here's a section of my xorg.conf i used to get my screen working, as my initial install was only using 1/4 of the screen as well.. this fixed things for me. of course replace the name of the graphics card with whatever's in your ibook, but i'm guessing its probably the same as mine.

```
Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
Identifier "Color LCD"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
Monitor "Color LCD"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubsection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection
```

As old as this thread may be, it is worth a mention that the information in the post I have quoted has worked on an iBook 500. After editing xorg.conf, a reboot is required, then the resolution must be manually applied for the Displays menu.

OS used is 9.04-PPC.

---

