---
title: "installed camE where is * Options in ~/.camErc ?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by uncreative on 2006-09-21
I can't find * Options in ~/.camErc anywhere -- know where that is?

---

### Post by AndyCooll on 2006-09-21
This refers to a configuration file that is in your home folder. In the command line the "~" refers to your home folder and the "." (dot) folder refers to a configuration file/folder that is hidden by default.

If you open up your home folder using the folder browser and then press CTRL+H these files and folders will appear.

:cool:

---

### Post by uncreative on 2006-09-21
I appreciate the response Andy, but when I hit Ctrl+H in my home folder (ie home/mike) I see a bunch of files with . int he front, but none that pertain to camE

Could they be anyplace else?

---

### Post by jcinmd on 2007-12-24
Below is my .camErc file with my comments after getting it to work well. I hope it helps you. I do like this application. --JC:

## --------------------------------------------------------------------
## My (user) 12/2007 comments prefaced with 2 hashes: ##
## I have Ubuntu 7.10 & Logitech 4000 Cam
##
## After installing, in the root terminal window, type: camE -help
## As root, I start my camE by typing: camE -c .camErc
## I don't know of a better way to stop it & reload the
## config file: '.camErc' besides using the BLOCKCAM/BLOCKUPLOAD
## or killing the process.
## The file you are reading didn't appear on my system after 
## installing camE so I got it from here: 
##     [http://www.enlightenment.org/viewvc/misc/camE/](http://www.enlightenment.org/viewvc/misc/camE/)
## I put it in the default dir of the user I run this as.
## I got the req'd log file name & info file name from reading this file.
## 0 is no, 1 is yes
## --------------------------------------------------------------------
[ftp]
host = ftp.hostgoeshere.net
user = userloginhere
pass = userpswdhere
dir  = /home/public/webcam
##Use something more secure though.
# where should the file end up? Also, this extension determines the file
# type the image is saved as. Try image.png for a png.
file = came.jpg
# camE uploads to a temp file, and moves it across when done
# this way people don't view half-uploaded images
## This is a nice feature
tmp  = uploading.jpg
# keep the connection open (1) or reopen it for each shot (0)
keepalive = 1
# do passive ftp?
## mine didn't work with passive so I set it at 0
passive = 0
#an interface to use for non-passive ftp.  use "-" to let libcurl choose, or
#use a real interface name.  (libcurl often chooses incorrectly)
## I still don't know what this means so I left it at the default
interface = -
# ftp debugging? (noisy)
## Shows a lots of status msgs for each upload in the terminal window
## ...I set at 1 until I'm satisfied my settings work well
debug = 1
# 
# Actually do the upload? If do = 0, just take and archive pics.
# 
do = 1
# Some servers require us to explicitly delete the previous image
# In that case, enable this option
## mine didn't work unless I did this
delete_first = 1
##delete_first = 0
# Determines how many shots are taken before an image is uploaded.
# (1 == every picture is uploaded, 10 would be every 10th image)
# (Defaults to 1 if not present)
upload_every = 1

# you can set ftp->do to 0 above and use scp instead - you still need
# the dir, file and tmp settings in the ftp section for this to work.
# scp also honors the upload_every setting from the ftp section, and
# will also default to a value of 1 if not present.

[scp]
# target = user@host
## ---------------------------------------------------------------
[grab]
# use 
##This command found my device: find /dev -name video*
##...it was the first one listed
device = /dev/video0
##I have a Logitech 4000 Pro - actually a Phillips chip
##so I had to get drivers for it specifically:
##Philips PWC-chip-based webcams
##Logitech 3000 and 4000 Pro, Notebook Pro, and Zoom
##[http://www.linux.com/base/ldp/howto/Webcam-HOWTO/hardware.html](http://www.linux.com/base/ldp/howto/Webcam-HOWTO/hardware.html)
##This command shows cam id: lsusb

# store temp image on local machine
temp_file = /tmp/came.jpg
# lag reduction, takes 5 shots, discards the first 4, thus clearing mmap
# buffers
## I set mine to 0
lag_reduce = 0
#lag_reduce = 5
# This goes at the bottom left, with the message from "infofile" appended.
# It is run through strftime, so date vars are expanded.
## I customized my date/time
text   = %m/%d/%Y %H:%M:%S %Z - 
width  = 320
height = 240
# delay between uploading one shot and starting the next
## mine set at 15 for 15 secs
delay  = 15
# do we want to correct the delay for a slow connect?
# (keeps the perpetually updating clients in sync)
correct = 1
# scale image resolution dynamically based on bandwidth?
# percentage of the delay to spend uploading the image,
# 100 disables, useful values are < 40
percent = 100

########################################################
# PWC specific features (only for philps cams right now)

# framerate of cam capture, lower fps -> less grainy image, more chance or
# blurred motion
#framerate = 5
## 10 seems to show less grain
framerate = 10

# image settings (0-100)
colour = 50
brightness = 50
contrast = 50
hue = 50
whiteness = 50

# White balance mode
# can be "auto", "indoor", "outdoor", "fluorescent" or "manual"
pwc_wb_mode = auto
# if _mode is set to manual, these two controls affect the balance
# (0-100)
pwc_wb_red = 50
pwc_wb_blue = 50

# Backlight compensation mode
# switched off, when set to 0
## 1 seems best
pwc_backlight_mode = 1
#pwc_backlight_mode = 1
########################################################
# where to log activity. comment out this line to disable logging
logfile = /home/itsme/.camlog
# gets the message text from here. one line allowed only. means you can do
# stuff like echo "sleeping and stuff" > ~/.caminfo
##It wouldn't work w/my own file name so I stuck with the default
##...in my case it was/is weather data
##infofile = /home/itsme/weather/weatherStationData.htm
infofile = /home/itsme/.caminfo
# directory to archive pics in. They are datestamped and saved in here.
archive = /opt/images/webcam
## didn't work if this was set at 0
##archive = 0
# archive pics in datestamped subdirs
# (1 == with subdirs, 0 == without subdirs)
archive_subdirs = 0
# extension (determines type) of archived images.
archive_ext = jpg
# determines how many shots are taken before a pic is archived
# (1 == every pic, 0 == don't archive)
## I turned this off, too much disk activity & used space over time
archive_shot_every = 0
#archive_shot_every = 1
# create archive thumbnails enable/disable flag and give width/height
archive_thumbnails_dir    = /opt/images/webcam/thumbnails
archive_thumbnails_create = 0
archive_thumbnails_width  = 120
archive_thumbnails_height = 90
# jpeg quality (you can save as png etc too, but then quality does squat)
quality = 80
input  = 0
# 0 for PAL, 1 for NTSC
## Left this at default, don't know which is better in USA
norm   = 0
# Goes in the top right. strftime() is run on this too, so put date stuff in
# if you like
## Put whatever you want
title_text = It's Me TV
# color/transparency of title text
title_r = 255
title_g = 255
title_b = 0
title_a = 255
# font for title text. fontname/size
title_font = Arial_Bold/10
# fancy font styles
# title_style = /path/to/title.style
# color/transparency of message text
text_r = 255
text_g = 255
text_b = 0
text_a = 255
# font for message text. fontname/size
text_font = Arial_Bold/8
# fancy font styles
# text_style = /path/to/text.style
# color/transparency of rectangle behind text
# make it 0,0,0,0 to disable.
bg_a = 0
bg_b = 0
bg_g = 0
bg_a = 75
#bg_a = 100
# directory to look for ttf fonts in
## Mine was in a different dir than the default setting.
## You have to actually see the font name sans extension and use it
## and in my case the font was: Arial_Bold.ttf
## For the below line use only the dir, not the specific font.
ttf_dir = /usr/share/fonts/truetype/msttcorefonts
#ttf_dir = /usr/X11R6/lib/X11/fonts/TrueType
# ***************************************************************************
# file to check for before shooting. while this file exists, no shots will
# be taken.
# ***************************************************************************
blockfile = /home/root/BLOCKCAM
# ***************************************************************************
# image to upload when blockfile is first put in place
offline_image = /home/itsme/.block.jpg
# ***************************************************************************
# File to check before shotting, while this file exists, shots will be taken.
# but not uploaded. blockimage will not be uploaded if you set this.
uploadblockfile = /home/root/BLOCKUPLOAD
# ***************************************************************************
# Shots will only be taken/uploaded if the specified interface is active.  
## Run this command to see what yours is: ifconfig 
#watch_interface = ppp0
watch_interface = eth0
## It wouldn't work with 0, couldn't disable it
##watch_interface = 0
# image to overlay
## I'm not using this but left it at default
overlay_image = /home/itsme/.lb.png
overlay_x = 5
overlay_y = 5
## I left all the rest as is/was
# do things. like play sounds or whatever. Each is a shell command.
#action_pre_shot
#action_post_shot
#action_post_upload
# image processing
# crop = 1
# crop_width = 320
# crop_height = 240
# crop_x = 20
# crop_y = 20
#
# scaling is applied after cropping, so you can###
# remove borders then stretch up the result
# scale = 1
# scale_width = 640
# scale_height = 480
#
# Flip the image horizontally or vertically.
# Horizontal flipping is useful for some Philips cams
# which give a mirrored image when used with the pwc module.
# flip_horizontal = 1
# flip_vertical = 1
#
# Change the orientation of the image.
# Useful if your camera is on its side (for whatever reason).
# 1 rotates clockwise by 90 degrees, 2, rotates clockwise by 180 degrees, 
# 3 rotates clockwise by 270 degrees.
# orientation = 1;

---

