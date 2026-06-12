---
title: "No sound from flv file . movie plays ok"
date: 2007-01-06
forum: Apple PPC Users
---

### Post by oswaldkelso on 2007-01-06
Hi I have the script from [http://1024k.de/bookmarklets/video-bookmarklets.html]("http://1024k.de/bookmarklets/video-bookmarklets.html")

installed in firefox and can down load and watch youtube and google videos in vlc or totem fine. The only problem is I have no sound in flash .flv files.

 Is there a way to get the sound to work, the avi and mp4 files play ok

G4 867 with etch fluxbox and rox-filer.

thanks

---

### Post by ssam on 2007-01-07
try mplayer, that works for me in ubuntu 6.10 (edgy)

---

### Post by oswaldkelso on 2007-01-07
Thanks for getting back. Unfortunately Mplayer is the only player I cant get to work with video, sound with  mp3's play??  I've tried several versions just incase but have the altivec version installed which should be the correct one for my mac. 

I'll have a look and see if I can find some liberays 

cheers anyway

---

### Post by ssam on 2007-01-08
do you have ffmpeg installed?

---

### Post by oswaldkelso on 2007-01-10
Yes but not a peep!! other formate give sound but not flv??

I'm not at home at the moment so I'll reinstall it when i get back and see if that works.

---

### Post by ubuntubrian on 2007-01-13
use mplayer with the binary codecs from the mplayer website. Plays flash and wmv and everything else I've thrown at it, except swf files and for that I use gnash or I use ffmpeg and a script and then watch them on totem or xine. Here's the script which I did not write:

#!/bin/bash
#
# script written by Ed Hargin to convert flvs from places like youtube and googlevideos to mpg files.
#
# note to self: $1 = 'flv filename'
#
#   todo:
# - make the script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert?

flv_file=$1

####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i $flv_file -ab 56 -ar 22050 -b 500 -s 320x240 $name.mpg
}  

# Variables declared in above line (brackets are defaults used if option is omitted) 
#
# -ab = averate bitrate of music in kbit/s (default = 64)
# -ar = audio sampling frequency (default = 44100 Hz)
# -b  = video bitrate in kbit/s (default = 200 kb/s)
# -s  = set frame size (wxh) (default = 160x128)

###################
# Rename Function #
###################
#this function asks what you want to call the new file created, and acts accordingly.

rename ()
{
echo "By default the file will be named $flv_file.mpg - do you want to change this? (Y/N)"
read rename_answer
	if [ "$rename_answer" = "y" ];
		then echo "What do you want to call it? (.mpg will automatically be appended to the filename)"
		read name
		echo "Converting flv file to $name.mpg"

	else [ "$rename_answer" = "n" ];
		name=$flv_file.mpg
		echo "Converting file to $name"

	fi
}


#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.

function flvdelete {

	echo "Do you want to delete the original flv file? (Y/N)"

	read reply

	if [ "$reply" = "y" ];
 		then rm $flv_file
		echo "File deleted: $flv_file"  #should I build in some kind of detection of 'need to be root to delete'?

	elif [ "$reply" = "n" ];
 		then echo "Leaving file alone: $flv_file"

	fi
}

###############
# Main Script #
###############

rename ;
convert ;
flvdelete 

exit

---

### Post by digbysellers on 2007-02-15
[http://vixy.net/flv_converter](http://vixy.net/flv_converter)

Maybe this will do what our operating system cannot. 

Or boot into Windows. Just like when one needs to burn a DVD at less than a liteon burner's maximum write speed. =(

---

### Post by digbysellers on 2007-02-15
What's frustrating is that sound works when playing video from the Youtube website through the browser. 
If I had more suitable computing skills, I'd say that could be a hint at the problem?

---

### Post by konungursvia on 2007-03-13
You should also try selecting various audio codecs manually in your video player. There could be up to a couple dozen, and one of them may do the job.

---

### Post by joyolee on 2007-03-21
i do have the same problem~

anyone have some ideas?

Thx

---

