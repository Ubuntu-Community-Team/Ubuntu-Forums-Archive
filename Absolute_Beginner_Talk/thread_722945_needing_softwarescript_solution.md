---
title: "needing software/script solution"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Knacker on 2008-03-13
I've spent the past couple of days looking for a program or a script that will do a pretty simple task for me and can't find answers anywhere. I'm hoping that one of you wise folk will have a shockingly simple/obvious solution or a suggestion. 

The task: 
To automate the copying all directories + files from hundreds of CDRs to my hard drive. Basically, I'm looking for a something like the auto-rip funtion in grip or itunes, but for data cds. When running (in the background or whatever), the script or program would automatically detect a disc in the drive and start copying everything on a CDR to a set location on the HDD...when done copying, would eject the disc.  

If there's an application that will do this, I'd be grateful for a link. I've got no "game" when it comes to writing even wee-little scripts; but if a little script is the solution I'm looking for, could someone recommend a person/place where I could get help with this? 

I'm at a loss. Really really grateful for any thoughts or ideas. 
Thanks in advance! (And sorry if this is the wrong place in the forums to post this...)

---

### Post by Hospadar on 2008-03-13
Well to start, [here]("http://www.freeos.com/guides/lsst/") is a guide on scripting, it might help.

If you just want to copy everything over from a cd to a certain directory, that's easy and probably doesn't even require a script, just a simple terminal command. something like```
cp -rf /media/cdrom/* /path/where/you/want/to/put/stuff
```wait till it finishes and pop out the cd, then every time you put in a new cd, just up arrow in the terminal to repeat the last command and enter.

Also note, your /media/cdrom might be named slightly different, so browse to your /media folder and make sure you get the right folder.

Also as an explanation, "cp" is a terminal command to copy files, the arguments "-rf" say to copy recursively (go into folders) and to force copies (so it doesn't ask you about every file) and then the source file (the asterisk says any file in that folder, and then the target folder/file.

This isn't really automatic though, you might want to google around for "running a scrip on mount" or something like that.  I suspect there is a way to do it, I just don't know what it is.

---

### Post by Knacker on 2008-03-13
Thanks, this is useful. It's really the ability to just switch discs and let the script do the rest that I'm looking for... seems like it would be a common enough problem and a simple enough fix, but still haven't found anything through google. thanks again! will keep looking...

---

### Post by Knacker on 2008-03-13
I've found scripts to automatically mount, then dump contents, then unmount Flash Drives and Digital Cameras...but I have no idea whether these are relevant, to say nothing of how I would modify them to make them work for CDs... 
Is this useful?
[[http://www.mbeckler.org/scripts.html]](http://www.mbeckler.org/scripts.html])

Automatic Digital Camera Unloader

This script will automatically unload your digital camera's pictures. It is very similar to the Automatic Pocket-Drive Backup script above, but it merely creates a dated directory and copies over the pictures. You will have to customize the top three variables (MOUNTPOINT, SUBFOLDER, and PICTURESDIR) which will be different for everybody's computer and camera.
#!/bin/bash
# Script to automatically unload (without removing) pictures from a camera.
# Created a folder based on today's date, and copy all files over.
#
# Written by Matthew Beckler ( matthew @ mbeckler . org )
MOUNTPOINT="/mnt/usb"
SUBFOLDER="$MOUNTPOINT/dcim/101msdcf/"
PICTURESDIR="/home/matthew/pictures/$(date +%Y%m%d)"

HADTOMOUNT=0

echo "Checking if device is mounted"
mount | grep -i $MOUNTPOINT &> /dev/null
if [ $? -eq 0 ]
then
	echo "Device is already mounted"
else
	echo "Mounting device . . ."
	mount $MOUNTPOINT &> /dev/null
	if [ $? -ne 0 ]
	then
		echo "Could not mount device"
		exit 1
	fi
	HADTOMOUNT=1
fi

echo "Checking if source directory exists"
if [ ! -e $SUBFOLDER ]
then
	echo "The source directory $SUBFOLDER does not exist."
	echo "Are you sure this is a digital camera?"
	exit 1
fi

echo "Checking if destination directory exists"
if [ -e $PICTURESDIR ]
then
	echo "The directory '$PICTURESDIR' already exists"
	exit 1
else
	echo "Creating directory: '$PICTURESDIR' . . ."
	mkdir $PICTURESDIR
fi

echo "Copying pictures . . ."
cp -av $SUBFOLDER* $PICTURESDIR

echo "Finished copying pictures"

if [ $HADTOMOUNT -eq 1 ]
then
	echo "Unmounting device . . ."
	umount $MOUNTPOINT
	if [ $? -ne 0 ]
	then
		echo "Could not unmount device"
	fi
fi
exit 0

---

