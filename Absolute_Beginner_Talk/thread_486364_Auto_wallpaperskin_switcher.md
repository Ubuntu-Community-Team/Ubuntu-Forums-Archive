---
title: "Auto wallpaper/skin switcher"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by crav on 2007-06-27
For starters, I'll warn that perhaps that perhaps this thread is a little advanced for the Absolute Beginner Forum.

I'm looking to further customize my desktop. I'm not doing Beryl or anything like that, I just want it to look a little prettier.

What I'm looking to do is have my wallpaper automatically switch every X minutes. When my wallpaper switches, I'd like my conky configuration file to change its colors, to stand out well on the new wallpaper.

My first problem is with the wallpaper. There are two ways I figure the wallpaper is stored in Ubuntu:
1. In Windows, when you set the wallpaper, it copies the file as a bitmap and hides it deep within the Windows files; that way, if the original file gets deleted or moved, the wallpaper will be unaffected.
2. Somewhere in a config file, there's a variable that points out where the desired wallpaper.

If I can get to either this wallpaper file or this config file, I figure I can easily change the wallpaper without going through all the gnome menus.

Once this wallpaper file has been properly changed, changing the conky configis easy, whether by overwriting it, or simply changing the necessary lines.

After these two files have been changed, the appropriate things simply need to be refreshed.


SOOOOO... after all that, anyone know where the wallpaper is stored, and how I can do all this switching?

---

### Post by freecheeseman on 2007-06-28
Your wallpaper settings are visible through gconf-editor under:
/desktop/gnome/background/picture_filename

you should be able to find most color settings by poking around in there.

you could edit it with a script on the command line using gconftool,
look at --help-client

if you can put that in a script and run it whenever you like,
or possibly schedule it.

-freecheeseman

---

### Post by gjtoth on 2007-06-28
Desktop Drapes

---

### Post by crav on 2007-06-28
gjtoth: That doesn't handle all I want, I'm looking to also change my conky config file to update with settings that more appropriately match the new wallpaper.

Based on talking to some people, it looks like a bash script would be the easiest or best way to go. Unfortunately, I don't know much about bash scripting, and the guides I find online want to teach me everything, and I really only need to do a few [should be fairly basic] things.

Here's the basic algorithm for what I'm trying to accomplish, I know, it's simple as heck, but hey, I'm still new at this whole linux thing!

```
Get Uptime
   If Uptime is evenly divisible by 15 minutes:  (ie, times ending in :00, :15, :30, :40)
	Read line 16 of /home/USERNAME/.gconf/desktop/gnome/background/%gconf.xml
	If filename is 1        
		Overwrite line 16 of /home/USERNAME/.gconf/desktop/gnome/background/%gconf.xml with 2
		Overwrite line 54 of /home/USERNAME/.conkyrc with setting 2
	If filename is 2
		Overwrite line 16 of /home/USERNAME/.gconf/desktop/gnome/background/%gconf.xml with 3
		Overwrite line 54 of /home/USERNAME/.conkyrc with setting 3
	...etc...
	Refresh Desktop
```

---

### Post by prince_niceguy on 2007-08-21
> **gjtoth said:**
> Desktop Drapes

Thanks... that worked for me... I was using KDE for long and this was by default. Moved to Gnome after some issues with compiz ...

---

### Post by gregbazar on 2007-09-29
Hope you enjoy this - works great for me.

Alows you to point to a directory via the command line, and have your wallpaper automatically switched every x number of seconds.

I added support for zoom, centered, gradient colors in the background etc, all from the command line.



```

#! /usr/bin/env python

# Original Code from https://www.blogger.com/comment.g?blogID=6924450&postID=112965042778894599
# Updates for added functionality by Greg Bazar 9/29/07 - greg --- at --- ironfish -- dot -- net
#  -- somebody who knows what they are doing should put this in an applet form

from optparse import OptionParser
import os
import sys, string, time
import random

def changeWallpaper(filename):
        cmd = string.join(["gconftool -s /desktop/gnome/background/picture_filename -t string \"",filename,"\""],'')
        os.system(cmd) # execute system command

# Parse commandline arguments
parser = OptionParser()
parser.add_option("-f", "--folder", dest="folder", help="use wallpapers from FOLDER", metavar="FOLDER")
parser.add_option("-i", "--interval", type="float", dest="interval", default=300, help="time interval in seconds", metavar="INTERVAL")
parser.add_option("-m", "--mode", type="string", dest="wallpaper_mode", default="centered", help="Wallpaper can be displayed in several modes: none, wallpaper, centered, scaled, stretched, zoom")
parser.add_option("-d", "--default", dest="default_image", help="specify default image when program is killed", metavar="FILENAME", default="nothing.gif")
parser.add_option("-c", "--bg-color-mode", dest="bg_color_mode", default="solid", help="Background Color Options:  solid, hg (horizontal gradient, vg (vertical gradient)",metavar="COLOR_MODE")

(options, args) = parser.parse_args()

# Validate for presence of valid folder
if options.folder is None:
        raise ValueError, "No valid folder specified"
if not(os.path.isdir(options.folder)):
        raise ValueError, "The folder specified is not valid"

# Set Background Color Mode
if options.bg_color_mode == "vg":
	cmd = "gconftool -s /desktop/gnome/background/color_shading_type -t string \"vertical-gradient\""
	os.system(cmd) # execute system command

elif options.bg_color_mode == "hg":
	cmd = "gconftool -s /desktop/gnome/background/color_shading_type -t string \"horizontal-gradient\""
	os.system(cmd) # execute system command

else:
	cmd = "gconftool -s /desktop/gnome/background/color_shading_type -t string \"solid\""
	os.system(cmd) # execute system command




# Set wallpaper display mode
cmd = string.join(["gconftool -s /desktop/gnome/background/picture_options -t string \"", options.wallpaper_mode ,"\""],'')
os.system(cmd) # execute system command

# Make list of images
imagefilelist = [filename for filename in os.listdir(options.folder)
                if (filename.lower().endswith("jpg")
                or filename.lower().endswith("png")
                or filename.lower().endswith("gif"))]
imagefilelist = [string.join([os.path.normpath(options.folder),imgFile],"/") for imgFile in imagefilelist]

# Validate for presence of images
if (len(imagefilelist) == 0):
        raise ValueError, "Folder does not contain any image files"

count=0 #init index
random.shuffle(imagefilelist) #randomize wallpaper order
try:
        while (True):
                if (count < len(imagefilelist) -1):
                        count = count + 1
                else:
                        count = 0
                time.sleep(options.interval)
                changeWallpaper(imagefilelist[count])


except KeyboardInterrupt:
       print options.default_image
       cmd = string.join(["gconftool -s /desktop/gnome/background/picture_filename -t string \"", options.default_image ,"\""],'')
       os.system(cmd) # execute system command
       pass

```

---

### Post by prince_niceguy on 2007-09-29
install destkop drapes or alternates select pcitures folder as the wall paper... and make a link to other wallpaper folders in picture folder and it will switch automatically...

or install kde and use kde. it has feature of using wallpaper and also specify the directory from which to pick it up..

---

### Post by brundlelinux on 2007-10-14
Or try Wallpaper Tray.  Never used Drapes, but it seems that Tray and Drapes do the same thing.

---

### Post by happy-and-lost on 2007-10-14
*sudo apt-get install wallpaper-tray* ;)

---

### Post by Trymic on 2007-12-27
I am using drapes and i am very satisfied

---

