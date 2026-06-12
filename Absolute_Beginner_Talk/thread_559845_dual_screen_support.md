---
title: "dual screen support"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-09-25
i have two screens and an nvidia 6200 with a vga and a dvi jack
i want to use two screens and expand my desktop across the two screens
one is a crt and is connected through an adapter to the dvi
the other is an lcd and is connected to the vga port
the only thing is i dont know how to do this
theyr both presently connected and on but te crt is displaying a bar across the screen thats kind of like you get when your cable is out
help please?

---

### Post by overdrank on 2007-09-25
> **99bluefoxx said:**
> i have two screens and an nvidia 6200 with a vga and a dvi jack
i want to use two screens and expand my desktop across the two screens
one is a crt and is connected through an adapter to the dvi
the other is an lcd and is connected to the vga port
the only thing is i dont know how to do this
theyr both presently connected and on but te crt is displaying a bar across the screen thats kind of like you get when your cable is out
help please?

Hi you can try  Twinview
[http://ubuntuforums.org/showthread.php?t=301946&highlight=dual+monitor+support](http://ubuntuforums.org/showthread.php?t=301946&highlight=dual+monitor+support)

---

### Post by funpop on 2007-09-25
maybe nvidias config tool can help you setting this up:

if you have the restricted drivers enabled, type:

nvidia-settings

in a terminal

---

### Post by 99bluefoxx on 2007-09-25
allright
thanks much^^

---

### Post by 99bluefoxx on 2007-09-25
> **funpop said:**
> maybe nvidias config tool can help you setting this up:

if you have the restricted drivers enabled, type:

nvidia-settings

in a terminal
not much in that for my needs
thanks anyways

---

### Post by 99bluefoxx on 2007-09-25
> **99bluefoxx said:**
> not much in that for my needs
thanks anyways
i cant seem to find my vid card on this list [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html) 
what would be the equivelant of a bfg graphics nvidia 6200 oc?

---

### Post by aJayRoo on 2007-09-25
If you are using the Nvidia restricted driver then try typing (after backing up you X server configuration file of course!):
```
gksudo nvidia-settings
```
into a terminal like funpop suggested. When the configuration tool opens select 'X server Display Configuration' in the left hand panel. Make sure you have both displays plugged in and click the 'Detect Displays' button. You should see a second display appear in the image at the top. Click on this display in the image and click the 'Configure...' button and select the twinview mode. Then you can select the correct resolution and click the 'Save to X configuration File' button. Be warned that if you are using Beryl/Compiz this action will probably alter your X configuration in a way that makes the title bars of windows disappear. This is relatively easy to fix, I'm sure there are many posts concerning it, but to be safe make sure to make that backup before proceeding! This is the method I use to configure my displays for twinview mode.

---

### Post by overdrank on 2007-09-25
> **99bluefoxx said:**
> i cant seem to find my vid card on this list [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html) 
what would be the equivelant of a bfg graphics nvidia 6200 oc?

Hi check your lspci  out put from the terminal. I would think the geforce 6200

---

### Post by 99bluefoxx on 2007-09-25
> **overdrank said:**
> Hi check your lspci  out put from the terminal. I would think the geforce 6200
i used the command
this is what it outputted

```
bluefoxx@azurE-prIDE:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. Unknown device 0327
00:00.1 Host bridge: VIA Technologies, Inc. Unknown device 1327
00:00.2 Host bridge: VIA Technologies, Inc. Unknown device 2327
00:00.3 Host bridge: VIA Technologies, Inc. Unknown device 3327
00:00.4 Host bridge: VIA Technologies, Inc. Unknown device 4327
00:00.5 PIC: VIA Technologies, Inc. Unknown device 5327
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6327
00:00.7 Host bridge: VIA Technologies, Inc. Unknown device 7327
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. Unknown device a327
00:09.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0b.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
bluefoxx@azurE-prIDE:~$ 

```

---

### Post by overdrank on 2007-09-25
That is correct
00:0b.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)

---

### Post by 99bluefoxx on 2007-09-25
so then i use the nvidia-glx?
im a bit cautious of it cause last time that installed my x server got totally screwed and my desktops would not start
in fact it started up entirely in text based mobe

---

### Post by overdrank on 2007-09-25
> **99bluefoxx said:**
> so then i use the nvidia-glx?
im a bit cautious of it cause last time that installed my x server got totally screwed and my desktops would not start
in fact it started up entirely in text based mobe

HI that I do not know I have not setup a dual monitor setup. I would make a backup of your xorg before any changes 
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by 99bluefoxx on 2007-09-25
it did that automatically this time
last time i typed the command shown on the package description sudo nvidia-glx-config enable

---

### Post by markp1989 on 2007-09-25
hey, i  have the same graphics card, if you do get it setup how you want tell me , because i would like to do this, i just dont want to buy another monitor if it dont work

---

### Post by hotweiss on 2007-09-25
Gutsy Gibbon has dual screen support, why not download it?

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml)

---

### Post by markp1989 on 2007-09-25
> **hotweiss said:**
> Gutsy Gibbon has dual screen support, why not download it?

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml)

its going to be out in less then a month so il wait till the official release

---

### Post by 99bluefoxx on 2007-09-25
> **hotweiss said:**
> Gutsy Gibbon has dual screen support, why not download it?

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml)
i want to but im on an connection thats 
only about 30kb/s
aka shaw high speed light
maybe once the free cds are available ill request them
or is there a torrent for the file?

---

### Post by hotweiss on 2007-09-25
At 30 kb/s you should be able to download it overnight... And yes, there are torrents available:

[http://cdimage.ubuntu.com/releases/gutsy/tribe-5/](http://cdimage.ubuntu.com/releases/gutsy/tribe-5/)

---

### Post by 99bluefoxx on 2007-09-25
> **markp1989 said:**
> its going to be out in less then a month so il wait till the official release
dude, your desktop is almost identicle to an earlier revision of mine!!
old: acer aspire sa 20 celeron d 2.93 ghz^ 3.54ghz 768 ram 80gb eide wd800 nvidia 6200 256 oc, original mobo generic crappy thing, replaced with asrock p4vm890 via chipset, dual cd drive[cdrw/dvdrom, cdrw] booting windows, then linux[windows was screwed by repare person
current xplio case(old one was too kicked up) 
tri cd drives[cdrw/dvdrom, cdrw, cdrom] 250 gb ultra ide seagate[rest of hdw same]
lol

---

### Post by 99bluefoxx on 2007-09-25
> **hotweiss said:**
> At 30 kb/s you should be able to download it overnight... And yes, there are torrents available:

[http://cdimage.ubuntu.com/releases/gutsy/tribe-5/](http://cdimage.ubuntu.com/releases/gutsy/tribe-5/)
im not allowed to leave it on overnight, the fans to keep it cool are to noisy >.<
not to mention that any computer i have owned becomes tempermental and crashes programs and stuff if left on without a restart of somekind for moar than 9 houres
although the computer <i>does</i> make a nice foot warmer device...

---

### Post by markp1989 on 2007-09-25
> **99bluefoxx said:**
> dude, your desktop is almost identicle to an earlier revision of mine!!
old: acer aspire sa 20 celeron d 2.93 ghz^ 3.54ghz 768 ram 80gb eide wd800 nvidia 6200 256 oc, original mobo generic crappy thing, replaced with asrock p4vm890 via chipset, dual cd drive[cdrw/dvdrom, cdrw] booting windows, then linux[windows was screwed by repare person
current xplio case(old one was too kicked up) 
tri cd drives[cdrw/dvdrom, cdrw, cdrom] 250 gb ultra ide seagate[rest of hdw same]
lol


cool, most of my computer is as it was when it arived here , all i have changed is the ram, graphics card and dumped an old IDE hard drive in it.

im thinking of changing the cpu cooler , the current 1 is very nosy when doing cpu intensive tasks

---

### Post by hotweiss on 2007-09-25
Just use Bit Torrent when ever you can I guess... Or go to an internet cafe, download and burn it...

---

### Post by 99bluefoxx on 2007-09-25
> **markp1989 said:**
> cool, most of my computer is as it was when it arived here , all i have changed is the ram, graphics card and dumped an old IDE hard drive in it.

im thinking of changing the cpu cooler , the current 1 is very nosy when doing cpu intensive tasks
the cpu cooler on mine broke so i had to adapt a bunch of old p1 cooler fans to it
works just as good, and cools the ram heatsink i made at the same time

---

### Post by 99bluefoxx on 2007-09-25
> **hotweiss said:**
> Just use Bit Torrent when ever you can I guess... Or go to an internet cafe, download and burn it...
actually im downloading it through ktorrent right now XP

---

### Post by markp1989 on 2007-09-25
> **99bluefoxx said:**
> the cpu cooler on mine broke so i had to adapt a bunch of old p1 cooler fans to it
works just as good, and cools the ram heatsink i made at the same time

how did it break?

---

### Post by funpop on 2007-09-26
nvidia-glx-new is the driver you need for a geforce 6xxx

---

### Post by 99bluefoxx on 2007-09-26
> **markp1989 said:**
> how did it break?
a blade broke off when it snagged the audio cable leading to a cd drive. it then started to drag against the inner case of the fan, creating a horrendus noise, and warping the little plastic rivet thingy that held the blades to the assembly, allowing the fan blades to jut outwards and catch moar wires, and my fingers when i was moving the wires away. those things are damn sharp too, still have a scab on one of my fingers from that and that was two or three weeks ago
><

---

### Post by markp1989 on 2007-09-26
> **99bluefoxx said:**
> a blade broke off when it snagged the audio cable leading to a cd drive. it then started to drag against the inner case of the fan, creating a horrendus noise, and warping the little plastic rivet thingy that held the blades to the assembly, allowing the fan blades to jut outwards and catch moar wires, and my fingers when i was moving the wires away. those things are damn sharp too, still have a scab on one of my fingers from that and that was two or three weeks ago
><

I done a similar thign on one of my old computers, the entire case used to vibrate, you could hear it from down stairs lol

---

### Post by 99bluefoxx on 2007-09-26
> **markp1989 said:**
> I done a similar thign on one of my old computers, the entire case used to vibrate, you could hear it from down stairs lol
lol
its hard on the ears, not to mention it stops cooling the cpu, which = doom for cpu
i got lucky, my celeron d ran with a half gig overclock for atleast an hour with no heatsinkcooling, and at its naitive speed with NO heatsink, and its still going 0.0 the thing is damn near industructable lol

---

### Post by markp1989 on 2007-09-26
> **99bluefoxx said:**
> lol
its hard on the ears, not to mention it stops cooling the cpu, which = doom for cpu
i got lucky, my celeron d ran with a half gig overclock for atleast an hour with no heatsinkcooling, and at its naitive speed with NO heatsink, and its still going 0.0 the thing is damn near industructable lol

blody hell im suprised you didn't end up burning it out

---

### Post by 99bluefoxx on 2007-09-26
> **aJayRoo said:**
> If you are using the Nvidia restricted driver then try typing (after backing up you X server configuration file of course!):
```
gksudo nvidia-settings
```
into a terminal like funpop suggested. When the configuration tool opens select 'X server Display Configuration' in the left hand panel. Make sure you have both displays plugged in and click the 'Detect Displays' button. You should see a second display appear in the image at the top. Click on this display in the image and click the 'Configure...' button and select the twinview mode. Then you can select the correct resolution and click the 'Save to X configuration File' button. Be warned that if you are using Beryl/Compiz this action will probably alter your X configuration in a way that makes the title bars of windows disappear. This is relatively easy to fix, I'm sure there are many posts concerning it, but to be safe make sure to make that backup before proceeding! This is the method I use to configure my displays for twinview mode.
ok when i try that this is output: [http://99bluefoxx.deviantart.com/art/ubuntu-forums-thingy-65849954](http://99bluefoxx.deviantart.com/art/ubuntu-forums-thingy-65849954)
note that this is a screenshot of the output from your command line.

---

### Post by 99bluefoxx on 2007-09-26
> **markp1989 said:**
> blody hell im suprised you didn't end up burning it out
so am i
im lucky too cause i cant affored to replace it, although theres a place ni kitsolano that has a bunch of 478 cpu's real cheap
but i live in surry so its a pain to get there >P

---

### Post by aJayRoo on 2007-09-26
Ah ok, I see what you mean about there being nothing there for you! I guess the features of the nvidia-settings program depend on the driver version you are using. I seem to remember seeing what you see in your screenshot but I cannot remember why it was like that, sorry. I'm using Feisty at the moment so have forgotten what it was like setting up twin monitors in Edgy. The only advice I can give you now is to make sure you are not using the legacy Nvidia driver as it will not work well with your card as it is relatively new.

---

### Post by 99bluefoxx on 2007-09-26
> **aJayRoo said:**
> Ah ok, I see what you mean about there being nothing there for you! I guess the features of the nvidia-settings program depend on the driver version you are using. I seem to remember seeing what you see in your screenshot but I cannot remember why it was like that, sorry. I'm using Feisty at the moment so have forgotten what it was like setting up twin monitors in Edgy. The only advice I can give you now is to make sure you are not using the legacy Nvidia driver as it will not work well with your card as it is relatively new.
nah im not using the legacy driver
further more i just upgraded to feisty fawn and encountered a slight problem
more details here
[http://ubuntuforums.org/showthread.php?p=3430676](http://ubuntuforums.org/showthread.php?p=3430676)

---

### Post by 99bluefoxx on 2007-09-27
> hey, i have the same graphics card, if you do get it setup how you want tell me , because i would like to do this, i just don't want to buy another monitor if it don't work- sorry to say but I've decided to give up for now, i figure the second screen is too old for Linux, it doesn't appear to detect on the xorg.conf if i hook it up to vga and it displays incorrectly when it gets into X, vertically replicating the screen image so I'm gonna wait till som1 gives me another flatscreen
> nvidia-glx-new is the driver you need for a geforce 6xxxI'm gonna attempt to install this one with some caution if i can get a utility to back my system up to cdr, and i mean my harddrive, not just repos. i don't care if i have to use multiple cds i just wanna have it on cd[files, installed programs, that kind of stuff]
got a suggestion?
> Just use Bit Torrent when ever you can I guess... Or go to an internet cafe, download and burn it...meh, i didn't have anything much else to do today so i am downloading it now via ktorrent, started this morning and surprisingly it is almost done, 75% and two hours to go...
as for my second monitor i probably will keep it and leave it plugged in, the output it gives makes a rather interesting visualization if im listening to music...

---

### Post by 99bluefoxx on 2007-09-27
blarg
after i shut down something happened to the x server ans nvidia-glx, so i installed glx-new as suggested and tried that out
and omg it works
heres new settings menu
[http://99bluefoxx.deviantart.com/art/forums-thingy2-65921162](http://99bluefoxx.deviantart.com/art/forums-thingy2-65921162)
and this menu ish the one i use then
[http://99bluefoxx.deviantart.com/art/forums-thingy3-65921415](http://99bluefoxx.deviantart.com/art/forums-thingy3-65921415)
gonna restart x now and hope for teh best
thanks for help everyone^^

---

