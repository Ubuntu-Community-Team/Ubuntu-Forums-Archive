---
title: "MacBook Pro Display Problems in Gutsy"
date: 2007-09-28
forum: Apple Intel Users
---

### Post by E Gardner on 2007-09-28
Hello-

I just installed the beta version of 7.10 and have a problem. I have a 1st generation MacBook Pro with an ATI x1600 card. Upon a clean install, after using the new tools to install the restricted fglrx driver, the display looks crisp and clear. But as soon as I restart/log out and return to Ubuntu, the resolution is shot and I can't figure out how to get it set properly. In the new "screen and graphics" manager, I cannot find the option to get 1440x900 resolution, even when I select for "model" the entry "LCD 1440x900". Every time I return to the screen/graphics manager the model resets to "plug and play" and I cannot get it to change.

This is a big problem - as I type this I have trouble reading the text. Please help!

---

### Post by cyberdork33 on 2007-09-28
> **E Gardner said:**
> Hello-

I just installed the beta version of 7.10 and have a problem. I have a 1st generation MacBook Pro with an ATI x1600 card. Upon a clean install, after using the new tools to install the restricted fglrx driver, the display looks crisp and clear. But as soon as I restart/log out and return to Ubuntu, the resolution is shot and I can't figure out how to get it set properly. In the new "screen and graphics" manager, I cannot find the option to get 1440x900 resolution, even when I select for "model" the entry "LCD 1440x900". Every time I return to the screen/graphics manager the model resets to "plug and play" and I cannot get it to change.

There have been a few complaints about the new autodetection stuff built into parts of the updated xorg. (You are lucky to have a screen at all! Some machines just get a black screen).

can you give the output of:
```
xrandr -d :0 --verbose
```

---

### Post by E Gardner on 2007-09-28
Okay, here is the output. I was able to set the resolution to "1400x1050" prior to this, which is the closest I could find to my screen. But even that doesn't seem to be what I'm actually getting; it's like the x-output is way too big for my monitor to fit all at once, and rather distorted as well.

Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1050
default connected 1400x1050+0+0 (0x89) normal (normal) 0mm x 0mm
        Identifier: 0x7f
        Timestamp:  1289104684
        Subpixel:   horizontal rgb
        Clones:    
        CRTC:       0
        CRTCs:      0
  1152x864 (0x80)   59.7MHz
        h: width  1152 start    0 end    0 total 1152 skew    0 clock   51.8KHz
        v: height  864 start    0 end    0 total  864           clock   60.0Hz
  1024x768 (0x81)   47.2MHz
        h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.1KHz
        v: height  768 start    0 end    0 total  768           clock   60.0Hz
  800x600 (0x82)   28.8MHz
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.0KHz
        v: height  600 start    0 end    0 total  600           clock   60.0Hz
  640x480 (0x83)   18.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz
  640x400 (0x84)   15.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   24.0KHz
        v: height  400 start    0 end    0 total  400           clock   60.0Hz
  512x384 (0x85)   11.8MHz
        h: width   512 start    0 end    0 total  512 skew    0 clock   23.0KHz
        v: height  384 start    0 end    0 total  384           clock   60.0Hz
  400x300 (0x86)    7.2MHz
        h: width   400 start    0 end    0 total  400 skew    0 clock   18.0KHz
        v: height  300 start    0 end    0 total  300           clock   60.0Hz
  320x240 (0x87)    4.6MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   14.4KHz
        v: height  240 start    0 end    0 total  240           clock   60.0Hz
  320x200 (0x88)    3.8MHz
        h: width   320 start    0 end    0 total  320 skew    0 clock   12.0KHz
        v: height  200 start    0 end    0 total  200           clock   60.0Hz
  1400x1050 (0x89)   88.2MHz
        h: width  1400 start    0 end    0 total 1400 skew    0 clock   63.0KHz
        v: height 1050 start    0 end    0 total 1050           clock   60.0Hz

---

### Post by cyberdork33 on 2007-09-28
The highest resolution that it is saying the monitor can support is 1400 x 1050. (which it also says is the currently set mode.

> it's like the x-output is way too big for my monitor to fit all at once what exactly do you mean by that? How is it distorted... does it look squished in the vertical direction? I do not have a Macbook Pro, so I am unsure of the native resolution of the screen. What is the highest resolution you can use in OSX?

I will look into some info as I think you can define a new mode with xrandr, in the meantime, you might want to look for an already filed bug report, or start a new one and try to add that xrandr output from when it is working correctly, and when it is not...

---

### Post by voided3 on 2007-09-28
All 15" MBPs have a 1440x900 native resolution.

---

### Post by cyberdork33 on 2007-09-28
From 'man xrandr':
> --newmode <name> mode
New modelines can be added to the server and then associated with outputs.  This option does the former. The mode is specified using the ModeLine syntax for  xorg.conf:  hdisp  hsyncstart hsyncend htotal vdisp vsyncstart vsyncend vtotal flags. flags can be zero or more of +HSync, -HSync, +VSync, -VSync, Interlace, DoubleScan, CSync, +CSync, -CSync.It seems that you can add to the available modes for an output, but you need to have the correct full modeline to do so. I will look around to see if I can find it. If we can get the correct modeline, then I can give you the commands to fix it, but you will probably have to use them everytime you start xorg since everything resets each time you restart. It will still be wise to file a bug report as this could be considered a High priority bug for Gutsy.

EDIT: Ok, let's try this. I found this modeline several times for a 15" Macbook Pro...
```
xrandr -d :0 --newmode "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
```Now you should see 1440x900 available in your xrandr query command:
```
xrandr -d :0 -q --verbose
```Note the Screen Identifer (It shows as 0x7f in your output above, but double check this after adding the new mode), and note the identifier for the added mode (this is a value in parenthesis similar to the screen identifier). Then you issue the command:
```
xrandr -d :0 --output *screen_identifier* --mode *mode_identifier*
```As an example, from your previous output, if I wanted to change to the 800x600 resolution, the full command would be:
```
xrandr -d :0 --output 0x7f --mode 0x82
```

I hope this works for you.

---

### Post by E Gardner on 2007-09-28
Thanks for the quick response. I will test this out and post my results. I would post a bug report, but I am afraid that I don't even know the proper terminology to correctly describe what the problems are...

---

### Post by cyberdork33 on 2007-09-28
> **E Gardner said:**
> Thanks for the quick response. I will test this out and post my results. I would post a bug report, but I am afraid that I don't even know the proper terminology to correctly describe what the problems are...

It's not that hard, just describe what the problem is the best you can, what you expected to happen, what hardware you have, etc. It is better to have something other than nothing. You can post the output of things such as the xrandr query (before adding your custom mode). You can make the output of such a command go to a text file like this:
```
xrandr -d :0 -q --verbose > xrandroutput.txt
```
They may ask you for the output of other things too.

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

We have a similar issue on older radeon hardware right now (using the open source ati driver). You can look at it and see what we have done as your would be a similar problem.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716)

---

### Post by E Gardner on 2007-09-28
Okay, I have yet to try the terminal commands posted above, but I have had some success playing with the options in the GUI.

Before, when I went to the screen and graphics preferences manager, I could select "LCD Panel 1440x900" under the "model" setting, but I was unable to then find the corresponding resolution in the "resolution" pull-down menu.

I set this as the display anyway, and restarted the computer. Upon returning to the screen and graphics preferences, I was now able to find an entry for 1440x900 (although the screen was currently set, for some reason, at 2048x1536), and was able to get the resolution correct.

Now when I first start Ubuntu, the login screen still looks as though it were set at 2048x1536 or some similarly large size (I can't see everything I should be able to on the screen at once). When I log in, everything is oversized for a moment, but then after a second the display automatically reformats for the correct resolution (1440x900) and everything is usable. So I guess this is some kind of bug? I will see if I can post the relevant section of xorg.conf and maybe people who understand it will have an idea of what is going on.

---

### Post by cyberdork33 on 2007-09-28
Ok, I might have a better fix then...

In your xorg.conf, you may have a virtual line, change it to the largest resolution you want.
```
**Virtual   1440 900
```**

---

