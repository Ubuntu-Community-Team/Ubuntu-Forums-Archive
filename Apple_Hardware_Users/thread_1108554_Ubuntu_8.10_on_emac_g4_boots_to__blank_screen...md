---
title: "Ubuntu 8.10 on emac g4 boots to  blank screen.."
date: 2009-03-27
forum: Apple Hardware Users
---

### Post by pwn1j on 2009-03-27
After successfully installing ubuntu 8.10 ppc on an 800mhz emac, 512mb of memory, 60gb hard drive 
It will boot into yaboot but no further.  At the yaboot prompt i press enter it starts to boot but goes into a blank screen with a solid dash in the top left corner(not blinking).  If i let it sit at this stage for a couple minutes the screen eventually turns off.. any and all help would be greatly appreciated.  thanks

---

### Post by Buckfast Bulletmagnet on 2009-04-07
I don't really know anything, but i've just managed to install 9.04 on a 1.25ghz emac really very easily - held down option key with the ppc.iso boot disk in, selected the disk and followed the instructions. I am struggling with my bl**dy speedtouch 330 modem though. Works fine on the intel machine with USBadslMODEMMANAGER but seems to be a way above my noob head problem on ppc machines..........

BB

---

### Post by stream303 on 2009-04-09
Interrupt the automatic yaboot countdown by hitting TAB.

Then type
```
Linux video=ofonly
```
and see how far you get.

If this works to at least get you past this point, you can make it permanent by adding video=ofonly to the "append=" statements in /etc/yaboot.conf.  Make the system aware of this change with
```
sudo ybin -v
```

It is possible that you will still need to manually modify your /etc/X11/xorg.conf to get X to work properly however.

Don't be surprised if the apps don't seem to work - you may want to either back down to 8.04.1 LTS, or perhaps install 9.04 Jaunty when it comes out very soon.

---

### Post by roym4 on 2009-04-09
The solution is to make some changes to your /etc/X11/xorg.conf file.

Standard installation does not configure X correctly, and reconfiguring (sudo dpkg-reconfigure -phigh xserver-xorg) does no better. A manual fix is required. In the file /etc/X11/xorg.conf, replace the Monitor section with this:

Section "Monitor"
       Identifier      "iMac"
       Option          "DPMS"
       HorizSync       71-73
       VertRefresh     70-140
       Modeline "1024x768" 99.190000 1024 1072 1168 1376 768 769 772 810 +HSync +VSync
       Modeline "1280x960" 122.240000 1280 1328 1424 1696 960 961 964 1002 +HSync +VSync     
EndSection

In the Screen section, add "1280x960" to each Modes line, like this:

Modes      "1280x960" "1024x768" "800x600" "640x480"

When using Intrepid (8.10) an xorg.conf file is not automatically generated or is blank. You can run sudo dpkg-reconfigure -phigh xserver-xorg in order to generate an xorg.conf file. You can then make the above modifications.

On some eMacs, you'll also need to replace the Screen section with this:

Section "Screen" 
       Identifier  "Default Screen"
       Monitor     "Configured Monitor"
       Device      "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x960" "1152x870" "1024x768"
EndSubSection
EndSection

A few eMacs, primarily the ones with small speaker holes, will require a different xorg.conf changes. the three changes are listed below: Add an option line to the Device section:

Section "Device"
Option  "ConnectorTable" "100,1,0,1,108,2,0,1"
EndSection

Also, add a Modeline to the Monitor section:

Modeline "1024x768" 99.07 1024 1088 1200 1376 768 769 772 809 +HSync +VSync

Finally change the Screen section to include a Display subsection:

SubSection "Display"
   Viewport  0 0
   Depth     24
   Modes     "1024x768"
EndSubSection

---

### Post by Exodist on 2009-09-11
I know this thread is old. 
I have tried the above above and the screen isnt going blank now, X is just crashing and sending me to the CLI.

I cant tell what is wronge here since I havent messed with editing the xorg.conf files (used to be xfree86) in 6+ years. But isnt there suposed to be a section on the video card? 

Yea dont ask to post my xorg. I am on my PC and my issue is on my eMac.

---

### Post by B_Free on 2009-09-11
Why does roym4 add a Depth number? I think the subsection is understandable, you are just refining the configured "Default Screen". I have read a number of books and forums, all seem to be saying approximately the same thing. But there are differences.
As far as the blank screen, just for the heck of it, do the **command (apple) key and F4** when the curser is blinking. It worked for me.

---

### Post by Exodist on 2009-09-11
> **B_Free said:**
> Why does roym4 add a Depth number? I think the subsection is understandable, you are just refining the configured "Default Screen". I have read a number of books and forums, all seem to be saying approximately the same thing. But there are differences.
As far as the blank screen, just for the heck of it, do the **command (apple) key and F4** when the curser is blinking. It worked for me.

It states the screen color Depth in case the video is higher.

I am not really familiar with Macs, what does Command(AppleKey) F4 do anyway?

I did finally get everything working. I didnt know there was version 9.04 for PPC out yet since its NOT listed on the documentation or in the Apple section of the forums.

---

### Post by B_Free on 2009-09-11
[http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)

[http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

A book told me if the system hangs when starting up, (screen goes black, like you said) press the command+F4 keys. It happened to me, just like yourself. I pressed the command+F4 keys. The system continued and everything was fine.

My system profiler (before I installed Ubuntu) in Mac OSX, had a depth of 32. Would I put 32 or 24?

---

### Post by Exodist on 2009-09-11
> **B_Free said:**
> [http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)

[http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

A book told me if the system hangs when starting up, (screen goes black, like you said) press the command+F4 keys. It happened to me, just like yourself. I pressed the command+F4 keys. The system continued and everything was fine.

My system profiler (before I installed Ubuntu) in Mac OSX, had a depth of 32. Would I put 32 or 24?

Nothing "hangs", The screen was going blank due to a miss configured Xorg.conf in 8.04 and 8.10. It went blank soon as GDM gathered its settings.
I was able to jump to other terms and use the cli without a hitch.

---

