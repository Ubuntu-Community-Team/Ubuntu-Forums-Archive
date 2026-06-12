---
title: "[Guide] Setting Up Tablet PC Screen Rotation"
date: 2013-02-15
forum: Art &amp; Design
---

### Post by ATXChris on 2013-02-15
Hello Ubuntu forums, I'm posting this here because I thought it might be useful to anyone who owns a tablet PC, as sort of an all-in-one guide to get a core function of tablet/laptop hybrids working. This is copy and pasted from my post over on ThinkPad forums (where I made it). Just felt it could be useful here too.

> Hello ladies and gentlemen, this is my way to help the community back in return for helping me. I hope you find it useful and please leave any comments on what to improve and such!

In this guide you will find how to set up screen rotation on ThinkPad tablet/laptops on a Linux distribution. This is a two part guide; first, we will get auto-rotation working and second, we will bind a 90* counter-clock-wise rotation to a key (usually the rotate key on the face of the tablet).

[size=200]_**Part One: Automatic Rotation**_[/size]
A very nice quality-of-life feature of ThinkPad tablets is the automatic screen rotation. When the screen is rotated and folded down, the laptop knows to change the screen orientation... or at least, it should. Now the script below works for Lenovo/IBM, HP, Fujitsu, and Dell tablet hybrids. Below is the link to the LaunchPad webpage for the program:

[Magick Rotation](https://launchpad.net/magick-rotation)

This is a fairly easy to use program, as it has an installer after you extract the .tar.bz file that works on Ubuntu, Fedora, both versions of Linux Mint, and openSUSE. Because it works on Ubuntu, I will venture to say it will run on all (semi) official variants, which are Lubuntu, Xubuntu, Ubuntu Studio, and Kubuntu. However, I only use Xubuntu so I can only confirm it does indeed work on that particular variant. As a note, inside of the .tar.bz, is a file with manual installation instructions, which presumably help you install it on other Linux distributions such as Bodhi Linux.

Here is what the program looks like after it is installed;

[img]http://i1291.photobucket.com/albums/b546/ThinkPad-Artist/MagickRotationSetup_zps824cd266.png[/img]

As you can see, it is very simple. By default, the rotation state is set to right, but I have mine set to inverted. Also by default, Magick Rotation is told to start on computer start. Finally, by default (underneath Advanced Settings) is the command to show CellWriter when the tablet is rotated and hide when it is unrotated. CellWriter is one on screen keyboard that is available through the Ubuntu Software Center. In my limited use, it works pretty well so far. Obviously you can leave these lines but if you don't have CellWriter installed, you computer may pop a notification of calling a program that doesn't exist. Personally, I like it better than OnBoard that comes default on Xubuntu. Plus, the commands already there, so it's easy.

So that was the easy part, now for something that can prove a bit trickier...

[size=200]_**Part Two: 90* CCW Rotation Script**_[/size]
So this simple script is a script that, when used, rotates the screen 90* Counter-Clock-Wise (if ran without swinging the screen) and changes your inputs to act accordingly. So let's get started...

Please Note: Credit for this goes to the Wacom Linux guys over at SourceForge, found here;
[Wacom Linux Pages](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

[size=150]_**Step One: Get Input Names**_[/size]
This first step is very important, because without using your models specific names of the TouchPad, Stylus, and TrackPoint, it WILL NOT FUNCTION. So first thing is to open a terminal and run the following command (If you use any external inputs, such as a Wacom Tablet or Mouse, PLUG THEM IN NOW!):

```
xinput list
```

Which will give you a window like this:

[img]http://i1291.photobucket.com/albums/b546/ThinkPad-Artist/xinputlist_zps2ce32942.png[/img]

[size=150]_**Step Two: Make the Script**_[/size]
Now, keep that open and make a new empty file (Right Click > New Document > Empty File) and copy this script into it (again, thank the Wacom Linux guys!);

```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input devices.

case "$rotation" in
    normal)
    # rotate to the left
    xrandr -o left
    xsetwacom set stylus rotate ccw
    xsetwacom set eraser rotate ccw
    xsetwacom set touch rotate ccw
    ;;
    left)
    # rotate to inverted
    xrandr -o inverted
    xsetwacom set stylus rotate half
    xsetwacom set eraser rotate half
    xsetwacom set touch rotate half
    ;;
    inverted)
    # rotate to the right
    xrandr -o right
    xsetwacom set stylus rotate cw
    xsetwacom set eraser rotate cw
    xsetwacom set touch rotate cw
    ;;
    right)
    # rotate to normal
    xrandr -o normal
    xsetwacom set stylus rotate none
    xsetwacom set eraser rotate none
    xsetwacom set touch rotate none
    ;;
esac
```

Now is where you are gonna fly solo for a little bit. Looking at your xinput list, replace 'stylus', 'eraser' and 'touch' with the NAMES (not id=#'s) of your 'Virtual core pointers' (the first half or so of the list). For example, my file looks like this:

```
#!/bin/sh

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation.

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"

# Using current screen orientation proceed to rotate screen and input devices.

case "$rotation" in
    normal)
    # rotate to the left
    xrandr -o left
    xsetwacom set Wacom Tablet stylus rotate ccw
    xsetwacom set Wacom Tablet eraser rotate ccw
    xsetwacom set TPPS/2 IBM TrackPoint rotate ccw
    xsetwacom set USB OPTICAL MOUSE rotate ccw
    ;;
    left)
    # rotate to inverted
    xrandr -o inverted
    xsetwacom set Wacom Tablet stylus rotate half
    xsetwacom set Wacom Tablet eraser rotate half
    xsetwacom set TPPS/2 IBM TrackPoint rotate half
    xsetwacom set USB OPTICAL MOUSE rotate half
    ;;
    inverted)
    # rotate to the right
    xrandr -o right
    xsetwacom set Wacom Tablet stylus rotate cw
    xsetwacom set Wacom Tablet eraser rotate cw
    xsetwacom set TPPS/2 IBM TrackPoint rotate cw
    xsetwacom set USB OPTICAL MOUSE rotate cw
    ;;
    right)
    # rotate to normal
    xrandr -o normal
    xsetwacom set Wacom Tablet stylus rotate none
    xsetwacom set Wacom Tablet eraser rotate none
    xsetwacom set TPPS/2 IBM TrackPoint rotate none
    xsetwacom set USB OPTICAL MOUSE rotate none
    ;;
esac
```

**Note:** Make note of something here; I've included in mine, 'USB OPTICAL MOUSE'. This is my cheap wired mouse. It should be on your xinput list if you listened to directions and plugged it in.  :P 

[size=150]_**Step Three: Save and Change Permissions of the Script**_[/size]
Now, save this script to somewhere you can find and access it with sudo (preferably, I haven't tested it in a root location). I put mine in ~/usr/share/ and named it rotate. You do not need to append a file type to the end (i.e no .sh) Open a terminal at this location (either Right Click > Open Terminal Here or open a terminal and use the 'cd' command to get there) and run this command to make it executable;

```
sudo chmod +x
```

And you're good to go, just don't double click on it or your screen will rotate without you. If you do and your screen rotates, and easy way to get back is to keep hitting Enter (because the file is highlighted).

[size=150]_**Step Four: Bind the Script**_[/size]
Now to make your keyboard shortcut. Again, this is distribution specific, and may be accomplished with a bit more work from the terminal, but Xubuntu includes a GUI for this. Below is a quick guide for Xubuntu Users, which may help other distributions;

**First, go to Settings Manager and find Keyboard**

[img]http://i1291.photobucket.com/albums/b546/ThinkPad-Artist/Settings_zps72740b61.png[/img]

**Next, click on the tab that says Application Shortcuts and click Add**

[img]http://i1291.photobucket.com/albums/b546/ThinkPad-Artist/ApplicationShortcuts_zpsb565c9fc.png[/img]

**Finally, use the little Open button to find your script file.**

[img]http://i1291.photobucket.com/albums/b546/ThinkPad-Artist/Shortcut_zps5bdd3eb4.png[/img]

And then it will ask for a command. Merely press the button you wish to register to the script (In my case, I pushed the button on my screen bezel). All done!



Thanks for reading guys! Please comment with any suggestions or if you would like another guide to setting up something in Xubuntu or Linux in general!stripstrip

Again, I know each of these guides are available through googling, but perhaps this way, it can be a one stop shop for people who just want it to work. I also have screen shots from my setup included to help people who need visual guides. Enjoy! ):P

---

### Post by Benja1972 on 2013-04-29
Very very nice! That is what I am looking for my ThinkPad Twist. Thank you very much!

---

