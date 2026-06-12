---
title: "Installation with TV as monitor?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2006-08-06
This might not be possible to do, but I have no access to a monitor at this time so I'm using the S-Video out on my Geforce 4mx to display to my television.

It boots fine from the install CD and goes for a while doing the installation but at a certain point it seems to switch video modes. I can hear the TV change frequencies or warble over to another setting.  Is there anyway to get around this or am I going to have to wait to find a regular monitor?

---

### Post by Monsieur le Comte on 2006-08-06
Oh, and CTRL-ALT-F1 works to get me to a command line.  Thanks!

---

### Post by kebes on 2006-08-06
It is possible to do. What you have to do is modify your "X window video options". To do this, find your "xorg.conf" file, which is probably located at:
/etc/X11/xorg.conf

This file contains all the information for outputting your video mode. It is ignored at the command-line stage, but is invokved when your GUI environment starts up. It can be a bit complicated to set up, but there is plenty of documentation on "xorg.conf", such as:
[http://www.die.net/doc/linux/man/man5/xorg.conf.5.html](http://www.die.net/doc/linux/man/man5/xorg.conf.5.html)

For adding a TV specifically (instead of a monitor), you can check out things like:
[http://en.wikibooks.org/wiki/MythTV/Installing#Configure_TV-out](http://en.wikibooks.org/wiki/MythTV/Installing#Configure_TV-out)

You'll have to do everything from the commandline (using "nano xorg.conf" to edit the file, etc.). Briefly, what you need to do is add something like:

```

Section "Monitor"
    Identifier "Television"
    # D: 34.563 MHz, H: 37.244 kHz, V: 73.897 Hz
    HorizSync   30-68
    VertRefresh 50-120
    Mode "720x480"
         DotClock 34.564
         HTimings 720 752 840 928
         VTimings 480 484 488 504
         Flags "-Hsync" "-Vsync"
    EndMode
EndSection

```

To your "xorg.conf" file. Note that this is for an NTSC television (North America) whereas a european TV would require different settings since it is PAL. The above is just an example: check to make sure that the settings are okay for your TV, as it is possible to damage some equipment with bad values for the sync or refresh.

You would then, later on in "xorg.conf" identify the above monitor as a screen you want to use. So you would add something like:
```

Section "Screen"
        Identifier "TVScreen"
        Device "TVOutCard"
        Monitor "Television"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
                   Depth 24
                   FbBpp 32
                   Modes "720x480"
        EndSubsection
EndSection

```

Note that the line:
Device "TVOutCard"
should be modified to refer to whatever device you are using for TV-Out capabilities. Look elsewhere in your xorg.conf and see what devices are listed.

Finally you need to activate this Screen as being the one you want to use. Modify the appropriate section of "xorg.conf":
```

Section "ServerLayout"
    Identifier "TV Layout"
    Screen "TVScreen"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
EndSection
```

Obviously your file will look a bit different from the one I'm showing. For "ServerLayout" you should only have to change the "Screen" line. Then try to restart the GUI ("startx" from command line, or reboot the computer, or use Ctrl+Alt+F7 to go back to your GUI instance and then Ctrl+Alt+Backspace to restart it), and see if it works.

It will probably take some fiddling to get the TV-out to work properly, but it is possible. Note that TV resolution is really quite low (720X480) compared to normal computer monitors, so you won't be able to "fit" much on screen. It's really not a great way to interact graphically with your computer... but it's better than nothing if you don't have a monitor anywhere.

---

### Post by Monsieur le Comte on 2006-08-06
Now, is it possible to edit this before I do the installation?  I ran it again and it seems to get all the way through the progress bar that shows up and seems to be moving to the x windows system when it goes off (just like you said).

So should I CTRL-ALT-F1 to the command line, edit that file and resume the installation process?  How do I get back to the GUI installer from the CLI?

Thanks for the help!

---

### Post by Monsieur le Comte on 2006-08-06
I just tried the safe video mode of booting from the disc and that works fine.  Is there anything I can throw in to the boot command to specify a certain video mode through the install?


UPDATE:  Ok, so I should have just messed around with it more on my own before asking.  I was able to boot in safe video mode and now I am running the actual installer just fine.

Thanks for your help!  It'll be very useful when I finish the install and get need to set up the monitor!

---

