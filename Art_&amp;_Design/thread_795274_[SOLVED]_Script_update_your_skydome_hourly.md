---
title: "[SOLVED] Script: update your skydome hourly"
date: 2008-05-15
forum: Art &amp; Design
---

### Post by chewearn on 2008-05-15
I run my desktop with compiz fusion cube set at 100% transparency.  I put a nice picture as the skydome, which serve as the wallpaper in this set-up.

However, I got tired of looking at the same old desktop background all the time, and I'm too lazy to change it, so I wrote a bash script that update the skydome hourly.

Tweak the first part of the script to match your pictures and files location.

```

#!/bin/bash

# -------- Set the following variables to your own config ----------------

# Note: filenames must be 00, 01, ..., 12; 00 is midnight, 12 is noon
FILEEXT=.jpg
FILEPATH=$HOME/arts/skydome/

# ------------------------------------------------------------------------


GCONFPATH=/apps/compiz/plugins/cube/screen0/options/skydome_image

sleep 30

while [ 1 ]; do
    HOUR=`date +"%H"`

    # convert 24 hours time to "hours to/from noon"
    if [ $HOUR -gt '12' ]; then
        HOUR1=$[24-$HOUR]
        if [ $HOUR1 -lt '10' ]; then
            HOUR1=0$HOUR1
        fi
    else
        HOUR1=$HOUR
    fi

    gconftool-2 -s -t string $GCONFPATH $FILEPATH$HOUR1$FILEEXT

    # sleep until next hour
    while [ 1 ]; do
        MIN=$[60-$[`date +"%M"`]]m
        HOUR1=`date +"%H"`
        if [ $HOUR -ne $HOUR1 ]; then
            break;
        fi

        sleep $MIN
    done
done


```Here is a set of pictures:
[http://chew4097.googlepages.com/home](http://chew4097.googlepages.com/home)

Note:
The original pictures are png, but googlepages converted it to jpg. :(
It's not ground breaking, but I'm not an artist either. :mrgreen:

If you find bug please tell me.
If you created your own set of pictures, I would love to download them. :mrgreen:

.

---

### Post by dustoulis on 2010-04-29
Hello there. I was searching throughout google for a plugin or something that would change automatically the skydome. Obviously you were trying the same thing and therefore u created the script. Unfortunatelly im a newbie on Linux and i would really apreciate a guide on how i can make this script work for me, cause i have no idea. And which value i need to change to make it change in different period of time? 

Thnx.

---

### Post by chewearn on 2010-04-30
hi dustoulis
Mmm, has it been two years since I wrote this script?  How time flies.

When I wrote this script I have very limited knowledge of Linux.  The timing for changing the skydome is hardcoded and I used "sleep" command to set the interval.  That's not a good solution as it turned out.  A better solution is to use built-in Linux anacron function (anacron is this is similar to the Scheduler in Windows).

By default, anacron is accessed from the command line.  But a GUI is available to be installed separately, called the "gnome-schedule".  You can find this application via the Synaptic Package Manager.  Using gnome-schedule, it should be self-explanatory how to set-up to run a recurring task.

As to the task itself, you will still need a script (but should be simpler that the one I had previously, because there is no need to fiddle with the timing).  Here is a sample, bearing in mind I hacked this out in 10 minutes without testing. :mrgreen:

```

#!/bin/bash

# -------- Set the following variables to your own config ----------------

# Note: filenames must be 00, 01, ..., 12; 00 is midnight, 12 is noon
FILEEXT=.jpg
FILEPATH=$HOME/arts/skydome/

# ------------------------------------------------------------------------

GCONFPATH=/apps/compiz/plugins/cube/screen0/options/skydome_image

HOUR=`date +"%H"`

# convert 24 hours time to "hours to/from noon"
if [ $HOUR -gt '12' ]; then
    HOUR1=$[24-$HOUR]
    if [ $HOUR1 -lt '10' ]; then
            HOUR1=0$HOUR1
    fi
else
    HOUR1=$HOUR
fi

gconftool-2 -s -t string $GCONFPATH $FILEPATH$HOUR1$FILEEXT

```Copy/paste the script to a text file, save the file somewhere out of the way (e.g. "$HOME/bin").  Set the executable bit for the file, then set the task to run recurrently.

---

### Post by r0g on 2012-10-21
Hi, sorry to revive a long dead thread but it helped me in writing the following script that lets you...

1) Step forwards and backwards through your skydome folder (next/last)
2) Set a random skydome
3) Set the latest image
4) Delete an image from the skydome folder and replace it with the next one.

Hope someone finds this useful,

Cheers,

Roger

:guitar:

```

#!/usr/bin/python
# newsky.py - skydome image manager/changer for compiz cube under gnome
# v0.1, (c)2012 Roger Heathcote, GPL2 licensed, bugs etc to opensource@technicalbloke.com
# Usage newsky.py [latest(default)|next|last|random|kill]

# Edit these settings to suit...

skydome_folder = "/home/yourname/pictures/skydomes"
patterns = ["*.jpeg", "*.jpg", "*.png"]
mode = "latest"

# Don't edit below this line unless you really know what you are doing!...

import os, sys, code, glob, string, random, subprocess

current_image = None

# If argument is specified set mode to that
if sys.argv[1:2]:
    mode = sys.argv[1]

# Grab lsit of picture file names from skydome folder
pictures = []
for pattern in patterns:
    pictures = pictures + glob.glob( skydome_folder + os.sep + pattern )

if mode == "latest":
    current_image = max( (os.stat(x)[9], x) for x in pictures )[1]

if mode == "random":
    current_image = random.choice( pictures )

# Note next and prev are in OS order, not sorted by date. Kill removes current file and loads the next one.
if mode == "next" or mode == "prev" or mode == "kill":

    # Retreive current image file path from gconf
    if "check_output" in dir( subprocess ): # new in 2.7
        current_image = subprocess.check_output(["gconftool-2", "-g", "/apps/compiz/plugins/cube/screen0/options/skydome_image"]).strip()
    else: # for 2.6 and older - yuck!
        current_image = subprocess.Popen(["gconftool-2", "-g", "/apps/compiz/plugins/cube/screen0/options/skydome_image"], stdout=subprocess.PIPE)
        current_image = current_image.communicate()[0].strip()

    # Process argument
    try:
        idx = pictures.index( current_image )
        if mode == "kill":
            os.remove( current_image )
            mode = "next"
        if mode == "next":
            idx = idx + 1
            if idx >= len( pictures ): idx = 0
        if mode == "prev":
            idx = idx - 1
            if idx < 0: idx = len( pictures ) - 1
        current_image = pictures[idx]
    except IndexError:
        print "Current pic not in skydomes folder, not changing:", current_image

# Change image or fail
if current_image:
    subprocess.Popen(["gconftool-2", "-s", "-t", "string", "/apps/compiz/plugins/cube/screen0/options/skydome_image" , current_image])
else:
    print "Fail. Valid options are: latest, random, next, prev, kill"
```

---

### Post by nothingspecial on 2012-10-23
Old thread.

Closed.

---

