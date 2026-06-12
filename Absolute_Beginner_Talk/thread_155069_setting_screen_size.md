---
title: "setting screen size"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by obzone on 2006-04-04
I see there are threads about this but I can't get anywhere:

My system is quite old and the installation has given an 800x600 sized screen which is useless.
I want to reset it to 1024x768?  or even 1280x720 but don't know how to. 

It seems first I have to be 'root' or 'su' but I don't know how to do that.
Then I have to reconfigure the xserver.

Where can I find information as to how to do that?
Tim

---

### Post by johnnymac on 2006-04-04
The video card may not let you do 1024x768...but if you must try do this from a terminal:

First, make a backup of your xorg.conf file
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg_bk

```

Second, edit your xorg.conf file.
```

sudo gedit /etc/X11/xorg.conf

```

Third, look for a section called Screen, you'll see a bunch of display modes there and add your display mode (1024x768) along with the rest of them.  Something like this:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

Lastly save the file and restart your xserver by doing CTRL+ALT+BACKSPACE

Now, when it comes back and you log in...if you don't have 1024x768 resolution your video card can't do it.

GL

---

### Post by obzone on 2006-04-04
I tried changing the xorg.conf file. It now has the 1024 resolution option listed but if I go into System/preferences/screen resolution it still gives me the same option, 800, and 640

The system is dual boot and the windows 98SE boot works at 1024 resolution
I did have a 17in CRT screen but now have a 15in wide screen which works with windows.

Any suggestions or is that it?
Tim

---

### Post by johnnymac on 2006-04-04
Is your screen resolution 1024x768 now?  If it isn't, make sure you restart xserver or reboot your system.  This time if it doesn't come up in 1024x768 look here 

```
gedit /var/log/Xorg.0.log
```

And look to see if you have any errors near the bottom.

If none of this works, you can run this (make sure you kill your Xserver first by CTRL+ALT+BACKSPACE (do it until you get a terminal and no GUI)
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

The above will reconfigure your xorg and should give you an option to select default resolution.

GL

---

### Post by obzone on 2006-04-04
Thanks for the options
The log gives various Trident setting from 640x480 to 1280x1024
It then lists 'not using default mode' with various errors of  bad mode clock, vrefresh out of range. The 1024x768 error is bad mode clock/interlace/doublescan 

sudo dpkg-reconfigure -phigh xserver-xorg

On entering the command line you gave me gives a warning:
overwriting possibly-customised configurations file
I rebooted and went into Screen Resolution and it gave me a load of options.
I set 1024x768 and 1280x768 and they both worked

Thanks for all your help and suggestions
Tim

---

