---
title: "Mac Mini resolution out of range at grub and desktop enviroment"
date: 2020-07-12
forum: Apple Hardware Users
---

### Post by viarippa11 on 2020-07-12
Hi, I have a trouble with a computer where I installed Ubuntu 20.04, which doesn't recognize my display properly. I managed to set a proper resolution adding following xrandr commands to my .profile file:

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr --addmode HDMI-3 1600x900_60.00
xrandr --output HDMI-3 --mode 1600x900_60.00
```

Now I'd like at least to set proper resolution to gnome, in order to correctly display the login screen (at the moment I have just one user with automatic access just to set things right, but I'm planning to add two more user each with its password). I edited /etc/gdm3/Init/default but nothing changed, I have a message on my monitor saying "out of range" resolution. I also copied my ~/.config/monitors.xlm to /var/lib/gdm3/.config folder but again, with no result

Plus, I'd like to be able to see the grub menu, even in a lower than native resolution, but editing the config file and setting the GRUB_GFXMODE and GRUB_GFXPAYLOAD variables gave no results. 

It seems that the computer believes that the correct output should be 1920x1080, but it's obviously wrong because maximum resolution is 1600x900. I'm suspecting that it could have something to do with the framebuffer and some kernel module but I'm not that skilled to mess with those things. 

How can I troubleshoot this problem? Any help is much appreciated.

---

### Post by oldfred on 2020-07-13
You may have to install read-edid.
Monitor EDID
sudo get-edid | parse-edid
[http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor](http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor)

What brand/model system?
What video card/chip?
What monitor, although above command should show details.

---

### Post by viarippa11 on 2020-07-20
Hi fred, thank you for your reply and sorry me for the late answer.
Answering your questions:
- System is a Mac Mini
- Video card is integrated Intel graphics:
```
description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
```
- Monitor is an HP model 2009v

I tried to install the utility you suggested me and the output was:
```
Section "Monitor"
    Identifier "HP 2009"
    ModelName "HP 2009"
    VendorName "HWP"
    # Monitor Manufactured week 38 of 2009
    # EDID version 1.3
    # Digital Display
    DisplaySize 440 250
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 24-85
    VertRefresh 48-76
    # Maximum pixel clock is 150MHz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 248x155, 60Hz

    #Extension block found. Parsing...
    Modeline     "Mode 12" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 1" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 2" 
    Modeline     "Mode 3" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 4" 
    Modeline     "Mode 5" 
    Modeline     "Mode 6" 
    Modeline     "Mode 7" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 8" 
    Modeline     "Mode 9" 
    Modeline     "Mode 10" 
    Modeline     "Mode 11" 
    Option "PreferredMode" "Mode 12"
EndSection


```

But I don't know at all what does this command do and how it can help solving my problem. What should I do now?

---

### Post by oldfred on 2020-07-20
It says it sees your monitor.
And Intel video should just work.

But Apple Mac are different.
Moving to Apple subforum.

I saved some old threads, do not have much that is new. But do not know details of Macs.

[SOLVED] Video performance of Ubuntu 16.04 on 2007 Mac Mini 2,1 (Intel Integrated 945GM/GMS)
[https://ubuntuforums.org/showthread.php?t=2349732](https://ubuntuforums.org/showthread.php?t=2349732)
Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel)
[https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767)
Mac Mini 
[http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/)
[http://askubuntu.com/questions/563401/efi-boot-ubuntu-14-04-on-a-mac-without-refind](http://askubuntu.com/questions/563401/efi-boot-ubuntu-14-04-on-a-mac-without-refind)
[http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890](http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
[http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac](http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac lpost by  trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)

---

### Post by viarippa11 on 2020-08-06
Hi oldfred, thank you for your kind reply and sorry for my late answer. If you need further details about this kind of mac, it's this one:
[https://support.apple.com/kb/SP632?locale=en_US](https://support.apple.com/kb/SP632?locale=en_US)
I browsed the links you posted but unfortunately I didn't find anything useful....

---

### Post by oldfred on 2020-08-06
Do not know Mac, and those links are about all I can help with. 
Hopefully someone with Mac will respond.  

You can bump after 12 hours to move thread up and then those in different time zones may see it.

---

### Post by gsahli on 2020-08-07
Have you tried editing grub config file and modifying GRUB_CMDLINE_LINUX to add vga=xxx parameter? Plus the changes you mentioned above.
Look here:
[https://linuxhint.com/set_screen_resolution_linux_kernel_boot/](https://linuxhint.com/set_screen_resolution_linux_kernel_boot/)

and don't forget to run sudo update-grub after changes (sorry - if this is what you did before)

---

### Post by viarippa11 on 2020-08-09
hi @gsahli, thank you for your message. I already read the article you posted but the very strange thing is that if I boot with another monitor (my LCD TV) and then switch the video cable to my PC monitor (the HP one), when i get to the console it looks like (when I run the vbeinfo command) the only supported resolution is 1920x1080, which is actually not supported by the HP monitor (max res is 1600x900). If I keep the video cable connected to the TV, instead, grub console says the only one supported video resolution is 1360x768, which is of course supported since my television is a full HD certified one. That's very weird and I don't know how could I force with some low level command any resolution (even lower than 1600x900) which could be supported by my HP monitor....
This is for the grub part. When comes the time for gdm3, instead, I am sure that I can be able to force the 1600x900 resolution since with xrandr commands I managed to set a proper resolution in the user session. The only thing I am missing now is setting 1600x900 resolution at the login screen, which means editing some global configuration file (which is unknown to me at the moment)

---

### Post by oldfred on 2020-08-09
If you look at grub.cfg it has several places where video or font are set.
> function load_video 
if loadfont $font ; then
  set gfxmode=auto

And you set gfxmode in /etc/default/grub

> # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


You can uncomment the gfxmode and change to the X by Y setting that you want.
Then
sudo update grub.

---

### Post by viarippa11 on 2020-08-09
Hi oldfred, I know that parameter of the grub config file and I already tried setting several video resolution, including 640x480, 800x600 and 1024x768 but none of them has worked (of course every time I updated grub via the sudo update-grub command). I'm wondering if it exists another way beyond setting the GRUB_GFXMODE parameter to set the video resolution. 

In order to summarize the current situation, at the moment my mac behaves like this:
- Mac powers on, boot apple chime sound at efi boot: screen says resolution out of range
- grub menu: resolution is out of range
- ubuntu startup & splash screen: resolution is out of range
- ubuntu login screen: resolution is out of range
- ubuntu user session (I have just one user with auto login): resolution is correctly set at 1600x900 via xrandr commands added to the gdm3 config file

---

### Post by oldfred on 2020-08-09
From grub menu use commands to get to grub's terminal and run this. Grub may not see same video as system.

vbeinfo

Then uncomment gfxmode and change to one of values shown by command above.

---

### Post by viarippa11 on 2020-08-09
Hi oldfred, I already tried that command in the Grub console. Situation is as follows:
- if I use my lcd TV as a monitor the only one resolution that seems to be supported is 1360x768
-if I boot using the HP monitor then switch the video cable to the lcd TV (since it's impossible to have video output using the HP monitor) the only one resolution displayed is 1920x1080, which is (as said) unsupported by the HP monitor (official specs say that maximum resolution is 1600x900)
...does this mean that I'm screwed and there is no solution to my problem, or the only possible solution is to buy a new monitor? :(
(I hope that what I've written is understandable.. Sorry me but I'm not a native English speaker...)

---

### Post by oldfred on 2020-08-09
It sounds like it is defaulting to 1920x1080, and then your monitor does not work as you posted originally.

But that is more the video driver settings. And I thought grub tried to use the system default unless you reset with gfxmode setting in grub.

Cannot really help, as do not know Mac.

---

### Post by viarippa11 on 2020-08-10
That's exactly what happens: computer believes the right monitor resolution is 1920x1080, but this is not supported by the monitor. That's really weird. Any case, thank you very much for your effort.

---

### Post by viarippa11 on 2020-08-23
After another weekend of testing and googling, I was wondering if perhaps this discussion couldn't be moved to another section, such as some hardware or video section. I believe this issue is not something that has to do with apple architechture, rather than correctly setting xorg and/or gdm3 configuration. This mac is very similar to a standard desktop PC: CPU, chipset and graphics are from Intel, the RAM is the same mounted on any IBM compatible machine and it mounts a standard SATA 2,5'' hard drive...

I tried to edit xorg.conf and a bunch of other configuration files but computer still defaults to 1920x1080. I think this issue is somewhat related to framebuffer, though I'm not that skilled to know how this is related to the display server. If I issue sudo fbset, the output is:

```
mode "1920x1080"
    geometry 1920 1080 1920 1080 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

```

I tried to run this command on another PC that works and the output is the right screen resolution.
[FONT=arial]
Furthermore, this ([https://pastebin.com/fY70UZh3](https://pastebin.com/fY70UZh3)) is the content of[/FONT] ~/.local/share/xorg/Xorg.0.log and, as far as I know, it seems that 1920x1080 is autodetected for some reason, even if it doesn't work. Obviously X chooses the highest possible but I don't know how to avoid it.[FONT=arial][/FONT]

---

