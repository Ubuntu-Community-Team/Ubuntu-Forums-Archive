---
title: "[SOLVED] Recovery mode"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by dpwilson on 2008-03-31
What exactly is recovery mode on the boot menu?  I had kubuntu 7.10 installed and run the updates, it asked if I wanted to upgrade and did so.  A message came up saying not to shut down or interrupt or something to that effect.  Well after sitting overnight and nothing happening, I had no other choice, at least  none that I know of to reboot.  Now, it wont boot up to the Kubuntu version.  When I get to the boot screen, it lists recovery mode and I clicked it.  It run through a ton of stuff and finally stopped with the cursor flashing at root or somthing.  

What do I do from there?  IS there any way to get it working again?  Its no real big deal as I have that installed on one hard drive and other ubuntu 7.04, 7.10 and windows installed on others.

Any advice?

---

### Post by Oldsoldier2003 on 2008-03-31
> **dpwilson said:**
> What exactly is recovery mode on the boot menu?  I had kubuntu 7.10 installed and run the updates, it asked if I wanted to upgrade and did so.  A message came up saying not to shut down or interrupt or something to that effect.  Well after sitting overnight and nothing happening, I had no other choice, at least  none that I know of to reboot.  Now, it wont boot up to the Kubuntu version.  When I get to the boot screen, it lists recovery mode and I clicked it.  It run through a ton of stuff and finally stopped with the cursor flashing at root or somthing.  

What do I do from there?  IS there any way to get it working again?  Its no real big deal as I have that installed on one hard drive and other ubuntu 7.04, 7.10 and windows installed on others.

Any advice?

Recovery mode boots you into single user mode as root. You can use this mode to repair your system should something go south. If you let us knw what error messages you recieve when you try to boot normally we can help you out with what you needt o do to recover.

---

### Post by mister_pink on 2008-03-31
Recovery mode doesn't do anything itself as such, it just gives you a command line prompt on a system that won't otherwise boot so you can try and fix it yourself. What happens exactly if you try and boot normally, any error messages or anything?

---

### Post by dpwilson on 2008-03-31
I get no error messages or anything, just a black screen with the cursor blinking.

I am not sure where things went wrong, I downloaded all updates/upgrade files and then as it went to "installing" it just sat there at 0%.  It said it may take several hours so I went to bed and the next morning it was still at 0%.  I hesitantly shut down and when I tried to boot back up, nothing, black screen.  

Its no big deal if its shot, but just wondering if it can be fixed.

---

### Post by dpwilson on 2008-03-31
OK, here is what happens.  I just tried to boot into kubuntu 7.10 and it starts up with the kubuntu and loading this and that and the progress bar moves, then as if its giong to start it goes black and thats all she wrote.  

Any ideas?

---

### Post by dstew on 2008-03-31
Since recovery mode gets you a command line, your basic underlying system is working fine. The problem seems to be with your graphical user interface (the Gnome desktop). You should try to reconfigure the xserver, the software that runs the display.

From a recovery boot, enter on the command line:```
sudo dpkg-reconfigure xserver-xorg
```This gets you a text-based reconfiguration program that goes through the elements of your desktop, like keyboard and display, and lets you set them up again. Answer the questions the best you can (read the explanations). When you get to the display set-up, choose the **vesa** display driver, and a resolution that is not too high. If you know what resolution you actually use, choose that.

After you are done reconfiguring, it will get you back to the command line. Enter```
startx
```to start the xserver, and see if you get a desktop.  If you do, you can try to improve the graphics with some other GUI-based configuration steps. Look for a restricted driver in the Restricted Drivers Manager, and if you have one, install it.

---

### Post by dpwilson on 2008-04-01
> **dstew said:**
> Since recovery mode gets you a command line, your basic underlying system is working fine. The problem seems to be with your graphical user interface (the Gnome desktop). You should try to reconfigure the xserver, the software that runs the display.

From a recovery boot, enter on the command line:```
sudo dpkg-reconfigure xserver-xorg
```This gets you a text-based reconfiguration program that goes through the elements of your desktop, like keyboard and display, and lets you set them up again. Answer the questions the best you can (read the explanations). When you get to the display set-up, choose the **vesa** display driver, and a resolution that is not too high. If you know what resolution you actually use, choose that.

After you are done reconfiguring, it will get you back to the command line. Enter```
startx
```to start the xserver, and see if you get a desktop.  If you do, you can try to improve the graphics with some other GUI-based configuration steps. Look for a restricted driver in the Restricted Drivers Manager, and if you have one, install it.

OK, did that and here is the output after I entered "startx"

Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux MAIN 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:1
2 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http:wwwiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!)notice, (II) informational, 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown,
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  1 05:35:43 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors ab
ove for possible reasons
	(you may have to look at the server log to see warnings)
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error: 
no screens found
X10: fatal IO error 104 (Connection reset by peer) on X server ":0.)"
	after 0 request (0 known processed) with 0 events remaining.
root@MAIN:~#

---

### Post by forrestcupp on 2008-04-01
maybe try booting to recovery and type
```
apt-get install kubuntu-desktop
```
to try finishing whatever it was trying to do when it didn't complete.

---

### Post by dpwilson on 2008-04-01
ran apt-get install kubuntu-desktop and same message as above when trying to boot.

any other ideas?

---

### Post by dstew on 2008-04-01
Please post the output of```
cat /etc/X11/xorg.conf
```

---

### Post by dpwilson on 2008-04-02
cat: /etc/x11/xorg.conf: no such file or directory

---

### Post by kpkeerthi on 2008-04-02
> **dpwilson said:**
> cat: /etc/x11/xorg.conf: no such file or directory

You mistyped the command dstew suggested. Try again and post the content here inside [code] tags.

---

### Post by mister_pink on 2008-04-02
In case you're not seeing it - file names are case sensitive. If you copy+paste command line things then you cant mess up things like that or similar looking letters like I and l !

---

### Post by dpwilson on 2008-04-02
> **mister_pink said:**
> In case you're not seeing it - file names are case sensitive. If you copy+paste command line things then you cant mess up things like that or similar looking letters like I and l !

I forgot about them being case sensitive.  I will try that again this afernoon after work.  Unfortunately, I cant copy/paste since I have to go from windows to check the forum for replies, then boot to kubuntu to try it out.

---

### Post by mister_pink on 2008-04-02
Ah yes, that is a bit of a pain. There are text only based web browsers so you can look things up without rebooting. I think there's one installed by default but I can't remember what its called, but you can install lynx. Its not brilliant but you can do basic browsing.

---

### Post by dpwilson on 2008-04-02
Hope this is what is supposed to look like

```

EndSection
Section "Screen"
Indentifier   "DefaultScreen"
Device         "nVidia Corporation NV34 [GEForce FX 5200]"
Monitor       "L1928NV"
Default Depth    24
Subsection "Display"
                    Modes   "1280x1024"  "1152x864"  "1024x768"  "800x600"  "640x480"
EndSubSection
EndSection
Section "ServerLayout"
  Identifier "DefaultLayout"
  Screen  "DefaultScreen"
  Input Device  "Generic Keyboard"
  Input Device  "Configured Mouse"

# Uncomment if you have a wacom tablet
# Input Device    "Stylus"    "SendCoreEvents"
# Input Device    "Cursor"    "SendCoreEvents"
# Input Device    "Eraser"    "SendCoreEvents"
EndSection

```

---

### Post by dstew on 2008-04-02
That's not the whole thing, is it? There must be more at the top.

Also, to install kubuntu-desktop, you might need to use sudo:```
sudo apt-get install kubuntu-desktop
```If there are pieces that haven't been installed, it will re-start from wherever it left off.

---

### Post by dpwilson on 2008-04-02
Please dont tell me there is more...The only way I know to post it here is to handcopy it, then type it up.  Is there an easier way?  Anyway, that is from the top of the screen.  I wondered if there was more up above that, but how would I get there.  I tried to "arrow" up , but when I clicked the up arrow, it just pasted the command back on the screen that I typed in and the other arrow keys put some funky symbols.  Would "page up" take me there?  I just thought of that so, take it easy on me if so, I had a long day at work and my brain is fried. 
 I will try the sudo apt-get again and see what happens and let ya know.  

Thanks for everyones help so far.

---

### Post by dstew on 2008-04-02
To see the output one page at a time, you can use the **more** command instead of the cat command:```
more /etc/X11/xorg.conf
```You can also copy the file to a floppy disk, and transfer it to another computer. It is just a plain text file. But, I don't want to make you hand copy it all. Just do the **sudo apt-get install kubuntu-desktop** command when you get a chance and let us know what happens.

---

### Post by dpwilson on 2008-04-03
```
sudo apt-get install kubuntu-desktop
```
didnt write it down, but output was something like newest version installed, 0 upgraded, 0 installed or 
something like that and then back to the com. prompt.

My floppy drive didnt last a month and I never replaced it.  Is there a way to copy it to a usb flash drive as a text file?  Unfortunately, I can get on here before work for 20 minutes or so and after work in the evenings when the kids give me a chance so my responses may  be a little slow.

---

### Post by mister_pink on 2008-04-03
If you can see your windows disc in ubuntu you could copy it straight there. Otherwise a flash drive could work. Dont know if theyre automatically mounted in recovery mode, if not youll need to do:
```
cd /media
mkdir flash
fdisk -l
```
Thats a small L at the end there. From that output note which one you think your flash drive is. Probably sdc1. You should be able to guess from the size. Also note the filesystem from the last column. Then do:
```
mount -t FILESYSTEM /dev/sdX1 flash/
cp /etc/X11/xorg.conf flash/

```
Replacing X with the letter you found above and FILESYSTEM with the filesystem (probably "vfat", if the last column of the fdisk output said anything with FAT in it, like FAT16.)

Edit: On second thoughts, all this could be mildly pointless, seeing as it will be a fairly standard file as you did the reconfigure command. Maybe try reinstalling the desktop package. Could take a while: 
```

apt-get --reinstall install kubuntu-desktop

```

---

### Post by dpwilson on 2008-04-05
I think I am giving up on this one.  Can't get things to work and really, not very concerned with it.  I have ubuntu 7.04/7.10 also installed and use them.  Thanks for any help and advice that was given.  I will most likely remove/format the drive and install 8.04 when its released.  Going to post a new problem with my 7.04 that I have been fighting for awhile.

---

