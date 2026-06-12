---
title: "Help I miss Paint Shop Pro"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by StueyB on 2006-02-21
Hi peeps,

Can anyone suggest an application that can be used to replace the functions I use within this application. 

All I want to is have a very fast image crop and resize tool. Basically I need to take images down to thumbs by croping and resizing but gimp seems so awkward. 

To put it into context, in paint shop pro I can do 1 crop with custom settings in about 5 seconds as opposed to not having a clue in gimp. Also I do a LOT of thumbs, on average 200 or so a day! Can anyone recommend a package/help me sort out gimp so that it will do this ?

Cheers

Stuart

---

### Post by BitTorrentBuddha on 2006-02-21
I suggest the [GIMPshop plugin](gimpshop.net)

---

### Post by TrendyDark on 2006-02-21
It may help you to know that the crop tool has a different icon. Paint Shop Pro is about on the same level as Gimp (& under GimpShop). Good thing you're not used to Photoshop as I am.

---

### Post by tadashi on 2006-02-21
Have you tried to run Paint Shop Pro in Wine (Windows Emulator)?  Not sure about he thumbnailing program.  I am trying to switch from ACDSee to Gimp myself which has the thumbnailing plug-in.

Here is how to resize in Gimp: [http://gimps.de/en/tutorials/gimp/picture-photo-image/resize-size/](http://gimps.de/en/tutorials/gimp/picture-photo-image/resize-size/)

Here is how to crop:
[http://mailman.linuxchix.org/pipermail/courses/2005-January/001608.html](http://mailman.linuxchix.org/pipermail/courses/2005-January/001608.html)

Here is an online books on Gimp:
[http://gimp-savvy.com/BOOK/](http://gimp-savvy.com/BOOK/)

---

### Post by kwaanens on 2006-02-21
[QUOTE=StueyB]Also I do a LOT of thumbs, on average 200 or so a day! Can anyone recommend a package/help me sort out gimp so that it will do this ?[/QUOTE]

I use ImageMagick for this.
Install ImageMagick and use this script:

```
#!/bin/sh
for i in "$@"; do
convert -size 60x60 "$i" -resize 60x60 +profile "*" \
        "`dirname $i`/thumb_`basename $i`"
done
```

This makes new images in 60x60 pixels, with the names name "thumb_orginalname.*"

Put this in a text file, for instance in /home/[user]/script
Then:
sudo ln -s /home/[user]/script/image_thumb /usr/bin/

EDIT: Then run:
$ image_thumb /home/[user]/image.directory

- Ketil

---

### Post by mcduck on 2006-02-21
First, install Imagemagick with apt-get or nautilus.

Then run 'gedit ~/.gnome2/nautilus-scripts/resize_to_640x480'
Paste this there and save:
```

#!/bin/sh
SMALL="pics_680x480"
TINY="ico"
PICS="*.JPG *.JPEG *.jpg *.jpeg *.png *.PNG"
   if [ ! -d "$SMALL" ]; then
     mkdir -m 777 $SMALL
   fi
   if [ ! -d "$SMALL/$TINY/" ]; then
     mkdir -m 777 $SMALL/$TINY/
   fi
for z in $PICS; do
  za=$(($za+1))
done
factor=$((100/$za))
i=0
(for a in $PICS; do
if [ -e "$a" ]; then
   w=$(($w+$factor))
   i=$(($i+1))
   echo $w
   echo "#converting... $a"
   convert -size 640x480 "$a" -resize 640x480 -quality 86 "$SMALL/$a"
   convert "$SMALL/$a" -strip "$SMALL/$a"
   convert -size 200x150 "$SMALL/$a" -thumbnail 200x150  "$SMALL/$TINY/$a"
   if [ "$i" -eq "$za" ]
    then
     echo 100
     echo "#done"
   fi
fi
done)|zenity --progress --title="$NAUTILUS_SCRIPT_CURRENT_URI" --text="converting..." --percentage=0  --auto-close


```

Last, run 'chmod ug+x ~/.gnome2/nautilus-scripts/resize_to_640x480'

Now right-click inside any directory in file manager and select scripts/resize_to_640x480 from the popup menu and all images will be resized to 640x480 and 200x150 sizes and placed into a new directory. :D

---

### Post by engla on 2006-02-21
Note that it should also be possible to create a launcher with any of the above scripts and have an icon on your panels or the desktop to which you can drop images to make thumbnails

---

### Post by Madpilot on 2006-02-21
gThumb has some thumbnail creation utilities, which I admit I haven't used yet... but AFAIK you can point it at a directory full of pictures and it'll create thumbnails for all of them.

---

### Post by mcduck on 2006-02-22
ImageMagick can also do the cropping for you. And lots more. Here are some examples to get you started: [http://www.cit.gu.edu.au/~anthony/graphics/imagick6/]("http://www.cit.gu.edu.au/~anthony/graphics/imagick6/")

---

### Post by Perfect Storm on 2006-02-22
You might give pixel32 a chance if you don't mind paying a little for a paint program: [http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)
There's a demo there to try.

---

### Post by StueyB on 2006-02-22
[QUOTE=Madpilot]gThumb has some thumbnail creation utilities, which I admit I haven't used yet... but AFAIK you can point it at a directory full of pictures and it'll create thumbnails for all of them.[/QUOTE]

Thank you to everyone that replied. Gthumb fits the description well! Its by no means perfect but its easy enough and quick enough for what I need. You have saved me having to faff about with Wine :)

---

### Post by pedalwrench on 2007-05-20
THX mcduck!:D

I edited the script a bit to add script comments, 800x600 resolution, and text on the image.

```
#!/bin/sh
# This Script converts images that are in JPG and PNG format to smaller web sizes
# Original Script:
#	http://ubuntuforums.org/showthread.php?t=134170&highlight=auto+resize+images
#	Thanks mcduck
# I added script comments, text-on-image and 800x600 resolution
# Script is GPL
# Have Fun!
# Jeremy Schroeder
# www.spudz.org
#
## Options ##
# 
# Folder Names
RESIZED="resized"
MEDIUM="800x600"
SMALL="680x480"
TINY="thumbnails"
## text-on-image
# leave TEXT blank "" to disable
# Year
DATE="2007"
# Text to be written
TEXT="Jeremy Schroeder - images@spudz.org - All Rights Reserved, $DATE"
# Text Size
TEXTSIZE="11"

### Please do not edit below ###

# image types
PICS="*.JPG *.JPEG *.jpg *.jpeg *.png *.PNG"
# Make Dirs
# make main dir
   if [ ! -d "$RESIZED" ]; then
     mkdir -m 777 $RESIZED
   fi
# make 800x600 dir
   if [ ! -d "$RESIZED/$MEDIUM/" ]; then
     mkdir -m 777 $RESIZED/$MEDIUM/
   fi
# make 640x480 dir
   if [ ! -d "$RESIZED/$SMALL/" ]; then
     mkdir -m 777 $RESIZED/$SMALL/
   fi
# make Thumbnail dir
   if [ ! -d "$RESIZED/$TINY/" ]; then
     mkdir -m 777 $RESIZED/$TINY/
   fi
for z in $PICS; do
  za=$(($za+1))
done
factor=$((100/$za))
i=0
(for a in $PICS; do
if [ -e "$a" ]; then
   w=$(($w+$factor))
   i=$(($i+1))
   echo $w
   echo "#converting... $a"
# Converting files commands
   	convert -size 800x600 "$a" -resize 800x600 -quality 86 -pointsize $TEXTSIZE -draw "gravity south fill black  text 0,12 '$TEXT' fill white  text 1,11 '$TEXT' " "$RESIZED/$MEDIUM/$a"
	convert "$RESIZED/$MEDIUM/$a" -strip "$RESIZED/$MEDIUM/$a"
   	convert -size 640x480 "$RESIZED/$MEDIUM/$a" -resize 640x480 -quality 86 "$RESIZED/$SMALL/$a"
   	convert "$RESIZED/$MEDIUM/$a" -strip "$RESIZED/$MEDIUM/$a"
   	convert -size 200x150 "$RESIZED/$MEDIUM/$a" -thumbnail 200x150 "$RESIZED/$TINY/$a"
   if [ "$i" -eq "$za" ]
    then
     echo 100
     echo "#done"
   fi
fi
done)|zenity --progress --title="$NAUTILUS_SCRIPT_CURRENT_URI" 
--text="converting..." --percentage=0  --auto-close


```

---

### Post by MockY on 2007-05-20
Do you think you could modify it a bit more, so a user could pick at least 2 more sizes. 1200 and 1600 maybe?

---

### Post by zenkaon on 2007-05-20
I you are using kde then you can simply go to the directory with all of your images using konquerer, 
click on tools->create image gallery 
and then choose the size of your thumbnails. Just ignore the gallery it generates and take the thumbnails from the thumbs directory it creates.

It's using Imagemagic as a backend, but you don't need to worry about that

---

### Post by MockY on 2007-05-20
Here is the script I use. Works extremely well and I could easily add more sizes.

```

#!/bin/bash
# Author : Mathieu Vilaplana <mathieu@creationgif.com>
# Date : 09/03/2005
#depends: imagemagick, zenity
# thanks to coffe
#version 0.4
#	- check mime type
#since v 0.4, solve bug with filename spaces
#version 0.6
#	- correct bug in filename with spaces
#     - create a subdirectory to create images

#test if a file has been selected
if [ $# -eq 0 ]; then
	zenity --error --title="error" --text="You must select at least 1 file to process"
	exit 1
fi

#=========================
#       SELECT SIZE DIALOG
title="Choose which sizes to scale to"
imgsize=`zenity --title "$title"  --list --separator=" " --column="size" "160x120" "320x240" "640x480" "800x600" "800x600" "1024x768" "1152X864" "1600X1200" `

#if $? != 0, user click on cancel button, so exit
if [ "$?" != 0 ] ; then
	exit
fi

#user must select a target size
imgsize=`echo $imgsize | sed 's/ max//g'`
if [ ! "$imgsize" ]; then
	zenity --error --title="error" --text="select a target size"
	exit
fi

#transform 640x480 en 640x640 for convert to respect proportions
himgsize=$imgsize
val1=`echo "$imgsize" | awk -F'x' '{ print $1  }'`
imgsize="${val1}x${val1}"

#       END SELECT SIZE DIALOG
#=========================


#Select only images
nb_images=0;
selection="";
while [ $# -gt 0 ]; do
	isimage=`file -bi "$1" | grep image | wc -l` 
	if [ $isimage -eq 1 ]; then
		selection[$nb_images]=$1
		let "nb_images++"
	fi
	shift
done

#create directory if not exist and at least one image to process
if [ ! -d $himgsize  ] && [ "$nb_images" -gt "0" ];then
		mkdir $himgsize
fi

n=$nb_images
let "n=n-1"
(for i in `seq 0 $n`;do
	picture=${selection[$i]}
	let "compteur += 1"
	echo "# Processing image $compteur / $nb_images $picture ..."
	convert -quality 80 -resize $imgsize "$picture" $himgsize/"$picture"
	let "progress = compteur*100/nb_images"
	echo $progress
done
) |
        zenity --progress --auto-close --title="Scaling images"  --text="Processing images ..."  --percentage=0


```

---

