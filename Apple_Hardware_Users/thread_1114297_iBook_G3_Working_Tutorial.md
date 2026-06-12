---
title: "iBook G3 Working Tutorial"
date: 2009-04-02
forum: Apple Hardware Users
---

### Post by mellflores1 on 2009-04-02
[SIZE=4][B][I][CENTER]Work in Progress[/CENTER]
[/I][/B][/SIZE]
[CENTER]As it says above, this is a work-in-progress. It will be updated when I find something new.[/CENTER]
*I do not take credit for getting this to work. Most of the things that didn't work before now work thanks to the Ubuntu developers.*
**[COLOR=Red]Tested on Ubuntu 9.04 Jaunty Jackalope Beta. Should work on 9.04 and above.[/COLOR]**
**[COLOR=DarkOrange]Tested on iBook G3. 500 MhZ. 384 MB RAM. 8 MB VRAM.[/COLOR]**

Keyboard-[COLOR=Green]Works[/COLOR]
Keyboard Brightness/Volume Control-
Screen-[COLOR=Green]Works[/COLOR]
Sleep-[COLOR=DarkOliveGreen]Works[/COLOR] (doesn't sleep when closed. must select from menu.)
USB-[COLOR=Green]Works[/COLOR]
Firewire-N/A
Ethernet-N/A
Sound-[COLOR=Green]Works[/COLOR]
Mic-[COLOR=Red]Doesn't work[/COLOR]
WiFi-[COLOR=Green]Works[/COLOR]
Trackpad-[COLOR=Green]Works[/COLOR] (F12 for right-click)

[SIZE=6][COLOR=SeaGreen]Installation[/COLOR][/SIZE]
[Download Ubuntu PowerPC.]("http://cdimage.ubuntu.com/ports/releases/jaunty/beta/")
I used the LiveCD but the alternate install should work fine to.
Burn it to a CD and boot your iBook from it.(Press C after you hear the startup chime.
Press TAB key.
Type in ```
live-nosplash-powerpc
``` (or something similar to that. should be on the second line all the way to the left.)
Be patient, it takes a while.
Don't do anything until you are on the Ubuntu Desktop.
If your screen is in the top, left corner and there's two of the same thing, don't panic.
To fix the screen you can either do it while still running the LiveCD(what I did) or wait until you have installed it to your HD.
The instructions below in the [COLOR=Red]Screen Resolution[/COLOR] section works for both methods.
Make sure you can hear sound (should hear drums when entering desktop)
On the top bar, press the little button that looks like a cell-phone signal.
Connect to a network to test if WiFi is working.
If everything is working fine, install Ubuntu.
There is an option for Macintosh keyboards.
I used the whole disk since it's only 10gb but those of you who replaced the HD can set up a separate partition.
Go through with the install.
Reboot.
[SIZE=7]Getting everything to work[/SIZE]
[SIZE=5][COLOR=Red]Screen Resolution[/COLOR][/SIZE]
If your screen is small and in the top, left corner of the screen with the exact same thing under it, follow the instructions below.
Run the following command in the terminal. It will shut down X Windows.
```
sudo /etc/init.d/gdm stop
```Once it is closed type in the following codes:
If the method doesn't work for you the first time, redo it but this time enter the following code
```
sudo dpkg-reconfigure xserver-xorg
```and go through it.
Now enter the code below
```
sudo nano /etc/X11/xorg.conf
```Then, edit it to match this:
```
Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```The method above was posted on [this thread]("http://ubuntuforums.org/showthread.php?t=780235") by [chriz74]("http://ubuntuforums.org/member.php?u=570112").
To start X Windows again, enter
```
sudo /etc/init.d/gdm start
```Now you should have the desktop in 1024x768!:p
To be continued....when i have time...

---

### Post by anandrajny on 2009-04-18
I've the same Ibook G3 500mhz and 640mb RAM and I've made it work too on 9.04. 

I just used the alternate installation CD. The installation was so smooth. It used to be a little bit more complicated with 8.04 and 8.10.

Is it just my imagination or something else but I think the computer is faster with Jaunty. The sound works out of the box. All the basics works. Ethernet, My Airport Express like card from a third party vendor that I bought from Ebay. External USB mouse.

Haven't tried the more complicated ones. Like Keyboard backlight, CPU scaling etc. 

The only problem is with the obvious graphics showing up in 800x600 split into 2 computer screen.

My old xorg.conf used in 8.04 worked just fine with a minor alteration under driver. It used to be "ati" but it didnt' work anymore. I changed it to "fbdev" and it worked. My working xorg.conf is as below. 

```

Section "Device"
       Identifier      "Configured Video Device"
       Driver          "fbdev"                [COLOR="Red"] #(It was "ati" before)[/COLOR]
       BusID           "PCI:0:16:0"
       Option          "UseFBDev"              "false"
EndSection

Section "Monitor"
       Identifier      "Configured Monitor"
       HorizSync       58-62
       VertRefresh     75-117
       Option "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Monitor         "Configured Monitor"
       Device          "Configured Video Device"
       DefaultDepth 24
       SubSection "Display"
       Depth 24
       Modes "1024x768"
       EndSubSection
EndSection
```

---

### Post by JGreenidge on 2009-04-18
Greetings!

Though I'm a non-techie with a 900mHz G3 14" iBook, I'd be happy to contribute to this forum topic anyway I can! Your already listed points are straight on!

My main issues right now is the uncontrollable backlight and that Jaunty keeps the drive spinning and heats up the unit till the fan revs up and never backs down. To me a energy saver "cut drive when not required" mode is needed.

Good job!

Geekless Jim

---

### Post by stream303 on 2009-04-18
You guys are doing a great job for the ppc-G3 owners with those nice reports.

For cpu-frequency scaling, in my mind just installing **cpudyn** from the repos should do the trick, rather than relying on the default on-demand which usually requires a modification to the config file to get it to work.

For me, cpudyn is the right choice if you want frequency scaling since it has a very low-latency switch - you do anything and it immediately goes into full-speed, and then backs down very quickly as well.  Some might say that it is best to just let the cpu run as fast as it can all the time so it will go back to sleep faster, but if you desire frequency scaling, cpudyn is my choice for single-cpu ppc boxes.

And since Jaunty is still rc-status, be sure to run top or install HTOP and see if there are any runaway processes eating up the cpu time.  This has happened to me in the past only on my G4 iBook with Network Manager, although they say that has been fixed.  It is still a good idea to check top or htop every once in awhile.

Keep up the good reports - and that nice xorg.conf posting for Jaunty!

---

### Post by anandrajny on 2009-04-18
Dear Mellflores1,

I would be grateful if you could let me know the instructions and code of your working keyboard backlight. It's very confusing to me what they've written in other places. I've tried it before on 8.04 and 8.10 and it didn't work out.

Thanks in advance.

---

### Post by anandrajny on 2009-04-18
Dear JGreenidge,

Anybody that could install or have the guts to try and install an ancient ibook with the newest version Linux OS like Ubuntu which an average person is dreadful of, and even worse, a Release Candidate,  is a techie guy in my dictionary. So, whether you like it or not, you are a geek too. LOL.

There are like 100,000 tech geniuses in the Linux community but since we are the first ones to take the risk and spend time in the Jaunty & Ibook Department on this forum, we are the masters of this thread.

> **JGreenidge said:**
> Greetings!

Though I'm a non-techie with a 900mHz G3 14" iBook, I'd be happy to contribute to this forum topic anyway I can! Your already listed points are straight on!

My main issues right now is the uncontrollable backlight and that Jaunty keeps the drive spinning and heats up the unit till the fan revs up and never backs down. To me a energy saver "cut drive when not required" mode is needed.

Good job!

Geekless Jim

---

### Post by kavon89 on 2009-04-18
Thank you so much for this tutorial. I'm downloading Xubuntu 9.04 Release Candidiate and I'll try to remember to post what works and doesn't etc.

---

### Post by JGreenidge on 2009-04-19
> **anandrajny said:**
> Dear JGreenidge,

Anybody that could install or have the guts to try and install an ancient ibook with the newest version Linux OS like Ubuntu which an average person is dreadful of, and even worse, a Release Candidate,  is a techie guy in my dictionary. So, whether you like it or not, you are a geek too. LOL.

Naw, you give me WAY too much credit! I simply followed the directions of installing Ubuntu to a "T" as described those on some Ubuntu PPC page. That's why I don't understand why so many seem to have trouble just installing the CD. Maybe I fluked out, I dunno. Like I won't touch Terminal on my own like a hot potato till I find someone's proven lead. Like getting the HD spun down and the heat off and getting the F-keys to work for the screen backlight. I think the secret to getting more people happy into Ubuntu are clear concise step-by-step instructions that don't treat the newbie like a rocket scientist, and one shouldn't have to go treasure hunting all over the web for such enlightenment! That's why I hope this topic remains the watering hole for the PPC Ubuntu newbie who simply wants a break from Tiger and Panther -- my main reason resurrecting my iBook with Ubuntu.

Another hang; Now I do have Tiger on another partition on my iBook but no Ubuntu desktop icons, but do see Tiger icons on Ubuntu's desktop. It's be a nice way to access files from each OS if I can do this.

Truly Geekless Jim

---

### Post by anandrajny on 2009-04-20
> **mellflores1 said:**
> [SIZE=4][B][I][CENTER]Work in Progress[/CENTER]
[/I][/B][/SIZE]
[CENTER]As it says above, this is a work-in-progress. It will be updated when I find something new.[/CENTER]
*I do not take credit for getting this to work. Most of the things that didn't work before now work thanks to the Ubuntu developers.*
**[COLOR=Red]Tested on Ubuntu 9.04 Jaunty Jackalope Beta. Should work on 9.04 and above.[/COLOR]**
**[COLOR=DarkOrange]Tested on iBook G3. 500 MhZ. 384 MB RAM. 8 MB VRAM.[/COLOR]**

Keyboard-[COLOR=Green]Works[/COLOR]
Keyboard Brightness/Volume Control-
Screen-[COLOR=Green]Works[/COLOR]
Sleep-[COLOR=DarkOliveGreen]Works[/COLOR] (doesn't sleep when closed. must select from menu.)
USB-[COLOR=Green]Works[/COLOR]
Firewire-N/A
Ethernet-N/A
Sound-[COLOR=Green]Works[/COLOR]
Mic-[COLOR=Red]Doesn't work[/COLOR]
WiFi-[COLOR=Green]Works[/COLOR]
Trackpad-[COLOR=Green]Works[/COLOR] (F12 for right-click)

[SIZE=6][COLOR=SeaGreen]Installation[/COLOR][/SIZE]
[Download Ubuntu PowerPC.]("http://cdimage.ubuntu.com/ports/releases/jaunty/beta/")
I used the LiveCD but the alternate install should work fine to.
Burn it to a CD and boot your iBook from it.(Press C after you hear the startup chime.
Press TAB key.
Type in ```
live-nosplash-powerpc
``` (or something similar to that. should be on the second line all the way to the left.)
Be patient, it takes a while.
Don't do anything until you are on the Ubuntu Desktop.
If your screen is in the top, left corner and there's two of the same thing, don't panic.
To fix the screen you can either do it while still running the LiveCD(what I did) or wait until you have installed it to your HD.
The instructions below in the [COLOR=Red]Screen Resolution[/COLOR] section works for both methods.
Make sure you can hear sound (should hear drums when entering desktop)
On the top bar, press the little button that looks like a cell-phone signal.
Connect to a network to test if WiFi is working.
If everything is working fine, install Ubuntu.
There is an option for Macintosh keyboards.
I used the whole disk since it's only 10gb but those of you who replaced the HD can set up a separate partition.
Go through with the install.
Reboot.
[SIZE=7]Getting everything to work[/SIZE]
[SIZE=5][COLOR=Red]Screen Resolution[/COLOR][/SIZE]
If your screen is small and in the top, left corner of the screen with the exact same thing under it, follow the instructions below.
Run the following command in the terminal. It will shut down X Windows.
```
sudo /etc/init.d/gdm stop
```Once it is closed type in the following codes:
If the method doesn't work for you the first time, redo it but this time enter the following code
```
sudo dpkg-reconfigure xserver-xorg
```and go through it.
Now enter the code below
```
sudo nano /etc/X11/xorg.conf
```Then, edit it to match this:
```
Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```The method above was posted on [this thread]("http://ubuntuforums.org/showthread.php?t=780235") by [chriz74]("http://ubuntuforums.org/member.php?u=570112").
To start X Windows again, enter
```
sudo /etc/init.d/gdm start
```Now you should have the desktop in 1024x768!:p
To be continued....when i have time...

Dear Mellflores1,

I would be grateful if you could let me know the instructions and code of your working keyboard backlight. It's very confusing to me what they've written in other places. I've tried it before on 8.04 and 8.10 and it didn't work out.

Thanks in advance.

---

### Post by cyberdork33 on 2009-04-20
> **anandrajny said:**
> Dear Mellflores1,

I would be grateful if you could let me know the instructions and code of your working keyboard backlight. It's very confusing to me what they've written in other places. I've tried it before on 8.04 and 8.10 and it didn't work out.

Thanks in advance.

The iBook G3 doesn't have a keyboard backlight.

---

### Post by anandrajny on 2009-04-20
> **cyberdork33 said:**
> The iBook G3 doesn't have a keyboard backlight.

No wonder I've never been able to make it work. LOL!

---

### Post by anandrajny on 2009-04-20
Okay guys. One more problem.

I somehow messed up my Ubuntu 9.04 PowerPC software sources list.
Can someone please post the default sources.list for me or is there a way with CLI to restore back the original sources.list?

Greatly appreciated.

---

### Post by raysaunders on 2009-04-21
Thanks for the sort-out on the Monitor resolution. Much appreciated.

As far as sound capture is concerned, the iBook's own Mic picks up sound using Sound Recorder as long as I do NOT have the default "CD Quality, Lossy (.ogg type)" selected in the "Record as:" menu.

I just installed Ubuntu Netbook Remix on top and apart from an unfortunate black pointer instead of the default white pointer, it all seems to work pretty seamlessly. Unfortunately, it's not possible to change the faulty pointer in Appearance preference panel so I suppose it is a bug.

Had to hunt around here to remind myself that F12 acts as the right-click!

Otherwise, I may have (finally) found a usable modern system with which to breath new life into these old iBook G3 laptops that I have stored at the back of the cupboard.

---

### Post by JGreenidge on 2009-04-21
> **anandrajny said:**
> No wonder I've never been able to make it work. LOL!

I do believe somewhere on-line (heard it on MacInTouch I think) of instructions on how to rig your G3 to have one.

Geekless Jim

---

### Post by JGreenidge on 2009-04-21
> **raysaunders said:**
> Thanks for the sort-out on the Monitor resolution. Much appreciated.

Had to hunt around here to remind myself that F12 acts as the right-click!



Is there anyway to re-assign that F-12 right-click function to use a Command or Option key along with your mouse click instead?

Still looking for a means of using F keys to control screen backlight and turn off/idle hard-drive.


Geekless Jim

---

### Post by stream303 on 2009-04-21
This might be interesting for controlling the backlight / sleep functions - if it works on the G3:

[http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)

I'm still playing around with it on my G5.  I guess one could remap a key to a shell script or single commandline maybe...

---

### Post by cyberdork33 on 2009-04-21
> **JGreenidge said:**
> Is there anyway to re-assign that F-12 right-click function to use a Command or Option key along with your mouse click instead?

Still looking for a means of using F keys to control screen backlight and turn off/idle hard-drive.
Some info here might be helpful:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by moocow1452 on 2009-04-22
A couple of days ago, I downloaded the daily build of 9.04 to do necromancy of an old G3 for my sister. Got a select and install package error at 85%, but retrying fixed that easily enough. The problem comes in that it refuses to login to the username/password, and insists that the combination is incorrect. Tried it multiple times with mutiple passwords, no dice. Any Ideas?

---

### Post by cyberdork33 on 2009-04-22
> **moocow1452 said:**
> A couple of days ago, I downloaded the daily build of 9.04 to do necromancy of an old G3 for my sister. Got a select and install package error at 85%, but retrying fixed that easily enough. The problem comes in that it refuses to login to the username/password, and insists that the combination is incorrect. Tried it multiple times with mutiple passwords, no dice. Any Ideas?
Someone was having an issue like this before. The installer wasn't making the password set correctly. You can boot into recovery mode (which gives you a root console) and you can set the passwd for your using there.

---

### Post by jodawe on 2009-04-23
Thanks very much for this tutorial.  Setting up Jaunty on my g3 500mhz was a breeze.  

Has anyone successfully got a media player to playback divx files?  I've tried vlc, mplayer and totem with no luck.

---

### Post by moocow1452 on 2009-04-23
> **cyberdork33 said:**
> Someone was having an issue like this before. The installer wasn't making the password set correctly. You can boot into recovery mode (which gives you a root console) and you can set the passwd for your using there.

Thanks, I couldn't access failsafe mode, but a new .ISO did the trick.

---

### Post by kylepp on 2009-05-01
I can't seem to get suspend/sleep or hibernate working in 9.04, although it sounds for the above posts that it should work out of the box. Any ideas? I also don't have the normal gnome power manager applet in my menu bar.

(ibook2 G3 700 mhz, 384 mb RAM)

Thanks

---

### Post by stream303 on 2009-05-01
Suspend and sleep have always been problems on ppc, beyond those of even normal pc's.  So don't pull your hair out trying to get it working - ati and nvidia haven't released any ppc docs to Linux devs as far as I know.

Most attempts that I've tried can get the system to sleep, but you just won't wake up. :)

---

### Post by anandrajny on 2009-05-03
I think the screen light can be controlled by fn+F1 and fn+F2. The volume control and the eject buttons work for me as well if I press them together with fn key. My machine is IBOOK G3 500mhz.

> **JGreenidge said:**
> Is there anyway to re-assign that F-12 right-click function to use a Command or Option key along with your mouse click instead?

Still looking for a means of using F keys to control screen backlight and turn off/idle hard-drive.


Geekless Jim

---

### Post by anandrajny on 2009-05-03
I'm on a IBOOK G3 500mhz machine.
My suspend works just fine and wakes up just fine. For me personally, 9.04 is the best that happened to PowerPC. Everything works just right out of the box. The PowerPC team has outdone themselves.> **stream303 said:**
> Suspend and sleep have always been problems on ppc, beyond those of even normal pc's.  So don't pull your hair out trying to get it working - ati and nvidia haven't released any ppc docs to Linux devs as far as I know.

Most attempts that I've tried can get the system to sleep, but you just won't wake up. :)

---

### Post by anandrajny on 2009-05-23
> **jodawe said:**
> Thanks very much for this tutorial.  Setting up Jaunty on my g3 500mhz was a breeze.  

Has anyone successfully got a media player to playback divx files?  I've tried vlc, mplayer and totem with no luck.

Yeah. Mine doesn't play any video either which includes, wmv, divx, xvid etc. I've installed vlc,mplayer and so on.
It used to work on 8.04 and 8.10. It's sad.

---

### Post by vijaym on 2009-05-26
Here's the thing.

My g3 ibook with an Airport card - using the orinoco driver.
Installed 9.04 and gnome

Would not do the WPA wireless thing. The only options tended to be WEP.

found assistance and guidance on this link.

[http://wiki.debian.org/orinoco](http://wiki.debian.org/orinoco)

Now WPA wireless works

---

### Post by JGreenidge on 2009-06-03
> **vijaym said:**
> Here's the thing.

My g3 ibook with an Airport card - using the orinoco driver.
Installed 9.04 and gnome

Would not do the WPA wireless thing. The only options tended to be WEP.

found assistance and guidance on this link.

[http://wiki.debian.org/orinoco](http://wiki.debian.org/orinoco)

Now WPA wireless works

Please help me out here! I'm not a geek! I heard for ages that you can't have WPA on a G3 iBook! I read your Debian link and it's all Greek to me! Can anyone offer step by step instructions on how to do this? Not just for me, but the home school next door just getting into Ubuntu!

I'm still trying to find a way to handle the screen brightness under Ubuntu other than pre-setting it in Tiger, abd forget the sleep thing! Ubuntu is SOOO close now to being fringe perfect anf just misses the mark with these drawbacks!

Geekless Jim!

---

### Post by Martron2020 on 2009-06-12
thanks a bunch for the xorg.conf info!  1st time linux user on g3 500 iBook.
I used an app called sidetrack in OSX, added sidescrolling to the trackpad.  is there something like that for ubuntu?

---

### Post by moocow1452 on 2009-06-13
Quick question guys, I have a Linksys G wifi usb stick, #wusb54gc, and am trying to get it to work with a g3 ibook with 9.04. Any ideas, cause I am completely hopeless with hardware accesories.

---

### Post by ant2ne on 2009-06-24
> **cyberdork33 said:**
> Someone was having an issue like this before. The installer wasn't making the password set correctly. You can boot into recovery mode (which gives you a root console) and you can set the passwd for your using there.IT was me. [http://ubuntuforums.org/showthread.php?t=1068532](http://ubuntuforums.org/showthread.php?t=1068532) And you never answered me before, how do I boot into recovery mode with yaboot instead of grub?

---

### Post by ant2ne on 2009-06-25
Well I did another install and this one worked. I didn't get locked out this time. Of course, I selected auto login which I may want to change in the future.

One thing I need to get fixed, there is no WPA on my wireless connection options. [I did get WPA to work with wicd]("http://forums.debian.net/viewtopic.php?t=36050&highlight=ibook"), back when I booted debian. Now that I use ubuntu, I'd rather get it to work with the already included ubuntu connection utility. Anyone have any luck with that?

---

### Post by ant2ne on 2009-06-27
it seems the [orinoco driver]("http://wiki.debian.org/orinoco#supported-airport") is broken. I performed the steps. Using the driver from the git and by downloading the attachment of the orinoco-devel message both drivers did put WPA into the list of choices, but the ibook would no longer connect to any wireless networks.


```
sudo rm /lib/firmware/agere_sta_fw.bin
``` did not restore the default WEP connection 


:confused:

---

### Post by edwith on 2009-06-28
Thanks Guys followed you"re lead. now have it up and running in full screen on a g3powerbook pismo 400mhz with 384 ram. 
used 9.04 Ubuntu ppc regular. only change I made was to use gedit instead of nano and while X11 was running and saved. 
reboot brought it in for me. I used the r128 driver not the fb.
Thanks again!

---

### Post by ant2ne on 2009-06-29
See post 33 of this thread [http://ubuntuforums.org/showpost.php?p=7525577&postcount=33]("http://ubuntuforums.org/showpost.php?p=7525577&postcount=33")

---

### Post by caalamus on 2009-07-18
**YES!**


I have this exact problem with screen reso!

trying to adjust in the preferences results in things getting worse and requires reinstall (for novices like myself at least) 

...will try fix when I get home!


My 500Mhz G3 iBook, dual usb, running 640mb of RAM with firewire 400 & an original airpot card uses the eject button for right click...

I'll also try holding FN to use eject as eject!

Yous have made my day!!!

...or night as it were :]


Now how about "Jack" in Ubuntu 9.04 (or XUbuntu) so I can start recording???


(so happy!!!)

---

### Post by caalamus on 2009-07-18
o.k.

Fn+Eject works like a charm.

:]


The rest, not so much.

I tried the string of code on the first page... for fixing screen resolution. 

After:

sudo /etc/init.d/gdm stop

...my screen goes black, which as I understand is supposed to happen.

There is a flashing cursor top left... but it is entirely non responsive. I can't type!

If I try:
sudo dpkg-reconfigure xserver-xorg

or:

sudo /etc/init.d/gdm stop

&

sudo dpkg-reconfigure xserver-xorg

together, I get this help file... blue and grey. It's about reconfiguring  xserver-xorg... but that's it... dead end & nothing to edit.

Totally out of my league!


[B][COLOR="Red"]HELP PLEASE!!!
[/COLOR][/B]
:[

I was so excited.

---

### Post by caalamus on 2009-08-04
I figured it out...

once you get to that grey and blue screen, configuring xserver yada yada yada... you can't proceed using enter or return. You use escape... or at least I had to.


See below

Screen Resolution
If your screen is small and in the top, left corner of the screen with the exact same thing under it, follow the instructions below.
Run the following command in the terminal. It will shut down X Windows.
Code:

sudo /etc/init.d/gdm stop

(which may result in an inoperative blank screen. reboot and go to the next step )

Once it is closed type in the following codes:
If the method doesn't work for you the first time, redo it but this time enter the following code
Code:
sudo dpkg-reconfigure xserver-xorg
and go through it.


(which requires configuring settings for keyboard layout and confused the bejesus out of me since I got stuck on the same screen till I realized it was necessary to use escape, not enter or return to continue to the next step )





Now enter the code below
Code:
sudo nano /etc/X11/xorg.conf
Then, edit it to match this:
Code:
Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
The method above was posted on this thread by chriz74.

To start X Windows again, enter
Code:
sudo /etc/init.d/gdm start




WORKS LIKE A CHARM!

---

### Post by caalamus on 2009-08-04
now how about my non responsive cd drive?

---

### Post by rjcalifornia on 2009-08-06
How about the fact I can't watch Divx or AVI videos?  

Note: I installed the ubuntu-restricted

---

### Post by Horusrogue on 2009-09-07
> **RandyVanBuren said:**
> How about the fact I can't watch Divx or AVI videos?  

Note: I installed the ubuntu-restricted

Running xubuntu 9.04.

Slightly different fixes for the fluxbox gui resolution wise.
Right click was EJECT...the mac battery ran out (oops, wall charger went into powerless socket) and now I HAVE to use FN+f12 to get right click.

Won't eject dvd, but a simple TERMINAL command "eject" does it perfectly. 

Sound and network work out of box. Brightness up and down work with function keys. 
WILL NOT PLAY FLASH online for some reason. 
Will NOT PLAY DIVX with anything. Totem, (vlc crashes for EVERYTHING including audio), mplayer. Whats the catch?
I have ffmpeg. 

Does the external monitor work? I guess thats a fluxbox issue I have to resolve.
USB works fine too.

---

### Post by rjcalifornia on 2009-09-07
> **Horusrogue said:**
> Running xubuntu 9.04.

Slightly different fixes for the fluxbox gui resolution wise.
Right click was EJECT...the mac battery ran out (oops, wall charger went into powerless socket) and now I HAVE to use FN+f12 to get right click.

Won't eject dvd, but a simple TERMINAL command "eject" does it perfectly. 

Sound and network work out of box. Brightness up and down work with function keys. 
WILL NOT PLAY FLASH online for some reason. 
Will NOT PLAY DIVX with anything. Totem, (vlc crashes for EVERYTHING including audio), mplayer. Whats the catch?
I have ffmpeg. 

Does the external monitor work? I guess thats a fluxbox issue I have to resolve.
USB works fine too.

Hey, I had the same problems with Ubuntu. I find myself now using Kubuntu Jaunty Jackalope, and it plays everything and more. 3gp, mkv, mov and mp4 are supported by Xine for Kubuntu. For some reason, it doesn't work under Ubuntu Jaunty Jackalope. Besides that, repositories on kubuntu doesn't expires like in Ubuntu... 

Oh, and it looks AWESOME! Right out of the box. No need to download something, it just looks great. Ubuntu looks old compared to Kubuntu Jaunty Jackalope. Plasma Dashboard it's just great.

---

### Post by ant2ne on 2009-09-07
> **RandyVanBuren said:**
> Hey, I had the same problems with Ubuntu. I find myself now using Kubuntu Jaunty Jackalope,.... What about WPA? I'd switch to kubuntu for WPA.

---

### Post by rjcalifornia on 2009-09-07
> **ant2ne said:**
> What about WPA? I'd switch to kubuntu for WPA.

Sorry, don't know anything about that. I don't have a wireless adapter for my ibook g3.....

---

### Post by Horusrogue on 2009-09-08
> **RandyVanBuren said:**
> Hey, I had the same problems with Ubuntu. I find myself now using Kubuntu Jaunty Jackalope, and it plays everything and more. 3gp, mkv, mov and mp4 are supported by Xine for Kubuntu. For some reason, it doesn't work under Ubuntu Jaunty Jackalope. Besides that, repositories on kubuntu doesn't expires like in Ubuntu... 

**Oh, and it looks AWESOME! Right out of the box. No need to download something, it just looks great. Ubuntu looks old compared to Kubuntu Jaunty Jackalope. Plasma Dashboard it's just great.**

And it runs great? I only have the 256 MB model. 
Are you suggesting I switch? Will the performance be similar between Fluxbox and the Kubuntu default gui? Likely not.
But you are saying videos should play....

[SIZE=7]Also:[/SIZE] Does anyone know how to switch to an external monitor? I tried a tutorial about that with ATI chipsets..but it did not work. 
I have the cord that converts the mini-vga? Or whatever to normal vga. It works ON BOOTUP but when the OS loads..nothing.
I keep trying to use XRANDR...but how would I do it? I have added a monitor section in my xorg.conf....

---

### Post by rjcalifornia on 2009-09-08
> **Horusrogue said:**
> And it runs great? I only have the 256 MB model. 
Are you suggesting I switch? Will the performance be similar between Fluxbox and the Kubuntu default gui? Likely not.
But you are saying videos should play....

[SIZE=7]Also:[/SIZE] Does anyone know how to switch to an external monitor? I tried a tutorial about that with ATI chipsets..but it did not work. 
I have the cord that converts the mini-vga? Or whatever to normal vga. It works ON BOOTUP but when the OS loads..nothing.
I keep trying to use XRANDR...but how would I do it? I have added a monitor section in my xorg.conf....

oh... 256 MB... I have 640 MB, and yes, it runs great, better than Ubuntu..... I thought it was going to be slow and exasperating, but it turned out that it's not that heavy....

Probably you should stick with Xubuntu or Debian Lenny :(

---

### Post by Horusrogue on 2009-09-08
> **RandyVanBuren said:**
> oh... 256 MB... I have 640 MB, and yes, it runs great, better than Ubuntu..... I thought it was going to be slow and exasperating, but it turned out that it's not that heavy....

Probably you should stick with Xubuntu or Debian Lenny :(

Would anyone know if Kubuntu with the Fluxbox gui would simply fix the video issue and yet run just as fast?

---

### Post by micomarata on 2009-09-26
Need Help on my ibook g3. i just download the ubuntu 9.04 powerpc. i follow the instruction of chriz74 and after i fished all the procedures mg ibook requires a username and password? and its always counting in  10sec? any idea whats the username and password? and can some one give me help installing my ubuntu on my ibook? ASAP....
:(

---

### Post by Horusrogue on 2009-09-27
> **micomarata said:**
> Need Help on my ibook g3. i just download the ubuntu 9.04 powerpc. i follow the instruction of chriz74 and after i fished all the procedures mg ibook requires a username and password? and its always counting in  10sec? any idea whats the username and password? and can some one give me help installing my ubuntu on my ibook? ASAP....
:(

Is this the 500 model? 

Username and password? Maybe something like root and root or admin/admin?

Installation? Simply boot off cd/dvd (was for me) by holding down the C key (I think it was)
Choose the linux distro and yea....installation from there should be fariyl basic (as far as OS installs go).

I would RECOMMEND Xubuntu 9.04 vs straight out ubuntu (unless you do a server install and then add on a gui of your choice) because it runs well enough initially on = or < 256 mb memory machines to set up an EVEN LIGHTER gui desktop.

---

### Post by micomarata on 2009-09-27
i just finished downloaded the ubuntu alternate cd 9.04 and same problem? i can't get pass on the username and password screen? no more counting from 10 sec.? i remember in the installation procedure the installation procedure requires for my full name? then a username and password and so i punch my username and password and the after a few minutes the installation finished. and it reboot. now the log in screen appear? need more help please....

---

### Post by Horusrogue on 2009-09-28
> **micomarata said:**
> i just finished downloaded the ubuntu alternate cd 9.04 and same problem? i can't get pass on the username and password screen? no more counting from 10 sec.? i remember in the installation procedure the installation procedure requires for my full name? then a username and password and so i punch my username and password and the after a few minutes the installation finished. and it reboot. now the log in screen appear? need more help please....

You can always enter the information (login) afterwards. If you are having password issue simply enter no password and set it later. 

Again, WHICH MODEL are you installing on?

---

### Post by micomarata on 2009-09-29
model: ibook g3  m6411 i think this is the model? so u mean i need to reinstall the ubuntu again?

---

### Post by BothEyesShut on 2009-09-30
:P

This tutorial definitely worked for me.  Got an old iBook G3 Dual USB with that tiny 12" screen looking pretty beautiful and running like a champ.

*NOTE: that /X11/ directory is not to be confused with /x11/.


Thanks, OP!

---

### Post by Horusrogue on 2009-10-01
> **BothEyesShut said:**
> :P

This tutorial definitely worked for me.  Got an old iBook G3 Dual USB with that tiny 12" screen looking pretty beautiful and running like a champ.

*NOTE: that /X11/ directory is not to be confused with /x11/.


Thanks, OP!
[B]
CAN YOU PLAY DIVX/XVID avi files?[/B]
I cannot and I installed xubuntu (works alright..mostly) and it does not.

---

### Post by Horusrogue on 2009-10-01
> **micomarata said:**
> model: ibook g3  m6411 i think this is the model? so u mean i need to reinstall the ubuntu again?

If you cannot log in do not set a password or username if you can during install.
**How much memory?**

---

### Post by ant2ne on 2009-10-03
> **BothEyesShut said:**
> *NOTE: that /X11/ directory is not to be confused with /x11/. nix is case sensitive. myfile.txt is not the same as Myfile.txt or MYFILE.TXT. You get used to it. It does make samba sharing interesting.

Does anyone know if there is a working flash for the ppc yet. I've got a bunch of macs waiting for ubuntu, but i want to play hulu (requires adobe flash) and youtube (gnash might work) and stuff.

---

### Post by mdonovan on 2009-10-04
Hi.

Has anyone got any idea how to get a PPC mozilla plugin for Flash ?

Or which Flash player to use to get websites using Flash to work under Mozilla ?

I have [Xubuntu up and running on my G3 iBook]("http://blog.mdonovan.co.uk/2009/07/at-last-xubuntu-on-my-g3-ibook.html") and all I think I am missing now is this Flash ability. Any ideas appreciated. Thanks.

---

### Post by Horusrogue on 2009-10-05
> **mdonovan said:**
> Hi.

Has anyone got any idea how to get a PPC mozilla plugin for Flash ?

Or which Flash player to use to get websites using Flash to work under Mozilla ?

I have [Xubuntu up and running on my G3 iBook]("http://blog.mdonovan.co.uk/2009/07/at-last-xubuntu-on-my-g3-ibook.html") and all I think I am missing now is this Flash ability. Any ideas appreciated. Thanks.

Nothing I have tried yet works. 

Also you can use the eject button with a keymap-remap. USE synaptic to find it. 

Can you run movies? Divx? Xvid?

---

### Post by micomarata on 2009-10-06
> **Horusrogue said:**
> If you cannot log in do not set a password or username if you can during install.
**How much memory?**

standard is 64mb and i put another 64mb total of 128 mb. so do i need to reinstall the ubuntu again?

---

### Post by micomarata on 2009-10-07
i just finished again installing for 5X ubuntu altenate cd. the problem still the same? i stuck on username/ password screen. i tried all the password and username (admin/admin, root/root, username/password) stiil i cn't pass the logins.

can someone HELP ME PLEASE!!!!!!!!!!!!!!!!:(

---

### Post by B_Free on 2009-10-07
Is this a PPC machine? Does the login have a count down just below the password box? If so, just let the time expire. It should just automatically log you in. It won't hurt trying.

---

### Post by avtolle on 2009-10-08
To the best of my knowledge,  there is no ppc flash and thus no plugin for the same.

---

### Post by micomarata on 2009-10-08
i use a ibook g3 with 15gig og hdd. i use the alternate cd powerpc no more countdown below. still i cnt pass throught the username/ppassword screen. incorrect username and password. i even try to put nothing upon installation on username and password. still no luck. PLEASE!!!!!! help me. im not dat techy on linux. hope you guys understand. :(](*,)

---

### Post by imET on 2009-10-09
First off thanks to OP, I managed to instal Xubuntu jaunty on a
iBook G3 500MHz 640MB RAM, 10GB drive. The splash screen with the progress bar
is still split in two parts, the lower section is about 1/5th of the screen,
even though the login screen is not split. (I didn't do autologin) I can live with that.
What I want to know is, how can I speed up the loading of the desktop.
It takes more than 2 minutes to show the desktop after logging in, but once logged in
everything seems ok.

---

### Post by rjcalifornia on 2009-10-12
> **micomarata said:**
> i use a ibook g3 with 15gig og hdd. i use the alternate cd powerpc no more countdown below. still i cnt pass throught the username/ppassword screen. incorrect username and password. i even try to put nothing upon installation on username and password. still no luck. PLEASE!!!!!! help me. im not dat techy on linux. hope you guys understand. :(](*,)


how about using kubuntu instead??:guitar:

---

### Post by ant2ne on 2009-10-13
> **RandyVanBuren said:**
> how about using kubuntu instead??:guitar:*sigh*

> **micomarata said:**
> i use a ibook g3 with 15gig og hdd. i use the alternate cd powerpc no more countdown below. still i cnt pass throught the username/ppassword screen. incorrect username and password. i even try to put nothing upon installation on username and password. still no luck. PLEASE!!!!!! help me. im not dat techy on linux. hope you guys understand. :(](*,)I had similar problem when installing latest debian on iBook. It took three tries before it installed. Try again, and be certain that the password you use doesn't include any funky characters. Regardless what others say, I know that the character ! and @ in a password can cause problems. So set a simple user name and a simple password.

---

### Post by goatkeeper on 2009-10-14
[SIZE=2]Hi, just downloaded Jaunty on my iBook the other day. Thanks to you guys the video problem got solved first thing. The install went smoothly; I could have slept through it. I never expected it to be that easy. I have everything I need for the immediate future. But two things, one perhaps rather dumb. How do you get the CD tray to open now that f12 is the control click without using the low tech paper clip in the hole? And yes, also, the little book seems to run hotter than under Tiger, and I know it shouldn't. Heat is the enemy. I'll try suggestions above if it seems to get out of control. Thank you. To be rid of Apple forever except for the beautiful hardware is a load off my back![/SIZE]

---

### Post by rjcalifornia on 2009-10-14
> **goatkeeper said:**
> [SIZE=2]Hi, just downloaded Jaunty on my iBook the other day. Thanks to you guys the video problem got solved first thing. The install went smoothly; I could have slept through it. I never expected it to be that easy. I have everything I need for the immediate future. But two things, one perhaps rather dumb. How do you get the CD tray to open now that f12 is the control click without using the low tech paper clip in the hole? And yes, also, the little book seems to run hotter than under Tiger, and I know it shouldn't. Heat is the enemy. I'll try suggestions above if it seems to get out of control. Thank you. To be rid of Apple forever except for the beautiful hardware is a load off my back![/SIZE]

open terminal:

then type 

```
eject
```

or....

right click on desktop, create a new "link to application" and on the "application" tab, and where it says "command" type "eject"

---

### Post by rpras on 2009-10-25
Just wanted to report that I successfully installed Jaunty on my iBook (600mhz/dual usb/snow/Airport).

I followed the instructions posted here and got everything to work.

[LIST]
[*]Sound worked out-of-the-box.
[*]Screen resolution needed fix following the method described in the first post.  The splash screen during boot is still 640x480 and mirrored.  I think I'll edit the boot options to specify "nosplash."
[*]Airport did give me some WPA problems.  I needed to download the firmware mentioned here: [http://wiki.debian.org/orinoco](http://wiki.debian.org/orinoco).  Just unzipped the file and placed the firmware file after renaming it in the /lib/firmware folder.  This method seemed to enable WPA.  However, connecting to my Netgear WGR 614 v6 router was very flaky.  Random drops and multiple attempts before Airport would connect.  I had to install wicd networking manager.  No drops since then.
[*]Touchpad tapping and dragging works -- I had to enable them, though.  You need to have powerpc-utils installed and then just "sudo trackpad show" to see what options are enabled by default.  Use "sudo trackpad tap" to enable tapping and "sudo trackpad drag" to enable dragging (credit: [http://ubuntuforums.org/showthread.php?t=211797](http://ubuntuforums.org/showthread.php?t=211797)).  To make these setting survive booting, see [http://ubuntuforums.org/showthread.php?t=488853](http://ubuntuforums.org/showthread.php?t=488853).
[*]Now if I could figure out how to make the trackpad do a right-click.
[/LIST]
I love ubuntu and these forums!  Have a 64-bit version running on my quad-core Q6600 machine.  But running it on the iBook is just too sweet.

Thanks.

---

### Post by ant2ne on 2009-10-26
> **rpras said:**
> 
[*]Airport did give me some WPA problems.  I needed to download the firmware mentioned here: [http://wiki.debian.org/orinoco](http://wiki.debian.org/orinoco).  Just unzipped the file and placed the firmware file after renaming it in the /lib/firmware folder.  This method seemed to enable WPA.  However, connecting to my Netgear WGR 614 v6 router was very flaky.  Random drops and multiple attempts before Airport would connect.  I had to install wicd networking manager.  No drops since then.
Now we are talking. I'm ready to break out the iBook and get WPA working on it!!

---

### Post by moocow1452 on 2009-10-26
I apperciate your guys work, but with the Final Release coming out in a week, what's the word on Karmic on PowerPC?

---

### Post by linuxopjemac on 2009-10-27
your best bet for making sleep work on a PPC based Mac is to use pmud

[http://sourceforge.net/projects/apmud/](http://sourceforge.net/projects/apmud/)

---

### Post by linuxopjemac on 2009-10-27
and to have all hotkeys working you might try [http://pbbuttons.berlios.de/](http://pbbuttons.berlios.de/)

---

### Post by eQuk on 2009-10-27
Installing ubuntu intrepid on my ibook G3 now, is there a way to stop the update manager bugging me about updating pixman and upgrading to jaunty, maybe some way to exclude them from updates?

---

### Post by rpras on 2009-11-02
> **rpras said:**
> Just wanted to report that I successfully installed Jaunty on my iBook (600mhz/dual usb/snow/Airport).

I followed the instructions posted here and got everything to work.

[LIST]
[*]Sound worked out-of-the-box.
[*]Screen resolution needed fix following the method described in the first post.  The splash screen during boot is still 640x480 and mirrored.  I think I'll edit the boot options to specify "nosplash."
[*]Airport did give me some WPA problems.  I needed to download the firmware mentioned here: [http://wiki.debian.org/orinoco](http://wiki.debian.org/orinoco).  Just unzipped the file and placed the firmware file after renaming it in the /lib/firmware folder.  This method seemed to enable WPA.  However, connecting to my Netgear WGR 614 v6 router was very flaky.  Random drops and multiple attempts before Airport would connect.  I had to install wicd networking manager.  No drops since then.
[*]Touchpad tapping and dragging works -- I had to enable them, though.  You need to have powerpc-utils installed and then just "sudo trackpad show" to see what options are enabled by default.  Use "sudo trackpad tap" to enable tapping and "sudo trackpad drag" to enable dragging (credit: [http://ubuntuforums.org/showthread.php?t=211797](http://ubuntuforums.org/showthread.php?t=211797)).  To make these setting survive booting, see [http://ubuntuforums.org/showthread.php?t=488853](http://ubuntuforums.org/showthread.php?t=488853).
[*]Now if I could figure out how to make the trackpad do a right-click.
[/LIST]
I love ubuntu and these forums!  Have a 64-bit version running on my quad-core Q6600 machine.  But running it on the iBook is just too sweet.

Thanks.

I guess I was way too early judging my Jaunty install.  Airport with WPA worked for a while but then I started having major problems.  "No DHCPOFFERS received."  Could not resolve the issue at all.  So I installed Karmic.  Still have the same issue in Karmic.

Looks like there is a problem with dhclient.  My searches have shown me a ton of posts that describe the issue, but no fix yet -- not for Jaunty nor for Karmic.

---

### Post by rpras on 2009-11-09
Fixed -- look at my posts in this thread: [http://ubuntuforums.org/showthread.php?t=1310313](http://ubuntuforums.org/showthread.php?t=1310313).  Karmic now runs beautifully on my iBook.  I've gotten it to start network using wireless connection to my AP at boot time.  No drops at all.

---

### Post by ant2ne on 2009-11-09
> **rpras said:**
> Fixed -- look at my posts in this thread: [http://ubuntuforums.org/showthread.php?t=1310313](http://ubuntuforums.org/showthread.php?t=1310313).  Karmic now runs beautifully on my iBook.How did you get it installed? See [http://ubuntuforums.org/showthread.php?p=8278234#post8278234](http://ubuntuforums.org/showthread.php?p=8278234#post8278234)

---

### Post by rpras on 2009-11-09
> **ant2ne said:**
> How did you get it installed? See [http://ubuntuforums.org/showthread.php?p=8278234#post8278234](http://ubuntuforums.org/showthread.php?p=8278234#post8278234)

I used the powerpc alternate ISO to burn a CD.  Looking at your other thread, I see your problem.  I think I ran into the same issue and decided to go with the alternate ISO precisely because I **could** get it to burn on a CD.  Looks like you found the same solution.

Good luck with your install.  Once you get it to work, it's slick!

---

### Post by rpras on 2009-11-14
> **ant2ne said:**
> How did you get it installed? See [http://ubuntuforums.org/showthread.php?p=8278234#post8278234](http://ubuntuforums.org/showthread.php?p=8278234#post8278234)

Were you able to get Karmic installed?

---

### Post by ant2ne on 2010-02-02
> **rpras said:**
> Were you able to get Karmic installed?I got 9.10 installed. But I still got no wpa. (I can't connect to non SSID broadcasting networks either. but that maybe a different issue.) Did you have to install the orinoco driver? [http://wiki.debian.org/orinoco]("http://wiki.debian.org/orinoco") I did that, because that is what I had to do with a debian install.

---

### Post by linuxopjemac on 2010-02-02
In Karmic I have trouble with WPA too. I changed to wicd, much better.

```
sudo apt-get install wicd
```

you probably have to do a reboot to see the new networkmanager in your panel.

---

### Post by LtPitt on 2010-02-02
> **micomarata said:**
> i use a ibook g3 with 15gig og hdd. i use the alternate cd powerpc no more countdown below. still i cnt pass throught the username/ppassword screen. incorrect username and password. i even try to put nothing upon installation on username and password. still no luck. PLEASE!!!!!! help me. im not dat techy on linux. hope you guys understand. :(](*,)

Did you check your little ibook date?
I had problems with mine because of a motherboard battery gone :/ :)

---

### Post by ant2ne on 2010-02-02
> **linuxopjemac said:**
> In Karmic I have trouble with WPA too. I changed to wicd, much better.

```
sudo apt-get install wicd
```

you probably have to do a reboot to see the new networkmanager in your panel.you can connect to wpa with wicd? no problems?

---

### Post by linuxopjemac on 2010-02-03
> you can connect to wpa with wicd? no problems? 

that's what I said, but I am on a MacBook 2,1....

---

### Post by ant2ne on 2010-02-03
> **linuxopjemac said:**
> that's what I said, but I am on a MacBook 2,1....MacBook != iBook 

[-X

---

### Post by linuxopjemac on 2010-02-04
Macbook &#8800; iBook (Intel vs PPC)

---

### Post by ant2ne on 2010-02-04
> **linuxopjemac said:**
> Macbook &#8800; iBook (Intel vs PPC)Right, and this thread is titled "iBook G3 Working Tutorial"

---

### Post by linuxopjemac on 2010-02-04
the question is, does wicd work for you or not? It has nothing to do whether you are on an iBook or not. Networkmanager is not very well in Karmic.

---

### Post by ant2ne on 2010-02-04
not to be dragged into a flame, but I'm certain wicd works with wpa for a lot of people. But this thread is iBook specific. I could post how wicd works very well on my Dell, and that would be about as helpful as information about it working on a MacBook. wicd doesn't work right out of the box with the iBook. If you got wicd to work, with an iBook, then you should share how.

---

### Post by ant2ne on 2010-02-05
Ok, I just now got this to work. So I have yet to implement permanent fixes. I have not removed network-manager. But, like rpras's solution, only command line wpa_supplicant works. On one WAP I did have random drops in connections. At home I logged in and had a steady connection. If I notice drops more drops I'll update this thread.

I had to do a fresh OS install of 9.10. I think I borked something the first time around and it was just keeping the driver from working. If you have been playing with this for awhile then you maybe better off wiping too.

**kernel version**
uname -r if you are better than 2.6.28 then you are golden. 9.10 will be good.

**install the driver**
[Download this driver]("http://ant2ne.com/downloads/orinoco.fw.tar.bz2"). Then unzip it and remove orinoco.fw
then 'sudo cp orinoco.fw /lib/firmware/agere_sta_fw.bin' then 'modprobe airport' and reboot.

**using wpa_supplicant**
I created a script called cygne.sc (the name of my home network) and put in it...
```
rm /var/run/wpa_supplicant/eth1
/sbin/wpa_supplicant -ieth1 -Dwext -ccygne.conf
```then I created a cygne.conf file and put in ...
```
ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="cygne"
    scan_ssid=0
    proto=WPA
    key_mgmt=WPA-PSK
    psk="mypasskey"
    pairwise=TKIP
    group=TKIP
}
```I think you need to use WPA1 and only TKIP on your WAP. No other WPA will work.

then " sudo ./cygne.sc" and the connection was made. I did have to open a second command window to type "sudo dhclient eth1" to get an IP. I suppose a 'sleep 20' and then the dhclient could be appended to cygne.sc

UPDATE: I did have drops. I removed network-manager and the drops seem to have stopped.

---

### Post by ant2ne on 2010-02-15
Well, 

Do to a lack of power management in ubuntu I went and tried slackintosh. And I'm very pleased. [Here is my tut]("http://www.ant2ne.com/?p=173").

---

### Post by linuxopjemac on 2010-02-16
Thanks for the installation manual, I made a link on my website to your manual. Good luck with Slackintosh.

---

### Post by the wizard of oz on 2010-03-02
> **LtPitt said:**
> Did you check your little ibook date?
I had problems with mine because of a motherboard battery gone :/ :)
Help, like Mikomarata I never get past the username/password screen; this has been driving me nuts for days!

Specs:
Apple iBook G3 12" (Late 2001 with Dual USB & FireWire)
640MB RAM
15GB HDD
500MHz PPC CPU

After replacing the original CD-ROM drive with a CD-RW/DVD-ROM drive from an old defunct laptop, adding a fresh 512MB RAM module, burning an alternate-CD PPC version of Linux Ubuntu 9.10 Karmic Koala to DVD, I didn't expect such a hard time getting my iBook running smoothly :( ...
Very frustrating, from a working Mac OS X 10.1.3, which was able to play DVD movies and run a bit faster after I performed the aforementionned upgrades, but not able to browse the modern internet very well, hence the Ubuntu installation, now I have nothing working at all :sad: .

So it could be the motherboard's battery?! How can I find out?

On a side note, some ideas on how to solve my issue with the small central hex screw of the iBook's lower case, which hex hole is worn out, disabling loosening of the said screw :oops: :frown: ...

---

### Post by linuxopjemac on 2010-03-02
[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0)

I wish I could make sticky posts in this forum....

---

### Post by the wizard of oz on 2010-03-02
Dank je wel / thanks ;) , that's probably the issue, since it displayed year 1904 in the Open Firmware!
I'm trying a reinstall now; I'll keep you posted.

---

### Post by linuxopjemac on 2010-03-02
you don't need to reinstall. Just set the date in open firmware and boot into Linux. Make sure that you set the time with ntp at boot. Then you don't have that problem anymore.

---

### Post by the wizard of oz on 2010-03-02
Too late! Nevermind, login worked. Thanks a lot, I really am very grateful.

Now to fix the display issue...

...and then op je gemak op je mac met ubuntu :) !

Yay, editing the conf file did the trick :D . Thanks for that too :) .

Now for some media fixes, and all will be great.

---

### Post by oswaldkelso on 2010-03-02
> **the wizard of oz said:**
> 
On a side note, some ideas on how to solve my issue with the small central hex screw of the iBook's lower case, which hex hole is worn out, disabling loosening of the said screw :oops: :frown: ...

You could try super glue.

Place some on your driver, taking care not to touch surounding plastic!! Leave for a hour. Fingers crossed ;)

---

### Post by the wizard of oz on 2010-03-03
> **oswaldkelso said:**
> You could try super glue.

Place some on your driver, taking care not to touch surounding plastic!! Leave for a hour. Fingers crossed ;)
I'll try that if I need to take it apart again, thanks for the suggestion.

Mmh, another issue has popped up, the CD/DVD drive doesn't seem properly recognized...
No DVD nor CD appears in "Places" when loaded; Under "Computer", "CD/DVD Drive" is present next to "Filesystem", but clicking it to open it doesn't do anything.
Properties of said CD/DVD Drive come as type, size, & volume "unknown" & location "unknow", so I guess this must be a mounting issue?!
Fn+Eject does work though, and when inserting a disc, it does spin, which seems coherent with the fact that I did manage to install the OS from that drive :D .
Any advice appreciated.

---

### Post by linuxopjemac on 2010-03-03
it's a bug, again, this could be a sticky...I don't know why people who have such authorities make a sticky out of this:

[http://ubuntuforums.org/showthread.php?t=1323153&highlight=cdrom&page=2](http://ubuntuforums.org/showthread.php?t=1323153&highlight=cdrom&page=2)

---

### Post by the wizard of oz on 2010-03-03
> **linuxopjemac said:**
> it's a bug, again, this could be a sticky...I don't know why people who have such authorities make a sticky out of this:

[http://ubuntuforums.org/showthread.php?t=1323153&highlight=cdrom&page=2](http://ubuntuforums.org/showthread.php?t=1323153&highlight=cdrom&page=2)
So [editing the fstab]("http://ubuntuforums.org/showpost.php?p=8119383&postcount=6") could be the answer?

I have this line
"/dev/hdb /media/cdrom0 udf, iso9660 user, noauto, exec, utf8, 0 0"

...do I have to change noauto to auto, or? Also in my media directory, cdrom and cdrom0 are two directories, not one directory and one file like in fellow ubuntu user AdamGott's case...

---

### Post by linuxopjemac on 2010-03-03
I have the following on a MacBook:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


So I would use the following in your /etc/fstab:

```
/dev/sr0        /dev/dvdrw     udf, iso9660 user, noauto, exec, utf8, 0 0
```


 
Join Date: Nov 2008
Beans: 22
	
Re: cd/dvd/usb automount not working - gnome-volume-manager or hal problem?
It was an fstab issue I guess. I changed my automount device to /dev/sr0 with a mount point of /dev/dvdrw. In my media directory there was a file called cdrom and a directory called cdrom0. The cdrom file linked to the cdrom0 directory and for some reason this was causing a bit of havoc. After I deleted both of these the automount now works for cd/dvd media and for USB.

I don't know why this was affecting USB but I guess it doesn't matter because it works now.

---

### Post by the wizard of oz on 2010-03-03
Nope, not working. I'll revert the /etc/fstab back to what it was.

Mounting /dev/hdb manually does load cdrom0 into media, but it won't read video DVD's very well at all in MPlayer, with sound & image lagging all over the place, and audio CD's give an error.

---

### Post by linuxopjemac on 2010-03-03
can you give me the output (the relevant passage) of dmesg after inserting a CD?

what about the following:

```
/dev/sr0        /media/cdrom0     udf, iso9660 user, noauto, exec, utf8, 0 0
```

---

### Post by the wizard of oz on 2010-03-03
when I mount using "mount /dev/hdb", after inserting a CD, I get:
"wronf fs type, bad option, bad superblock on /dev/hdb,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so"

would the last line of dmesg be relevant:
"isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16"?

I'm not so well versed in Linux command stuff, pardon me...

---

### Post by the wizard of oz on 2010-03-04
Bump.
So there's a definite bug with Karmic/PPC for optical drives? Nothing can be done? :( ...

Any chance this will be fixed in the next LTS release? Is there a distribution I should revert to in the meantime that does't have this bug?

---

### Post by ant2ne on 2010-03-16
I noticed that with ubuntu, the hard drive area of the ibook got very hot. I assumed this was just a mac 'feature' but then I installed [slackintosh]("http://www.ant2ne.com/?p=173") and it didn't get hot at all. I'm assuming that ubuntu is keeping the disk spinning or is accessing the disk excessively. Has anyone else noticed this? And found a solution? I'd much rather switch to ubuntu on my iBook, but slack is working great. If I could get power management and screen dimming and this ridiculous hard drive heat resolved in ubuntu then I'd switch asap! (Yes I have another ibook with ubuntu installed just for tinkering with.)

---

### Post by ant2ne on 2010-04-12
I spent some time and I got ubuntu working on my 800Mhz iBook G3 to my satisfaction.

My requirements
1 Functional Linux OS with GUI
2 Ethernet, and wifi with WPA
3 Power management including screen dimming and quick and reliable suspend and hibernation.
4 Ability to easily install applications with apt-get

[You can read all about it here.]("http://blog.computerant.com/2010/04/07/linux-on-the-ibook-varied-success-different-distributions/") If any of the steps are unclear, or you run into other difficulty, you could post a comment on the blog (preferred) or pm me here.

---

### Post by linuxopjemac on 2010-04-12
That's a great amount of work. Congratulations.

---

