---
title: "ASUS T91MT and Ubuntu 11.10 How-to"
date: 2012-02-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by thermatk on 2012-02-02
There are lots of pages on the Internet but they are mostly outdated so I have decided to try make a new one.

[SIZE="4"]**Installation**[/SIZE]
Get an (*?)Ubuntu 32 bit iso to your computer and get it on a USB flash or your external USB-CD/DVD. There is a How-to on the Ubuntu donload page so I think you don't need my comments. 
Insert it into your T91MT, start your netbook and press ESC till you see the menu where you can choose to boot from your flash drive.
When you see GRUB menu press tab and edit boot options:
delete the word "splash" and add "poulsbo.blacklist=yes psb_gfx.blacklist=yes". It doesn't matter that your boot options will be two strings long. Press Enter
You will boot up into Unity 2D with VESA drivers and 800x600 resolution. Double-click "Install on hard disk" launcher on the Desktop and go through a usual installation, except that you should choose to manual edit your partitions:
1.DO NOT CREATE swap partiotion and ignore that the setup will ask you to go back and create it (because of the SSD, you will kill it with swap)
2.Your "/" partition should be formatted as ext2 (same thing, SSD doesn't like journal of filesystem)

[SIZE="4"]**First boot**[/SIZE]
This time when you see your newly installed GRUB menu press "e" and edit the options as in the previous case: delete "splash" and add on its place "poulsbo.blacklist=yes psb_gfx.blacklist=yes". Press F10 to boot into your Ubuntu installation.
When you see the LightDM greeter choose to boot into Ubuntu 2D. Connect to the internet as WiFi and ethernet adaptors work out of the box perfectly.
Update you system to the latest state the repositories can give you by typing in Terminal(CTRL+ALT+T) ```

sudo apt-get update
sudo apt-get dist-upgrade
```
Now we will get the GMA500 graphics to work.

[SIZE="4"]**Graphics**[/SIZE]
Launch a terminal and type:
```

sudo add-apt-repository ppa:gma500/emgd110
sudo apt-get update
sudo apt-get install emgd-support
```
Wait till it finishes to install(some minutes) and after that type ```
sudo gedit /usr/share/X11/xorg.conf.d/10-emgd.conf
``` and replace everything there with that:
```
Section "ServerLayout"
     Identifier     "Default Layout"
     Screen 0       "Screen0"        0 0 
EndSection

Section "Device"
     Identifier                                           "Intel_EMGD-0"
     Driver                                               "emgd"
     VendorName                                           "Intel(R) DEG"
     BoardName                                            "Embedded Graphics"
     BusID                                                "0:2:0"
     Screen                                               0
#     VideoRAM                                             131072
     Option     "PcfVersion"                              "1792"
     Option     "ConfigId"                                "1"
#     Option     "PortDrivers"                             "lvds"
     Option     "ALL/1/name"                              "LVDS"
     Option     "ALL/1/General/DisplayConfig"             "1"
     Option     "ALL/1/General/DisplayDetect"             "1"
     Option     "ALL/1/General/shadowfb"                  "1"
     Option     "ALL/1/General/FbBlendOvl"                "1"
     Option     "ALL/1/General/OverlayNoClip"             "1"
     Option     "ALL/1/General/TuningWA"                  "1"
     Option     "ALL/1/Port/4/General/name"               "LVDS"
     Option     "ALL/1/Port/4/General/Edid"               "1"
     Option     "ALL/1/Port/4/General/EdidAvail"          "0"
     Option     "ALL/1/Port/4/General/EdidNotAvail"       "4"
     Option     "ALL/1/Port/4/General/CenterOff"          "1"
     Option     "ALL/1/Port/4/FpInfo/Height"              "600"
     Option     "ALL/1/Port/4/FpInfo/Width"               "1024"
     Option     "ALL/1/Port/4/Dtd/1/PixelClock"           "48959"
     Option     "ALL/1/Port/4/Dtd/1/HorzActive"           "1024"
     Option     "ALL/1/Port/4/Dtd/1/HorzSync"             "40"
     Option     "ALL/1/Port/4/Dtd/1/HorzSyncPulse"         "144"
     Option     "ALL/1/Port/4/Dtd/1/HorzBlank"            "288"
     Option     "ALL/1/Port/4/Dtd/1/VertActive"           "600"
     Option     "ALL/1/Port/4/Dtd/1/VertSync"             "1"
     Option     "ALL/1/Port/4/Dtd/1/VertSyncPulse"        "4"
     Option     "ALL/1/Port/4/Dtd/1/VertBlank"            "22"
     Option     "ALL/1/Port/4/Dtd/1/Flags"            "0xc000000"
#     Option     "ALL/1/Port/4/Attr/70"                    "0"
#     Option     "ALL/1/General/Accel"                     "1"
EndSection

Section "Screen"
     Identifier    "Screen0"
     Device        "Intel_EMGD-0"
     Monitor       "Monitor0"
     #     Monitor       "LVDS"
     SubSection    "Display"
         Depth     24
          Modes    "1024x600"
     EndSubSection

EndSection

Section "Monitor"
     Identifier   "LVDS"
     ModelName    "LCD Panel used by EMGD" 
EndSection

Section "DRI"
     Mode         0666
EndSection

Section "Extensions"
     Option "composite" "enable"
EndSection
```
Save file and close gedit.
In terminal type ```

sudo gedit /etc/default/grub
```
and in that file make the line GRUB_CMDLINE_LINUX_DEFAULT="[some options here]" look like 
```
GRUB_CMDLINE_LINUX_DEFAULT="poulsbo.blacklist=yes psb_gfx.blacklist=yes acpi_backlight=vendor noplymouth elevator=noop"
```
***Note:*** We've changed the elevator to noop because of SSD but to reduce the amount of operations it was done in this "Graphics" section :)
Save the file, exit gedit and in terminal type 
```
sudo update-grub
```
Wait till it finishes, now you shoul be able to boot up into Ubuntu without editing any lines of options.

[SIZE="4"]**SSD tweak**[/SIZE]
To save the SSD from dying you can not only use Ext2, live without swap and use noop elevator but also make some changes in fstab. In terminal type:
```
sudo gedit /etc/fstab
```
Find the line where your partitions are mounted and where there are options like "errors=remount-ro" add "noatime,nodiratime" to  make it(or them, if you have multiple partitions) look like 
```
errors=remount-ro,noatime,nodiratime 
```
Save the file, close gedit.

[SIZE="4"]**Not ready yet...**[/SIZE]
According to mtdev-test multitouch is working out of the box... but it's kinda "jumping" so it's very difficult to use things like TwoFing scrolling or Pinch-zoom.
To install most needed things in terminal type
```
sudo apt-get install utouch ginn easystroke
```
Ginn is working with a built-in wishes.xml well as you can do some TwoFing scrolling in Firefox for example... but it's very hard to scroll as you wish and unusable. A custom wishes.xml solves the problem a bit but not completely... pinch zoom is zooming about 10 more seconds after you have done your zoom and is unusable atm too... I need tips and help with touch :)
What i want else is to get easystroke with multitouch support but I don't know how to get that patch([http://ant1-antuan.blogspot.com/2011/11/easystroke-con-estensione-multitouch.html](http://ant1-antuan.blogspot.com/2011/11/easystroke-con-estensione-multitouch.html)) on easystroke. Please, we can do the interface touchfriendly and wonderful together...
There are still some questions about the acceleration of flash videos... The flash plugin from repositories gives you some performance and the one from Flas-aid works better, is newer but obviously is sometimes not accelerated. 
Mplayer-vaapi from this repository([https://launchpad.net/~sander-vangrieken/+archive/vaapi?field.series_filter=oneiric](https://launchpad.net/~sander-vangrieken/+archive/vaapi?field.series_filter=oneiric)) works in some cases but doesn't work in most.
Sound is not working! Why, it has been on emgd 1.8?
After the victory over all the hardware I will try to make a touchfriendly interface out of Xfce(I liked the easiness of theme files), KDE or something else.
Any ideas, questions, news, problems? Please discuss them, I'm an Ubuntu newbie and that's my first attempt to fight with all the hardware problems... :guitar: Sorry for my English and all the offtopic I wrote :)

[SIZE="4"]**What I'm doing at the moment**[/SIZE]
Will be back with Precise release! Sound is working, twofing is in heavy development I believe and some people have compiled EMGD 1.10 for Linux 3.2. Everything will probably be wonderful:)
**UPD**
Testing Precise, twofing is working and scrolling everything wonderful... but there are several GMA500 problems. It's starting, but no backlight control leads to very short battery life.

---

### Post by Lagroth on 2012-04-13
In case you think no one noticed or cared, Thank you for this =).  I'm going to try it out as soon as I have time. I'm stuck on ubuntu 10.10 atm because I hadn't found any instructions for the T91MT with a newer version.

If you wouldn't mind saving me the trouble of scouring the forums, what is the status of the video drivers? Has the manufacturer released new ones? are the open source ones now up to scratch? Do the ones you recommend mean that video is accelerated and the fancy window effects work (compiz??)?

Thanks again =)

---

### Post by fasteddie9318 on 2012-04-13
I also wanted to say thanks for this. I was pulling my hair out until I came upon this guide, and now it's working (almost) perfectly. My one issue is with rotating the screen into tablet mode. I know the screen rotate button doesn't work, but I can't even use xrandr to change the screen orientation in terminal; I get a badmatch error. Is there something else I should be doing? Should I just wait for the 12.04 release and reinstall everything then?

---

### Post by thermatk on 2012-04-14
**Lagroth,** thank you for your reply, I'm glad that it's exciting not for me only :) 
Currently, there are wonderful open source video drivers in Precise and even far more better in Linux 3.3 and 3.3-drm-next and these drivers give the best 2D acceleration I have seen on GMA500. I have never seen people who are running some 3D on T91MT so the only problem with them is that there is no video acceleration...
And there are proprietar EMGD drivers for Ubuntu 11.10 which are working well but not perfect and I can't say that there are as satble in 2D as the open source but they have 3D and va and can play YouTube 1080p and OpenGL ES desktops like KDE. As you should know, Unity3D is not working on EMGD and there is no Compiz in Unity2D...  
There is a build of Linux Mint with the latest kernel and EMGD and I can post it here if you wish to try it out.
All the information that you want can be found here: 
[GMA500 Megathread]("http://ubuntuforums.org/showthread.php?t=1229345&page=527")

What I don't like in 11.10 is lack of multitouch... that's why I want Precise and it's only 13 days away from starting to imitate stability :D
Btw, Plippo has already developed a Precise ready version of his twofinger scroll-zoom-super app

**fasteddie9318,** that's wonderful that it worked for you! Can you please  post what exactly you did for others to see what to do get it all together :) I will upgrade my guide after the Precise release and your comment
As for xrandr, I have tried it in Precise and it's working WITH the button but I don't know what exactly I did so you have to wait till Precise is out and I will upgrade my guide to make it the best OS for T91MT :) 12 days?

---

### Post by thermatk on 2012-05-26
I have achieved great success with Precise and will write about it soon:)

---

### Post by pmarki on 2012-09-21
12.04 works just great with small modifications from [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

Unfortunatelly xrandr doesn't work so I can't set extended desktop with projector.
So my netbook is unuseble for me as I need this function during presentations.
Anyone can help?

EDIT
I found answer!
Maybe it help somebody else, so:
I've installed  xserver-xorg-video-modesetting and dependecies  from 

ppa:xorg-edgers/ppa

created xorg.conf: [http://pastebin.com/909sKXSU](http://pastebin.com/909sKXSU)

and upgraded kde to 4.9 and everything works :)

---

