---
title: "[SOLVED] ManDVD"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-11-12
Hi I have installed this program and keep getting to the generate slide show point when it returns this error...can someone please help a newb on what is going on..I've installed so many packages you'd think christmas was round the corner...oh it is.. Thanks in advance

Error message truncated to line

[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio for /home/nigel/Music/Podcasts/triple j_ WE LOVE AUSMUSIC/institut_polaire.mp3...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/nigel/Videos/New man/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

I am sure it is simple thanks

Nigel

---

### Post by mridkash on 2007-11-12
I get the same error while using dvd-slideshow (command line) to make slideshows.

When I look at the log, ffmpeg says unknown error.
There is an option in dvd-slideshow to use mp2 instead of ac3 for sound. mp2 works ok.

---

### Post by hogwartsnigel on 2007-11-12
Thanks,
I will be trying to do as you did but would appreciate a how to..incase (as will be the case I screw it up.
so i type dvd-slideshow in command and alter the text ok here goes....gulp.

Nigel

---

### Post by hogwartsnigel on 2007-11-12
Ok time to show my dumbness,
I type dvd-slideshow and got what I think is a help file. I found the command -mp2 but don't know what to do with this. Umm
scared (I know wussy) to amend anything and I'll wait for anyones advisory.

Skulking in the corner....

Nigel

---

### Post by mridkash on 2007-11-12
dvd-slideshow is a program to make slideshows in vob format.

First you create a text file of your images using dir2slideshow command. more details [http://dvd-slideshow.sourceforge.net/wiki/Dir2slideshow_0.8.0](http://dvd-slideshow.sourceforge.net/wiki/Dir2slideshow_0.8.0)

Then you use dvd-slideshow command to make a slideshow of the images by passing the text file you generated earlier as input. Here you have to pass the argument -mp2

more info: [http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page)

examples: [http://dvd-slideshow.sourceforge.net/wiki/Examples](http://dvd-slideshow.sourceforge.net/wiki/Examples)

---

### Post by hogwartsnigel on 2007-11-12
Thanks mridkash,
I knew it was a program and a resource that manDVD utilised. I still am not sure though (I am a little slow) how I can configure manDVD to do this. Do I have to go through the whole process describe to creat a text file and amend for each slideshow??
I want Mandvd to work is there a way I can amend from within it to automate past the error I am getting whilst using this? Is there another program??
This is to be eventually used by my wife and therefore needs to be a simple to use program for creating a slideshow and anchoring it within a dvd menu.

Thanks 

Nigel

---

### Post by toastydave1 on 2007-11-24
this problem is caused by a yet to be updated version of dvd-slideshow working with a new version of ffmpeg,

to fix it and get ac3 sound working you need to edit your dvd-slideshow script file found in

/usr/bin/dvd-slideshow.

open as root and search for the audio bitrate, (just search for 192) 

where you find this put a capital K after it (for thousand)

for example, were it read  

if [ "$ac3" -eq 1 ] ; then
		checkforprog ffmpeg
		myecho "[dvd-slideshow] Creating ac3 audio for $file..."
		ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab 192 -acodec ac3 -ar 48000 -ac 6 

change to 

if [ "$ac3" -eq 1 ] ; then
		checkforprog ffmpeg
		myecho "[dvd-slideshow] Creating ac3 audio for $file..."
		ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab 192K -acodec ac3 -ar 48000 -ac 6 

do this for all the 192's in the program file section

save the file and your done!

---

### Post by hogwartsnigel on 2007-11-24
Thanks Toast,
I am going to be so dumb but how do I edit the source, I opened it up in gedit but can't save as I don't have permission...how do I change to root and edit.

Thanks

Nigel

---

### Post by toastydave1 on 2007-11-25
yes no problem, I'm new as well!

you have to type 

sudo gedit /usr/bin/dvd-slideshow

(if you have the terminal window open you can select the above text and drag it to the terminal to avoid all the typing) 

then enter your password

Dave

Its a bit of a learning cliff if you have come from windows!

---

### Post by toastydave1 on 2007-11-25
heres my modded file if you want to copy, just cut and paste into (overwriting your existing file) from the #mark onwards (back up your original file first! it worked for me, by maybe not for you!!!)



#!/bin/bash
#    dvd-slideshow
#    Copyright 2003 Scott Dylewski  <scott at dylewski.com>
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program; if not, write to the Free Software
#    Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#

name='dvd-slideshow'
version='0.7.5'

echo "[dvd-slideshow]            dvd-slideshow $version"
echo "[dvd-slideshow]            Licensed under the GNU GPL"
echo "[dvd-slideshow]            Copyright 2003-2006 by Scott Dylewski"
echo "[dvd-slideshow]            "

## todo: (sorted by priority?)
# vcd and svcd support
#  smoother kenburns effect for slow pans
#  kenburns with rotation
# explain how to view subtitles after runnning dvd-slideshow
# explain difference between Low/Medium/High quality modes

## known bugs:
# dvd-slideshow < 0.7.4 does not work with bash >= 3.1
# continuous subtitles don't work across non-image/transition lines
# bug when first line/slide has a subtitle but no others do?
#
#  convert image.jpg -bordercolor black -border 0 "$tmpdir/fade_$dj.ppm" works for transparent .png images
# in ImageMagick > 6.0.6, but not in 6.0.6 for some reason.  (black output).  

changes ()
{
echo 'Changes:
0.7.5	
    New features & Changes:	
	Use "\n" to force line breaks up to two lines in title text (not titlebar yet).
	Fixed code to rotate images.  (not public yet)
	  Use image.jpg:duration:subtitle:[effect1:effect1_params:]rotate:angle
	Configuration variables will be read in sequence now.  So you can configure font
	  colors and sizes throughout the input file.
	Allow comments in all lines.  Everything after <space># will be ignored.
	Scroll effect is MUCH smoother for slow scrolls in high-quality mode! (takes 3x longer)
	Slideshow name -n is optional now.  Defaults to the base name of the input file.
        * Changed old "title" keyword to "titlebar:duration:toptitle:bottomtitle"
        * Added "title:duration:title_text" function where a single title is rendered in the middle of the screen.
	Add check for missing subtitle syntax in crop/scroll/kenburns.
	Longer progress bar.
	Reads ~/.dvd-slideshowrc in a loop for better debugging and security.
    Bug fixes: 	
	Added "+repage" in convert lines after cropping when using internal .mpc image format. 
	   ( Fixes Kenburns and crop errors with ImageMagick > 6.2.2 )
	Fixed kenburns problems with black backgrounds. 
	Fixed "geometry does not contain image" problem with kenburns effect.
	Works for slide or transition duration > 35 seconds now.
	Add quotes around yuv fifo to allow for spaces in output directory.
	Fixed "squishing" when fading out or crossfading to a scroll effect. 
	Fixed problem where audio "fadein" was being rendered as a subtitle.
	Traps bad duration=0 for images and effects.
0.7.4	
    Bug fixes: 	
	Changed mpeg2enc process file descriptor from 55 to 3 for
	compatibility with bash >= 3.1 (fixes hang at wait for mpeg2enc to finish)
	Echos details to logfile about mpeg2enc process for future debugging.
	Output directory gets created if it does not exist.
	Fixed bug in kenburns positioning with black background.
	Better error messages when no oggdec or lame found.
	Fixed error where kenburns intermediate files were not being deleted.
0.7.3	
    New features:	
	Fixed Kenburns zoom in adjusted to a "constant" velocity!  
	You can include other .txt files by using a line include:filename.txt in your input .txt file. Thanks Thomas Weber!
	User can manually add chapter markers by using the "chapter" keyword alone on one line of the input .txt file.
	Added variable "mpeg2enc_params" so advanced users can easily change the parameters.
	All timing accurate to 0.001 (1 ms) now.  
	Added -smp option to process faster on high-end machines. 
	Added -writechaps option to write out chapter markers to <slideshow_name>.chap
    Bug fixes: 	
	Fixed bugs causing errors when spaces were in paths.
	Fixed bugs in the audio processing: error on last audio file.
	Changed mpeg2enc -M 3 (use multiprocessors) to -M 0 because 1.8.0 was crashing on athlon 64 X2 machines.
	Added "-compose src-over" option to composite calls for compatibility with Debian Etch.
	Fixed bug when passing a single audio file longer than the slideshow.
	Removed rpm check for supporting applications.
	Checks for crossfade duration = 0 and handles it correctly.
	Checks that audio and image files exist while parsing .txt file.
	Fixed minor bug where an extra (non-existant) subtitle was rendered.
	Fixed bug when fading in to a first slide that is a scroll effect.
	Subtitle timing bug fixed!
	Small fix in displaying total number of pictures processed
	Better logging to logfile.
	Fixed ignored line if last line does not contain a line break.
0.7.2	
	Faster Kenburns effect rendering when using black background.
	Allow multiple sequential audio files in input .txt file.
	Changed "head -1" to "head -n 1"
	Allow .png and .jpeg extensions.
	allow \n in subtitles to designate end-of line breakpoints
	Checks for required program version better now.
	Fixed ppmtoy4m compatibility error for compatibility with
	mjpegtools >= 1.6.3-0.1
	Allow "exit" keyword in .txt file (for easier debugging).
	Fixed pixel aspect ratio problem. (hopefully)
	Add option to render subtitles with spumux and .srt files (beta)
	Cleans up old temporary files if they exist.
	Better logfile output.  Hopefully catches program call errors.
	Title2 text and bar locations referenced to bottom of frame
	for better PAL/NTSC compatibility.
	Subtitle stays constant between slides if they both
	have the same subtitle (thanks Andre Weilert)	
	All temporary files are created in a temporary directory now.
	Fixed bug when fading in to a scroll effect. (remove tab at EOL).
	Changed progress indicator slightly.
0.7.1	
	Added log file output to dvd-slideshow.log
	Updated documentation and examples.
	Background color can now take a #RRGGBB value.
	Nicer progress indicator.
	AC3 audio is now the default.  Pass -mp2 to force MP2 audio.
	Autocrop works on background images now also.
	Added code to check for all temporary fade_xxxx.ppm images
	before proceeding to encode mpeg video.  
	Fadein or crossfade to a scroll effect works correctly now.
0.7.0	
	Default variables can be set in a ${HOME}/.dvd-slideshowrc file
	Default variables can be set in the input .txt file
	Crossfade and fadein to kenburns effect correctly fades
	 to the first frame geometry instead of the whole image.
	New keywords for the start and end points in kenburns effect:
	 topleft/middle/middleright etc.  See docs for details.
	New keywords for the crop function also.
	9999 audio files possible now. Used to be a limit of 9
	Fixed bug when fading in to a cropped image.
	Removed -R 2 and -c options in mpeg2enc because
	 some people had problems.
	Fixed subtitle timing bug, so now the subtitles appear
	 and disappear closer to the correct time.
	Changed encoded audio bitrate from 224kb/s to 128kb/s
	Works with toolame 0.2m beta and 0.2L now
        Got rid of calls to NetPBM functions, so it is no longer required...
	Changed "wc -m" call to "wc --chars" for better compatibility.
	Fixed syntax so spaces should be allowed in input files now.
	Changed "seq 2 1" to "seq 2 -1 1" for better compatibility
	Added option to "autocrop" images (-c) that are close to the
		output aspect ratio, but not quite.
	Title syntax changed... (see documentation)
	Fadein/crossfade to a title or background slide works now.
	Fadein/fadeout/crossfade works when previous/next slide is not
	 actually an image/title/background. The next real slide will
	 be used instead.
	Fixed bug in Low quality mode (-L) (extracopies bug)
	Fixed bug with subtitles with new versions of imagemagick.
	White can be used a a background keyword for white backgrounds.

0.6.0	
	Fixed major bug/error when generating long slideshows. 
		Now all video gets piped in YUV fomat through mpeg2enc
		in one single block. (fix by Mike Beller)
	Added option to generate AC3 audio files (requires ffmpeg)
	Fixed title slide when using -L (low quality mode)	
	Allow for slide durations to be specified in hundreths of a second: 5.23
	Reports total audio and video lengths at the beginning of the code.
	Fixed bug when using subtitles. (no subtitles were generated)
	Changed output files to be .vob extension instead of .mpg	
	Better font searching (thanks Jim Crumley)
	Use backslash to escape a colon in subtitles (thanks Jim Crumley)
	Allow avi input files.  pre-alpha support.  (thanks Jim Crumley)
0.5.4	
	Added option to re-define background image from text file input.
	Code cleanup (slightly)
	Added support for two audio tracks.  
	Added audio effects:  fadein/fadeout	
	Default command-line audio fadein/fadeout time is 3 seconds.
0.5.2	
	Fixed bug in musictitle Title info parsing.
	Checks to make sure a slidshow name is passed.
	Added low-quality mode (-L) for testing.  Speeds things up about 4x.
	Reduced verbosity.
	Checks for required fonts. Subtitles look much better now.
	Word-wraps long subtitle lines into two lines.
0.5.0	
	Added KenBurns effect!  See docs for usage.
	Added scroll effect!  See docs for usage.
	Added crop effect.  See docs for usage.
	Audio can be started and stoped for multiple files within
		the text file.  See docs for usage.
	Added "musictitle" option for displaying audio info.
	You can now comment out lines in the textfile by using the # character.
	Also ignores blank lines in textfile.
	Fades can now have up to 9999 frames.
	Total slides can now be 9999.  You guys are crazy.
	fixed small bug when no chapters are specified.
	Chapter markers are now rounded up to the next full second due to
		a bug in some versions of dvdauthor.
	Only checks for oggdec or lame if you pass an ogg or mp3 file.
	Changed syntax of command line input for files and audio.
	Passing images on the command line is no longer "public". 
		Use the text file in put instead.
	Fixed audio problem with some mp3 files getting pops in them.
0.4.8   
	Changed audio to process raw (headerless) audio files before 
		joining them.
        Fixed bug when passing multiple audio files (again).
        Fixed audio fadein/fadeout time to 1 second
        Fixed bug in audio where it plays to fast when burned on dvd.
        Checks to make sure audio files exist before processing.
0.4.6	Fixed bug when passing multiple audio files. (thanks Scott Merrill)
	Removed -t option from toolame command for better support for old versions.
0.4.4	Only writes chapter markers when there is a picture or title
	First chapter marker is now fixed at time 0
	Max number of chapter markers is now 99 (thanks Jens Gecius)
	Fixed bug when checking for toolame (thanks Jens Gecius)
	Added "crossfade" option!
	Will use mpeg3cat from libmpeg3 to join mpegs if available.
	Small fix to allow semicolons in subtitles (thanks Jim Crumley)
	Added -s option to mpeg2enc calls for (maybe?) better compatibility.
0.4.2	Current working directory will be used if -o not specified.
	Allow "background" keyword in text file to insert background.
	Make sure all ImageMagick calls have -depth 8 to make ppmtoy4m happy.
	No font is specified in ImageMagick calls, so it should use the default.
	Changed default menu to a steelblue gradient when no image is passed.
0.4	Fixed bug when no background specified (again).
	Added error checking to make sure image files exist.
	Ogg audio format supported (you must have oggdec).
	Uses toolame for mp2 audio encoding when available.
	Audio timing improved.
	Fixed bug when double-quotes were in subtitle.
	Added black, fadein, and fadeout options in txtfile!
	-p  (PAL format option) added. Not tested, but should work.
0.3	Fixed error when no background specified.  Now default is black
	Added checking for required programs before running.
0.2	Initial release'
}

help ()
{
echo "`basename $0` Version $version "
echo 'http://dvd-slideshow.sourceforge.net'
echo 'Copyright 2003-2006 Scott Dylewski <scott at dylewski.com>'
echo 	 
echo 'Description: 
	Creates a dvd-compatible mpeg2 video from a bunch of images.
	You can add music if you want also. Supports several effects
	like fadein/fadeout/crossfade/crop/kenburns.  

Usage:
 dvd-slideshow [-n <slideshow_name>] [-o <output_directory>] [-b <background_jpeg>] 
  [-a <audio_file1> -a <audio_file2> ... -a <audio_fileN>] 
  [-p] [-L | -H] [-mp2] [-r] [-smp] -f input_file.txt
	
Options: 
 [-n slideshow_name]
	  The program uses this
	  string as the filename base for the output files
	  so you can distinguish it from other slideshows
	  that you can send to the same output directory.

 [-o <outupt directory>]
	  Directory where the final .vob and dvdauthor .xml files
	  will be written.  Default is to write in the directory
	  where dvd-slideshow was run.
 		
 [-b <background jpeg>]
	  Image to use for the background of the slideshow.
	  All of the pictures will be
	  overlaid on top of this background image. If no file 
	  is specified, black will be used for the slideshow
	  and a blue gradient for the title slide.
	  
 [-a <audio file>]
          Audio file to play in background during the slideshow.
          It will be faded out at the end.  Supports mp3, ogg, or wav
          formats at this point.  Multiple files will be joined.
	  See also the more flexible text file input method.
	  To pass multiple files, use the -a switch again.

 [-mp2]
	Use MP2 audio instead of AC3.
	Default audio format is now AC3 because it seems to be more
	compatible with the DVD hardware players.

 [-p]
	Use PAL output video format instead of NTSC

 [-L]
	Render a low-quality video suitable for debugging.
	This sets the resolution to 1/2 of full resolution and
	decreases the quality of fades/transitions.

 [-H]
	(Beta) Render a higher-quality video.  
	This uses the default dvd resolution and keeps all other output
	parameters the same, but enables some pixel-sampling methods
	that make the scroll effect look better at very slow velocities.
	This will make dvd-slideshow take up to 4x longer to process the
	scroll effect. Only applied when needed; the output will explain. 

 [-r]
 	Autocrop horizontal images to fill the full size of the screen.

 [-smp]
 	Enable more processes to run at the same time for multiprocessor
	machines.  Basically, this just renders each frame of a transition
	in the background at the same time, and then waits for them to be finished.
	Use this at your own risk on slower machines! If you do not have enough
	memory to hold all the frames for one "crossfade" or "kenburns" effect,
	then linux starts swapping to disk, and your machine may seem to lock
	up for a while.  I have crashed my old machine using this.
	USE THIS AT YOUR OWN RISK!

 [-nocleanup]
 	Leave temporary files in the temporary directory.  Useful for debugging.

 -h or -help 
   Prints this help. 

 -v or -version 
   Prints dvd-slideshow version number. 

 -f input_file.txt
          File to specify all the parameters and order easily
          for bigger slideshows. It uses the ':' character as a 
	  separator for the fields:
          [image.jpg|keyword]:duration:subtitle:effect:effect_params
          with each line being separate.  File options
          will override the ones passed on the command line.

	  NOTE: the effect parameters are separated by a semicolon ;
	  instead of a colon :

	  You can escape a colon with a backslash in subtitle text.

	  Durations can be specified in seconds with
	  up to three decimal points, like 5.583 seconds.

	  Keywords:
            title:duration:Title_text
                makes a title slide. Text is centered on the screen.
            titlebar:duration:Upper_Title:Lower_Title
                makes a title slide.  Upper and lower titles are
                optional; if one is missing, only the other will
                be displayed. White bands are underlayed behind
                the text.
	    musictitle:duration:subtitle:Title;Artist;Album
	   	makes a black frame with the song info 
		printed in the bottom left corner.
	    background:duration:subtitle:image 
	    	makes a slide with the current background 
		or it resets the current background image to a new one:
		"background:2:"  will display the current background
		for 2 seconds. 
		"background:2::image.jpg"  will set the background to
		image.jpg and also display it for 2 seconds.
		"background:0::image.jpg"  will set the background to 
		image.jpg, but will not use it until the next picture. 
		"black" or "white" can be used instead of an image 
		name to display a black or white background.
		You can also use a hex RGB code as the background color.
	    fadein:duration:subtitle
	    	fades in to the next slide
	    fadeout:duration:subtitle
	    	fades out to the background
	    crossfade:duration:subtitle
	    	fades from one picture to the next.

	    chapter
	  	Force manual chapter marker timing.  Chapter markers will
	  	only be created where the "chapter" keyword occurs.
		The default is to add chapter markers at every slide.
	    include:includefile.txt
	  	Other input files can be included in the input .txt file.
	  	The file includefile.txt will be concatenated in the
	  	place where the line occurs.
		Useful for setting up a bunch of variables, fonts, etc
		and then just including one standard file at the start of
		your input .txt file.
	    exit
		Stops the slideshow at the current point as if the input
		.txt file ended at this point. Useful for debugging.

	  Effects:
	    Effects are only used with images, not keywords.
	    In the following effects, x0,y0 represents the
	    top left corner of a defined box, and x1,y1 is
	    the bottom right corner. 
	    NOTE: the effect parameters are separated by a
	    semicolon ; instead of a colon :
            crop:
	    	image.jpg:dur:sub:crop:x0,y0;x1,y1
		Crops the image about the coordinates specified.
		Full box description:
	    	  x0,y0;x1,y1
		  Specifies the top-left(0) and bottom-right(1) points.
		Keyword description:
		  frame_size;frame_location
		  where frame_size indicates the fraction of the final 
		  dvd window width/height, and frame_location refers
		  to the CENTER POINT of the picture,
		  and can be any of the following keywords:
		 	topleft		top		topright
			left		middle		right
			bottomleft	bottom		bottomright
		   or
		 	x%,y%
			where % is a percentage of the window width,height
			starting from the top left corner of the dvd window.
		   or
		 	imagewidth | imageheight
			where the image width or height will be scaled to 
			fill the full width or height of the dvd screen.
		Crop examples:
	    	image.jpg:dur:sub:crop:651,390;1134,759
		image.jpg:dur:sub:crop:30%;60%,60%
		image.jpg:dur:sub:crop:50%;topleft
		image.jpg:dur:sub:crop:imageheight;left
	    kenburns:
	    	image.jpg:dur:sub:kenburns:start_box;end_box
		The kenburns effect will crop/zoom from the start
		to the end box.
	    	Where now we have start and end boxes, defined in
		the same way as in the "crop" function, but now
		we have two boxes defined.
		Full box description:
	    	  xs0,ys0;xs1,ys1;xe0,ye0;xe1,ye1
		  Specifies the top-left(0) and bottom-right(1) points.
		Keyword description:
		  start 0%-100%;start_location;end 0%-100%;end_location
		Kenburns examples:
	    	image.jpg:dur:sub:kenburns:651,390;1134,759;372,330;1365,1089
		image.jpg:dur:sub:kenburns:30%;60%,60%;75%;40%,50%
		image.jpg:dur:sub:kenburns:50%;topleft;50%;bottomright
		image.jpg:dur:sub:kenburns:100%;left;0,0;720,480
		image.jpg:dur:sub:kenburns:100%;left;imageheight;left
	    scroll:
	    	image.jpg:dur:sub:scroll:[left|right|up|down]
		This is most useful for displaying panorama-style
		pictures that are much wider than they are tall.
		This will automatically resize the picture so that
		the image height is equal to the video display 
		height (480) before scrolling (or conversely for tall
		images).

	    The subtitle field is optional, but if you are passing
	    effects after the subtitle field, be sure to include 
	    all the colons :: in order for the parser to get the
	    correct info.

	    When passing a picture, you can optionally use the
	    keyword "audio" instead of the integer duration in 
	    seconds.  What this does is force the duration of
	    that image to be the length of the previous audio 
	    track.  This is useful for making a music video dvd.

	  Audio:
	    Audio tracks can be inter-mixed with the video.  If 
	    an audio track is placed between two different images,
	    that audio track will begin playing at the start of the
	    second image.  When placing audio, use the syntax:

            audiofile:track:effect1:effect1_params:effect2:effect2_params

	    The audiofile can be a .ogg, .mp3, or .wav file.
	    Track is the resulting dvd audio track.
	    Effects are audio effects where
	    you can specify things like fadein/fadeout
	    for the audio.  Example:
            audiofile.ogg:1:fadein:3:fadeout:2

	    If you want to concatenate two audio files, just place them
	    one right after another.  
	
	Configuration file and variables:
	  You can configure some of the variables and settings
	  that control dvd-slideshow through keywords in the input
	  .txt file or through a ~/.dvd-slideshowrc file.  The heirarchy
	  is as follows: 
	  program defaults --> ~/.dvd-slideshowrc --> command-line --> input file variables
	  So the input file will over-ride your personal settings, etc.
	  The following variable are supported (with this syntax):
	   
	  debug=1       # 0 (low=default), 1 (some debug info), 2 (per frame info), 3 (function info)
	  pal=0  	# 0=ntsc 1=pal
	  ac3=1         # 0=mp2 audio 1=ac3 audio
	  copy=0        # add copies of original images to the output directory
	  autocrop=1    # autocrop images to fill full screen

	  font_dir="/usr/share/fonts"
	  font='n019004l.pfb' # helvetica bold URW font is default, but you should specify full path.

	  ## Subtitle:
	  subtitle_font_size=24

	  ## Title:
	  title_font_size=48
	  title_font_color="black"  # or use hex "#RRGGBB"

	  ## top title:
	  toptitle_font_size=48
	  toptitle_font_color="black"  # or use hex "#RRGGBB"
	  toptitle_bar_height=125  # 0 for no 50% white behind text
	  toptitle_text_location_x=80
	  toptitle_text_location_y=50

	  # bottom title: 
	  bottomtitle_font_size=36
	  bottomtitle_font_color="black"  # or use hex "#RRGGBB"
	  bottomtitle_bar_location_y=156 # relative to bottom of image
	  bottomtitle_bar_height=55  # 0 for no 50% white behind text
	  bottomtitle_text_location_x=0
	  bottomtitle_text_location_y=155
'

# -c      (pre-alpha do not use!)
#	  Add chapter selection sub-menu. (when used with dvd-menu)
#
# -B     (pre-alpha do not use!)
#	Add browsable slideshow in sub-menu. (when used with dvd-menu)
#	When browsing through the pictures, there will be no audio. 
#	99 slides maximum.
#
# -M 	(not working.  do not use)
#	  Render a medium-quality video.
#
# -border N	(not implemented yet!)
#	Add a border of N pixels around the image for better display
#	on TV screens which always seem to crop some of the picture.'
	echo '  '
}

if [ $# -lt 1 ]; then
	echo "[dvd-slideshow] ERROR: Too few arguments"
	help
	exit 1
fi


###################################################################
# Default variables
# order of perference:  
# program defaults --> ~.dvd-slideshowrc --> command-line args --> .txtfile settings

## setup program default variables (user configurable)
debug=0 # 0-2
pal=1  
copy=0
low_quality=0
#medium_quality=0  #default
high_quality=0
autocrop=0
ac3=1
border=0  # not implemented yet
subtitle_type="render"	# format of subtitles. other values make dvd-slideshow render them internally.
#subtitle_type="srt"	# format of subtitles. other values make dvd-slideshow render them internally.
font_dir="/usr/share/fonts/"
default_font1='n019004l.pfb' # helvetica bold URW fonts
default_font2='helb____.ttf' # helvetica bold truetype
	  ## Subtitle:
	  subtitle_font_size=24

	  ## Title:
	  title_font_size=48
	  title_font_color='black'  # or use hex "#RRGGBB"

	  ## top title:
	  toptitle_font_size=48
	  toptitle_font_color='black' # or use hex "#RRGGBB"
	  toptitle_bar_height=125  # 0 for no 50% white behind text
	  toptitle_text_location_x=80
	  toptitle_text_location_y=50

	  # bottom title: 
	  bottomtitle_font_size=36
	  bottomtitle_font_color="black"  # or use hex "#RRGGBB"
	  bottomtitle_bar_location_y=156 # relative to bottom of image
	  bottomtitle_bar_height=55  # 0 for no 50% white behind text
	  bottomtitle_text_location_x=0
	  bottomtitle_text_location_y=155

logfile='dvd-slideshow.log'

##################################################################################
## not user configurable:
verbosity=0  # for mpeg2enc and such
slideshow_name=""
titletext=""
i_audio=0
j_audio=0
write_chap=0
subtitle_number=0
n=0
m=0
new_vob=0
browse_num=0
submenu=0
write_chaps=0
chapmenu=0
browsable=0
# these vars assist 'yuvcat' mode
yuvcat=1                    # tells if we're in yuvcat mode
yuvpid=0                    # pid of child mpeg2enc process
yuvfirstfile=1              # tells when to strip yuv headers
mpegid=0
subtitle_file="subtitles.srt"
write_last_subtitle=0
commandline_audiofiles=0
nocleanup=0
smp=0
function_error=0

####  read in user rc file, if it exists:
if [ -f "${HOME}/.dvd-slideshowrc" ] ; then
	myecho "[dvd-slideshow] Reading default variables in ${HOME}/.dvd-slideshowrc"
	tmptxtfile="tmp_txtfile.txt"
	total_lines=`wc -l "$input_txtfile" | awk '{print $1}'`
	total_lines=$(( $total_lines + 1 ))
	line=1
	while [ $line -ne $total_lines -a $total_lines -ne 0 ];
	do
	  thisline=`sed -n "$line"p "${HOME}/.dvd-slideshowrc"`
	  set_system_variables "${thisline}" 1  # do not print out results
	  set_variables "${thisline}" 1  # do not print out results
  	  line=$(( $line + 1 ))
	done
fi


theargs="$*"
## command-line settings:
for arg
do
	case "$arg" in
	-i) shift; image[$n]="$1"; let n=$n+1; shift;;
	-o) shift; outdir="${1%%/}"; shift ;; # ${1%%/} omits trailing slash from outdir
	-b) shift; bgfile="$1"; shift ;;
	-n) shift; slideshow_name="$1"; shift ;;
	-t) shift; time_per_picture="$1"; shift ;;  ## in tenths or hundredths of seconds?
#	-T) shift; titletext="$1"; shift ;;   ## need to specify this in the file
	-f) shift; input_txtfile="$1"; shift
                if [ ! -f "$input_txtfile" ] ; then
                echo "[dvd-slideshow] ERROR: Input file $input_txtfile does not exist."
                exit 1
                fi ;;
	-p) shift; pal=1 ;;  # use pal format
	-r) shift; autocrop=1 ;;  # autocrop landscape-oriented images
#	-border) shift; border="$1" ;;  # add border around image
	-C) shift; copy=1 ;;  # make backup copy of all pictures passed. 
#	-s) shift; submenu=1 ;;  # create a sub-menu with options (not working yet)
#	-c) shift; chapmenu=1 ; submenu=1 ;;  # create a chapter select sub-menu (implies submenu)
	-writechaps) shift; write_chaps=1 ;;  # Write out chapter times to $slideshow_name.chap
#	-B) shift; browsable=1 ; submenu=1 ;;  # create a browsable slideshow (not working)
	-L) shift; low_quality=1 ;;  # use low-quality mode
#	-M) shift; medium_quality=1 ;;  # use medium-quality mode (this will be default)
	-H) shift; high_quality=1 ;;  # ALPHA.  use high-quality mode (This might take much longer to process in the future)
	-mp2) shift; ac3=0 ;;  # use mp2 audio
	-ac3) shift; ac3=1 ;;  # use ac3 audio
	-smp) shift; smp=1 ;;  # use multi-threaded mode (might crash on slow machines?)
	-nocleanup) shift; nocleanup=1 ;;  # leave all temp files
	-V) shift; debug="$1"; shift ;;
	-a) shift; 
                # make sure the file exists and is the correct type!
                suffix=`echo "$1" | awk -F. '{print tolower($NF)}'`
                if [ "$suffix" == 'ogg' ] || [ "$suffix" == 'mp3' ] || [ "$suffix" == 'wav' ] ; then
                	if [ ! -f "$1" ] ; then
                       	 echo "[dvd-slideshow] ERROR: File $1 does not exist"
                         exit 1
                        fi
                        passed_audio[$m]="$1"
                        let m=$m+1
			commandline_audiofiles=$(( $commandline_audiofiles + 1 ))
                        shift;
                else
                       	 echo "[dvd-slideshow] ERROR: File $1 is not an ogg, mp3, or wav file."
                         exit 1
                fi ;;
	-h) help ; exit 0 ; shift ;;
	-?) help ; exit 0 ; shift ;;
	-help) help ; exit 0 ; shift ;;
	-version) echo "$version" ; exit 0 ; shift ;;
	esac
done

##################################################################
### no more user input after this line?

###################################################################
## Functions:

myecho ()
{
	## use this version of echo to write to screen and to the logfile:
	echo "$*"
	echo "$*" >> "$outdir/$logfile"
}

logecho ()
{
	## use this version of echo to write to the logfile:
	echo "$*" >> "$outdir/$logfile"
}

myechon ()
{
	## use this version of echo to write to screen and to the logfile:
	echo -n "$*"
	echo -n "$*" >> "$outdir/$logfile"
}


## check_rm checks to see if the file exists before it's deleted:
check_rm ()
{
	if [ -f "$1" ] ; then
		rm "$1"
	fi
}

cleanup ()
{
if [ "$nocleanup" -eq 0 ] ; then
	## clean up temporary files
	myecho "[dvd-slideshow] cleanup..."
	check_rm temp_slideshow_image.ppm ; check_rm temp.ppm
	check_rm temp_slideshow_image_scaled.ppm
	check_rm "$tmpdir/slideshow_background.ppm"
	check_rm "$tmpdir/slideshow_background.mpc"
	check_rm "$tmpdir/slideshow_background.cache"
	check_rm "$tmpdir/title_background.png"
#	check_rm "$tmpdir/${slideshow_name}.chap"
	check_rm "$tmpdir/${slideshow_name}".spumux
#	check_rm "$tmpdir/"
	check_rm "$tmpdir/trash.txt"
	check_rm "$tmpdir/browse.spumux"
	check_rm "$tmpdir/$subtitle_file"
	check_rm "$tmpdir/subtitle.png"
	check_rm "$tmpdir/dvd_title.png"; check_rm "$tmpdir/dvd_title_2.png"
	check_rm "$tmpdir/video.mpg"
	check_rm "$tmpdir/video_0.mpg"
	check_rm "$tmpdir/audio1.mp2"; check_rm "$tmpdir/audio2.mp2"
	check_rm "$tmpdir/audio1.wav"; check_rm "$tmpdir/audio2.wav"
	check_rm "$tmpdir/audio.raw"; check_rm "$tmpdir/audio_new.raw"
	check_rm "$tmpdir/box.png"
	check_rm "$tmpdir/up_arrow.png"; check_rm "$tmpdir/left_arrow.png"; check_rm "$tmpdir/right_arrow.png"
	check_rm "$tmpdir/up_arrow_mask.png"; check_rm "$tmpdir/left_arrow_mask.png"; check_rm "$tmpdir/right_arrow_mask.png"
	check_rm "$tmpdir/menu_ur.png"; check_rm "$tmpdir/menu_lur.png"; check_rm "$tmpdir/menu_lu.png"
	check_rm "$tmpdir/menu_mask_ur.png"; check_rm "$tmpdir/menu_mask_lur.png"; check_rm "$tmpdir/menu_mask_lu.png"
	check_rm "$tmpdir/temp.png"; check_rm "$tmpdir/temp2.png"
	check_rm "$tmpdir/audio1.ac3"; check_rm "$tmpdir/audio2.ac3"
	check_rm "$tmpdir/temp_slideshow_image.png"
	check_rm "$tmpdir/temp_slideshow_image.mpc"
	check_rm "$tmpdir/temp_slideshow_image.cache"
	check_rm "$tmpdir/temp_slideshow_image_scaled.jpg"
	check_rm "$tmpdir/temp_slideshow_image_scaled.mpc"
	check_rm "$tmpdir/temp_slideshow_image_scaled.cache"
	check_rm "$tmpdir/title.ppm"
	check_rm "$tmpdir/temp.ppm"
	check_rm "$tmpdir/title1.ppm"
	check_rm "$tmpdir/kenburns_????.mpc" 
	check_rm "$tmpdir/kenburns_????.cache"
	check_rm "$outdir/$tmptxtfile"
	k=0
	dk=0
	for file in "${image[@]}"; do
 		[ $k -lt 1000 ] && dk="0$k" || dk=$k
 		[ $k -lt 100 ] && dk="00$k" || dk=$dk
 		[ $k -lt 10 ] && dk="000$k" || dk=$dk
		check_rm "$tmpdir/fade_$dk.ppm"
		check_rm "$tmpdir/audio1_$dk.wav"
		check_rm "$tmpdir/audio1_$dk.raw"
		check_rm "$tmpdir/audio2_$dk.wav"
		check_rm "$tmpdir/audio2_$dk.raw"
		check_rm "$tmpdir/slide_$k.ppm"
		check_rm "$tmpdir/slide_$k"_thumb.ppm
		check_rm "$tmpdir/slide_nav_$dk".ppm
		check_rm "$tmpdir/slide_$dk.mpg"
		check_rm "$tmpdir/subtitle_$k.png"
		check_rm "$tmpdir/slide_$k.mpc"
		check_rm "$tmpdir/slide_$k.cache"
		let k=$k+1
	done
        if [ "$yuvcat" -eq 1 ]; then
                check_rm "$tmpdir/$yuvfifo"
                if [ "$yuvpid" -ne 0 ]; then
                        kill -TERM $yuvpid
                fi
        fi
	## that should be everything.  Now try deleting tempdir:
	rm -r "$tmpdir"
fi
}

forcequit () ## function gets run when we have some sort of forcequit...
{
	## clean up temporary files
	cleanup
	exit
}

trap 'forcequit' INT
trap 'forcequit' KILL
trap 'forcequit' TERM

## check for the necessary programs:
checkforprog ()
{
        it=`which $1 2> /dev/null`
        if [ -z "$it" ] ; then
                myecho "[dvd-slideshow] ERROR: $1 not found! "
                myecho "[dvd-slideshow] Check the dependencies and make sure everything is installed."
                exit 1
        fi
}

checkfor_oggdec ()
{
        it=`which oggdec 2> /dev/null`
        if [ -z "$it" ] ; then
                myecho "[dvd-slideshow] ERROR: oggdec not found! "
                myecho "[dvd-slideshow] You need to download the vorbis-tools package"
		myecho "[dvd-slideshow] in order to use .ogg audio files."
                exit 1
        fi
}

checkfor_lame ()
{
        it=`which lame 2> /dev/null`
        if [ -z "$it" ] ; then
                myecho "[dvd-slideshow] ERROR: lame not found! "
                myecho "[dvd-slideshow] You need to download the lame package"
		myecho "[dvd-slideshow] in order to use .mp3 audio files."
                exit 1
        fi
}


rpmversion ()
{
	if [ -z `which rpm 2> /dev/null` ] ; then
		ver=''
	else
		ver=`rpm -q $1`
	fi
	if [ "`echo $ver | awk -F- '{print $1}'`" == "$1" ] ; then
		# rpm returned version of program
		vers=`echo $ver | awk -F- '{print $2}'`
#		echo "[dvd-slideshow] Found $1 version $vers"
	else
		# no rpm, try other methods
		vers=0  # no version found (yet)	
#		echo "[dvd-slideshow] Found $1"
	fi
	echo "$vers"  # returns 0 if no version found, but executable exists
}

hms ()
{
	## pass a number in thousandths of seconds and get back a 
	## time code of the form HR:MM:SS.XXX
	if [ -z "$1" ] ; then
		myecho "[dvd-slideshow] Error in hms function"	
		function_error=1
	else
		hours=$(( $1 / 3600000 )) ; [ $hours -eq 0 ] && hours="0" 
		it=$(( $1 - $hours * 3600000 ))
		minutes=$(( $it / 60000 )) ; [ $minutes -eq 0 ] && minutes="0" 
		it=$(( $1 - $minutes * 60000 ))
		seconds=$(( $it / 1000 )) ; [ $seconds -eq 0 ] && seconds="0" 
		thousandths=$(( $it - $seconds * 1000 )) ;
		characters=`echo "$thousandths" | wc --chars`
		if [ $characters -eq 1 ] ; then
			thousandths_out="000"  # empty string!
		elif [ $characters -eq 2 ] ; then
			thousandths_out="00$thousandths"  # 1 decimal place
		elif [ $characters -eq 3 ] ; then
			thousandths_out="0$thousandths"  # 2 decimal places
		elif [ $characters -eq 4 ] ; then
			thousandths_out="$thousandths"  # 3 decimal places
		else
			myecho "[dvd-slideshow] Error in hms function"	
			function_error=1
		fi
		it="$hours:$minutes:$seconds.$thousandths_out"
		echo "${it}"
	fi
}

#hmsss ()
#{
#	## pass a number in thousandths of seconds and get back a 
#	## time code of the form HR:MM:SS.XX0
#	if [ -z "$1" ] ; then
#		echo ''
#	else
#		hours=$(( $1 / 360000 )) ; [ $hours -eq 0 ] && hours="00" 
#		it=$(( $1 - $hours * 360000 ))
#		minutes=$(( $it / 6000 )) ; [ $minutes -eq 0 ] && minutes="00" 
#		it=$(( $1 - $minutes * 6000 ))
#		seconds=$(( $it / 100 )) ; [ $seconds -eq 0 ] && seconds="00" 
#		thousandths=$(( $it - $seconds * 100 )) ; [ $thousandths -eq 0 ] && thousandths="00" 
#		it="$hours:$minutes:$seconds.$thousandths"0
#		echo "${it}"
#	fi
#}

hms2seconds ()
{
	## pass a number in H:MM:SS.xxx and get back number of seconds
	if [ -z "$1" ] ; then
		echo ''
	else
		hours=`echo $1 | cut -d: -f1`
		minutes=`echo $1 | cut -d: -f2`
		seconds=`echo $1 | cut -d: -f3 | cut -d. -f1`
		fraction=`echo $1 | cut -d: -f3 | cut -d. -f2`
		characters=`echo "$fraction" | wc --chars`
		if [ "$characters" -eq 1 ] ; then ## no decimal was specified
			duration_ms="0"
		elif [ "$characters" -eq 2 ] ; then ## 1 decimal was specified
			duration_ms="$fraction"00
		elif [ "$characters" -eq 3 ] ; then ## 2 decimal was specified
			duration_ms="$fraction"0
		elif [ "$characters" -eq 4 ] ; then ## 3 decimal was specified. 
			duration_ms="$fraction"
		else
			echo "[dvd-slideshow] ERROR: Duration string $1 is bad."
			echo "[dvd-slideshow] 	Probably too many decimal places.  "
			echo '[dvd-slideshow]   There is no point specifying 0.0001 seconds."'
			# try rounding to only 3 decimal places?	
			function_error=1
		fi
		it=$(( $seconds + $minutes * 60 + $hours * 3600 ))
		## round up thousandths?
		echo "$it"."$duration_ms"
	fi
}


max ()
{
	## get the max of the arguments
	last_number=0
	for number
	do
		if [ "$number" -gt "$last_number" ] ; then
			last_number="$number"
		fi
	done
	echo "$last_number"
}

min ()
{
	## get the min of the arguments
	last_number=10000000000000000
	for number
	do
		if [ "$number" -lt "$last_number" ] ; then
			last_number="$number"
		fi
	done
	echo "$last_number"
}

addzeros ()
{
			[ $1 -lt 1000 ] && dj2="0$1" || dj2=$1
			[ $1 -lt 100 ] && dj2="00$1" || dj2=$dj2
			[ $1 -lt 10 ] && dj2="000$1" || dj2=$dj2
			echo "$dj2"
}

# strip every yuv file except the first
yuvstrip ()
{
       read junk
       cat
       return 0
}


encode ()
{
if [ "$yuvcat" -eq 0 ]; then
       if [ "$pal" -eq 1 ] ; then
               ppmtoy4m -v $verbosity -n "$frames" -r -S "$subsample" -F 25:1 -A 59:54 -I p "$tmpdir/slide_$i.ppm" | mpeg2enc $mpeg2enc_params -o "$tmpdir/slide_$di.mpg" >> "$outdir/$logfile" 2>&1
       else
               ppmtoy4m -v $verbosity -n "$frames" -r -S "$subsample" -F 30000:1001 -A 10:11 -I p "$tmpdir/slide_$i.ppm" | mpeg2enc $mpeg2enc_params -o "$tmpdir/slide_$di.mpg" >> "$outdir/$logfile" 2>&1
       fi
else  #yuvcat mode, so just write the yuv out to fd 3, which is the mpeg2enc process
       if [ "$pal" -eq 1 ] ; then
		if [ "$yuvfirstfile" -eq 1 ]; then
			yuvfirstfile=0
                    ppmtoy4m -v $verbosity -n "$frames" -r -S "$subsample" -F 25:1 -A 59:54 -I p "$tmpdir/slide_$i.ppm" >&3
		else
                    ppmtoy4m -v $verbosity -n "$frames" -r -S "$subsample" -F 25:1 -A 59:54 -I p "$tmpdir/slide_$i.ppm" | yuvstrip >&3
		fi
       else
		if [ "$yuvfirstfile" -eq 1 ]; then
	               yuvfirstfile=0
                   ppmtoy4m -v $verbosity -n "$frames" -r -S "$subsample" -F 30000:1001 -A 10:11 -I p "$tmpdir/slide_$i.ppm" >&3
		else
                   ppmtoy4m -v $verbosity -n "$frames" -r -S "$subsample" -F 30000:1001 -A 10:11 -I p "$tmpdir/slide_$i.ppm" | yuvstrip >&3
		fi
       fi
fi
}


encode_menu ()
{
if [ "$pal" -eq 1 ] ; then
        ppmtoy4m -v 0 -n 1 -r -S "$subsample" -F 25:1 -A 59:54 -I p "$1" | \
	mpeg2enc $mpeg2enc_params -o "$tmpdir/menu.mpg" >> "$outdir/$logfile" 2>&1
else
        ppmtoy4m -v 0 -n 1 -r -S "$subsample" -F 30000:1001 -A 10:11 -I p "$1" | \
	mpeg2enc $mpeg2enc_params -o "$tmpdir/menu.mpg" >> "$outdir/$logfile" 2>&1
fi
}

encode_fade ()
{
if [ "$yuvcat" -eq 0 ]; then
	## xargs is required since cat can't seem to cat more than about 1000 frames at a time.
       if [ "$pal" -eq 1 ] ; then
               find "$tmpdir" -name fade\*.ppm -type f -print0 | sort -z -d | xargs -0 cat | ppmtoy4m -v $verbosity -n 0 -S "$subsample" -F 25:1 -A 59:54 -I p | mpeg2enc $mpeg2enc_params -o "$tmpdir/slide_$di.mpg" >> "$outdir/$logfile" 2>&1
       else
               find "$tmpdir" -name fade\*.ppm -type f -print0 | sort -z -d | xargs -0 cat | ppmtoy4m -v $verbosity -n 0 -S "$subsample" -F 30000:1001 -A 10:11 -I p | mpeg2enc $mpeg2enc_params -o "$tmpdir/slide_$di.mpg" >> "$outdir/$logfile" 2>&1
       fi
else  #in yuvcat mode, write the yuv out to fd 3, which is the mpeg2enc process
       if [ "$pal" -eq 1 ] ; then
		if [ "$yuvfirstfile" -eq 1 ]; then
               		yuvfirstfile=0
                   find "$tmpdir" -name fade\*ppm -type f -print0 | sort -z -d | xargs -0 cat | ppmtoy4m -v $verbosity -n 0 -S "$subsample" -F 25:1 -A 59:54 -I p >&3
		else
                   find "$tmpdir" -name fade\*ppm -type f -print0 | sort -z -d | xargs -0 cat | ppmtoy4m -v $verbosity -n 0 -S "$subsample" -F 25:1 -A 59:54 -I p | yuvstrip >&3
		fi
       else
		if [ "$yuvfirstfile" -eq 1 ]; then
               		yuvfirstfile=0
                   find "$tmpdir" -name fade\*.ppm -type f -print0 | sort -z -d | xargs -0 cat | ppmtoy4m -v $verbosity -n 0 -S "$subsample" -F 30000:1001 -A 10:11 -I p | cat >&3
		else
#                   cat "$tmpdir"/fade_*.ppm | ppmtoy4m -v $verbosity -n 0 -S "$subsample" -F 30000:1001 -A 10:11 -I p | yuvstrip >&3
                   find "$tmpdir" -name fade\*.ppm -type f -print0 | sort -z -d | xargs -0 cat | ppmtoy4m -v $verbosity -n 0 -S "$subsample" -F 30000:1001 -A 10:11 -I p | yuvstrip >&3
		fi
       fi
fi
}

waitforfile ()
{
	# $1 is the filename
	## wait for the file to exist...
	while [ ! -f "$1" ] 
	do
		sleep 1s
	done
}

waitforfiles ()
{
	# $1 is the filename (with path)
	# $2 is the max digits in the series
	# $1_$2.ppm
	## wait for all files in a fade to exist...
	dir_tmp=`dirname "$1"`
	for i_tmp in `seq 1 $2` ; do
		di_tmp=`addzeros $i_tmp`
		newfile_tmp="$1"_$di_tmp.ppm
		while [ ! -f "$newfile_tmp" ] 
		do
			sleep 1s
		done
	done
}

extracopies ()
{
	this_frame=$1
	total_frames=$2
	waitforfile "$tmpdir/fade_$dj.ppm" 
#	if [ "$low_quality" -eq 1 ] ; then  # fix bug on my machine
#		sleep 2s
#	fi

	if [ $stepsize -gt 1 ] ; then
		if [ $this_frame -eq $total_frames ] ; then
			## last frame in sequence, don't make any copies!
			echo -n ''
		elif [ $this_frame -gt $(( $total_frames - $stepsize )) ] ; then
			## make ( $total_frames - $this_frame ) copies
			for it in `seq 1 $(( $total_frames - $this_frame ))`; do
				dj2=`addzeros $(( $this_frame + $it ))`
				cp "$tmpdir/fade_$dj.ppm" "$tmpdir/fade_$dj2.ppm"
				waitforfile "$tmpdir/fade_$dj2.ppm"   # need on slow systems?
			done
		else
			## loop over number of copies = stepsize-1
			for it in `seq 1 $(( $stepsize - 1 ))`; do
				dj2=`addzeros $(( $this_frame + $it ))`
				cp "$tmpdir/fade_$dj.ppm" "$tmpdir/fade_$dj2.ppm"
				waitforfile "$tmpdir/fade_$dj2.ppm"   # need on slow systems?
			done
		fi
	fi
}

duration2ms ()
{
	## break up the duration into the integer seconds and ms:
	local l_duration_sec=`echo $1 | awk -F. '{ print $1 }'`
	[ -z "$l_duration_sec" ] && l_duration_sec=0 
	local l_duration_ms=`echo $1 | awk -F. '{ print $2 }'`
	local l_characters=`echo "$l_duration_ms" | wc --chars`
	if [ -z "$l_duration_ms" ] ; then
		l_duration_ms=0 
	elif [ "$l_characters" -eq 1 ] ; then
		## no decimal was specified
		l_duration_ms=0
	elif [ "$l_characters" -eq 2 ] ; then
		## 1 decimal was specified
		l_duration_ms="$l_duration_ms"00
	elif [ "$l_characters" -eq 3 ] ; then
		## 2 decimal was specified
		l_duration_ms="$l_duration_ms"0
	elif [ "$l_characters" -eq 4 ] ; then
		## 3 decimal was specified. 
		echo -n ""	
	else
		myecho "[dvd-slideshow] ERROR: Duration string $1 is bad."
		myecho "[dvd-slideshow] 	Probably too many decimal places.  "
		myecho "[dvd-slideshow]   There is no point specifying more than 0.001 seconds."
		cleanup ; exit 1
	fi
	out_duration="$(( 1000 * $l_duration_sec + $l_duration_ms ))"
	echo "$out_duration"
}

nextslidename ()
{
	## get next slide:
	nextimage=''
	increment=1
	while [ $(( $i + $increment )) -le ${#image[@]} ] ; do
		image1="${image[$(($i+$increment))]}" ; dur1="${duration[$(($i+$increment))]}" ; image_file1=${image_file[$i+$increment]}
#		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		if [ $image_file1 -eq 1 ] || [ "$image1" == 'title' ] || [ "$image1" == 'titlebar' ] || ( [ "$image1" == 'background' ] && [ "$dur1" -ne 0 ] ) ; then
			nextimage="$image1"
			break
		else 
			## next line is not an image!
			increment=$(( $increment + 1 ))	
		fi
	done
	if [ -z "$nextimage" ] ; then
		myecho ""
		myecho '[dvd-slideshow] ERROR: Could not find a valid next slide'
		myecho '[dvd-slideshow]        This happens when a fade cannot locate a future image in your .txt file'
		myecho '[dvd-slideshow]	     Fix this in your input file and re-run dvd-slideshow.'
		cleanup; exit 0
	else
		echo "$nextimage"
	fi
}

nextslideincrement ()
{
	nextimage=''
	increment=1
	while [ $(( $i + $increment )) -le ${#image[@]} ] ; do
		image1="${image[$(($i+$increment))]}" ; dur1="${duration[$(($i+$increment))]}" ; image_file1=${image_file[$i+$increment]}
#		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		if [ $image_file1 -eq 1 ] || [ "$image1" == 'title' ] || [ "$image1" == 'titlebar' ] || ( [ "$image1" == 'background' ] && [ "$dur1" -ne 0 ] ) ; then
			nextimage="$image1"
			break
		else 
			## next line is not an image!
			increment=$(( $increment + 1 ))	
		fi
	done
	if [ -z "$nextimage" ] ; then
		myecho ""
		myecho '[dvd-slideshow] ERROR: Could not find a valid next slide'
		myecho '[dvd-slideshow]        This happens when a fade cannot locate a future image in your .txt file'
		myecho '[dvd-slideshow]	     Fix this in your input file and re-run dvd-slideshow.'
		cleanup; exit 0
	else
		echo "$increment"
	fi
}

previousslideppm ()
{
	## get previous image:
	if [ -f "$tmpdir/slide_$(($i-1)).ppm" ] ; then
		previousimage="$tmpdir/slide_$(($i-1)).ppm"
	elif [ -f "$tmpdir/slide_$(($i-2)).ppm" ] ; then
		previousimage="$tmpdir/slide_$(($i-2)).ppm"
	elif [ -f "$tmpdir/slide_$(($i-3)).ppm" ] ; then
		previousimage="$tmpdir/slide_$(($i-3)).ppm"
	else 
		## previous line is not an image!
		myecho ""
		myecho '[dvd-slideshow] ERROR: Could not find a valid previous image'
		myecho '[dvd-slideshow]	     This happens when a fade cannot locate a previous image in your .txt file'
		myecho '[dvd-slideshow]	     Fix this in your input file and re-run dvd-slideshow.'
		cleanup; exit 0
	fi
	echo "$previousimage"
}

titlebarslide ()
{
	## $1 contains the head title, and $2 contains the sub-title
	local title1="$1"
	local title2="$2"
	# figure out actual coordinates:
	if [ "$low_quality" -eq 1 ] ; then
		## top title:
		local f_toptitle_font_size=$(( $toptitle_font_size / 2 ))
		local f_toptitle_bar_height=$(( $toptitle_bar_height / 2 ))
		local f_toptitle_text_location_x=$(( $toptitle_text_location_x / 2 ))
		local f_toptitle_text_location_y=$(( $toptitle_text_location_y / 2 ))
		# bottom title:
		local f_bottomtitle_font_size=$(( $bottomtitle_font_size / 2 ))
		local f_bottomtitle_bar_location_y=$(( $bottomtitle_bar_location_y / 2 ))
		local f_bottomtitle_bar_height=$(( $bottomtitle_bar_height / 2 ))
		local f_bottomtitle_text_location_x=$(( $bottomtitle_text_location_x / 2 ))
		local f_bottomtitle_text_location_y=$(( $bottomtitle_text_location_y / 2 ))
	else
		local f_toptitle_font_size=$(( $toptitle_font_size ))
		local f_toptitle_bar_height=$(( $toptitle_bar_height ))
		local f_toptitle_text_location_x=$(( $toptitle_text_location_x ))
		local f_toptitle_text_location_y=$(( $toptitle_text_location_y ))
		# bottom title:
		local f_bottomtitle_font_size=$(( $bottomtitle_font_size ))
		local f_bottomtitle_bar_location_y=$(( $bottomtitle_bar_location_y ))
		local f_bottomtitle_bar_height=$(( $bottomtitle_bar_height ))
		local f_bottomtitle_text_location_x=$(( $bottomtitle_text_location_x ))
		local f_bottomtitle_text_location_y=$(( $bottomtitle_text_location_y ))
	fi
	## now the title2 y-locations were specified relative to the bottom of the image
	## but imagemagick needs them relative to the top of the image:
	f_bottomtitle_bar_location_y=$(( $dvd_height - $f_bottomtitle_bar_location_y ))
	f_bottomtitle_text_location_y=$(( $dvd_height - $f_bottomtitle_text_location_y ))
	local title2_bgtop=$f_bottomtitle_bar_location_y
	local title2_bgbot=$(( $f_bottomtitle_bar_location_y + $f_bottomtitle_bar_height ))

	if [ -z "$title1" ] && [ -z "$title2" ] ; then
		myecho "[dvd-slideshow] ERROR: No title text was found. Syntax:"
		myecho "[dvd-slideshow]        titlebar:duration:TopTitle:BottomTitle"
		cleanup; exit 1
	fi
	check_rm "$tmpdir/title1.ppm"

	if [ -n "$title1" ] ; then  # title1 exists
		if [ "$f_toptitle_bar_height" -ne 0 ] ; then
			convert -size "$resolution" xc:transparent -fill white \
		       	-draw "Rectangle 0,0,$dvd_width,$f_toptitle_bar_height" miff:- | \
			composite -compose src-over -type TrueColor -depth 8 -dissolve 50 - \
			"$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"	
		else
			cp "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"
		fi
		convert -size "$resolution" xc:transparent -fill "$toptitle_font_color" \
		-pointsize "$f_toptitle_font_size" -gravity NorthWest $font \
		-draw "text $f_toptitle_text_location_x,$f_toptitle_text_location_y \"${title1}\"" miff:- | \
		composite -compose src-over -type TrueColor -depth 8 - \
		"$tmpdir/slide_$i.ppm" "$tmpdir/title1.ppm"
		cp "$tmpdir/title1.ppm" "$tmpdir/title.ppm"
	fi
	if [ -n "$title2" ] ; then # title2 exists
		if [ "$f_bottomtitle_bar_height" -ne 0 ] ; then
			convert -size "$resolution" xc:transparent -fill white -quality 100\
			-draw "Rectangle 0,$title2_bgtop,$dvd_width,$title2_bgbot" "$tmpdir/title_background.png"
		else
			convert -size "$resolution" xc:transparent "$tmpdir/title_background.png"
		fi
		if [ -f "$tmpdir/title1.ppm" ] ; then # use title1 image
			composite -compose src-over -type TrueColor -depth 8 -dissolve 50 -quality 100 "$tmpdir/title_background.png" \
			"$tmpdir/title1.ppm" "$tmpdir/slide_$i.ppm"	
		else  # use background image (no first title)
			composite -compose src-over -type TrueColor -depth 8 -dissolve 50 -quality 100 "$tmpdir/title_background.png" \
			"$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"	
		fi
		convert -size "$resolution" xc:transparent -fill "$bottomtitle_font_color" \
			-pointsize "$f_bottomtitle_font_size" -gravity North $font \
			-draw "text $f_bottomtitle_text_location_x,$f_bottomtitle_text_location_y \"${title2}\"" miff:- | \
		composite -compose src-over -type TrueColor -depth 8 - \
			"$tmpdir/slide_$i.ppm" "$tmpdir/title.ppm"
	fi
	check_rm "$tmpdir/title1.ppm"
}

titleslide ()
{
	## $1 contains the title
	title="$1"
	if [ -z "$title" ] ; then
		myecho "[dvd-slideshow] ERROR: No title text was found. Syntax:"
		myecho "[dvd-slideshow]        title:duration:Title_text"
		cleanup; exit 1
	fi
	check_rm "$tmpdir/title.ppm"

	if [ "$low_quality" -eq 1 ] ; then
		local f_title_font_size=$(( $title_font_size / 2 ))
	else
		local f_title_font_size=$(( $title_font_size ))
	fi
	## if background is black and font color is black, change font color to white
	if [ "$bgfile" == 'black' ] && [ "$title_font_color" == 'black' ] ; then
		title_font_color='white'
	fi

#		it=`echo "${subtitle[$i]}" | awk -F'\\' '{print $2}' | cut -c 1`
#		if [ "$it" == 'n' ] ; then
	## check to see if we find any user-specified breaks \n
	it=`echo "$title" | awk -F'\\' '{print $2}' | cut -c 1`
	if [ "$it" == 'n' ] ; then
		logecho "[dvd-slideshow] Found \\n in title"
		# user entered a \n to force line wraps
		# break lines at line wraps
		title1=`echo "${title}" | awk -F'\\' '{print $1}'`
		title2=`echo "${title}" | awk -F'\\' '{print $2}' | cut -c 2-`
		convert -size "$resolution" xc:transparent -fill $title_font_color \
		-pointsize $f_title_font_size -gravity Center $font -annotate 0 "$title1\n$title2" miff:- | \
		composite -compose src-over -type TrueColor -depth 8 - \
		"$tmpdir/slideshow_background.ppm" "$tmpdir/title.ppm"
	else	# no forced line wraps.  Eventually Check for long lines
		convert -size "$resolution" xc:transparent -fill $title_font_color \
		-pointsize $f_title_font_size -gravity Center $font -draw "text 0,0 \"${title}\"" miff:- | \
		composite -compose src-over -type TrueColor -depth 8 - \
		"$tmpdir/slideshow_background.ppm" "$tmpdir/title.ppm"
	fi
}

checkforautocrop ()
{
	if [ "$autocrop" -eq 1 ] ; then
		# figure out whether to autocrop the image or not
	        image_width=`imagewidth "$1"`
	        image_height=`imageheight "$1"`
	        ratio="$(( 100* $image_width / $image_height ))"
	        out_ratio="$(( 100* $dvd_width / $dvd_height ))"
		do_autocrop_w=0 ; do_autocrop_h=0
		out_ratio_plus=$(( $out_ratio + 30 ))
		out_ratio_minus=$(( $out_ratio - 30 ))
		if [ "$ratio" -gt $out_ratio_minus ] && [ $ratio -lt $out_ratio_plus ]; then
			## if ratio is +/- 30 from output ratio 
			if [ "$ratio" -lt "$(( $out_ratio ))" ] ; then
				do_autocrop_h=1 # image too wide, crop height
			elif [ "$ratio" -gt "$(( $out_ratio ))" ] ; then
				do_autocrop_w=1 # image too tall, crop width
			fi
		fi
		[ $debug -ge 3 ] && myecho "[dvd-slideshow:checkforautocrop] image_width=$image_width image_height=$image_height ratio=$ratio out_ratio=$out_ratio"
		[ $debug -ge 3 ] && myecho "[dvd-slideshow:checkforautocrop] do_autocrop_w=$do_autocrop_w  do_autocrop_h=$do_autocrop_h"
	else
		do_autocrop_h=0 ; do_autocrop_w=0
	fi
}

background ()
{
		## input is:  $1 = effect/image
		# output is written to "$tmpdir"/slideshow_background.ppm 
		bg="$1"
		if [ -f "$bg" ] ; then # if effect is a background file
			myecho "[dvd-slideshow] Creating background using ${bg}"
			checkforautocrop "$bg"
                       if [ "$do_autocrop_w" -eq 1 ]; then   
                               # autocrop background image width (width too large)
                               convert "${bg}" -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" \
                               -gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' -type TrueColor -depth 8 "$tmpdir"/slideshow_background.ppm
                       elif [ "$do_autocrop_h" -eq 1 ]; then
                               # autocrop background image height (height too large)
                               convert "${bg}" -resize "$sq_to_dvd_pixels" -resize "$dvd_width"x \
                               -gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' -type TrueColor -depth 8 "$tmpdir"/slideshow_background.ppm
                       else
                               #don't autorop
                               convert "${bg}" -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" -bordercolor black -border "$dvd_width"x240 \
                               -gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' -type TrueColor -depth 8 "$tmpdir"/slideshow_background.ppm
                       fi
			bgfile="$bg"
		elif [ "$bg" == 'black' ] ; then  # I guess we could add other types of backgrounds here!
			## use plain black background with no picture
			myecho "[dvd-slideshow] Creating black background"
			convert -size "$dvd_width"'x'"$dvd_height" xc:black -type TrueColor -depth 8 "$tmpdir"/slideshow_background.ppm
			bgfile="black"
		elif [ "$bg" == 'white' ] ; then  # I guess we could add other types of backgrounds here!
			## use plain white background with no picture
			myecho "[dvd-slideshow] Creating white background"
			convert -size "$dvd_width"'x'"$dvd_height" xc:white -type TrueColor -depth 8 "$tmpdir"/slideshow_background.ppm
			bgfile="white"
		elif [ "${bg:0:1}" == '#' ] ; then  # user passed a #RRGGBB hex color
			myecho "[dvd-slideshow] Creating $bg color background"
			convert -size "$dvd_width"'x'"$dvd_height" xc:"$bg" -type TrueColor -depth 8 "$tmpdir"/slideshow_background.ppm
			bgfile="hex"
		else
			myecho "[dvd-slideshow] ERROR: No background file specified!"
			myecho "[dvd-slideshow] 	Correct syntax is:"
			myecho "[dvd-slideshow] background:duration:subtitle:background_image_or_color"
			exit 1
		fi
#		convert "$tmpdir/slideshow_background.ppm" -type TrueColor -depth 8 "$tmpdir/slideshow_background.mpc"
}

coordinates_in_dvd_aspect_ratio_frame ()
{
	# dvd_width dvd_height image_width image_height x_coordinate y_coordinate
	#dvd_width=$1; dvd_height=$2
	#image_width=$3; image_height=$4
	#x_image_coordinate=$5 y_image_coordinate=$6
	# output: x_dvd_coordinate y_dvd_coordinate

	## calculate frame size after adding black side bars for portrait pictures:
	ratio=$(( 1000* $3 / $4 ))
	out_ratio=$(( 1000* $1 / $2 ))  
	if [ "$ratio" -gt "$(( $out_ratio ))" ] ; then
		# image width greater than output width at same scale
		new_image_width=$3
		new_image_height=`div10 $(( 10* $2 * $3 / $1 ))`
		x_dvd_coordinate=0
		y_dvd_coordinate=`div10 $(( 10*( $new_image_height - $4 ) / 2 ))`
	elif [ "$ratio" -le $(( $out_ratio )) ] ; then
		# image height greater than output height at same scale 
		new_image_width=`div10 $(( 10* $1 * $4 / $2 ))`
		new_image_height=$4
		y_dvd_coordinate=0
		x_dvd_coordinate=`div10 $(( 10*( $new_image_width - $3 ) / 2 ))`
	fi
	# calculate coordinate transformation by xi,yi
#	x_dvd_coordinate=$(( $x_image_coordinate - $xi ))
#	y_dvd_coordinate=$(( $y_image_coordinate - $yi ))
}

parse_window ()
{
	# pass a string $1 (kenburns start or end arguments)
	# and parse_window will output coordinates xc,yc,xw,yh
	## where xc,yc is the center of the image.  xw,yh is the width and height.
	## Parse the parameters for kenburns or crop effects
	# xi,yi is the top left corner of the image relative to the DVD frame
	# xw,yh are the width and height of the crop (must be even numbers)
	# xc,yc are the center coordinates of the image relative to the DVD frame
	# x0,y0 is the top left corner of the crop in the image frame.
	# x1,y1 is the bottom right corner of the crop in the image frame.
	# textfile format is:  
	# file:duration:comment:kenburns:xs0,ys0;xs1,ys1;xe0,ye0;xe1,ye1;[startangle,endangle]
	# or
	# file:duration:comment:kenburns:start 0%-100%;start_location;end 0%-100%;end_location;[startangle,endangle]
	# where 0%-100% indicates the fraction of the window width/height, and
	# where start_location and end_location can be:
	# 	topleft			topmiddle|top		topright
	#	middleleft|left		middle			middleright|right
	#	bottomleft		bottommiddle|bottom	bottomright
	# or
	# 	x%,y%
	#	where % is a percentage of the window width/height starting from the
	# 	top left corner of the screen.
	# or
	# 	imagewidth | imageheight
	#	where the window width or height will be scaled to fill the full
	#	width or height of the dvd screen.
	#	
	# ( angles not implemented yet! )
	# and the optional startangle,endangle parameters will allow for rotation of the image during
	# the kenburns effect.  Startangle is optional, and if omitted, will default to zero.
	# Positive numbers denote clockwise rotation, and negative numbers denote counter-clockwise rotation.
	# 

	it=`echo "$1" | awk -F';' '{print $1}' | awk -F% '{print NF}'`
	firstarg=`echo "$1" | awk -F';' '{print $1}'`
	image_width="`imagewidth "$2"`" 
	image_height="`imageheight "$2"`"
	## calculate frame size after adding black side bars for portrait pictures:
	ratio=$(( 1000* $image_width / $image_height ))
	out_ratio=$(( 1000* $dvd_width / $dvd_height ))  # doesn't change during script
	if [ "$ratio" -gt "$(( $out_ratio ))" ] ; then
		# image width greater than output width at same scale
		new_image_width=$image_width
		new_image_height=`div10 $(( 10* $dvd_height * $image_width / $dvd_width ))`
		xi=0
		yi=`div10 $(( 10*( $new_image_height - $image_height ) / 2 ))`
	elif [ "$ratio" -le $(( $out_ratio )) ] ; then
		# image height greater than output height at same scale 
		new_image_width=`div10 $(( 10* $dvd_width * $image_height / $dvd_height ))`
		new_image_height=$image_height
		yi=0
		xi=`div10 $(( 10*( $new_image_width - $image_width ) / 2 ))`
	fi
#	if [ $image_width -gt $image_height ] ; then
#		# landscape: width will be scaled to the output DVD width
#		#	top/bottom might have black bars
#		new_image_height=$(( $image_width * $dvd_height / $dvd_width ))
#		new_image_width=$image_width
#		xi=0
#		yi=`div10 $(( 10*( $new_image_height - $image_height ) / 2 ))`
#	else
#		# portrait: height will be scaled to the output DVD height
#		#	sides will have black bars
#		new_image_width=$(( $image_height * $dvd_width / $dvd_height ))
#		new_image_height=$image_height
#		yi=0
#		xi=`div10 $(( 10*( $new_image_width - $image_width ) / 2 ))`
#	fi
	if [ "$it" -eq 2 ] || [ "$firstarg" == 'imagewidth' ] || [ "$firstarg" == 'imageheight' ] ; then 
		## use "keywords"

		## first parse the zoom amount:
		loc=`echo "$1" | awk -F';' '{print $2}'`
		if [ "$firstarg" == 'imagewidth' ] ; then 
			# scale width to equal output dvd width:
			xw=$image_width
			yh=`div10 $(( 10 * $dvd_height * $xw / $dvd_width ))`
		elif [ "$firstarg" == 'imageheight' ] ; then 
			# scale height to equal output dvd width:
			yh=$image_height
			xw=`div10 $(( 10 *$dvd_width * $yh / $dvd_height ))`
		else
			zoom_percent=`echo "$1" | awk -F';' '{print $1}' | awk -F% '{print $1}'`
			[ $debug -ge 3 ] && myecho "[dvd-slideshow:parse_window] zoom=$zoom_percent, loc=$loc "
			xw=`div10 $(( 10 * $new_image_width * $zoom_percent / 100 ))`
			yh=`div10 $(( 10 * $new_image_height * $zoom_percent / 100 ))`
		fi
		## next line is because we want the zoom % coordinates to be relative to the
		## whole screen size, so if you have a tall, narrow picture, 50% will mean
		## half of the height, etc...	
		# now, calculate the actual coordinates:
		[ $debug -ge 3 ] && myecho "[dvd-slideshow:parse_window] xw=$xw yh=$yh"

		## middle calculations are for using the "middle" keywords:
		ymiddle0=`div10 $(( 10 *$new_image_height / 2 - 10 *$yh / 2 ))`
		ymiddle1=`div10 $(( 10 *$new_image_height / 2 + 10 *$yh / 2 ))`
		xmiddle0=`div10 $(( 10 *$new_image_width / 2 - 10 *$xw / 2 ))`
		xmiddle1=`div10 $(( 10 *$new_image_width / 2 + 10 *$xw / 2 ))`
		[ $debug -ge 3 ] && myecho "[dvd-slideshow:parse_window] ymiddle0=$ymiddle0 ymiddle1=$ymiddle1  xmiddle0=$xmiddle0 xmiddle1=$xmiddle1"

		## now parse the box location:
		it=`echo "$1" | awk -F';' '{print $2}' | awk -F% '{print NF}'`
		if [ "$it" -ge 2 ] ; then # second arg contains a %
			# location is specified a a percent of the window size
			xcenter_pct=`echo "$1" | awk -F';' '{print $2}' | awk -F',' '{print $1}' | awk -F% '{print $1}'`
			ycenter_pct=`echo "$1" | awk -F';' '{print $2}' | awk -F',' '{print $2}' | awk -F% '{print $1}'`
#			[ $debug -ge 3 ] && myecho "[dvd-slideshow] xcenter_pct=$xcenter_pct ycenter_pct=$ycenter_pct"
			[ -z "$xcenter_pct" ] && (myecho '[dvd-slideshow] Error: bad xcenter percentage' ; cleanup; exit 1)
			[ -z "$ycenter_pct" ] && (myecho '[dvd-slideshow] Error: bad ycenter percentage' ; cleanup; exit 1)
			xcenter=`div10 $(( 10 * $new_image_width * $xcenter_pct / 100 ))`
			ycenter=`div10 $(( 10 * $new_image_height * $ycenter_pct / 100 ))`
#			[ $debug -ge 3 ] && myecho "[dvd-slideshow:parse_window] xcenter=$xcenter ycenter=$ycenter"
			x0=$(( $xcenter - $xw / 2 )) ; x1=$(( $xcenter + $xw / 2 ))
			y0=$(( $ycenter - $yh / 2 )) ; y1=$(( $ycenter + $yh / 2 ))
		elif [ "$loc" == 'topleft' ] ; then
			x0=0; x1=$xw
			y0=0; y1=$yh
		elif [ "$loc" == 'middleleft' ] || [ "$loc" == 'left' ] ; then
			x0=0; x1=$xw
			y0=$ymiddle0; y1=$ymiddle1
		elif [ "$loc" == 'bottomleft' ] ; then
			x0=0; x1=$xw
			y0=$(( $new_image_height - $yh )) ; y1=$new_image_height
		elif [ "$loc" == 'topmiddle' ] || [ "$loc" == 'top' ] ; then
			x0=$xmiddle0; x1=$xmiddle1
			y0=0; y1=$yh
		elif [ "$loc" == 'middle' ] || [ "$loc" == 'center' ] ; then
			x0=$xmiddle0; x1=$xmiddle1
			y0=$ymiddle0; y1=$ymiddle1
		elif [ "$loc" == 'bottommiddle' ] || [ "$loc" == 'bottom' ] ; then
			x0=$xmiddle0; x1=$xmiddle1
			y0=$(( $new_image_height - $yh )) ; y1=$new_image_height
		elif [ "$loc" == 'topright' ] ; then
			x0=$(( $new_image_width - $xw )) ; x1=$new_image_width
			y0=0; y1=$yh
		elif [ "$loc" == 'middleright' ] || [ "$loc" == 'right' ] ; then
			x0=$(( $new_image_width - $xw )) ; x1=$new_image_width
			y0=$ymiddle0; y1=$ymiddle1
		elif [ "$loc" == 'bottomright' ] ; then
			x0=$(( $new_image_width - $xw )) ; x1=$new_image_width
			y0=$(( $new_image_height - $yh )) ; y1=$new_image_height
		else	
			myecho "[dvd-slideshow] Error: bad syntax in kenburns/crop location: $loc"
			cleanup; exit 1
		fi
	else  # check for original format with explicit start/end coordinates:
		## coordinate system is relative to the actual picture, unscaled!!!
		## we need to convert this to the buffered (dvd aspect ratio) coordinate system!!!	
		x0=`echo "$1" | awk -F';' '{print $1}' | awk -F',' '{print $1}'`
		y0=`echo "$1" | awk -F';' '{print $1}' | awk -F',' '{print $2}'`
		x1=`echo "$1" | awk -F';' '{print $2}' | awk -F',' '{print $1}'`
		y1=`echo "$1" | awk -F';' '{print $2}' | awk -F',' '{print $2}'`

		
		# width and height of area passed:
		xw=$(( $x1 - $x0 )) ; yh=$(( $y1 - $y0 ))

#		if [ "$x0" -lt "$image_width" ] ; then 
#			# x start is inside image
#		else
#			# scale width to equal output dvd width:
#			xw=$image_width
#			yh=$(( $dvd_height * $xw / $dvd_width )) 
#		fi
#
#		if [ "$yh" -lt "$image_height" ] ; then 
#			# y coordinates are inside image
#		else
#			# scale height to equal output dvd width:
#			yh=$image_height
#			xw=$(( $dvd_width * $yh / $dvd_height ))
#		fi
#
#		xi0=$(( $x0-$xi )); yi0=$(( $y0-$yi )) 
#		xi1=$(( $x1-$xi )); yi1=$(( $y1-$yi )) 
#		[ $debug -ge 3 ] && myecho "[dvd-slideshow:parse_window] image crop coordinates=$xi0,$yi0 ; $xi1,$yi1"

		## make sure the image crop coordinates are not outside the image:
		[ $xi -eq 0 ] && x0=$x0 || x0=$(( $x0 + $xi ))
		[ $xi -eq 0 ] && x1=$x1 || x1=$(( $x1 + $xi ))
		[ $yi -eq 0 ] && y0=$y0 || y0=$(( $y0 + $yi ))
		[ $yi -eq 0 ] && y1=$y1 || y1=$(( $y1 + $yi ))
	fi
}

is_even ()
{
	# returns 0 or 1 depending on wether the number is even or not
	number=$1
	fraction=`expr $number % 2`
	if [ $fraction -eq 0 ] ; then
		echo "1"
	else
		echo "0"
	fi
}


todec000 ()
{
	factor_whole=$(( $1 / 1000 ))
	factor_dec=$(( $1 % 1000 ))
	if [ $factor_dec -lt 0 ] ; then
		factor_dec=$(( -1 * $factor_dec ))
	fi
	if [ ${#factor_dec} -eq 2 ] ; then
		factor_dec="0$factor_dec"
	elif [ ${#factor_dec} -eq 1 ] ; then
		factor_dec="00$factor_dec"
	elif [ ${#factor_dec} -eq 0 ] ; then
		factor_dec="000"
	fi
	echo "$factor_whole.$factor_dec"
}

div1000 ()
{
	# takes a number and divides by 1000, rounding appropriately
	number=$1
	whole=`expr $number / 1000`
	fraction=`expr $number % 1000`
	if [ $fraction -ge 500 ] ; then
		whole=$(( $whole + 1 ))  # round up
	fi
	echo $whole
}

div1000_2 ()
{
	# takes a number and divides by 1000, rounding to the nearest factor of 2
	number=$1
	whole=`expr $number / 2000`
	fraction=`expr $number % 2000`
	if [ $fraction -ge 1000 ] ; then
		whole=$(( 2* $whole + 2 ))  # round up
	else
		whole=$(( 2* $whole ))
	fi
	echo $whole
}

div1000_up ()
{
	# takes a number and divides by 1000, rounding up
	number=$1
	whole=`expr $number / 1000`
	fraction=`expr $number % 1000`
	if [ $fraction -ge 1 ] ; then
		whole=$(( $whole + 1 ))  # round up
	else
		whole=$(( $whole ))
	fi
	echo $whole
}

div10 ()
{
	# takes a number and divides by 10, rounding appropriately
	number=$1
	whole=`expr $number / 10`
	fraction=`expr $number % 10`
	if [ $fraction -ge 5 ] ; then
		whole=$(( $whole + 1 ))  # round up
	fi
	echo $whole
}

imagewidth ()
{
	it="`identify "$1" | awk -F'JPEG ' '{print $2}' | cut -d 'x' -f 1`"
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'PNM ' '{print $2}' | cut -d 'x' -f 1`"
	fi
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'PNG ' '{print $2}' | cut -d 'x' -f 1`"
	fi
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'MPC ' '{print $2}' | cut -d 'x' -f 1`"
	fi
	it="$(( $it * $sq_pixel_multiplier / 1000 ))"
	echo "$it"
}

imagewidth_sq ()
{
	it="`identify "$1" | awk -F'JPEG ' '{print $2}' | cut -d 'x' -f 1`"
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'PNM ' '{print $2}' | cut -d 'x' -f 1`"
	fi
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'PNG ' '{print $2}' | cut -d 'x' -f 1`"
	fi
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'MPC ' '{print $2}' | cut -d 'x' -f 1`"
	fi
	echo "$it"
}


imageheight ()
{
	it="`identify "$1" | awk -F'JPEG ' '{print $2}'  | cut -d 'x' -f 2 | cut -d ' ' -f 1`"
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'PNM ' '{print $2}'  | cut -d 'x' -f 2 | cut -d ' ' -f 1`"
	fi
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'PNG ' '{print $2}'  | cut -d 'x' -f 2 | cut -d ' ' -f 1`"
	fi
	if [ -z $it ] ; then
		it="`identify "$1" | awk -F'MPC ' '{print $2}'  | cut -d 'x' -f 2 | cut -d ' ' -f 1`"
	fi
	echo "$it"
}

crop_parameters ()
{
	# converts the crop parameters reference in the full dvd aspect ratio
	# frame back to the actual crop parameters needed in the original 
	# image frame.
	#
	# the input coordinates are relative to the original image size, buffered out to
	# the output dvd aspect ratio
	#	
	# using the parameters x0,y0 ; x1,y1 ; xi,yi in memory (x1000)
	# output is just the crop parameters:
	# c_width, c_height xc0,yc0  (for the actual crop)
	# and for the corresponding composite command:
	# xci,yci for the location of the top left corner of the cropped image
	# relative to the output window.
	#
	# top left corner of dvd window is 0,0
	# top left corner of image is at xi,yi   from parse_window
	# top left corner of the cropped image is at x0,y0
	#
	# i.e., the "i" reference frame is in the unbuffered image (image alone)
	
	##############################################
	## figure out the size of the window scaled to the original image size:
	ratio=$(( 1000* $image_width / $image_height ))
	out_ratio=$(( 1000* $dvd_width / $dvd_height ))  # doesn't change during script
#	if [ "$ratio" -gt "$(( $out_ratio ))" ] ; then
#		# image width greater than output width at same scale
#		newwidth=$image_width
#		newheight=$(( $dvd_height * $image_width / $dvd_width ))
#	elif [ "$ratio" -le $(( $out_ratio )) ] ; then
#		# image height greater than output height at same scale 
#		newwidth=$(( $dvd_width * $image_height / $dvd_height ))
#		newheight=$image_height
#	fi
#	out_ratio=$(( 1000* $newwidth / $newheight ))  # this number is correct
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] -- input: x0=`todec000 $x0` y0=`todec000 $y0` x1=`todec000 $x1` y1=`todec000 $y1`     xi=$xi yi=$yi (dvd window)"
#	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] width=$image_width height=$image_height new_width=$newwidth new_height=$newheight ratio=`todec000 $ratio` out_ratio=`todec000 $out_ratio`"

	##############################################
	## shift coordinate system to start at xi,yi: (all integers)
	xi0=$(( $x0- 1000*$xi )); yi0=$(( $y0- 1000*$yi )) # already x1000
	xi1=$(( $x1- 1000*$xi )); yi1=$(( $y1- 1000*$yi )) # already x1000
	w=$(( $xi1 - $xi0 )) # already x1000
	h=$(( $yi1 - $yi0 ))	 # already x1000
#	out_ratio=$(( $w / $h )) ## should be same as before because coordinate system transformation preserves this.
#	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] xi0,yi0=$xi0,$yi0 xi1,yi1=$xi1,$yi1   w=$w h=$h  ratio=$ratio out_ratio=$out_ratio"
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] xi0,yi0=`todec000 $xi0`,`todec000 $yi0` xi1,yi1=`todec000 $xi1`,`todec000 $yi1`   w=`todec000 $w` h=`todec000 $h`  ratio=`todec000 $ratio` out_ratio=`todec000 $out_ratio` (i=image ref frame)"

	##############################################
	## figure out where to crop the image:
	## (make sure the image crop coordinates are not outside the image)
	[ $xi0 -lt 0 ] && xc0=0 || xc0=$xi0 
	[ $xi1 -gt "$(( 1000 * $image_width ))" ] && xc1=$(( 1000 * $image_width )) || xc1=$xi1
	[ $yi0 -lt 0 ] && yc0=0 || yc0=$yi0
	[ $yi1 -gt "$(( 1000 * $image_height ))" ] && yc1=$(( 1000 * $image_height )) || yc1=$yi1
	c_width=$(( $xc1 - $xc0 )) ; c_height=$(( $yc1 - $yc0 )) # already x1000
	crop_ratio=$(( 1000 * $c_width / $c_height ))  
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] xc0,yc0=`todec000 $xc0`,`todec000 $yc0` xc1,yc1=`todec000 $xc1`,`todec000 $yc1`   c_width=`todec000 $c_width` c_height=`todec000 $c_height`   crop_ratio=$crop_ratio (crop params in image fr)"

	##############################################
	## where to put the top left corner of the cropped image relative to the background?
	deltax=$(( 1000 * 1000 * 1000 * $dvd_width / $c_width )); deltay=$(( 1000* 1000 * 1000 * $dvd_height / $c_height ))
	## rescale % will be the smaller of the two deltas: 
	[ $deltax -lt $deltay ] && rescale=$deltax || rescale=$deltay # already x1000
#myecho "[dvd-slideshow:cp] deltax=$deltax deltay=$deltay rescale=$rescale xi0=$xi0 yi0=$yi0"
	if [ $xi0 -lt 0 ] ; then
		## left of cropped image is in the middle of the dvd window
		xci=`div1000 $(( $rescale * -1 * $xi0 / 1000 ))`
	else
		## left of cropped image should be at x=0 afterward
		xci=0
	fi
	if [ $yi0 -lt 0 ] ; then  ###*  rescale=deltax
		## top of cropped image is in the middle of the dvd window
		yci=`div1000 $(( $rescale * -1 * $yi0 / 1000))`
	else
		## top of cropped image should be at y=0 afterward
		yci=0
	fi
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] xci0,yci0=`todec000 $xci`,`todec000 $yci`  c_width,c_height=`todec000 $c_width`,`todec000 $c_height` (location of cropped image in dvd window)"

#		myecho "[dvd-slideshow:crop_parameters] predicted resized_width=$predicted_resized_width resized_height=$predicted_resized_height"
#	fi 

	c_width=`div1000 $(( $xc1 - $xc0 ))` ; c_height=`div1000 $(( $yc1 - $yc0 ))`

#	echo "[dvd-slideshow:crop_parameters] crop_ratio=$crop_ratio out_ratio=$out_ratio"
	if [ "$crop_ratio" -gt $out_ratio ] ; then
		# image width greater than output width at same scale
		resized_width=$(( 1000 * $dvd_width ))
		resized_height=$(( 1000 * $c_height * $dvd_width / $c_width ))
	elif [ "$crop_ratio" -lt $out_ratio ] ; then
		# image height greater than output height at same scale 
		resized_height=$(( 1000 * $dvd_height ))
		resized_width=$(( 1000 * $c_width * $dvd_height / $c_height ))
	else # crop_ratio = out_ratio.  good.
		resized_height=$(( 1000 * $dvd_height ))
		resized_width=$(( 1000 * $dvd_width ))
	fi
	predicted_resized_width=`div1000 $resized_width`
	predicted_resized_height=`div1000 $resized_height`
#	myecho "[dvd-slideshow:crop_parameters] resized_width=`todec000 $resized_width` resized_height=`todec000 $resized_height` diff=$diff"
#	myecho "[dvd-slideshow:crop_parameters] predicted resized_width=$predicted_resized_width resized_height=$predicted_resized_height"
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] output: xc0,yc0=$xc0,$yc0 xc1,yc1=$xc1,$yc1 c_width,c_height=$c_width,$c_height ratio=$crop_ratio $out_ratio  xci,yci=$xci,$yci"
	xc0_dec=`todec000 $xc0 | awk -F. '{print $2}'`
	yc0_dec=`todec000 $yc0 | awk -F. '{print $2}'`
	xc0_whole=$(( $xc0 / 1000 )); yc0_whole=$(( $yc0 / 1000 ))
#	xc0=`div1000 $xc0` ; yc0=`div1000 $yc0`  # rounding was causing problems... need to round down.
	xc0=$(( $xc0 / 1000 )) ; yc0=$(( $yc0 / 1000 ))
	xci=`div1000 $xci` ; yci=`div1000 $yci`  # rounding might cause problems.  watch this.
	## make sure xci + predicted_resized_width < dvd_width 
	## and yci + predicted_resized_height < dvd_height
	if [ $(( $yci + $predicted_resized_height )) -gt $dvd_height ] ; then
		yci=$(( $yci - 1 ))
#		myecho "[dvd-slideshow:crop_parameters] Correcting yci - 1 "
	fi
	if [ $(( $xci + $predicted_resized_width )) -gt $dvd_width ] ; then
		xci=$(( $xci - 1 ))
#		myecho "[dvd-slideshow:crop_parameters] Correcting xci - 1 "
	fi
#	w=`div1000 $w` ; h=`div1000 $h`
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:crop_parameters] output: c_width,c_height=$c_width,$c_height ratio=$crop_ratio $out_ratio xc0,yc0=$xc0,$yc0 xci,yci=$xci,$yci"
	# used output is:
	# xc0,yc0 (coordinates of the top left corner of the image crop in the image frame)
	# c_width,c_height (crop width and height in the image frame)
	# xi0,yi0 (coordinates of where to put the top left corner of the image on the background)
}


mycrop ()
{
	# my crop function:  does all the cropping on the current image
	# using the parameters x0,y0 ; x1,y1 ; xi,yi in memory
	# output is just the crop parameters:
	# c_width, c_height xc0,yc0  (for the actual crop)
	# and:
	# xci,yci for the location of the top left corner of the cropped image
	# relative to the output window.
	# note that the c_width x c_height must maintain the correct aspect ratio,
	# so we need to round this appropriately so the image aspect ratio doesn't 
	# keep changing during the pan/zoom.

	## the input coordinates are relative to the original image size, buffered out to
	## the output dvd aspect ratio
	
	## we need to convert the existing coordinates back to the actual image coordinates:
	## top left corner of dvd window is 0,0
	## top left corner of image is at xi,yi
	## top left corner of the cropped image is at x0,y0

	x_width=$(( $x1 - $x0 )) ; y_height=$(( $y1 - $y0 ))
	out_ratio=$(( 1000* $x_width / $y_height ))
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:mycrop] mycrop input: xcenter=$x_center ycenter=$y_center w=$x_width h=$y_height ratio=$out_ratio"

	## figure out the size of the window scaled to the original image size:
	ratio=$(( 1000* $image_width / $image_height ))
	out_ratio=$(( 1000* $dvd_width / $dvd_height ))
	if [ "$ratio" -gt "$(( $out_ratio ))" ] ; then
		# image width greater than output width at same scale
		newwidth=$image_width
		newheight=$(( $dvd_height * $image_width / $dvd_width ))
	elif [ "$ratio" -le $(( $out_ratio )) ] ; then
		# image height greater than output height at same scale 
		newwidth=$(( $dvd_width * $image_height / $dvd_height ))
		newheight=$image_height
	fi
	out_ratio=$(( 1000* $newwidth / $newheight ))  # this number is correct
#	[ $debug -ge 0 ] && myecho "[dvd-slideshow] new_width=$newwidth new_height=$newheight ratio=$out_ratio"

	## shift coordinate system to start at xi,yi:
	xi0=$(( $x0-$xi )); yi0=$(( $y0-$yi )) 
	xi1=$(( $x1-$xi )); yi1=$(( $y1-$yi )) 
	w=$(( $xi1 - $xi0 ))
	h=$(( $yi1 - $yi0 ))	
	out_ratio=$(( 1000* $w / $h )) ## should be same as before because coordinate system transformation preserves this.
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:mycrop] image crop coordinates=$xi0,$yi0 ; $xi1,$yi1 w=$w h=$h ratio=$out_ratio"

	## make sure the image crop coordinates are not outside the image:
	[ $xi0 -lt 0 ] && xc0=0 || xc0=$xi0 
	[ $xi1 -gt $image_width ] && xc1=$image_width || xc1=$xi1
	[ $yi0 -lt 0 ] && yc0=0 || yc0=$yi0
	[ $yi1 -gt $image_height ] && yc1=$image_height || yc1=$yi1
	c_width=$(( $xc1 - $xc0 )) ; c_height=$(( $yc1 - $yc0 ))
	out_ratio=$(( 1000* $c_width / $c_height )) ## 
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:mycrop] image crop coordinates=$xi0,$yi0 ; $xi1,$yi1 w=$w h=$h ratio=$out_ratio"

	## where to put the top left corner of the cropped image relative to the background?
	deltax=$(( 10000* $dvd_width / $c_width )); deltay=$(( 10000* $dvd_height / $c_height ))
	## rescale % will be the smaller of the two deltas:  10000 is to retain the resolution until dividing.
	[ $deltax -lt $deltay ] && rescale=$deltax || rescale=$deltay
	if [ $xi0 -lt 0 ] ; then
		## left of cropped image is in the middle of the dvd window
		xci=`div10 $(( $rescale * -1 * $xi0 / 1000 ))`
	else
		## left of cropped image should be at x=0 afterward
		xci=0
	fi
	if [ $yi0 -lt 0 ] ; then
		## top of cropped image is in the middle of the dvd window
		yci=`div10 $(( $rescale * -1 * $yi0 / 1000 ))`
	else
		## top of cropped image should be at y=0 afterward
		yci=0
	fi
	[ $debug -ge 3 ] && myecho "[dvd-slideshow:mycrop] image crop coordinates=$xi0,$yi0 ; $xi1,$yi1 w=$w h=$h ratio=$out_ratio"
}

wavlength ()
{
		sox "$1" -e stat 2> "$tmpdir"/trash.txt 
		song_length=`cat "$tmpdir"/trash.txt | grep 'Length (seconds):' | awk -F: '{print $2}' | tr -d [:blank:]`
		song_length_seconds=`echo $song_length | awk -F. '{print $1}'`
		if [ -z "$song_length_seconds" ] ; then song_length_seconds=0 ; fi
		song_length_ms=`echo $song_length | awk -F. '{printf ("%3.3f",$0)}' | awk -F. '{print $2}'`
		## make sure we have two decimal places?
		if [ -z "$song_length_ms" ] ; then song_length_ms=0 ; fi
		song_length=$( echo "scale=0; 1000 * $song_length_seconds + $song_length_ms" | bc )
		rm "$tmpdir"/trash.txt
		echo "$song_length"
}

rawlength ()
{
		sox -t raw -r 48000 -w -s -c 2 "$1" -e stat 2> "$tmpdir"/trash.txt 
		song_length=`cat "$tmpdir"/trash.txt | grep 'Length (seconds):' | awk -F: '{print $2}' | tr -d [:blank:]`
		song_length_seconds=`echo $song_length | awk -F. '{print $1}'`
		if [ -z "$song_length_seconds" ] ; then song_length_seconds=0 ; fi
		song_length_ms=`echo $song_length | awk -F. '{printf ("%3.3f",$0)}' | awk -F. '{print $2}'`
		## make sure we have two decimal places?
		if [ -z "$song_length_ms" ] ; then song_length_ms=0 ; fi
		song_length=$( echo "scale=0; 1000 * $song_length_seconds + $song_length_ms" | bc )
		rm "$tmpdir"/trash.txt
		echo "$song_length"
}

progressbar ()
{
	## display progress bar as frame $fr progresses to $frames
	## input 1 = $fr 
	## input 2 = $frames
	fr=$1 ; frames=$2
	thisbar=$(( $fr * 59 / $frames  ))
	if [ "$thisbar" -gt "$lastbar" ] ; then
		delta=$(( $thisbar - $lastbar ))
		if [ "$delta" -eq 1 ] ; then 
			echo -n "#"
		elif [ "$delta" -eq 2 ] ; then
			echo -n "##"
		elif [ "$delta" -eq 3 ] ; then
			echo -n "###"
		elif [ "$delta" -eq 4 ] ; then
			echo -n "####"
		elif [ "$delta" -eq 5 ] ; then
			echo -n "#####"
		elif [ "$delta" -eq 6 ] ; then
			echo -n "######"
		elif [ "$delta" -eq 7 ] ; then
			echo -n "#######"
		elif [ "$delta" -eq 8 ] ; then
			echo -n "########"
		elif [ "$delta" -eq 9 ] ; then
			echo -n "#########"
		else 
			echo -n "##########"
		fi
		lastbar="$thisbar"
	fi
}

finish_progressbar ()
{
	thisbar=$(( $fr * 59 / $frames  ))
	if [ "$thisbar" -lt 60 ] ; then
		delta=$(( 60 - $thisbar ))
		if [ "$delta" -eq 1 ] ; then 
			echo "#"
		elif [ "$delta" -eq 2 ] ; then
			echo "##"
		elif [ "$delta" -eq 3 ] ; then
			echo "###"
		elif [ "$delta" -eq 4 ] ; then
			echo "####"
		elif [ "$delta" -eq 5 ] ; then
			echo "#####"
		elif [ "$delta" -eq 6 ] ; then
			echo "######"
		elif [ "$delta" -eq 7 ] ; then
			echo "#######"
		elif [ "$delta" -eq 8 ] ; then
			echo "########"
		elif [ "$delta" -eq 9 ] ; then
			echo "#########"
		else 
			echo "##########"
		fi
	fi
	logecho "[dvd-slideshow]############################################################"
}

set_system_variables ()
{
	## check for config variables: only specified once per slideshow
	config=`echo "$1" | cut -d= -f1 | tr -d [:blank:]`
	config2=`echo "$1" | cut -d= -f2 | awk -F' #' '{print $1}' | tr -d [:blank:]`
	## check for global configuration variables:
	case "$config" in 
		debug) debug="$config2" ; logecho "[dvd-slideshow] debug=$debug" ; return 0 ;;
		pal) pal="$config2" ; logecho "[dvd-slideshow] pal=$pal" ; return 0 ;;
		ac3) ac3="$config2" ; logecho "[dvd-slideshow] ac3=$ac3" ; return 0 ;;
		copy) copy="$config2" ; logecho "[dvd-slideshow] copy=$copy" ; return 0 ;;
		autocrop) autocrop="$config2" ; logecho "[dvd-slideshow] autocrop=$autocrop" ; return 0 ;;
		font) [ -f "$config2" ] && (font="-font $config2" ; logecho "[dvd-slideshow] font=$font") ; return 0 ;;  #global font
		# subtitle
		subtitle_type) subtitle_type="$config2" ; logecho "[dvd-slideshow] subtitle_type=$subtitle_type" ; return 0 ;;
# eventually	subtitle_font) subtitle_font="-font $config2" ; logecho "[dvd-slideshow] subtitle_font=$subtitle_font" ; return 0 ;;
		subtitle_font_size) subtitle_font_size="$config2" ; logecho "[dvd-slideshow] subtitle_font_size=$subtitle_font_size" ; return 0 ;;
		*) return 1 ;;
	esac
}

set_variables ()
{
	## check for config variables:
	config1=`echo "$1" | cut -d= -f1 | tr -d [:blank:]`
	config2=`echo "$1" | cut -d= -f2 | awk -F' #' '{print $1}' | tr -d [:blank:]`
	[ -n "$2" -a "$2" == 1 ] && noecho=1 || noecho=0
	## check for global configuration variables:
	case "$config1" in 
		# title
		title_font) title_font="$config2" ; [ "$noecho" -eq 0 ] && echo "title_font=$title_font" ;;
		title_font_size) title_font_size="$config2" ; [ "$noecho" -eq 0 ] && echo "title_font_size=$title_font_size" ;;
		title_font_color) title_font_color="$config2" ; [ "$noecho" -eq 0 ] && echo "title_font_color=$title_font_color" ;;
		# top title
		toptitle_font_size) toptitle_font_size="$config2" ; [ "$noecho" -eq 0 ] && echo "toptitle_font_size=$toptitle_font_size" ;;
		toptitle_font_color) toptitle_font_color="$config2" ; [ "$noecho" -eq 0 ] && echo "toptitle_font_color=$toptitle_font_color" ;;
		toptitle_bar_height) toptitle_bar_height="$config2" ; [ "$noecho" -eq 0 ] && echo "toptitle_bar_height=$toptitle_bar_height" ;;
		toptitle_text_location_x) toptitle_text_location_x="$config2" ; [ "$noecho" -eq 0 ] && echo "toptitle_text_location_x=$toptitle_text_location_x" ;;
		toptitle_text_location_y) toptitle_text_location_y="$config2" ; [ "$noecho" -eq 0 ] && echo "toptitle_text_location_y=$toptitle_text_location_y" ;;
		# bottom title
		bottomtitle_font_size) bottomtitle_font_size="$config2" ; [ "$noecho" -eq 0 ] && echo "bottomtitle_font_size=$bottomtitle_font_size" ;;
		bottomtitle_font_color) bottomtitle_font_color="$config2" ; [ "$noecho" -eq 0 ] && echo "bottomtitle_font_color=$bottomtitle_font_color" ;;
		bottomtitle_bar_location_y) bottomtitle_bar_location_y="$config2" ; [ "$noecho" -eq 0 ] && echo "bottomtitle_bar_location_y=$bottomtitle_bar_location_y" ;;
		bottomtitle_bar_height) bottomtitle_bar_height="$config2" ; [ "$noecho" -eq 0 ] && echo "bottomtitle_bar_height=$bottomtitle_bar_height" ;;
		bottomtitle_text_location_x) bottomtitle_text_location_x="$config2" ; [ "$noecho" -eq 0 ] && echo "bottomtitle_text_location_x=$bottomtitle_text_location_x" ;;
		bottomtitle_text_location_y) bottomtitle_text_location_y="$config2" ; [ "$noecho" -eq 0 ] && echo "bottomtitle_text_location_y=$bottomtitle_text_location_y" ;;
	esac
}

############################################# End of functions

## check that input files and directories exist:
if [ -z "$input_txtfile" ] ; then
	input_txtfile="$1"
fi
if [ ! -f "$input_txtfile" ] ; then
	echo "[dvd-slideshow] ERROR: Input file $input_txtfile does not exist."
	exit 1
fi

# make sure a slideshow name was given:
if [ -z "$slideshow_name" ] ; then
	slideshow_name="`basename "$input_txtfile" .txt`"
#	echo "[dvd-slideshow] ERROR:  You must specify a slideshow name with -n <slideshow name>"
	echo "[dvd-slideshow] Using default slideshow name: $slideshow_name"
#	exit 1
fi

# verity output directory exists:
if [ -z "$outdir" ] ; then
	if [ -w "`pwd`" ] ; then
		echo "[dvd-slideshow] Output directory not specified."
		echo "[dvd-slideshow] Using `pwd`"
		outdir="`pwd`"
	else
		echo '[dvd-slideshow] ERROR: Output directory not specified.'
		exit 0
	fi
fi

## make sure output directory can be written to:
if [ ! -w "$outdir" ] ; then
	echo "[dvd-slideshow] Creating output directory $outdir"
	mkdir -p "$outdir"
	if [ ! -w "$outdir" ] ; then
		echo "[dvd-slideshow] ERROR: Output directory is not writeable!"
		exit 1
	fi
fi
	
tmpdir="$outdir/dvd-slideshow_temp_$$"
yuvfifo="dvdss-pipe-$$"   # pipe to mpeg2enc process

## create temporary directory:
if [ -d "$tmpdir" ] ; then
	echo "[dvd-slideshow] Removing old temporary directory $tmpdir"
	rmdir "$tmpdir"
fi
mkdir "$tmpdir"

## initialize log file:
echo "[dvd-slideshow] `date`" > "$outdir/$logfile"
logecho "[dvd-slideshow] Command line was:"
logecho "[dvd-slideshow] $0 $theargs"
logecho "[dvd-slideshow] dvd-slideshow version $version" 
logecho "[dvd-slideshow] `uname -a`"
logecho "[dvd-slideshow] Output directory=$outdir" 

## report version of bash for debugging:
logecho "[dvd-slideshow] Using `which bash` version `bash --version | head -n 1`"
bashversion=`bash --version | head -n 1 | awk '{print $4}' | awk -F. '{print $1"."$2}'`
#logecho "bash version is $bashversion"


## Check for required programs
# ppmtoy4m
# progver="`rpmversion mjpegtools`"
checkforprog ppmtoy4m
progver=`mplex 2>&1 | grep version | awk '{ print $4 }'`
logecho "[dvd-slideshow] Found mjpegtools version $progver"
if ppmtoy4m -S 420mpeg2 xxxxx 2>&1 | grep -q xxxxx; then
	logecho "[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2"
	subsample='420mpeg2'
else
	logecho "[dvd-slideshow] Using mjpegtools subsampling -S 420_mpeg2"
	# ppmtoy4m did not accept the -S 420mpeg2 option
	# so it's probably a version older than 1.6.3
	subsample='420_mpeg2'
fi
	
checkforprog sox
progver=`sox -h 2>&1 | head -n 1 | awk '{ print $3 }'`
logecho "[dvd-slideshow] Found sox version $progver"

checkforprog convert
progver=`convert -help | head -n 1 | awk '{ print $3 }'`
logecho "[dvd-slideshow] Found ImageMagick version $progver"

checkforprog dvdauthor
progver=`dvdauthor -h 2>&1 | head -n 1 | awk '{ print $3 }'`
logecho "[dvd-slideshow] Found dvdauthor version $progver"

# ffmpeg
if [ "$ac3" -eq 1 ] ; then
	it=`which ffmpeg 2> /dev/null`
       if [ -z "$it" ] ; then
               # no ffmpeg!  use mp2 audio instead:
               myecho "[dvd-slideshow] Warning:  no ffmpeg found for AC3 audio encoding."
               myecho "[dvd-slideshow]           Using MP2 audio instead."
               myecho "[dvd-slideshow]           MP2 audio is less compatible with DVD player hardware."
               ac3=0
	else
		# found ffmpeg
		
		logecho "`ffmpeg -version 2>&1`"
	fi
fi
################################################## done finding programs

#  Set default font:
default_font1=`find $font_dir -name $default_font1 | head -n 1`
default_font2=`find $font_dir -name $default_font2 | head -n 1`  # in case font1 isn't found

# verify fonts exist:
if [ -f "$default_font1" ] ; then 
	font="-font $default_font1"
elif [ -f "$default_font2" ] ; then
	font="-font $default_font2"
else
	myecho "[dvd-slideshow] Cannot find default fonts.  Using default ImageMagick font."
	font=""
fi
# subtitle_font="$font"  # default value unless user passes values in config file.
logecho "[dvd-slideshow] Font=$font"
###############################

if [ -f "$tmpdir/slide_1.ppm" ] || [ -f "$tmpdir/slideshow_background.ppm" ] || [ -f "$tmpdir/subtitles.srt" ] || [ -f "$tmpdir/fade_0001.ppm" ] ; then
	myecho "[dvd-slideshow] Found old files in output directory.  Removing them..."
	cleanup
fi


logecho "[dvd-slideshow] ####################################"
myecho "[dvd-slideshow] Parsing input .txt file $input_txtfile"

## loop over input .txt file to include any other files:
## thanks to Thomas Weber for this feature!
## modified slightly by Scott Dylewski
# create a tepmorary text file

tmptxtfile="tmp_txtfile.txt"
check_rm "$tmpdir/$tmptxtfile"

total_lines=`wc -l "$input_txtfile" | awk '{print $1}'`
total_lines=$(( $total_lines + 1 ))
line=1

while [ $line -ne $total_lines -a $total_lines -ne 0 ];
do
  # Search for include in line
  thisline=`sed -n "$line"p "$input_txtfile"`
  mygrep=`echo "$thisline" | grep -i ^include`
  if [ -n "$mygrep" ]; then
	  # Extract file name out of line: Correct statement is include:filename.txt
	  incfile=`echo $thisline | awk -F: '{print $2}'`
	  # Check if the incfile is present
	  if [ -r "$incfile" ]; then
	    # Append contents of the incfile to the temporary file
	    myecho "[dvd-slideshow] Including input file $incfile"
	    cat "$incfile" >> "$tmpdir/$tmptxtfile"
## cat removed the backslashes protecting special characters?
#	    sed -e '/*/p' >> "$tmpdir/$tmptxtfile"
	  fi
  else
	   # Print lines in the temporary file
	   sed -n "$line"p "$input_txtfile" >> "$tmpdir"/"$tmptxtfile"
  fi
  line=$(( $line + 1 ))
done 
echo " " >> "$tmpdir"/"$tmptxtfile"  # make sure last line has a return character.

lastbar=0
## loop over input .txt file, looking first for config variables
let i=0
total_video_length=0
audio_inside_txtfile=0
imagefiles=0 ; moviefiles=0 ; audiofiles=0
background_slides=0; transitions=0; titles=0
manual_chapter_markers=0
spumux_header=0

## let's parse the txtfile:
total_lines=`wc -l "$tmpdir/$tmptxtfile" | awk '{print $1}'`
total_lines=$(( $total_lines + 1 ))
let line=1

echo -n "[dvd-slideshow] "  # for progressbar
while [ $line -ne $total_lines -a $total_lines -ne 0 ];
do
	progressbar $line $total_lines
        # change @: which is "escaped" : to something else so that
        # it doesn't separate parameters.
        thisline=`sed -n "$line"p "$tmpdir/$tmptxtfile" | sed -e 's/\\\:/xxx_xxx/g'`
	if [ "${thisline:0:1}" == '#' ] ; then
		line=$(( $line + 1 ))
		continue # commented line. ignore it.
	elif [ -z `echo "$thisline" | tr -d [:blank:]` ] ; then
		line=$(( $line + 1 ))
		continue # blank line. ignore it.
	elif [ "$thisline" == 'exit' ] ; then
		line=$(( $line + 1 ))
		break # skip ahead
	fi 

	# check for system variables:
	set_system_variables "${thisline}"
	if [ "$?" -eq 0 ] ; then
		## need to ignore these lines from now on!
		line=$(( $line + 1 )) ; continue
	fi

	image[$i]=`echo "${thisline}" | awk -F' #' '{print $1}' | cut -d: -f1`
	filetype[$i]=`echo "${image[$i]}" | awk -F. '{print tolower($NF)}'`
	duration[$i]=`echo "${thisline}" | cut -d: -f2 | awk -F' #' '{print $1}'`
	[ -z "${duration[$i]}" ] && duration[$i]=0
	subtitle[$i]=`echo "${thisline}" | cut -d: -f3 | awk -F' #' '{print $1}'`

	## check for other variable settings:
	it=`set_variables "${thisline}" 0`  
	if [ -n "$it" ] ; then
		## need to process these lines still!  Variable was found.
		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		duration[$i]=0
        	subtitle[$i]=''
		i=$(( $i+1 )) ; line=$(( $line + 1 )) ; continue
	fi

	## check data file type and build arrays
        # change "xxx_xxx" back to ":"
        # - this should only be needed in subtitle
        subtitle[$i]=`echo ${subtitle[$i]} | sed -e 's/xxx_xxx/:/g'`

	if [ "${image[$i]}" == 'background' ] ; then  # trap potential # before hex color:
		effect1[$i]=`echo "${thisline}" | cut -d: -f4 | awk -F':#' '{print $1}' | awk -F' #' '{print $1}'`
	else
		effect1[$i]=`echo "${thisline}" | cut -d: -f4 | awk -F' #' '{print $1}'`
	fi
	if [ "${filetype[$i]}" == 'musictitle' ] || [ "${filetype[$i]}" == 'title' ] || [ "${filetype[$i]}" == 'Title' ] ; then
		effect1_params[$i]=`echo "${thisline}" | cut -d: -f5 | awk -F' #' '{print $1}'`
	else
		effect1_params[$i]=`echo "${thisline}" | cut -d: -f5 | awk -F' #' '{print $1}' | tr -d [:blank:]`
	fi
	effect2[$i]=`echo "${thisline}" | cut -d: -f6 | awk -F' #' '{print $1}'`
	effect2_params[$i]=`echo "${thisline}" | cut -d: -f7 | awk -F' #' '{print $1}' | tr -d [:blank:]`
	effect3[$i]=`echo "${thisline}" | cut -d: -f8 | awk -F' #' '{print $1}'`
	effect_params3[$i]=`echo "${thisline}" | cut -d: -f9 | awk -F' #' '{print $1}' | tr -d [:blank:]`
	effect4[$i]=`echo "${thisline}" | cut -d: -f10 | awk -F' #' '{print $1}'`
	effect_params4[$i]=`echo "${thisline}" | cut -d: -f11 | awk -F' #' '{print $1}' | tr -d [:blank:]`

	if [ "${filetype[$i]}" == 'jpg' ] || [ "${filetype[$i]}" == 'png' ] || [ "${filetype[$i]}" == 'jpeg' ] ; then
		## make sure file exists:
                if [ ! -f "${image[$i]}" ] ; then
			myecho ""
                	myecho "[dvd-slideshow] ERROR: Image ${image[$i]} does not exist"
                	exit 1
                fi
		image_file[$i]=1 ; audio_file[$i]=0 ; avi_file[$i]=0
                ## optinally copy images to new directory for backup onto dvd:
                newname=`echo "${slideshow_name}" | sed -e 's/ /_/g'`
                if [ "$copy" -eq 1 ] ; then
                        mkdir -p "$outdir/$newname"_pics
                fi
                if [ "$copy" -eq 1 ] ; then
                        cp "${image[$i]}" "$outdir/$newname"_pics
                fi
		if [ "${duration[$i]}" == '0' ] ; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Bad duration time of zero:"
			myecho "[dvd-slideshow]	$thisline"
			myecho "[dvd-slideshow] You need to specify a non-zero duration"
			cleanup; exit 1
		fi
		duration_ms=`duration2ms ${duration[$i]}`
		total_video_length="$(( $total_video_length + $duration_ms ))"
		imagefiles=$(( $imagefiles + 1 ))
		## check for common syntax errors:
		## forgetting subtitle in crop/scroll/kenburns:
		if [ "${subtitle[$i]}" == 'crop' ] && [ "${effect1[$i]}" != 'crop' ] ; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Bad syntax in line:"
			myecho "[dvd-slideshow]	$thisline"
			myecho "[dvd-slideshow] You probably forgot to add an empty subtitle placeholder:"
			myecho "[dvd-slideshow] image.jpg:duration::crop:50%;middle"
			myecho "[dvd-slideshow] image.jpg:duration:my subtitle:crop:50%;middle"
			cleanup; exit 1
		fi
		if [ "${subtitle[$i]}" == 'scroll' ] && [ "${effect1[$i]}" != 'scroll' ] ; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Bad syntax in line:"
			myecho "[dvd-slideshow]	$thisline"
			myecho "[dvd-slideshow] You probably forgot to add an empty subtitle placeholder:"
			myecho "[dvd-slideshow] image.jpg:duration::scroll:right"
			myecho "[dvd-slideshow] image.jpg:duration:my subtitle:sroll:right"
			cleanup; exit 1
		fi
		if [ "${subtitle[$i]}" == 'kenburns' ] && [ "${effect1[$i]}" != 'kenburns' ] ; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Bad syntax in line:"
			myecho "[dvd-slideshow]	$thisline"
			myecho "[dvd-slideshow] You probably forgot to add an empty subtitle placeholder:"
			myecho "[dvd-slideshow] image.jpg:duration::kenburns:50%;middle:75%:right"
			myecho "[dvd-slideshow] image.jpg:duration:my subtitle:kenburns:50%;middle:75%:right"
			cleanup; exit 1
		fi
		#######################################################################
		## Roate?
		## rotate image first, then apply other effects?
		for e in `seq 2 -1 1`; do
			if [ "$e" -eq 1 ] ; then
				this_effect="${effect1[$i]}"
				this_effect_params="${effect1_params[$i]}"
			elif [ "$e" -eq 2 ] ; then
				this_effect="${effect2[$i]}"
				this_effect_params="${effect2_params[$i]}"
			fi
	#		myecho "effect=$this_effect params=$this_effect_params"
			if [ "${image_file[$i]}" -eq 1 ] && [ "$this_effect" == 'rotate' ] ; then 
				logecho "[dvd-slideshow] Rotating ${image[$i]} $this_effect_params"
				## get basename of image:
				suffix=`echo "${image[$i]}" | awk -F. '{print tolower($NF)}'`	
				it=`basename "${image[$i]}" .$suffix`
				convert "${image[$i]}" -background transparent -bordercolor transparent -rotate "$this_effect_params" -quality 100 "$tmpdir"/"$it"_rotated.png
				image[$i]="$tmpdir"/"$it"_rotated.png
				if [ "$e" -eq 1 ] ; then
					effect1[$i]="${effect2[$i]}"
					effect1_params[$i]="${effect2_params[$i]}"
					effect2[$i]=''
					effect2_params[$i]=''
				elif [ "$e" -eq 2 ] ; then
					effect2[$i]=''
					effect2_params[$i]=''
				fi
			fi
		done
		#######################################################################

	elif [ "${image[$i]}" == 'fadein' ] || [ "${image[$i]}" == 'fadeout' ] || [ "${image[$i]}" == 'crossfade' ] ; then
		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		if [ "${duration[$i]}" == '0' ] ; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Bad duration time of zero:"
			myecho "[dvd-slideshow]	$thisline"
			myecho "[dvd-slideshow] You need to specify a non-zero duration"
			cleanup; exit 1
		fi	
		duration_ms=`duration2ms ${duration[$i]}`
		total_video_length="$(( $total_video_length + $duration_ms ))"
		transitions=$(( $transitions + 1 ))
	elif [ "${image[$i]}" == 'title' ] || [ "${image[$i]}" == 'Title' ] ; then
                if [ -z "${subtitle[$i]}" ] && [ -z "${effect1[$i]}" ] ; then
			echo ""
			myecho "[dvd-slideshow] ERROR: no title text found in line:"
			myecho "[dvd-slideshow] ${thisline}"
			cleanup; exit 1
		fi
		if [ "${duration[$i]}" == '0' ] ; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Bad duration time of zero:"
			myecho "[dvd-slideshow]	$thisline"
			myecho "[dvd-slideshow] You need to specify a non-zero duration"
			cleanup; exit 1
		fi
		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		duration_ms=`duration2ms ${duration[$i]}`
		total_video_length="$(( $total_video_length + $duration_ms ))"
		titles=$(( $titles + 1 ))
        elif [ "${image[$i]}" == 'titlebar' ] || [ "${image[$i]}" == 'Titlebar' ] ; then
                if [ -z "${subtitle[$i]}" ] && [ -z "${effect1[$i]}" ] ; then
			echo ""
			myecho "[dvd-slideshow] ERROR: no titlebar text found in line:"
			myecho "[dvd-slideshow] ${thisline}"
			cleanup; exit 1
		fi
                if [ "${duration[$i]}" == '0' ] ; then
                        myecho ""
                        myecho "[dvd-slideshow] ERROR: Bad duration time of zero:"
                        myecho "[dvd-slideshow] $thisline"
                        myecho "[dvd-slideshow] You need to specify a non-zero duration"
                        cleanup; exit 1
                fi
                image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
                duration_ms=`duration2ms ${duration[$i]}`
                total_video_length="$(( $total_video_length + $duration_ms ))"
                titles=$(( $titles + 1 ))
	elif [ "${image[$i]}" == 'chapter' ] || [ "${image[$i]}" == 'Chapter' ] || [ "${image[$i]}" == 'CHAPTER' ] ; then
		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		duration[$i]=0;
		duration_ms=`duration2ms ${duration[$i]}`
		total_video_length="$(( $total_video_length + $duration_ms ))"
	elif [ "${image[$i]}" == 'background' ] ; then
		if [ "${duration[$i]}" != 0 ] ; then
			background_slides=$(( $background_slides + 1 ))
		fi
		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		duration_ms=`duration2ms ${duration[$i]}`
		total_video_length="$(( $total_video_length + $duration_ms ))"
        elif [ "${filetype[$i]}" == 'avi' ] ; then
                image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=1
		### need to get the length of the video here and set the duration
		### so the audio is the correct length!
		checkforprog tcprobe
        	video_length=`tcprobe -i "${image[$i]}" 2> /dev/null | grep 'duration=' | awk -F'duration=' '{print $2}'`
		it=`hms2seconds "$video_length"`
		it=`duration2ms $it`
		duration[$i]="$it"
        	myecho "[dvd-slideshow] AVI video length=$video_length duration=$it"
		## optionally copy images to new directory for backup onto dvd:
		newname=`echo "${slideshow_name}" | sed -e 's/ /_/g'`
		if [ "$copy" -eq 1 ] ; then
			mkdir -p "$outdir/$newname"_pics
		fi
		if [ "$copy" -eq 1 ] ; then
			cp -af "${image[$i]}" "$outdir/$newname"_pics
		fi
		moviefiles=$(( $moviefiles + 1 ))
	elif [ "${filetype[$i]}" == 'ogg' ] || [ "${filetype[$i]}" == 'mp3' ] || [ "${filetype[$i]}" == 'wav' ] || [ "${image[$i]}" == 'silence' ]; then
		## make sure audio file exists (if not silence):
                if [ "${image[$i]}" != 'silence' -a ! -f "${image[$i]}" ] ; then
			myecho ""
                	myecho "[dvd-slideshow] ERROR: Audio file ${image[$i]} does not exist"
                	cleanup; exit 1
                fi
		audio_inside_txtfile=1
		audio_file[$i]=1 ; image_file[$i]=0 ; avi_file[$i]=0
		effect1[$i]=`echo "${thisline}" | cut -d: -f3 | awk -F' #' '{print $1}'`  # no subtitle for audio 
		effect1_params[$i]=`echo "${thisline}" | cut -d: -f4 | awk -F' #' '{print $1}' | tr -d [:blank:]`
		effect2[$i]=`echo "${thisline}" | cut -d: -f5 | awk -F' #' '{print $1}'`
		effect2_params[$i]=`echo "${thisline}" | cut -d: -f6 | awk -F' #' '{print $1}' | tr -d [:blank:]`
		if [ "${effect1[$i]}" != 'fadein' ] && [ -n "${effect1[$i]}" ]; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: First audio effect must be fadein"
			cleanup; exit 1
		fi
		if [ "${effect2[$i]}" != 'fadeout' ] && [ -n "${effect2[$i]}" ]; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Second audio effect must be fadeout"
			cleanup; exit 1
		fi
		## get audio track number:
		if [ -z "${duration[$i]}" ] ; then 
			# duration is the field for the audio track numuber
			# if empty, assume track=1
			audio_track[$i]='1'
		elif [ "${duration[$i]}" -gt 2 ]; then
			myecho ""
			myecho "[dvd-slideshow] ERROR: Only 2 audio tracks supported at this time."
			myecho "[dvd-slideshow]        Fix this audio file track number!"
			myecho "[dvd-slideshow]        $thisline"
			cleanup; exit 1
		else
			# use the duration as the audio track number:
			audio_track[$i]="${duration[$i]}"
		fi
		## get filetype:
		if [ "${filetype[$i]}" == 'ogg' ] ; then
			checkfor_oggdec
		fi
		if [ "${filetype[$i]}" == 'mp3' ] ; then
			checkfor_lame
		fi
		duration[$i]=0
		audiofiles=$(( $audiofiles + 1 ))
	else
		image_file[$i]=0 ; audio_file[$i]=0 ; avi_file[$i]=0
		duration_ms=`duration2ms ${duration[$i]}`
		total_video_length="$(( $total_video_length + $duration_ms ))"
	fi
#	echo "line=$i"
	line=$(( $line + 1 ))
	i=$(( $i + 1 ))
done  ## end of loop over input .txt file  ##################################
finish_progressbar

# check to see if any functions had errors:
if [ $function_error -eq 1 ] ; then
	cleanup
	exit 1
fi

#############################################################################
# verity fonts exist at ~/.spumux/ for spumux:
if [ "$subtitle_type" == 'srt' ] || [ "$subtitle_type" == "SRT" ] ; then
	if [ ! -f ~/.spumux/arial.ttf ] ; then
		# look for fonts in $font_dir/msttcorefonts	
		# if yours is somewhere else, let me know so I can add it to the search path.
		if [ -f $font_dir/msttcorefonts/arial.ttf ] ; then
			myecho "[dvd-slideshow] Copying $font_dir/msttcorefonts/arial.ttf to $HOME/.spumux/arial.ttf"
			mkdir -p "$HOME/.spumux"	
			cp "$font_dir/msttcorefonts/arial.ttf" "$HOME/.spumux"
		else
			myecho "[dvd-slideshow] ERROR: cannot find $HOME/.spumux/arial.ttf"
			myecho "[dvd-slideshow] You need some fonts in the ~/.spumux directory"
			myecho "[dvd-slideshow] in order to use .srt files rendered by spumux."
			myecho "[dvd-slideshow] Try downloading truetype fonts, and copy"
			myecho "[dvd-slideshow] arial.ttf into the ~/.spumux directory"
			myecho "[dvd-slideshow] "
			myecho "[dvd-slideshow] Rendering subtitles using dvd-slideshow instead."
			subtitle_type="render"
		fi
	fi
	echo "" >> "$tmpdir/$subtitle_file"
fi

## summarize scan of .txt file:
if [ $commandline_audiofiles -eq 0 ] ; then
	myecho "[dvd-slideshow] Found $imagefiles images."
	myecho "[dvd-slideshow] Found $audiofiles audio files."
elif [ $audiofiles -eq 0 ] ; then
	myecho "[dvd-slideshow] Found $imagefiles images."
	myecho "[dvd-slideshow] Found $commandline_audiofiles audio files."
else
	myecho "[dvd-slideshow] Found $imagefiles images"
	myecho "[dvd-slideshow] Found $commandline_audiofiles audio files on command-line."
	myecho "[dvd-slideshow] Found $audiofiles audio files in .txtfile."
fi
myecho "[dvd-slideshow] Found $background_slides background slides."
myecho "[dvd-slideshow] Found $titles title slides."
myecho "[dvd-slideshow] Found $transitions transitions (fadein/fadeout/crossfade)."
# myecho ", and $moviefiles videos"

## summarize configuration:
[ "$pal" -eq 1 ] && ntsc_or_pal="PAL" || ntsc_or_pal="NTSC"
[ "$ac3" -eq 1 ] && mp2_or_ac3="AC3" || mp2_or_ac3="MP2"
#myecho "[dvd-slideshow] Configuration summary:"
myecho "[dvd-slideshow] Video: $ntsc_or_pal  Audio: $mp2_or_ac3"
myecho "[dvd-slideshow] Debug=$debug  Autocrop=$autocrop Subtitles=$subtitle_type"
if [ "$manual_chapter_markers" == 1 ] ; then
	myecho "[dvd-slideshow] Chapter markers= Manual"
fi	
if [ "$smp" == 1 ] ; then
	myecho "[dvd-slideshow] Using SMP optimizations for multi-processor machines"
fi	
if [ "$nocleanup" == 1 ] ; then
	myecho "[dvd-slideshow] Leaving all temporary files in temp directory"
fi	
if [ "$low_quality" -eq 1 ] ; then
	myecho "[dvd-slideshow] WARNING: Using low-quality mode."
	myecho "[dvd-slideshow]   This mode is for testing only."
	myecho "[dvd-slideshow]   output resolution is $dvd_width"x"$dvd_height"
	myecho "[dvd-slideshow]   Ignore [mpeg2enc] warnings (usually)"
elif [ "$high_quality" -eq 1 ] ; then
	myecho "[dvd-slideshow] Using high-quality mode.  "
fi


## convert command-line audio files to wav format first, so we know how long they are:
if [ -n "${passed_audio[0]}" ] && [ $audio_inside_txtfile -eq 0 ] ; then  ## only command-line passed audio
	total_audio_length=0
	track=1 ; i=1
	myecho "[dvd-slideshow] Decoding command-line passed audio files..."
	for file in "${passed_audio[@]}"; do
		## verify files exist:
		if [ ! -f "$file" ] ; then
			myecho "[dvd-slideshow] ERROR: file $file does not exist."
			cleanup ; exit 1
		fi
		suffix=`echo "$file" | awk -F. '{print tolower($NF)}'`
		audio_index_padded=`addzeros "$i_audio"`
		if [ "$suffix" == "mp3" ] ; then
			myecho "[dvd-slideshow] Decoding mp3 audio: $file"
			lame --decode "$file" "$tmpdir/audio$track"_"$audio_index_padded.wav" 2> /dev/null
		elif [ "$suffix" == "ogg" ] ; then
			myecho "[dvd-slideshow] Decoding ogg audio: $file"
			oggdec --quiet -o "$tmpdir/audio$track"_"$audio_index_padded.wav" "$file"
		elif [ "$suffix" == "wav" ] ; then
			myecho "[dvd-slideshow] Processing wav audio $file"
			cp "$file" "$tmpdir/audio$track"_"$audio_index_padded.wav"
		else
			myecho "[dvd-slideshow] ERROR:  Unknown audio file format.  Must be .mp3, .ogg, or .wav"
		fi	
		length=`wavlength "$tmpdir/audio$track"_"$audio_index_padded.wav"`
		length_array[$i]=`hms $length`
		total_audio_length="$(( $total_audio_length + $length ))"
#		myecho "[dvd-slideshow] length=$length total_audio_length=$total_audio_length"
		let i=$i+1
		i_audio=$(( $i_audio + 1 ))
	done
#	i=1
#	for file in "${passed_audio[@]}"; do
#		myecho "[dvd-slideshow] ${length_array[$i]} `basename \"$file\"`"
#		let i=$i+1
#	done
	# estimate total audio length:
	length_hms=`hms $total_audio_length`
elif [ -n "${passed_audio[0]}" ] && [ $audio_inside_txtfile -eq 1 ] ; then  ## only command-line passed audio
	myecho "[dvd-slideshow] WARNING:  You specified audio on the command line, and"
	myecho "[dvd-slideshow]           you have audio files inside your input .txt file"
	myecho "[dvd-slideshow]           Use one or the other, but not both!"
	myecho "[dvd-slideshow]           Ignoring command-line passed audio!"
fi

video_time_hms=`hms $total_video_length`
#myecho "[dvd-slideshow] Total audio length = $length_hms"
myecho "[dvd-slideshow] Total video length = $video_time_hms"

if [ ! -d "$outdir" ] ; then	
#        myecho "ERROR... output directory does not exist!"
#        exit
	myecho "creating directory $outdir"
	mkdir -p "$outdir"  # create directory
fi

#mpeg2enc_params='-v 0 -a 2 -q 8 -s -M 0 -f 8 -b 6000 -I 0'
mpeg2enc_params='-v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8'
#mpeg2enc_params='-v 0 -a 2 -s -M 0 -f 8 -b 6000'

if [ "$pal" -eq 1 ] ; then
	framerate='25'
	frames_per_sec=25000  # in ms
	sq_to_dvd_pixels='93.75x100%' # i.e., make the horizontal smaller
	sq_pixel_multiplier=$(( 1000 * 540 / 576 ))
		# see [http://www.uwasa.fi/~f76998/video/conversion](http://www.uwasa.fi/~f76998/video/conversion)
	if [ "$low_quality" -eq 1 ] ; then
		dvd_width='352' ; dvd_height='288'
		resolution='352x288'
	elif [ "$high_quality" -eq 1 ] ; then
		dvd_width='720' ; dvd_height='576'
		resolution='720x576'
	else
		dvd_width='720' ; dvd_height='576'
		resolution='720x576'
	fi
else  ## NTSC
	framerate='29.97'
	frames_per_sec=29970  # in ms
	sq_to_dvd_pixels='112.5x100%' # i.e., make the horizontal 12% larger
	sq_pixel_multiplier=$(( 1000 * 540 / 480 ))
		# see [http://www.uwasa.fi/~f76998/video/conversion](http://www.uwasa.fi/~f76998/video/conversion)
	if [ "$low_quality" -eq 1 ] ; then
		dvd_width='352' ; dvd_height='240'
		resolution='352x240'
	elif [ "$high_quality" -eq 1 ] ; then
		dvd_width='720' ; dvd_height='480'
		resolution='720x480'
	else
		dvd_width='720' ; dvd_height='480'
		resolution='720x480'
	fi
fi

has_subtitles=0
frame_time=0
total_slideshow_frames=0

#if [ "$low_quality" -eq 1 ] ; then
#	## subtitle:
#	subtitle_font_size=$(( $subtitle_font_size / 2 ))
#	## title:
#	title_font_size=$(( $title_font_size / 2 ))
#	## top title:
#	toptitle_font_size=$(( $toptitle_font_size / 2 ))
#	toptitle_bar_height=$(( $toptitle_bar_height / 2 ))
#	toptitle_text_location_x=$(( $toptitle_text_location_x / 2 ))
#	toptitle_text_location_y=$(( $toptitle_text_location_y / 2 ))
#	# bottom title:
#	bottomtitle_font_size=$(( $bottomtitle_font_size / 2 ))
#	bottomtitle_bar_location_y=$(( $bottomtitle_bar_location_y / 2 ))
#	bottomtitle_bar_height=$(( $bottomtitle_bar_height / 2 ))
#	bottomtitle_text_location_x=$(( $bottomtitle_text_location_x / 2 ))
#	bottomtitle_text_location_y=$(( $bottomtitle_text_location_y / 2 ))
#fi

## now the title2 y-locations were specified relative to the bottom of the image
## but imagemagick needs them relative to the top of the image:
#bottomtitle_bar_location_y=$(( $dvd_height - $bottomtitle_bar_location_y ))
#bottomtitle_text_location_y=$(( $dvd_height - $bottomtitle_text_location_y ))

orig_slideshow_name="${slideshow_name}"
slideshow_name=`echo "${slideshow_name}" | sed -e 's/ /_/g'`
if [ "$orig_slideshow_name" != "$slideshow_name" ] ; then
	myecho "[dvd-slideshow] Output filename is $slideshow_name"
fi
myecho "[dvd-slideshow] Temp dir is $outdir"/"dvd-slideshow_temp_$$"

# create the mpeg2enc pipeline here if we are in $yuvcat mode
if [ "$yuvcat" -eq 1 ]; then
       # create the fifo
       rm -f "$tmpdir/$yuvfifo"
       mkfifo "$tmpdir/$yuvfifo"

       # start the mpeg encoder, listening to the fifo, and keep the pid for later
#       mpeg2enc -v $verbosity -a 2 -q 4 -s -M 3 -f 8 -o "$tmpdir/video.mpg" < $tmpdir/$yuvfifo &
#       mpeg2enc $mpeg2enc_params -o "$tmpdir/video_"$mpegid".mpg" <$tmpdir/$yuvfifo >> "$outdir/$logfile" 2>&1 & 
#       mpeg2enc $mpeg2enc_params -o "$tmpdir/video_"$mpegid".mpg" < $tmpdir/$yuvfifo & 
       mpeg2enc $mpeg2enc_params -o "$tmpdir/video_"$mpegid".mpg" < "$tmpdir"/$yuvfifo >> "$outdir/$logfile" 2>&1 & 
       yuvpid=$!

       # open the fifo for writing as fd 3 (unlikely to be used!)
       exec 3>"$tmpdir/$yuvfifo"
	/usr/bin/lsof -a -u $USER -d 3 +c 0 -c dvd -c convert -c mpeg2 >> "$outdir/$logfile" 2>&1
fi

## make both a slideshow_background file and a title_background file
if [ -f "${bgfile}" ] ; then
	background "$bgfile"
else
	background "black"
fi

myecho "[dvd-slideshow]############################################################"

let i=0 # full
let v=0 # vob
image_number=1
for file in "${image[@]}"; do
	## convert i to a 2-digit text version so we can cat the mpgs together
	## in the correct order easily:
	di=`addzeros $i`
	## check for variable settings first:
#	echo "i=$i file=$file duration=${duration[$i]}"
	set_variables "$file" 1
	it=`set_variables "$file"`
	if [ -n "$it" ] ; then
		myecho "[dvd-slideshow] Set variable $it"
		i=$(( $i+1 )) ; continue
	fi
	
	if [ "${duration[$i]}" == 'audio' ] ; then
		## make the duration the length of the last audio track
		if [ -z "$song_length_ms" ] ; then
			myecho '# ERROR: You must have an audio track before a slide specifying "audio"'
			cleanup; exit 1
		fi
		duration[$i]="$song_length"	# in seconds
	fi	

	if [ -z "${duration[$i]}" ] ; then
		myecho "[dvd-slideshow] WARNING:  No duration specified for ${image[$i]}"
		myecho "[dvd-slideshow]	     Using default duration of 5 seconds"
		duration[$i]=5
	fi
	
	duration[$i]=`duration2ms ${duration[$i]}`  # duration in thousandths of a sec.
	
	## number of frames to render for this picture:
	frames=`div1000 $(( $frames_per_sec * ${duration[$i]} / 1000 ))` # both duration and fps are in ms
	## get start frame & time:
	slide_start_frame=$(( $total_slideshow_frames ))
	slide_start_time=$(( $slide_start_frame *1000 * 1000 / $frames_per_sec )) ## in thousandths of a sec.
	slide_start_hms=`hms "$slide_start_time"`
	if [ $debug -ge 1 ] ; then
		myecho "[dvd-slideshow] frames=$frames duration=`echo ${duration[$i]} | tr -d [:blank:]` ms"
		myecho "[dvd-slideshow] start_frame_number=$slide_start_frame slide_start_time=$slide_start_hms"
	fi
#	if [ -n ${duration[$i]} ] && [ ${duration[$i]} -ne 0 ] ; then
#		myecho "[dvd-slideshow] $i/${#image[@]} $file, `hms ${duration[$i]}` ${subtitle[$i]}"
#		myecho "[dvd-slideshow] $i/${#image[@]} $file, `hms ${duration[$i]}`"
#	else
#		myecho "[dvd-slideshow] $i/${#image[@]} $file"
#	fi
	if [ $debug -ge 2 ] ; then
		myecho "[dvd-slideshow] effect1='${effect1[$i]}' effect_params='${effect1_params[$i]}'"
		myecho "[dvd-slideshow] effect2='${effect2[$i]}' effect_params='${effect2_params[$i]}'"
	fi
        if [ "$file" == 'title' -o "$file" == 'Title' ] ; then
                myecho "[dvd-slideshow] Title `hms ${duration[$i]}`"
                if [ -n "${effect1[$i]}" ] ; then
                        myecho "[dvd-slideshow] WARNING: This keyword has changed in dvd-slideshow 0.7.5"
                        myecho "[dvd-slideshow]       Title only has one argument. Use titlebar for"
                        myecho "[dvd-slideshow]       the same menu type as before. See documentation."
                        myecho "[dvd-slideshow]       Only using one title line, centered in the screen."
                fi
                if [ -n "${subtitle[$i]}" ] ; then
                	title="${subtitle[$i]}"
		elif [ -n "${effect1[$i]}" ] ; then
                	title="${effect1[$i]}"
		else
			myecho "[dvd-slideshow] ERROR: no title text found in line:"
			myecho "[dvd-slideshow] ${thisline}"
			cleanup; exit 1
		fi
                subtitle[$i]=''  # set subtitle to nothing so we don't get a subtitle
                myecho "[dvd-slideshow]         Title=$title"
                ## now the slide may already exist if we had a fadein or crossfade before
                if [ ! -f "$tmpdir/slide_$i.ppm" ] ; then
                        titleslide "$title"
                        waitforfile "$tmpdir/title.ppm"
                        cp "$tmpdir/title.ppm" "$tmpdir/slide_$i.ppm"
                fi
                encode
                [ "$manual_chapter_markers" -eq 0 ] && write_chap=1
                myecho "[dvd-slideshow]############################################################"
        elif [ "$file" == 'titlebar' -o "$file" == 'Titlebar' ] ; then
                myecho "[dvd-slideshow] Titlebar `hms ${duration[$i]}`"
                title1="${subtitle[$i]}"
                subtitle[$i]=''  # set subtitle to nothing so we don't get a subtitle
                title2="${effect1[$i]}"
                myecho "[dvd-slideshow]         Title1=$title1"
                myecho "[dvd-slideshow]         Title2=$title2"
                ## now the slide may already exist if we had a fadein or crossfade before
                if [ ! -f "$tmpdir/slide_$i.ppm" ] ; then
                        titlebarslide "$title1" "$title2"
                        waitforfile "$tmpdir/title.ppm"
                        cp "$tmpdir/title.ppm" "$tmpdir/slide_$i.ppm"
                fi
                encode
                [ "$manual_chapter_markers" -eq 0 ] && write_chap=1
                myecho "[dvd-slideshow]############################################################"
	elif [ "$file" == 'musictitle' ] ; then
		## add a music-video style title page
		## format is:
		## musictitle:duration:subtitle:MusicTitle:MusicArtist;MusicAlbum
		myecho "[dvd-slideshow] Making musictitle slide:"
		Title="Title: ${effect1[$i]}"
		Artist="Artist: `echo ${effect1_params[$i]} | awk -F';' '{print $1}'`"
		Album="Album: `echo ${effect1_params[$i]} | awk -F';' '{print $2}'`"
		myecho "[dvd-slideshow] $Title $Artist $Album"
		# make the background (black) picture:
		convert -size "$resolution" xc:black -type TrueColor \
			-depth 8 "$tmpdir"/slideshow_background.ppm
		# draw text:
		if [ "$low_quality" -eq 1 ] ; then
			f_subtitle_font_size=$(( $subtitle_font_size / 2 ))
		else
			f_subtitle_font_size=$(( $subtitle_font_size ))
		fi
		if [ "$low_quality" -eq 1 ] ; then
			convert -depth 8 -size $resolution xc:transparent \
			-pointsize "$f_subtitle_font_size" -gravity SouthWest $font \
			-draw "fill white text 40,100 \"$Title\"" \
			-draw "fill white text 40,75 \"$Artist\"" \
			-draw "fill white text 40,50 \"$Album\"" -quality 100 "$tmpdir/dvd_title.png"
		else  # medium or high quality
			convert -depth 8 -size $resolution xc:transparent \
			-pointsize "$f_subtitle_font_size" -gravity SouthWest $font \
			-draw "fill white text 80,200 \"$Title\"" \
			-draw "fill white text 80,150 \"$Artist\"" \
			-draw "fill white text 80,100 \"$Album\"" -quality 100 "$tmpdir/dvd_title.png"
		fi
		composite -compose src-over -type TrueColor -depth 8 "$tmpdir/dvd_title.png" "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"
#		cp "$tmpdir/slide_$i.ppm" "$tmpdir/temp_slideshow_image.ppm"
#		subtitle[$i]=''  # set subtitle to nothing so we don't get a subtitle
		encode
		[ "$manual_chapter_markers" -eq 0 ] && write_chap=1
		myecho "[dvd-slideshow]############################################################"
        elif [ "${avi_file[$i]}" -eq 1 ] ; then  ############################
		## use ffmpeg to encode video.  No audio.  
		## maybe I'll add support for this later.
		myecho "[dvd-slideshow] AVI file passed.  Closing existing pipe to video_$mpegid.mpg"
		[ "$manual_chapter_markers" -eq 0 ] && write_chap=1
                new_vob=1
                # No browse nums yet
       		# just close the fifo and wait for the encoder to finish
		# close pipe to mpeg2enc
	        exec 3>&-  
	        wait $yuvpid
#	        yuvpid=0
		## increment mpeg id number:
		mpegid=$(( $mpegid + 1 ))
		## encode video
		myecho "[dvd-slideshow] Encoding ${image[$i]} to video_$mpegid.mpg"
		## try using tovid if it exists?
		it=`which tovid`
		if [ -n "$it" ] ; then
			# use tovid
			checkforprog tovid
			tovid -parallel -priority low -normalize -full -overwrite -ntsc -dvd "${image[$i]}" _new.mpg
			mv "${$image[$i]}"_new.mpg "$tmpdir/video_"$mpegid".mpg"
		else
			ffmpeg -i "${image[$i]}" -y -aspect 4:3 -s "$dvd_width"x"$dvd_height" -r $framerate -vcodec mpeg2video -an video_$mpegid.mpg >> "$outdir/$logfile" 2>&1
			if [ $? -ne 0 ] ; then
				## ffmpeg errored
				myecho "[dvd-slideshow] ERROR during ffmpeg execution!"
				myecho "[dvd-slideshow] see $outdir/$logfile for details"
				cleanup; exit 1
			fi
		fi
		## start a new mpeg2enc pipe
		mpegid=$(( $mpegid + 1 ))
	        # create the fifo
	        rm -f "$tmpdir/$yuvfifo"
		yuvfifo="/tmp/dvdss-pipe-$!"   # pipe to mpeg2enc process
	        mkfifo "$tmpdir/$yuvfifo"
	        # start the mpeg encoder, listening to the fifo, and keep the pid for later
		myecho "[dvd-slideshow] Opening new pipe to video_$mpegid.mpg"
	        mpeg2enc $mpeg2enc_params -o "$tmpdir/video_"$mpegid".mpg" < "$tmpdir/$yuvfifo" >> "$outdir/$logfile" 2>&1 &
	        yuvpid=$!
	        # open the fifo for writing as fd 3 (unlikely to be used!)
	        exec 3>"$tmpdir/$yuvfifo"
               	yuvfirstfile=1  # must not strip off headers for first frame of each video?
		myecho "[dvd-slideshow]############################################################"
	elif [ "${image_file[$i]}" -eq 1 ] && [ -z "${effect1[$i]}" ] ; then  ############################
		## use real jpeg. 
		## now the slide may already exist if we had a fadein or crossfade before
		myecho "[dvd-slideshow] $image_number/$imagefiles $file `hms ${duration[$i]}`"
		image_number=$(( $image_number + 1 ))
		if [ -n "${subtitle[$i]}" ] ; then
			myecho "[dvd-slideshow] Subtitle""= ${subtitle[$i]}"
		fi
		if [ ! -f "$tmpdir/slide_$i.ppm" ] ; then 
			checkforautocrop "${file}"	
			if [ "$do_autocrop_h" -eq 1 ] ; then
				convert "${file}" -resize "$sq_to_dvd_pixels" -resize "$dvd_width"x -type TrueColor -depth 8 \
				-gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' +repage miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 \
				- "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"
			elif [ "$do_autocrop_w" -eq 1 ] ; then
				convert "${file}" -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" -type TrueColor -depth 8 \
				-gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' +repage miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 \
				- "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"
			else
				convert "${file}" -resize "$sq_to_dvd_pixels" -resize $resolution -type TrueColor -depth 8 miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 \
				- "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"
			fi
		fi
		encode
		[ "$manual_chapter_markers" -eq 0 ] && write_chap=1
		new_vob=1
		myecho "[dvd-slideshow]############################################################"
	elif [ "$file" == 'fadein' ] ; then 
		## ok, let's copy the background and just fade the foreground:
		## check to make sure the next slide is an image:
		myecho "[dvd-slideshow] Fadein `hms ${duration[$i]}`"
		if [ -n "${subtitle[$i]}" ] ; then
			myecho "[dvd-slideshow] Subtitle""= ${subtitle[$i]}"
		fi
		nextslide=`nextslidename`
		increment=`nextslideincrement`
		if [ "${image[$i+1]}" == 'crossfade' ] ; then
			myecho "[dvd-slideshow] ERROR: Cannot fadein to a crossfade!"
			cleanup; exit 1
		elif [ "${image[$i+1]}" == 'fadein' ] ; then
			myecho "[dvd-slideshow] ERROR: Cannot fadein to another fadein!"
			cleanup; exit 1
		fi
		check_rm "$tmpdir/slide_$(($i+1)).ppm"  # make sure it doesn't already exist!
#		myecho "[dvd-slideshow] next slide=$nextslide  increment=$increment"
		## we need to prepare the NEXT image now:
		if [ "${effect1[$i+$increment]}" == 'crop' ] ; then  # if next picture is specifically cropped
			window=`echo "${effect1_params[$i+$increment]}" | awk -F';' '{print $1";"$2}'`
			parse_window "$window" "${image[$i+$increment]}"
			mycrop  # takes the parameters from <parse_window> and returns: 
			convert "${image[$i+$increment]}" -resize "$sq_to_dvd_pixels" -crop "$c_width"x"$c_height+$xc0+$yc0" +repage -resize $resolution miff:- | \
			composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
		elif [ "${effect1[$i+$increment]}" == 'kenburns' ] ; then  # if next picture has kenburns effect
			window=`echo "${effect1_params[$i+$increment]}" | awk -F';' '{print $1";"$2}'`
			parse_window "$window" "${image[$i+$increment]}"
			mycrop  # takes the parameters from <parse_window> and returns: 
			convert "${image[$i+$increment]}" -resize "$sq_to_dvd_pixels" -crop "$c_width"x"$c_height+$xc0+$yc0" +repage -resize $resolution miff:- | \
			composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"

                elif [ "$nextslide" == 'title' ] || [ "$nextslide" == 'Title' ] ; then
	                if [ -n "${subtitle[$i+$increment]}" ] ; then
	                	title="${subtitle[$i+$increment]}"
			elif [ -n "${effect1[$i+$increment]}" ] ; then
	                	title="${effect1[$i+$increment]}"
			else
				myecho "[dvd-slideshow] ERROR: no title text found in line:"
				myecho "[dvd-slideshow] ${thisline}"
				cleanup; exit 1
			fi
                        titleslide "$title"
                        waitforfile "$tmpdir/title.ppm"
                        mv "$tmpdir"/title.ppm "$tmpdir"/"slide_$(($i+1)).ppm"
                elif [ "$nextslide" == 'titlebar' ] || [ "$nextslide" == 'Titlebar' ] ; then
                        title1="${subtitle[$i+$increment]}"
                        title2="${effect1[$i+$increment]}"
                        titlebarslide "$title1" "$title2"
                        waitforfile "$tmpdir/title.ppm"
                        mv "$tmpdir"/title.ppm "$tmpdir"/"slide_$(($i+1)).ppm"
		elif [ "$nextslide" == 'background' ] && [ "${duration[$i+$increment]}" -ne 0 ] ; then
			bg="${effect1[$i+$increment]}"
			background "$bg"   # calls the background image subroutine
			cp "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
		elif [ "${effect1[$i+$increment]}" == 'scroll' ] ; then  # if next picture has scroll effect
                       # Resize the image first
                       image_width="`imagewidth "${image[$i+$increment]}"`"
                       image_height="`imageheight "${image[$i+$increment]}"`"
                       ## calculate frame size after adding black side bars for portrait pictures:
                       if [ $image_width -gt $image_height ] ; then
                               # landscape: 
                               convert -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" "${image[$i+$increment]}" -type TrueColor -depth 8 "$tmpdir"/temp_slideshow_image_scaled.mpc           
                       else
                               # portrait: 
                               convert -resize "$sq_to_dvd_pixels" -resize "$dvd_width" "${image[$i+$increment]}" -type TrueColor -depth 8 "$tmpdir"/temp_slideshow_image_scaled.mpc           
                       fi
                       # now the image is scaled correctly
                       image_width="`imagewidth_sq "$tmpdir/temp_slideshow_image_scaled.mpc"`"
                       image_height="`imageheight "$tmpdir/temp_slideshow_image_scaled.mpc"`"
                       [ "$debug" -ge 1 ] && myecho "[dvd-slideshow] image_width=$image_width image_height=$image_height"
                       if [ "${effect1_params[$i+$increment]}" == 'right' ] ; then
                               x0=0 ; y0=0
                               x1="$dvd_width"; y1="$image_height"
                       elif [ "${effect1_params[$i+$increment]}" == 'left' ] ; then
                               x0=$(( $image_width - $dvd_width )) ; y0=0
                               x1="$image_width"; y1="$image_height"
                       elif [ "${effect1_params[$i+$increment]}" == 'up' ] ; then
                               x0=0 ; y0=$(( $image_height - $dvd_height )) 
                               x1="$image_width"; y1="$image_height"
                       elif [ "${effect1_params[$i+$increment]}" == 'down' ] ; then
                               x0=0 ; y0=0
                               x1="$image_width"; y1="$dvd_height"
                       else
                               myecho "[dvd-slideshow] ERROR: bad effect parameters ${effect1_params[$i]}"
                               cleanup; exit 1
                       fi
                       xi=0 ; yi=0     
                       mycrop
                       convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$dvd_width"x"$dvd_height+$xc0+$yc0" +repage -resize $resolution miff:- | \
                       composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
		else # no manual cropping next picture and it's not a title or background
			checkforautocrop "${image[$(($i+$increment))]}"	
			if [ "$do_autocrop_h" -eq 1 ] ; then
				convert -resize "$sq_to_dvd_pixels" -resize "$dvd_width"x -type TrueColor -depth 8 \
				-gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' +repage "${image[$(($i+$increment))]}" miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
			elif [ "$do_autocrop_w" -eq 1 ] ; then
				convert -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" -type TrueColor -depth 8 \
				-gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' +repage "${image[$(($i+$increment))]}" miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
			else
				convert "${image[$(($i+$increment))]}" -resize "$sq_to_dvd_pixels" -resize $resolution -type TrueColor -depth 8 miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
			fi
		fi

		if [ "$low_quality" -eq 1 ] ; then
			stepsize=5
		elif [ "$high_quality" -eq 1 ] ; then
			stepsize=1
		else
			[ "$frames" -lt 45 ] && stepsize=1 || stepsize=2 
		fi
		## convert ppm to mpc for better speed:
		convert "$tmpdir/slide_$(($i+1)).ppm" -type TrueColor -depth 8 "$tmpdir/slide_$(($i+1)).mpc"
		## do two frames each loop so it's faster?
		echo -n  "[dvd-slideshow]"
		lastbar=0
		for fr in `seq 1 $stepsize $frames`; do
			dj=`addzeros $fr`
			progressbar $fr $frames
			percent=$(( 100 * $fr / $frames ))
			if [ "$smp" -eq 1 ] ; then
			(composite -compose src-over -gravity center -type TrueColor -depth 8 -dissolve $percent "$tmpdir/slide_$(($i+1)).mpc" "$tmpdir/slideshow_background.ppm" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
			else
			(composite -compose src-over -gravity center -type TrueColor -depth 8 -dissolve $percent "$tmpdir/slide_$(($i+1)).mpc" "$tmpdir/slideshow_background.ppm" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
			fi
		done
		waitforfiles "$tmpdir/fade" $dj
		encode_fade
		finish_progressbar
		rm "$tmpdir"/fade_????.ppm
	elif [ "$file" == 'crossfade' ] ; then  #############################################
		## ok, for crossfades, we need to fade both the foreground and background.
		## check to make sure the next slide is an image:
		## now make this get the last real image and the next real image
		## get next image:
		nextslide=`nextslidename`
		increment=`nextslideincrement`
		myecho "[dvd-slideshow] Crossfade `hms ${duration[$i]}`"
		if [ -n "${subtitle[$i]}" ] ; then
			myecho "[dvd-slideshow] Subtitle""= ${subtitle[$i]}"
		fi
		check_rm "$tmpdir/slide_$(($i+1)).ppm"  # make sure it doesn't already exist!
#		check_rm "$tmpdir/slide_$(($i+1)).cache"  # make sure it doesn't already exist!
#		myecho "[dvd-slideshow] next slide=$nextslide. increment=$increment."
		## last slide is slide_$(($i-1)).ppm (already rendered)
		## we need to prepare the NEXT image now:
		if [ "${effect1[$i+$increment]}" == 'crop' ] ; then  # if next picture is specifically cropped
			window=`echo "${effect1_params[$i+$increment]}" | awk -F';' '{print $1";"$2}'`
			parse_window "$window" "${image[$i+$increment]}"
			mycrop  # takes the parameters from <parse_window> and returns: 
			convert "${image[$i+$increment]}" -resize "$sq_to_dvd_pixels" -crop "$c_width"x"$c_height+$xc0+$yc0" +repage -resize $resolution -type TrueColor miff:- | \
			composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
		elif [ "${effect1[$i+$increment]}" == 'kenburns' ] ; then  # if next picture has kenburns effect
			window=`echo "${effect1_params[$i+$increment]}" | awk -F';' '{print $1";"$2}'`
			parse_window "$window" "${image[$i+$increment]}"
			mycrop  # takes the parameters from <parse_window> and returns: 
			convert "${image[$i+$increment]}" -resize "$sq_to_dvd_pixels" -crop "$c_width"x"$c_height+$xc0+$yc0" +repage -resize $resolution miff:- | \
			composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
		elif [ "${effect1[$i+$increment]}" == 'scroll' ] ; then  # if next picture has scroll effect
                       # Resize the image first
                       image_width="`imagewidth "${image[$i+$increment]}"`"
                       image_height="`imageheight "${image[$i+$increment]}"`"
                       ## calculate frame size after adding black side bars for portrait pictures:
                       if [ $image_width -gt $image_height ] ; then
                               # landscape: 
                               convert -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" "${image[$i+$increment]}" +repage -type TrueColor -depth 8 "$tmpdir"/temp_slideshow_image_scaled.mpc           
                       else
                               # portrait: 
                               convert -resize "$sq_to_dvd_pixels" -resize "$dvd_width" "${image[$i+$increment]}" +repage -type TrueColor -depth 8 "$tmpdir"/temp_slideshow_image_scaled.mpc           
                       fi
                       # now the image is scaled correctly
                       image_width="`imagewidth_sq "$tmpdir/temp_slideshow_image_scaled.mpc"`"
                       image_height="`imageheight "$tmpdir/temp_slideshow_image_scaled.mpc"`"
                       [ "$debug" -ge 1 ] && myecho "[dvd-slideshow] image_width=$image_width image_height=$image_height"
                       if [ "${effect1_params[$i+$increment]}" == 'right' ] ; then
                               x0=0 ; y0=0
                               x1="$dvd_width"; y1="$image_height"
                       elif [ "${effect1_params[$i+$increment]}" == 'left' ] ; then
                               x0=$(( $image_width - $dvd_width )) ; y0=0
                               x1="$image_width"; y1="$image_height"
                       elif [ "${effect1_params[$i+$increment]}" == 'up' ] ; then
                               x0=0 ; y0=$(( $image_height - $dvd_height )) 
                               x1="$image_width"; y1="$image_height"
                       elif [ "${effect1_params[$i+$increment]}" == 'down' ] ; then
                               x0=0 ; y0=0
                               x1="$image_width"; y1="$dvd_height"
                       else
                               myecho "[dvd-slideshow] ERROR: bad effect parameters ${effect1_params[$i]}"
                               cleanup; exit 1
                       fi
                       xi=0 ; yi=0     
                       mycrop
                       convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$dvd_width"x"$dvd_height+$xc0+$yc0" +repage -resize $resolution miff:- | \
                       composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
		elif [ "${image[$i+1]}" == 'crossfade' ] ; then
			myecho "[dvd-slideshow] ERROR: Cannot crossfade to another crossfade!"
			cleanup; exit 1
		elif [ "${image[$i+1]}" == 'fadeout' ] ; then
			myecho "[dvd-slideshow] ERROR: Cannot crossfade to a fadeout!"
			cleanup; exit 1
		elif [ "${image[$i+1]}" == 'fadein' ] ; then
			myecho "[dvd-slideshow] ERROR: Cannot crossfade to a fadein!"
			cleanup; exit 1
		elif [ "$nextslide" == 'title' ] || [ "$nextslide" == 'Title' ] ; then
	                if [ -n "${subtitle[$i+$increment]}" ] ; then
	                	title="${subtitle[$i+$increment]}"
			elif [ -n "${effect1[$i+$increment]}" ] ; then
	                	title="${effect1[$i+$increment]}"
			else
				myecho "[dvd-slideshow] ERROR: no title text found in line:"
				myecho "[dvd-slideshow] ${thisline}"
				cleanup; exit 1
			fi
			titleslide "$title"
			waitforfile "$tmpdir/title.ppm"
			mv "$tmpdir"/title.ppm "$tmpdir"/"slide_$(($i+1)).ppm"
                elif [ "$nextslide" == 'titlebar' ] || [ "$nextslide" == 'Titlebar' ] ; then
                        title1="${subtitle[$i+$increment]}"
                        title2="${effect1[$i+$increment]}"
                        titlebarslide "$title1" "$title2"
                        waitforfile "$tmpdir/title.ppm"
                        mv "$tmpdir"/title.ppm "$tmpdir"/"slide_$(($i+1)).ppm"
		elif [ "$nextslide" == 'background' ] && [ "${duration[$i+$increment]}" -ne 0 ] ; then
			bg="${effect1[$i+$increment]}"
			background "$bg"   # calls the background image subroutine
			cp "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
		else # no manual cropping next picture and it's not a title
			checkforautocrop "$nextslide"	
			if [ "$do_autocrop_w" -eq 1 ] ; then
				convert -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" -type TrueColor -depth 8 \
				-gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' +repage "${image[$(($i+$increment))]}" miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
			elif [ "$do_autocrop_h" -eq 1 ] ; then
				convert -resize "$sq_to_dvd_pixels" -resize "$dvd_width"x -type TrueColor -depth 8 \
				-gravity center -crop "$dvd_width"x"$dvd_height"'+0!+0!' +repage "${image[$(($i+$increment))]}" miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
			else
				convert "${image[$(($i+$increment))]}" -resize "$sq_to_dvd_pixels" -resize $resolution -type TrueColor -depth 8 miff:- | \
				composite -compose src-over -gravity center -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$(($i+1)).ppm"
			fi
		fi	
		## now do actual crossfade
		if [ "$low_quality" -eq 1 ] ; then
			stepsize=5
		elif [ "$high_quality" -eq 1 ] ; then
			stepsize=1
		else
			[ "$frames" -lt 45 ] && stepsize=1 || stepsize=2 
		fi
		## convert ppm to mpc for better speed?:
#		convert "$tmpdir/slide_$(($i+1)).ppm" -type TrueColor -depth 8 "$tmpdir/slide_$(($i+1)).mpc"
		lastslide="`previousslideppm`"
#		convert "$lastslide" -type TrueColor -depth 8 "$tmpdir/temp_slideshow_image.mpc"
		echo -n "[dvd-slideshow]"
		lastbar=0 # required for progressbar
		## do two frames each loop so it's faster?
		for fr in `seq 1 $stepsize $frames`; do
			progressbar $fr $frames
			dj=`addzeros $fr`
			percent=$(( 100 * $fr / $frames ))
			if [ "$smp" -eq 1 ] ; then
			(composite -compose src-over -gravity center -type TrueColor -depth 8 -dissolve $percent "$tmpdir/slide_$(($i+1)).ppm" "$lastslide" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
			else
			(composite -compose src-over -gravity center -type TrueColor -depth 8 -dissolve $percent "$tmpdir/slide_$(($i+1)).ppm" "$lastslide" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
			fi
		done
		waitforfiles "$tmpdir/fade" $dj
		encode_fade
		finish_progressbar 
		rm "$tmpdir"/fade_????.ppm
	elif [ "$file" == 'fadeout' ] ; then  #############################################
		## ok, let's copy the background and just fade the foreground:
		## number of frames to render is $frames
#		myecho "[dvd-slideshow] Doing fadeOUT to background...."
		myecho "[dvd-slideshow] Fadeout `hms ${duration[$i]}`"
		if [ -n "${subtitle[$i]}" ] ; then
			myecho "[dvd-slideshow] Subtitle""= ${subtitle[$i]}"
		fi
		## get last slide first?
		lastslide="`previousslideppm`"
		if [ "$low_quality" -eq 1 ] ; then
			stepsize=5
		elif [ "$high_quality" -eq 1 ] ; then
			stepsize=1
		else
			[ "$frames" -lt 45 ] && stepsize=1 || stepsize=2 
		fi
		if [ ! -f "$lastslide" ] ; then
			myecho "[dvd-slideshow] ERROR: $lastslide doesn't exist!"
			myecho "[dvd-slideshow]        you probably are fading without having"
			myecho "[dvd-slideshow]        specified a real image first."
			cleanup; exit 1
		fi
		if [ "${image[$i+1]}" == 'crossfade' ] ; then
			myecho "[dvd-slideshow] ERROR: Cannot fadeout to a crossfade!"
			cleanup; exit 1
		fi
		if [ "${image[$i+1]}" == 'fadeout' ] ; then
			myecho "[dvd-slideshow] ERROR: Cannot fadeout to another fadeout!"
			cleanup; exit 1
		fi
		convert "$lastslide" "$tmpdir/temp_slideshow_image.mpc"
		echo -n "[dvd-slideshow]"
		lastbar=0
		for fr in `seq 1 $stepsize $frames`; do
			dj=`addzeros $fr`
			progressbar $fr $frames
			percent=$(( 100 - 100 * $fr / $frames ))
			if [ "$smp" -eq 1 ] ; then
			(composite -compose src-over -gravity center -type TrueColor -depth 8 -dissolve $percent "$tmpdir/temp_slideshow_image.mpc" "$tmpdir/slideshow_background.ppm" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
			else
			(composite -compose src-over -gravity center -type TrueColor -depth 8 -dissolve $percent "$tmpdir/temp_slideshow_image.mpc" "$tmpdir/slideshow_background.ppm" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
			fi
		done
		waitforfiles "$tmpdir/fade" $dj
		encode_fade
		finish_progressbar	
		rm "$tmpdir"/fade_????.ppm
	elif [ "${image_file[$i]}" -eq 1 ] && [ "${effect1[$i]}" == 'crop' ] ; then  ######################
#		myecho "[dvd-slideshow] Cropping picture"
		myecho "[dvd-slideshow] $image_number/$imagefiles $file `hms ${duration[$i]}`"
		image_number=$(( $image_number + 1 ))
		myecho "[dvd-slideshow] Crop ${effect1_params[$i]}"
		if [ -n "${subtitle[$i]}" ] ; then
			myecho "[dvd-slideshow] Subtitle""= ${subtitle[$i]}"
		fi
		## now the slide may already exist if we had a fadein or crossfade before
		if [ ! -f "$tmpdir/slide_$i.ppm" ] ; then 
			window=`echo "${effect1_params[$i]}" | awk -F';' '{print $1";"$2}'`
			parse_window "$window" "$file"
			mycrop  # takes the parameters from <parse_window> and returns: 
			[ $debug -ge 1 ] && myecho "[dvd-slideshow] Crop $c_width"x"$c_height"+"$xc0"+"$yc0 composite" +"$xci"+$yci
			## now, do the actual crop:
			convert "${file}" -resize "$sq_to_dvd_pixels" -crop "$c_width"x"$c_height+$xc0+$yc0" +repage -resize $resolution -type TrueColor miff:- | composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"
		fi
		encode
		[ "$manual_chapter_markers" -eq 0 ] && write_chap=1
		new_vob=1
		myecho "[dvd-slideshow]############################################################"
	elif [ "${effect1[$i]}" == 'kenburns' ] ; then
		## Kenburns effect from starting point to ending point
#		myecho "[dvd-slideshow] Doing KenBurns Effect...."
#		myecho "[dvd-slideshow] This is very slow since it needs to work in all cases."
#		myecho "[dvd-slideshow] Use the faster scroll options for scrolling left/right/up/down."
		# x0,y0 is the top left corner of the image
		# x1,y1 is the bottom right corner of the image
		# xs0,ys1 is the starting point for the top left corner, etc
		# xe1,ye1 is the ending point for the bottom right corner
		# textfile format is:  
		# file:duration:comment:kenburns:xs0,ys0;xs1,ys1;xe0,ye0;xe1,ye1;startangle,endangle
		myecho "[dvd-slideshow] $image_number/$imagefiles $file `hms ${duration[$i]}`"
		image_number=$(( $image_number + 1 ))
		myecho "[dvd-slideshow] Kenburns ${effect1_params[$i]}"
		if [ -n "${subtitle[$i]}" ] ; then
			myecho "[dvd-slideshow] Subtitle""= ${subtitle[$i]}"
		fi
		image_width="`imagewidth "${file}"`"
		image_height="`imageheight "${file}"`"

		## now, the process should go as follows:
		## 1. figure out the start and end locations of the kenburns effect
		##	in the coordinate system of the "image scaled to display full screen"
		## 2. map those coordinates onto the actual picture coordinates
		## 3. Crop the image to size
		## 4. Place the cropped image in the correct position on the background.

		#####  Get parameters for start and end points of kenburns effect:
		window_start=`echo "${effect1_params[$i]}" | awk -F';' '{print $1";"$2}'`
		parse_window "$window_start" "$file"
		xs0=$x0 ; ys0=$y0 ; xs1=$x1 ; ys1=$y1
		if [ -z $x0 ] || [ -z $y0 ] || [ -z $x1 ] || [ -z $y1 ] ; then
			myecho "[dvd-slideshow] Error: No starting position found for kenburns effect"	
			myecho "[dvd-slideshow] Example: "
			myecho "[dvd-slideshow] image.jpg:duration:subtitle:kenburns:70%;topleft;75%;bottomright"	
			cleanup; exit 1
		fi
		window_end=`echo "${effect1_params[$i]}" | awk -F';' '{print $3";"$4}'`
		parse_window "$window_end" "$file"
		xe0=$x0 ; ye0=$y0 ; xe1=$x1 ; ye1=$y1
		if [ -z $x0 ] || [ -z $y0 ] || [ -z $x1 ] || [ -z $y1 ] ; then
			myecho "[dvd-slideshow] Error: No ending position found for kenburns effect"	
			myecho "[dvd-slideshow] Example: "
			myecho "[dvd-slideshow] image.jpg:duration:subtitle:kenburns:70%;topleft;75%;bottomright"	
			cleanup; exit 1
		fi
		if [ $xs0 -eq $xe0 ] && [ $ys0 -eq $ye0 ] && [ $xs1 -eq $xe1 ] && [ $ys1 -eq $ye1 ] ; then
			# start and end are the same!
			myecho "[dvd-slideshow] ERROR: Start and end of kenburns effect are the same!"	
			cleanup; exit 1
		fi

		# now get rotation angle:  (save for future version)
#		rotation_angle=`echo "${effect1_params[$i]}" | awk -F';' '{print $5}'`
#		start_angle=`echo "$rotation_angle" | awk -F',' '{print $1}'`
#		end_angle=`echo "$rotation_angle" | awk -F',' '{print $2}'`
#		if [ -z "$start_angle" ] && [ -z "$end_angle" ] ; then # no angle specified
#			start_angle=0 ; end_angle=0
#		elif [ -n "$start_angle" ] && [ -z "$end_angle" ] ; then # only one argument
#			start_angle=0
#			myecho "[dvd-slideshow] Rotating image during kenburns from $start_angle to $end_angle"
#		else
#			myecho "[dvd-slideshow] Rotating image during kenburns from $start_angle to $end_angle"
#		fi	

		#### now we have the parameters set up.  The coordinate system is relative to the 
		#### ORIGINAL image size, buffered out to the full DVD frame:
		# xi,yi   xw,yh  xs0,ys0  xs1,ys1  xe0,ye0  xe1,ye1

		s_width=$(( $xs1 - $xs0 )) ; s_height=$(( $ys1 - $ys0 ))
#		s_xcenter=`div10 $(( 10 * $xs0 + 10 * $s_width / 2 ))`
#		s_ycenter=`div10 $(( 10 * $ys0 + 10 * $s_height / 2 ))`
		e_width=$(( $xe1 - $xe0 )) ; e_height=$(( $ye1 - $ye0 ))
#		e_xcenter=`div10 $(( 10 * $xe0 + 10 * $e_width / 2 ))`
#		e_ycenter=`div10 $(( 10 * $ye0 + 10 * $e_height / 2 ))`
		[ $debug -ge 1 ] && myecho "[dvd-slideshow] Coordinate system is original image size buffered out to dvd aspect ratio"
		[ $debug -ge 1 ] && myecho "[dvd-slideshow] Start: width=$s_width height=$s_height  $xs0,$ys0 : $xs1,$ys1"
		[ $debug -ge 1 ] && myecho "[dvd-slideshow] End:   width=$e_width height=$e_height  $xe0,$ye0 : $xe1,$ye1"
		[ $debug -ge 1 ] && myecho "[dvd-slideshow] Image top left corner:   xi=$xi yi=$yi"

		##################################################################
		## so if we're using only 50% of the image, we can pre-crop the image before the
		## main loop to save some processing time...
		## get smallest size of image during effect to know how to rescale:
                min_width=`min $s_width $e_width`
                min_height=`min $s_height $e_height`
		xc0=`min $xs0 $xe0`; xc1=`max $xs1 $xe1`	
		yc0=`min $ys0 $ye0`; yc1=`max $ys1 $ye1`	
		## (make sure the image crop coordinates are not outside the image)
		[ $xc0 -lt $xi ] && xc0=0 || xc0=$(( $xc0 - $xi ))
		[ $yc0 -lt $yi ] && yc0=0 || yc0=$(( $yc0 - $yi ))
		[ $xc1 -gt $(( $xi + $image_width )) ] && xc1=$image_width || xc1=$(( $xc1 - $xi ))
		[ $yc1 -gt $(( $yi + $image_height )) ] && yc1=$image_height || yc1=$(( $yc1 - $yi ))
		c_width=$(( $xc1 - $xc0 )) ; c_height=$(( $yc1 - $yc0 ))
                [ $debug -ge 2 ] && myecho "[dvd-slideshow] Smallest window during kenburns is $min_width x $min_height"
		[ $debug -ge 2 ] && myecho "[dvd-slideshow] Pan/zoom uses $c_width x $c_height of original $image_width x $image_height image"
#               	image_factor_x=$(( 1000 * $min_width / $image_width ))
#               	image_factor_y=$(( 1000 * $min_height / $image_height ))
#               	out_factor_x=$(( 1000 * $min_width / $dvd_width ))
#               	out_factor_y=$(( 1000 * $min_height / $dvd_width ))
#               	[ $debug -ge 0 ] && myecho "[dvd-slideshow] image_size=$image_width"x"$image_height image_factor=$image_factor_x $image_factor_y out_factor=$out_factor_x $out_factor_y"
		did_resize=0

### now, for highest quality, do not resample the image to a reasonable size:  make sure the image
### has 2-3 times the resolution needed so it's not jerky when doing the kenburns effect
## for medium quality (default), resample the image to a reasonable size before doing the kenburns effect

	if [ 0 -eq 1 ] ; then
		if [ "$image_factor_x" -le 1000 ] && [ "$image_factor_y" -le 1000 ] && [ $min_width -gt $dvd_width ] && [ $min_height -gt $dvd_height ] ; then
			## just figure out how much to reszie here.  Make it a multiple of the dvd window size
			myecho "should resize"
#			if [ $c_width -ne $image_width ] || [ $c_height -ne $image_height ] ; then
#				[ $debug -ge 0 ] && myecho "[dvd-slideshow] Cropping from $xc0,$yc0 to $xc1,$yc1"
#			fi
			if [ "$image_factor_x" -gt "$image_factor_y" ] ; then
				[ $debug -ge 0 ] && myecho "[dvd-slideshow] Reducing image to width to $dvd_width"
#				convert "${image[$i]}" -resize "$sq_to_dvd_pixels" -crop "$c_width"x"$c_height"+$xc0+$yc0 -resize $dvd_width "$tmpdir"/temp_slideshow_image_scaled.jpg
				factor_change=$(( 100000 * $dvd_width / $image_width ))
			else
				[ $debug -ge 0 ] && myecho "[dvd-slideshow] Reducing image to height to $dvd_height"
#				convert "${image[$i]}" -resize "$sq_to_dvd_pixels" -crop "$c_width"x"$c_height"+$xc0+$yc0 -resize x"$dvd_height" "$tmpdir"/temp_slideshow_image_scaled.jpg
				factor_change=$(( 100000 * $dvd_height / $image_height ))
			fi
			factor_change_pct=`todec000 $factor_change`
#			did_resize=1
	fi

#		if [ $c_width -ne $image_width ] || [ $c_height -ne $image_height ] ; then
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Kenburns window is smaller than full image:"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Cropping from $xc0,$yc0 to $xc1,$yc1"
#			convert "${image[$i]}" -crop "$c_width"x"$c_height"+$xc0+$yc0 "$tmpdir"/temp_slideshow_image_scaled.ppm 
#			# Now we need to re-calculate the variables we need for the kenburns effect:
#			# xi,yi   xw,yh  xs0,ys0  xs1,ys1  xe0,ye0  xe1,ye1
#			# since we just did a crop, it should be a straight coordinate transformation
#			# about the uppper left corner of the crop window xc0,yc0:
#			image_width="`imagewidth "$tmpdir/temp_slideshow_image_scaled.ppm"`"
#			image_height="`imageheight "$tmpdir/temp_slideshow_image_scaled.ppm"`"
#			xw=$c_width; yh=$c_height
#			## but xi,yi need to be re-calculated because the image aspect ratio has changed:
#			coordinates_in_dvd_aspect_ratio_frame $dvd_width $dvd_height $xw $yh 0 0
#			new_xi=$x_dvd_coordinate ; new_yi=$y_dvd_coordinate
#			delta_xi=$(( $xi - $new_xi )) ; delta_yi=$(( $yi - $new_yi ))
#			xs0=$(( $xs0 - $xc0 - $delta_xi )) ; ys0=$(( $ys0 - $yc0 - $delta_yi ))
#			xs1=$(( $xs1 - $xc0 - $delta_xi )) ; ys1=$(( $ys1 - $yc0 - $delta_yi ))
#			xe0=$(( $xe0 - $xc0 - $delta_xi )) ; ye0=$(( $ye0 - $yc0 - $delta_yi ))
#			xe1=$(( $xe1 - $xc0 - $delta_xi )) ; ye1=$(( $ye1 - $yc0 - $delta_yi ))
#
#			s_width=$(( $xs1 - $xs0 )) ; s_height=$(( $ys1 - $ys0 ))
#			e_width=$(( $xe1 - $xe0 )) ; e_height=$(( $ye1 - $ye0 ))
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Image top left corner:   xi=$xi yi=$yi"
##			xi=$(( $xi - $xc0 )) ; yi=$(( $yi - $yc0 ))
#			xi=$new_xi ; yi=$new_yi
#			[ $xi -le 0 ] && xi=0 ; [ $yi -le 0 ] && yi=0
#
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Coordinates after cropping:"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Start: width=$s_width height=$s_height $xs0,$ys0 : $xs1,$ys1"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] End:   width=$e_width height=$e_height $xe0,$ye0 : $xe1,$ye1"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Image top left corner:   xi=$xi yi=$yi"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] new image size:   width=$image_width $xw height=$image_height $yh"
#			xw=$image_width; xh=$image_height
#		else
#			myecho "[dvd-slideshow] Using whole image. No cropping necessary"
#			convert "${image[$i]}" -resize $sq_to_dvd_pixels "$tmpdir"/temp_slideshow_image_scaled.ppm
#		fi

		factor_change=100000 ; factor_change_pct="100"
	fi

	
		## now, calculate the new kenburns coordinates for the new image:
#		image_width="`imagewidth_sq "$tmpdir/temp_slideshow_image_scaled.mpc"`"
#		image_height="`imageheight "$tmpdir/temp_slideshow_image_scaled.mpc"`"
#		## now we've cropped the image, so the aspect ratio has changed!
#		ratio=$(( 1000* $image_width / $image_height ))
#		out_ratio=$(( 1000* $dvd_width / $dvd_height ))  # doesn't change during script
#		if [ "$ratio" -gt "$(( $out_ratio ))" ] ; then
#			# image width greater than output width at same scale
#			newwidth=$image_width
#			newheight=`div10 $(( 10* $dvd_height * $image_width / $dvd_width ))`
#			xi_new=0
#			yi_new=`div10 $(( 10*( $newheight - $image_height ) / 2 ))`
#		elif [ "$ratio" -le $(( $out_ratio )) ] ; then
#			# image height greater than output height at same scale 
#			newwidth=`div10 $(( 10* $dvd_width * $image_height / $dvd_height ))`
#			newheight=$image_height
#			yi_new=0
#		xi_new=`div10 $(( ( 10*$newwidth - 10*$image_width ) / 2 ))`
#		fi
#		# so xi,yi is the top left corner of the image.  Since we just cropped
#		# we also need to know how much the xi,yi changed 
#		# and shift the coordinates by that amount also:
#		delta_xi=$(( $xi - $xi_new )); delta_yi=$(( $yi - $yi_new ))
#		myecho "delta_xi=$delta_xi delta_yi=$delta_yi"	
#		myecho "image_width=$image_width image_height=$image_height new_width=$newwidth new_height=$newheight"
#		[ $debug -ge 0 ] && myecho "[dvd-slideshow] Did resize.  new width=$image_width new height=$image_height resize=$factor_change_pct"%
#		if [ $did_resize -eq 1 ] ; then
#
#			xs0=`div10 $(( ($xs0-$xc0-$delta_xi) * $factor_change / 10000 ))`; ys0=`div10 $(( ($ys0-$yc0-$delta_yi) * $factor_change / 10000 ))`
#	       	        xs1=`div10 $(( ($xs1-$xc0-$delta_xi) * $factor_change / 10000 ))`; ys1=`div10 $(( ($ys1-$yc0-$delta_yi) * $factor_change / 10000 ))`
#	      	        xe0=`div10 $(( ($xe0-$xc0-$delta_xi) * $factor_change / 10000 ))`; ye0=`div10 $(( ($ye0-$yc0-$delta_yi) * $factor_change / 10000 ))`
#	      	        xe1=`div10 $(( ($xe1-$xc0-$delta_xi) * $factor_change / 10000 ))`; ye1=`div10 $(( ($ye1-$yc0-$delta_yi) * $factor_change / 10000 ))`
#			xi=$xi_new ; yi=$yi_new
#
#			s_width=$(( $xs1 - $xs0 )) ; s_height=$(( $ys1 - $ys0 ))
##			s_xcenter=`div10 $(( 10 * $xs0 + 10 * $s_width / 2 ))`
##			s_ycenter=`div10 $(( 10 * $ys0 + 10 * $s_height / 2 ))`
#			e_width=$(( $xe1 - $xe0 )) ; e_height=$(( $ye1 - $ye0 ))
##			e_xcenter=`div10 $(( 10 * $xe0 + 10 * $e_width / 2 ))`
##			e_ycenter=`div10 $(( 10 * $ye0 + 10 * $e_height / 2 ))`
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Coordinates after cropping:"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Start: width=$s_width height=$s_height $xs0,$ys0 : $xs1,$ys1"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] End:   width=$e_width height=$e_height $xe0,$ye0 : $xe1,$ye1"
#			[ $debug -ge 0 ] && myecho "[dvd-slideshow] Image top left corner:   xi=$xi yi=$yi"
#		fi

#	fi

#	convert "$tmpdir/temp_slideshow_image_scaled.ppm" -resize "$sq_to_dvd_pixels" "$tmpdir"/temp_slideshow_image_scaled.mpc		
	convert "${image[$i]}" -resize "$sq_to_dvd_pixels" +repage "$tmpdir"/temp_slideshow_image_scaled.mpc

		############################ end crop/resize large images

		## adjust step size: ##############################
#		[ "$frames" -lt 45 ] && stepsize=1 || stepsize=2 
		if [ "$low_quality" -eq 1 ] ; then
			stepsize=5
			interp=0
		elif [ "$high_quality" -eq 1 ] ; then
			stepsize=1
			interp=0
		else
			stepsize=1
			interp=0
		fi
#		echo 'x0,y0,x1,y1,xcenter,ycenter,xwidth,yheight,xc0,yc0,c_width,c_height' > kenburns_coordinates.csv
#		echo 'xc0,yc0,c_width,c_height,xci,yci,iwn,ihn,predicted_resized_width,predicted_resized_height,xc0_dec,yc0_dec' > kenburns_coordinates.csv
#		echo 'xc0,yc0,c_width,c_height,xci,yci,predicted_resized_width,predicted_resized_height' > kenburns_coordinates.csv
		if [ "$interp" -eq 1 ] ; then
			## create the 3 images representing shifted pixels:
			##  A B
			##  C 
			## where A is the original image
			iwn="`imagewidth_sq "$tmpdir/temp_slideshow_image_scaled.mpc"`"
			ihn="`imageheight "$tmpdir/temp_slideshow_image_scaled.mpc"`"
		               convert "$tmpdir/temp_slideshow_image_scaled.mpc" -type TrueColor -depth 8 "$tmpdir/A.mpc"
		               convert "$tmpdir/temp_slideshow_image_scaled.mpc" -type TrueColor -depth 8 -crop "$(($iwn-1))"x"$ihn"+1+0 +repage -background red -splice 1x0+"$(($iwn-1))"+"$ihn" "$tmpdir/B.mpc"
		               convert "$tmpdir/temp_slideshow_image_scaled.mpc" -type TrueColor -depth 8 -crop "$iwn"x"$(($ihn-1))"+0+1 +repage -background red -splice 0x1+"$iwn"+"$(($ihn-1))" "$tmpdir/C.mpc"
				convert -size "$c_width"x"$c_height" xc:transparent -resize "$dvd_width"x"$dvd_height"! "$tmpdir"/T.mpc
#	                convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$(($iwn-1))"x"$(($ihn-1))"+1+1 -background red -splice 1x1+"$(($iwn-1))"+"$(($ihn-1))" "$tmpdir/D.ppm"
		fi
#		if [ $xe0 -gt $xs0 ] ; then
#			xvelocity=$(( 1000 * ($xe0-$xs0) / $frames ))
#		else
#			xvelocity=$(( 1000 * ($xs0-$xe0) / $frames ))
#		fi
#		if [ $ye0 -gt $ys0 ] ; then
#			yvelocity=$(( 1000 * ($ye0-$ys0) / $frames ))
#		else
#			yvelocity=$(( 1000 * ($ys0-$ye0) / $frames ))
#		fi
#		if [ "$interp" -eq 1 ] && [ "$xvelocity" -lt 4000 -o "$yvelocity" -lt 4000 ] ; then
#			echo "[dvd-slideshow] Using interpolation. Velocity=$xvelocity $yvelocity"
#		else
#			echo "[dvd-slideshow] Using interpolation. Velocity=$xvelocity $yvelocity"
#			interp=0
#		fi

		## start loop for kenburns effect:
		echo -n  "[dvd-slideshow]"
		lastbar=0

		## need to summarize math here!
		#### smooth accel constants  fix from Daniel Bertrand
		smooth_ken=0
                if [ $smooth_ken -eq 1 ] && [ $frames -ge 30 ]; then
                        smooth_time=15; # number of frames for the smooth acceleration
                        smooth_end=$(($frames -$smooth_time)) # frame number for the beginning of the decel period
                        smooth_slope=$( echo "scale=9;$frames/($frames -$smooth_time)" | bc -l ) #slope of the normal kensburn period
                        smooth_offset=$( echo "scale=9;$frames-$smooth_slope/$smooth_time*($frames^2/2)" | bc -l ) #random constant in the decel equation
                fi

		for fr in `seq 1 $stepsize $frames`; do
			dj=`addzeros $fr`

                        if [ $smooth_ken -eq 1 ] && [ $frames -ge 30 ]; then
                            if [ $fr -le $smooth_time ] ; then
                                y=$( echo "scale=9;$smooth_slope/($smooth_time*2)*($fr^2)" | bc -l )
                            elif [ $fr -le $smooth_end ]; then
                                y=$( echo "scale=9;$smooth_slope*$fr-($smooth_time/2)*$smooth_slope" | bc -l )
                            else
                                y=$( echo "scale=9;-$smooth_slope/($smooth_time)*(($fr^2)/2-$frames*$fr)+$smooth_offset" | bc -l )
                            fi

                            if [ "$s_height" -eq "$e_height" ] ; then
                                logfactor=$( echo "scale=9;1000 * $y / $frames" | bc -l )
                            else
                                logfactor=$( echo "scale=9;l( 1- $y / $frames * ( 1 - $s_height / $e_height ) ) / l( $s_height / $e_height) * 1000" | bc -l )
                            fi

                        else  ## no start/stop speed adjustment
				if [ "$s_height" -eq "$e_height" ] ; then
	#				logfactor=$(( 1000 * $fr / $frames ))
					logfactor=$( echo "scale=3; 1000 * $fr / $frames" | bc )
				else
					logfactor=$( echo "l( 1- $fr / $frames * ( 1 - $s_height / $e_height ) ) / l( $s_height / $e_height) * 1000 " | bc -l )
				fi
			fi
			[ -z `echo $logfactor | awk -F. '{print $1}'` ] && logfactor=0$logfactor
#			frframes_linear=$(( 1000 * $fr / $frames ))
	                x0=$( echo "scale=3; 1000 * $xs0 + ($xe0-$xs0) * $logfactor" | bc )
	                y0=$( echo "scale=3; 1000 * $ys0 + ($ye0-$ys0) * $logfactor" | bc )
	                x1=$( echo "scale=3; 1000 * $xs1 + ($xe1-$xs1) * $logfactor" | bc )
	                y1=$( echo "scale=3; 1000 * $ys1 + ($ye1-$ys1) * $logfactor" | bc )
	                ## need to round the numbers for bash:
	                ## these are the "whole" integer portion of the number:
	                it=`echo "$x0" | awk -F. '{print $1}'` ; [ -z "$it" ] && x0=0 || x0="$it"
	                it=`echo "$y0" | awk -F. '{print $1}'` ; [ -z "$it" ] && y0=0 || y0="$it"
	                it=`echo "$x1" | awk -F. '{print $1}'` ; [ -z "$it" ] && x1=0 || x1="$it"
	                it=`echo "$y1" | awk -F. '{print $1}'` ; [ -z "$it" ] && y1=0 || y1="$it"
#			myecho "x0=$x0 y0=$y0 x1=$x1 y1=$y1 logfactor=$logfactor"
			if [ "$interp" -eq 1 ] ; then
				x0_d=$( echo "scale=3; $xs0 + ($xe0-$xs0) * $logfactor / 1000" | bc )
				y0_d=$( echo "scale=3; $ys0 + ($ye0-$ys0) * $logfactor / 1000" | bc )
				x1_d=$( echo "scale=3; $xs1 + ($xe1-$xs1) * $logfactor / 1000" | bc )
				y1_d=$( echo "scale=3; $ys1 + ($ye1-$ys1) * $logfactor / 1000" | bc )
			#	myecho "x0=$x0 x0_d=$x0_d y0=$y0 y0_d=$y0_d logfactor=$logfactor"
				x0_dec=`printf %3.3f $x0_d | awk -F. '{print "0."$2}'`; 
				y0_dec=`printf %3.3f $y0_d | awk -F. '{print "0."$2}'`;
				x1_dec=`printf %3.3f $x1_d | awk -F. '{print "0."$2}'`; 
				y1_dec=`printf %3.3f $y1_d | awk -F. '{print "0."$2}'`;
#				myecho "x0=$x0 x0_dec=$x0_dec y0=$y0 y0_dec=$y0_dec logfactor=$logfactor"
			fi
			crop_parameters # figure out final crop parameters  0.19s
#			myecho "x0=$x0 x0_dec=$x0_dec y0=$y0 y0_dec=$y0_dec logfactor=$logfactor"
			# outputs correct predicted_resized_width and predicted_resized_height

#			echo '$xc0,$yc0,$c_width,$c_height,$xci,$yci,$iwn,$ihn,$predicted_resized_width,$predicted_resized_height,$xc0_dec,$yc0_dec' >> kenburns_coordinates.csv
#			echo "$xc0,$yc0,$c_width,$c_height,$xci,$yci,$predicted_resized_width,$predicted_resized_height" >> kenburns_coordinates.csv

			[ $debug -ge 2 ] && myecho "[dvd-slideshow] $fr xc0,yc0=$xc0_whole.$xc0_dec,$yc0_whole.$yc0_dec cw,ch=$c_width,$c_height xci,yci=$xci,$yci"
			[ $debug -ge 2 ] && myecho "[dvd-slideshow] $fr xc0,yc0=$xc0,$yc0 cw,ch=$c_width,$c_height xci,yci=$xci,$yci"
			i_width=$predicted_resized_width; i_height=$predicted_resized_height

			if [ "$interp" -eq 1 ] ; then
				myecho "x0=$x0 y0=$y0 x0_dec=$x0_dec y0_dec=$y0_dec"
				## now, we're going to calculate the following parameters:
				# aA + bB + cC = Z
				# X = (1-alpha)*T + alpha*A
				# Y = (1-beta)*X + beta*B
				# Z = (1-gamma)*Y + gamma*C
				# if a,b,c != 1 
				# gamma= c
				# beta= b/(1-gamma)
				# alpha= a/[(1-beta)*(1-gamma)]

				# now a=Afactor b=bFactor c=cFactor
				# calculate subpixel-averaging weights:
	                        Afactor=$( echo "scale=3; 100*(1-$x0_dec)*(1-$y0_dec)" | bc )
	                        Bfactor=$( echo "scale=3; 100*($x0_dec)*(1-$y0_dec)" | bc )
	                        Cfactor=$( echo "scale=3; 100*(1-$x0_dec)*($y0_dec)" | bc )
#	                        Dfactor=$( echo "scale=3; ($x0_dec/1000)*($y0_dec/1000)" | bc )
	                        Afactor=`printf %3.0f $Afactor`
	                        Bfactor=`printf %3.0f $Bfactor`
	                        Cfactor=`printf %3.0f $Cfactor`
#	                        Dfactor=`printf %3.0f $Dfactor`
	
				if [ $Afactor -ne 100 -a $Bfactor -ne 100 -a $Cfactor -ne 100 ]; then
					gamma="$Cfactor"
	                        	beta=$( echo "scale=3; 100 * $Bfactor / ( 100 - $gamma )" | bc )
	                        	beta=`printf %3.0f $beta`
	                        	alpha=$( echo "scale=3; 100 * $Afactor / ( 100 - $beta ) / ( 100 - $gamma )" | bc )
	                        	alpha=`printf %3.0f $alpha`
	                        	myecho "Af=$Afactor Bf=$Bfactor Cf=$Cfactor alpha=$alpha beta=$beta gamma=$gamma"
				fi
			fi

			delta_width=$(( $dvd_width - $predicted_resized_width ))
			delta_height=$(( $dvd_height - $predicted_resized_height ))
#			myecho "delta_width=$delta_width delta_height=$delta_height"
			if [ $delta_width -le 4 ] && [ $delta_height -le 2 ] ; then
#				echo "[dvd-slideshow:Kenburns: delta_width=$delta_width delta_height=$delta_height"
				# force the output size to be exact:  no composite needed!
				if [ "$interp" -eq 1 ] ; then
					if [ $Afactor -ne 100 -a $Bfactor -ne 100 -a $Cfactor -ne 100 ]; then
						convert "$tmpdir"/A.mpc -crop "$c_width"x"$c_height"+"$xc0"+"$yc0" +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/A_temp.ppm"
						convert "$tmpdir"/B.mpc -crop "$c_width"x"$c_height"+"$xc0"+"$yc0" +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/B_temp.ppm"
						convert "$tmpdir"/C.mpc -crop "$c_width"x"$c_height"+"$xc0"+"$yc0" +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/C_temp.ppm"
						composite -compose src-over -dissolve "$alpha" "$tmpdir"/A_temp.ppm "$tmpdir"/T.mpc -type TrueColor -depth 8 "$tmpdir/X.ppm"
						composite -compose src-over -dissolve "$beta" "$tmpdir"/B_temp.ppm "$tmpdir"/X.ppm -type TrueColor -depth 8 "$tmpdir/Y.ppm"
						composite -compose src-over -dissolve "$gamma" "$tmpdir"/C_temp.ppm "$tmpdir"/Y.ppm -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm"
					else
						echo "one"
						if [ $Afactor -eq 1 ] ; then	
					  		(convert "$tmpdir/A.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
						elif [ $Afactor -eq 1 ] ; then	
							echo ""
						elif [ $Afactor -eq 1 ] ; then	
							echo ""
						fi
					fi
				else
					if [ $bgfile == 'black' ] ; then
					if [ "$smp" -eq 1 ] ; then
					  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
					else
					  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
					fi
					else
					if [ "$smp" -eq 1 ] ; then
					  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
					else
					  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
					fi
					fi
				fi
				i_width=$dvd_width; i_height=$dvd_height
			elif [ $bgfile == 'black' ] ; then
				# calculate border size for possible speed improvement:
				deltax=$(( $dvd_width - $i_width )) ; deltay=$(( $dvd_height - $i_height ))
				# splice in black background if we can for better speed!
				# split the difference between the two sides. If odd, add extra
				# to bottom right?
				left=$(( $xci )); right=$(( $deltax - $left ))
				top=$(( $yci )) ; bottom=$(( $deltay - $top ))
#	                        myecho "left=$left right=$right top=$top bottom=$bottom"
				if [ "$interp" -eq 1 ] ; then
					convert "$tmpdir"/A.mpc -crop "$c_width"x"$c_height"+"$xc0"+"$yc0" +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/A_temp.ppm"
					convert "$tmpdir"/B.mpc -crop "$c_width"x"$c_height"+"$xc0"+"$yc0" +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/B_temp.ppm"
					convert "$tmpdir"/C.mpc -crop "$c_width"x"$c_height"+"$xc0"+"$yc0" +repage -resize "$dvd_width"x"$dvd_height"! -type TrueColor -depth 8 "$tmpdir/C_temp.ppm"
					composite -compose src-over -dissolve "$alpha" "$tmpdir"/A_temp.ppm "$tmpdir"/T.mpc -type TrueColor -depth 8 "$tmpdir/X.ppm"
					composite -compose src-over -dissolve "$beta" "$tmpdir"/B_temp.ppm "$tmpdir"/X.ppm -type TrueColor -depth 8 "$tmpdir/Y.ppm"
					composite -compose src-over -dissolve "$gamma" "$tmpdir"/C_temp.ppm "$tmpdir"/Y.ppm -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm"
				elif [ "$smp" -eq 1 ] ; then
				  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height" -background black -splice "$right"x"$bottom"+$i_width+$i_height -splice "$left"x"$top" -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
				else
				  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height" -background black -splice "$right"x"$bottom"+$i_width+$i_height -splice "$left"x"$top" -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
# works with imagemagick > 6.0.6  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height" -bordercolor black -compose src-over -border 0 -background black -splice "$right"x"$bottom"+$i_width+$i_height -splice "$left"x"$top" -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
#				  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -write "$tmpdir/tmp1.ppm" -resize "$dvd_width"x"$dvd_height" -write "$tmpdir/tmp2.ppm" -bordercolor black -border 0 -background black -splice "$right"x"$bottom"+$i_width+$i_height -splice "$left"x"$top" -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
#				echo "[dvd-slideshow:Kenburns: crop_w=$c_width crop_h=$c_height"
#				  convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 "$tmpdir"/tmp1.ppm
#				iwn="`imagewidth_sq "$tmpdir/tmp1.ppm"`"
#				ihn="`imageheight "$tmpdir/tmp1.ppm"`"
#				echo "[dvd-slideshow:Kenburns: croped_w=$iwn croped_h=$ihn"
#				  convert "$tmpdir/tmp1.ppm" -resize "$dvd_width"x"$dvd_height" "$tmpdir/tmp2.ppm"
#				iwn="`imagewidth_sq "$tmpdir/tmp2.ppm"`"
#				ihn="`imageheight "$tmpdir/tmp2.ppm"`"
#				echo "[dvd-slideshow:Kenburns: resized_w=$iwn resized_h=$ihn predicted_w=$predicted_resized_width predicted_h=$predicted_resized_height"
#				  convert "$tmpdir/tmp2.ppm" -bordercolor black -border 0 -background black -splice "$right"x"$bottom"+$i_width+$i_height -splice "$left"x"$top" -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm"
#				iwn="`imagewidth_sq "$tmpdir/fade_$dj.ppm"`"
#				ihn="`imageheight "$tmpdir/fade_$dj.ppm"`"
#				echo "[dvd-slideshow:Kenburns: output_w=$iwn output_h=$ihn"
				fi
			else  
				if [ "$interp" -eq 1 ] ; then
	                           echo "Af=$Afactor Bf=$Bfactor Cf=$Cfactor"
				   convert "$tmpdir"/A.mpc -crop "$c_width"x"$c_height"+"$x0"+"$y0" -type TrueColor -depth 8 "$tmpdir/A_temp.ppm"
				   convert -crop "$c_width"x"$c_height"+"$x0"+"$y0" -type TrueColor -depth 8 "$tmpdir"/B.ppm "$tmpdir/B_temp.ppm"
				   convert -crop "$c_width"x"$c_height"+"$x0"+"$y0" -type TrueColor -depth 8 "$tmpdir"/C.ppm "$tmpdir/C_temp.ppm"
				    composite -compose src-over -dissolve "$Afactor" -type TrueColor -depth 8 "$tmpdir"/A_temp.ppm "$tmpdir"/C_temp.ppm "$tmpdir"/fade_$dj.ppm 
				elif [ "$smp" -eq 1 ] ; then
				  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height" -type TrueColor -depth 8 miff:- | composite -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 - "$tmpdir/slideshow_background.ppm" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &
				else
				  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+"$xc0"+"$yc0"\! +repage -resize "$dvd_width"x"$dvd_height" -type TrueColor -depth 8 png:- | composite - -compose src-over -geometry "+$xci+$yci" -type TrueColor -depth 8 "$tmpdir/slideshow_background.ppm" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames )
				fi
			fi
#				  (convert "$tmpdir/temp_slideshow_image_scaled.mpc" -crop "$c_width"x"$c_height"+$xc0+$yc0 +repage -resize "$dvd_width"x"$dvd_height" -compose src-over -bordercolor black -border 0 -background black -splice "$right"x"$bottom"+$i_width+$i_height -splice "$left"x"$top" -type TrueColor -depth 8 "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames ) &

			## calculating the following values should be quicker in the future:
			progressbar $fr $frames
		done
		waitforfiles "$tmpdir/fade" $dj
		encode_fade
		finish_progressbar
		## just in case we want to fade out or crossfade, we need to save the last image:
		mv "$tmpdir/fade_$dj.ppm" "$tmpdir/slide_$i.ppm"
		find "$tmpdir" -name fade\*.ppm -type f -print0 | xargs -0 rm
	elif [ "${effect1[$i]}" == 'scroll' ] ; then
#		myecho "[dvd-slideshow] Doing scroll effect"
		myecho "[dvd-slideshow] $image_number/$imagefiles $file `hms ${duration[$i]}`"
		myecho "[dvd-slideshow] Scroll ${effect1_params[$i]}"
		image_number=$(( $image_number + 1 ))
		if [ -n "${subtitle[$i]}" ] ; then
			myecho "[dvd-slideshow] Subtitle""= ${subtitle[$i]}"
		fi
		## assume a panorama image?  use full image height.
		# textfile format is:  
		# file:duration:comment:scrollright

		## resize the image first to speed things up:
		## remember output resolution is $dvd_width x $dvd_height

		image_width="`imagewidth "${file}"`"
		image_height="`imageheight "${file}"`"
		## calculate frame size after adding black side bars for portrait pictures:
		if [ $image_width -gt $image_height ] ; then
			# landscape:  (for scroll left/right)
			convert "${file}" -resize "$sq_to_dvd_pixels" -resize x"$dvd_height" +repage -type TrueColor -depth 8 "$tmpdir"/temp_slideshow_image_scaled.mpc		
		else
			# portrait:  (for scroll up/down )
			convert "${file}" -resize "$sq_to_dvd_pixels" -resize "$dvd_width" +repage -type TrueColor -depth 8 "$tmpdir"/temp_slideshow_image_scaled.mpc		
		fi

		# now the image is scaled so the height is correct
		image_width="`imagewidth_sq "$tmpdir/temp_slideshow_image_scaled.mpc"`"
		image_height="`imageheight "$tmpdir/temp_slideshow_image_scaled.mpc"`"
		[ "$debug" -ge 1 ] && myecho "[dvd-slideshow] image_width=$image_width image_height=$image_height"
		if [ "${effect1_params[$i]}" == 'right' ] ; then
#			myecho "[dvd-slideshow] Doing scroll right effect"
			xs0=0 ; ys0=0 # scroll right
			xs1="$image_width"; ys1="$image_height"
			xe0=$(( $image_width - $dvd_width )) ; ye0=0
			xe1="$image_width"; ye1="$image_height" # y doesn't change
		elif [ "${effect1_params[$i]}" == 'left' ] ; then
#			myecho "[dvd-slideshow] Doing scroll left effect"
			xs0=$(( $image_width - $dvd_width )) ; ys0=0
			xs1="$image_width"; ys1="$image_height" # y doesn't change
			xe0=0 ; ye0=0 # scroll left
			xe1="$image_width"; ye1="$image_height"
		elif [ "${effect1_params[$i]}" == 'up' ] ; then
#			myecho "[dvd-slideshow] Doing scroll up effect"
			xs0=0 ; ys0=$(( $image_height - $dvd_height )) 
			xs1="$image_width"; ys1="$image_height"
			xe0=0 ; ye0=0 # scroll up
			xe1="$dvd_width"; ye1="$dvd_height" # x doesn't change
		elif [ "${effect1_params[$i]}" == 'down' ] ; then
#			myecho "[dvd-slideshow] Doing scroll down effect"
			xs0=0 ; ys0=0 # scroll down
			xs1="$dvd_width"; ys1="$dvd_height" # x doesn't change
			xe0=0 ; ye0=$(( $image_height - $dvd_height )) 
			xe1="$image_width"; ye1="$image_height"
		else
			myecho "[dvd-slideshow] ERROR: bad effect parameters ${effect1_params[$i]}"
			cleanup; exit 1
		fi
		[ "$debug" -ge 2 ] && myecho "[dvd-slideshow] params=$xs0,$ys0 ; $xs1,$ys1 ; $xe0,$ye0 ; $xe1,$ye1"
		if [ "$low_quality" -eq 1 ] ; then
			stepsize=5; interp=0
		elif [ "$high_quality" -eq 1 ] ; then
			stepsize=1; interp=1
			
		else
#			[ "$frames" -lt 45 ] && stepsize=1 || stepsize=2 
			stepsize=1; interp=0
		fi
		if [ "$interp" -eq 1 ] ; then
			## create the 3 images representing shifted pixels:
			##  A B
			##  C 
			## where A is the original image
			iwn="`imagewidth_sq "$tmpdir/temp_slideshow_image_scaled.mpc"`"
			ihn="`imageheight "$tmpdir/temp_slideshow_image_scaled.mpc"`"
	                convert "$tmpdir/temp_slideshow_image_scaled.mpc" -type TrueColor -depth 8 "$tmpdir/A.mpc"
	                convert "$tmpdir/temp_slideshow_image_scaled.mpc" -type TrueColor -depth 8 -crop "$(($iwn-1))"x"$ihn"+1+0 +repage -background red -splice 1x0+"$(($iwn-1))"+"$ihn" "$tmpdir/B.mpc"
	                convert "$tmpdir/temp_slideshow_image_scaled.mpc" -type TrueColor -depth 8 -crop "$iwn"x"$(($ihn-1))"+0+1 +repage -background red -splice 0x1+"$iwn"+"$(($ihn-1))" "$tmpdir/C.mpc"
		fi
		xvelocity=$(( 1000 * ($xe0-$xs0) / $frames ))
		yvelocity=$(( 1000 * ($ye0-$ys0) / $frames ))
#		myecho "[dvd-slideshow] xVelocity=$xvelocity yVelocity=$yvelocity interp=$interp"
		if [ "$interp" -eq 1 ] && [ "$yvelocity" -eq 0 ] && [ "$xvelocity" -lt 5000 ] ; then
			myecho "[dvd-slideshow] Using interpolation. xVelocity=$xvelocity"
		elif [ "$interp" -eq 1 ] && [ "$xvelocity" -eq 0 ] && [ "$yvelocity" -lt 5000 ] ; then
			myecho "[dvd-slideshow] Using interpolation. yVelocity=$yvelocity"
		else
			myecho "[dvd-slideshow] Using standard method, not extra-smooth mode. "
			interp=0
		fi
		echo -n "[dvd-slideshow]"
		lastbar=0
		for fr in `seq 1 $stepsize $frames`; do
			dj=`addzeros $fr`
			x0=`div1000 $(( 1000 * $xs0 + $(($xe0-$xs0)) * 1000 * $fr / $frames ))`
			y0=`div1000 $(( 1000 * $ys0 + $(($ye0-$ys0)) * 1000 * $fr / $frames ))`
			progressbar $fr $frames
			if [ "$interp" -eq 1 ] ; then
				x0=$( echo "scale=3; $xs0 + ($xe0-$xs0)* $fr / $frames" | bc )
				y0=$( echo "scale=3; $ys0 + ($ye0-$ys0)* $fr / $frames" | bc )
				x0_dec=`printf %3.3f $x0 | awk -F. '{print "0."$2}'`; 
				y0_dec=`printf %3.3f $y0 | awk -F. '{print "0."$2}'`;
				## need to round the numbers for bash:
				it=`echo "$x0" | awk -F. '{print $1}'` ; [ -z "$it" ] && x0_whole=0 || x0_whole="$it"
				it=`echo "$y0" | awk -F. '{print $1}'` ; [ -z "$it" ] && y0_whole=0 || y0_whole="$it"
#				myecho "x0=$x0 y0=$y0 x0_whole=$x0_whole x0_dec=$x0_dec y0_whole=$y0_whole y0_dec=$y0_dec"
				# calculate subpixel-averaging weights:
	                        Afactor=$( echo "scale=3; 100*(1-$x0_dec)*(1-$y0_dec)" | bc )
	                        Bfactor=$( echo "scale=3; 100*($x0_dec)*(1-$y0_dec)" | bc )
	                        Cfactor=$( echo "scale=3; 100*(1-$x0_dec)*($y0_dec)" | bc )
#	                        Dfactor=$( echo "scale=3; ($x0_dec/1000)*($y0_dec/1000)" | bc )
	                        Afactor=`printf %3.0f $Afactor`
	                        Bfactor=`printf %3.0f $Bfactor`
	                        Cfactor=`printf %3.0f $Cfactor`
#	                        Dfactor=`printf %3.1f $Dfactordvd_width
#	                        echo "Af=$Afactor Bf=$Bfactor Cf=$Cfactor"
				it="${effect1_params[$i]}"
				if [ "$it" == 'down' ] || [ "$it" == 'up' ] ; then
				   convert -crop "$dvd_width"x"$dvd_height"+"$x0_whole"+"$y0_whole" +repage -type TrueColor -depth 8 "$tmpdir"/A.mpc "$tmpdir/A_temp.ppm"
				   convert -crop "$dvd_width"x"$dvd_height"+"$x0_whole"+"$y0_whole" +repage -type TrueColor -depth 8 "$tmpdir"/C.mpc "$tmpdir/C_temp.ppm"
				    if [ "$smp" -eq 1 ] ; then
				    (composite -compose src-over -dissolve "$Afactor" -type TrueColor -depth 8 "$tmpdir"/A_temp.ppm "$tmpdir"/C_temp.ppm "$tmpdir"/fade_$dj.ppm) &
				    else
				    composite -compose src-over -dissolve "$Afactor" -type TrueColor -depth 8 "$tmpdir"/A_temp.ppm "$tmpdir"/C_temp.ppm "$tmpdir"/fade_$dj.ppm 
				    fi
				else # left or right
				    convert "$tmpdir"/A.mpc -crop "$dvd_width"x"$dvd_height"+"$x0_whole"+"$y0_whole" +repage -type TrueColor -depth 8 "$tmpdir/A_temp.ppm"
				    convert "$tmpdir"/B.mpc -crop "$dvd_width"x"$dvd_height"+"$x0_whole"+"$y0_whole" +repage -type TrueColor -depth 8 "$tmpdir/B_temp.ppm"
				    if [ "$smp" -eq 1 ] ; then
				    (composite -compose src-over -dissolve "$Afactor" -type TrueColor -depth 8 "$tmpdir"/A_temp.ppm "$tmpdir"/B_temp.ppm "$tmpdir"/fade_$dj.ppm) &
				    else
				    composite -compose src-over -dissolve "$Afactor" -type TrueColor -depth 8 "$tmpdir"/A_temp.ppm "$tmpdir"/B_temp.ppm "$tmpdir"/fade_$dj.ppm
				    fi
				fi
			else
				if [ "$smp" -eq 1 ] ; then
				(convert -crop "$dvd_width"x"$dvd_height"+$x0+$y0 +repage -type TrueColor -depth 8 "$tmpdir/temp_slideshow_image_scaled.mpc" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames) &
				else
				(convert -crop "$dvd_width"x"$dvd_height"+$x0+$y0 +repage -type TrueColor -depth 8 "$tmpdir/temp_slideshow_image_scaled.mpc" "$tmpdir/fade_$dj.ppm" ; extracopies $fr $frames)
				fi
			fi
		done
		waitforfiles "$tmpdir/fade" $dj
		encode_fade
		finish_progressbar
		## just in case we want to fade out or crossfade, we need to save the last image:
		mv "$tmpdir/fade_$dj.ppm" "$tmpdir/slide_$i.ppm"
		find "$tmpdir" -name fade\*.ppm -type f -print0 | xargs -0 rm
		interp=0
	elif [ "$file" == 'black' ] ; then  ###############################################
		## use plain black background with no picture
		## phase out "black" tag.  Use background:::black instead
		myecho "[dvd-slideshow] ERROR: use of black is depreciated.  Use the syntax:"
		myecho "[dvd-slideshow]        background:duration:subtitle:black   instead of:"
		myecho "[dvd-slideshow]        black:duration:subtitle            <depreciated>"
		cleanup; exit 1
	elif [ "$file" == 'testslide' ] ; then  ###############################################
		## Create a slide of size 720x480 with yellow lines spaced every 100 pixels
		convert -size 720x480 xc:gray -fill yellow -draw "line 0,40,720,40 text 110,40 \"40\" line 0,140,720,140 text 110,140 \"140\" line 0,240,720,240 text 110,240 \"240\" line 0,340,720,340 text 110,340 \"340\" line 0,440,720,440 text 110,440 \"440\" " -fill orange -draw "line 60,0,60,480 text 60,180 \"60\" line 160,0,160,480 text 160,180 \"160\" line 260,0,260,480 text 260,180 \"260\" line 360,0,360,480 text 360,180 \"360\" line 460,0,460,480 text 460,180 \"460\" line 560,0,560,480 text 560,180 \"560\" line 660,0,660,480 text 660,180 \"660\" " -type TrueColor -depth 8 -resize "$sq_to_dvd_pixels" -resize "$resolution" -quality 100 "$tmpdir/slide_$i.ppm"
		encode
		myecho "[dvd-slideshow]############################################################"
	elif [ "$file" == 'exit' ] ; then  # Exit
		## stop here and finish .vob
		break
	elif [ "$file" == 'background' ] ; then  # Background
		bg="${effect1[$i]}"
		if [ -n "$bg" ] ; then
			background "$bg"   # calls the background image subroutine
		fi
		if [ "${duration[$i]}" -ne 0 ] ; then  
			myecho "[dvd-slideshow] $file `hms ${duration[$i]}`"
			## user wants to actually display background for a given time
			myecho "[dvd-slideshow] Displaying background image ${bgfile}"
			cp "$tmpdir/slideshow_background.ppm" "$tmpdir/slide_$i.ppm"
			if [ "${subtitle[$i]}" == 'black' ] ; then
				myecho "[dvd-slideshow] WARNING: Subtitle=${subtitle[$i]}. Are you sure?"
			elif [ -n "${subtitle[$i]}" ] ; then
				myecho "[dvd-slideshow] Subtitle=${subtitle[$i]}"
			fi
			encode
		fi
		myecho "[dvd-slideshow]############################################################"
#identify "$tmpdir/slide_$i.ppm"
	elif [ "`echo $file | tr -d [:blank:]`" == 'chapter' ] ; then  
		## create a chapter marker at this time, but don't do anything else...
		write_chap=1
		subtitle[$i]=''  # set subtitle to nothing so we don't get a subtitle
		myecho "[dvd-slideshow] Setting chapter marker at $slide_end_hms"
		myecho "[dvd-slideshow]############################################################"
	elif [ "${audio_file[$i]}" -eq 1 ] ; then  ###############################################
		myecho "[dvd-slideshow] Audiofile $file"
		if [ "${audio_track[$i]}" -eq 1 ] ; then
			audio_1[$i_audio]="${file}"
			audio1_effect1[$i_audio]="${effect1[$i]}"
			audio1_effect1_params[$i_audio]="${effect1_params[$i]}"
			audio1_effect2[$i_audio]="${effect2[$i]}"
			audio1_effect2_params[$i_audio]="${effect2_params[$i]}"
			audio_index="$i_audio"
			audio_index_padded=`addzeros "$i_audio"`
			i_audio=$(( $i_audio + 1 ))
		elif [ "${audio_track[$i]}" -eq 2 ] ; then
			audio_2[$j_audio]="${file}"
			audio2_effect1[$j_audio]="${effect1[$i]}"
			audio2_effect1_params[$j_audio]="${effect1_params[$i]}"
			audio2_effect2[$j_audio]="${effect2[$i]}"
			audio2_effect2_params[$j_audio]="${effect2_params[$i]}"
			audio_index="$j_audio"
			audio_index_padded=`addzeros "$j_audio"`
			j_audio=$(( $j_audio + 1 ))
		else
			myecho "[dvd-slideshow] ERROR: Bad audio track number."
			myecho "[dvd-slideshow]        only use audio track 1 or 2"
			cleanup; exit 1
		fi
		track="${audio_track[$i]}"
		suffix=`echo "$file" | awk -F. '{print tolower($NF)}'`
		if [ "$suffix" == "mp3" ] ; then
			myecho "[dvd-slideshow] decoding mp3 audio file... be patient..."
			lame --decode "${file}" "$tmpdir/audio$track"_"$audio_index_padded.wav" 2> /dev/null
		elif [ "$suffix" == "ogg" ] ; then
			myecho "[dvd-slideshow] decoding ogg audio... be patient."
			oggdec --quiet -o "$tmpdir/audio$track"_"$audio_index_padded.wav" "${file}"
		elif [ "$suffix" == "wav" ] ; then
			myecho "[dvd-slideshow] processing wav audio... we will splice it later."
			cp "${file}" "$tmpdir/audio$track"_"$audio_index_padded.wav"
		elif [ "$file" == 'silence' ]; then
			myecho "[dvd-slideshow] creating silent audio track... we will splice it later."
			sox -t raw -s -w -c 2 -r 48000 /dev/zero -t wav -c 2 -r 48000 \
				"$tmpdir/audio$track"_"$audio_index_padded.wav" trim 0 1
		else
			myecho "[dvd-slideshow] ERROR:  Unknown audio file format.  Must be .mp3, .ogg, .wav, or silence"
		fi
		## now set the starting and ending point of this audio track:
#		myecho "audio_track=${audio_track[$i]} "
		if [ "${audio_track[$i]}" -eq 1 ] ; then
			audio1_start[$audio_index]="$slide_start_time"   # in ms
			## set ending point of the audio track:
			if [ "$audio_index" -gt 0 ] ; then # not first audio track
				audio1_end[$(($audio_index-1))]="$slide_end_time"   # in ms from last slide
#				myecho "[dvd-slideshow] Set end time for audio file $audio_index to `hms $slide_end_time`"
			else # set audio end to zero for now...
				audio1_end[$audio_index]=0   # in ms from last slide
			fi
		elif [ "${audio_track[$i]}" -eq 2 ] ; then
			audio2_start[$audio_index]="$slide_start_time"   # in ms
			## set ending point of the audio track:
			if [ "$audio_index" -gt 0 ] ; then
				audio2_end[$(($audio_index-1))]="$slide_end_time"   # in ms from last slide
#				myecho "[dvd-slideshow] Set end time for audio file $audio_index to `hms $slide_end_time`"
			else # set audio end to zero for now...
				audio2_end[$audio_index]=0   # in ms from last slide
			fi
		fi
#		myecho "[dvd-slideshow] track=${audio_track[$i]} audio_start=$slide_start_time audio_end=$slide_end_time"
#		myecho "[dvd-slideshow] track=${audio_track[$i]} audio_start=${audio1_start[$audio_index]} audio_end=${audio1_end[$audio_index]}"
		sox "$tmpdir/audio$track"_"$audio_index_padded.wav" -e stat 2> "$tmpdir"/trash.txt 
		## need to fix this so it's accurate to 0.01 sec, not just 1 sec
		## this will get floor(time) now.
		song_length=`cat "$tmpdir"/trash.txt | grep 'Length (seconds):' | awk -F: '{print $2}' | awk -F. '{print $1}'`
		song_length_hms=`hms "$(( 1000 * $song_length))"`
		song_length_ms="$(( 1000 * $song_length))"
		subtitle[$i]=''  # set subtitle to nothing so we don't get a subtitle
		rm "$tmpdir"/trash.txt
		myecho "[dvd-slideshow]############################################################"
	else  
		myecho "[dvd-slideshow] Unrecognized or malformed line in your input file:"
		myecho "[dvd-slideshow] $file. effect=${effect1[$i]} effect_params=${effect1_params[$i]}"
		myecho "Fix it and try again."
		cleanup; exit 1
	fi
	
	## calculate the time point that we're at:
	total_slideshow_frames=$(( $total_slideshow_frames + $frames ))
	slide_end_frame="$total_slideshow_frames"
	slide_end_time=$(( $slide_end_frame * 1000 * 1000 / $frames_per_sec ))  ## in thousandths of a second
	slide_end_hms=`hms "$slide_end_time"`
	if [ "${audio_file[$i]}" -eq 0 ] && [ $debug -ge 2 ]; then 
		myecho "[dvd-slideshow] end_frame_number=$slide_end_frame end_time=$slide_end_hms"
	fi

	thumb_width=$(( ( $dvd_width - 100 ) / 6 ))
	thumb_height=$(( ( $dvd_height - 100 ) / 4 ))
	## setup the chapter markers at the start of each picture:
	if [ "$write_chap" -eq 1 ] ; then   # and chapter-select =1 
#		chapter_marker="$(( ( ($slide_start_time / 100) + 1 ) * 100 ))" ## round up chapter marker
		chapter_marker="$slide_start_time"  # 
		chaps[$this_chap]=`hms "$chapter_marker"`
		## now make a tiny thumbnail for the menu?:
		thumbs[$this_chap]="$tmpdir/slide_"$i"_thumb.ppm"
#		convert "$tmpdir/slide_$i.ppm" -depth 8 -resize "$thumb_width"x"$thumb_height" "$tmpdir"/slide_$i"_thumb.ppm"
		this_chap=$(($this_chap + 1))
		write_chap=0
	fi

	## now, create the xml file to pass to spumux
	if [ "$spumux_header" -eq 0 ]; then  # only do once on first pass:
		spumux_header=1
		echo '<subpictures>' > "$tmpdir/$slideshow_name".spumux
		echo '	<stream>' >> "$tmpdir/$slideshow_name".spumux
		continuous_subtitle_flag=0
	fi	

	## Subtitles ########################################################
	## add the subtitle track if it exists:
	if [ -n "${subtitle[$i]}" ] ; then
		has_subtitles=1
#	echo "$i subtitle_rendered=${subtitle[$i]}"
		## fix any special characters:
		subtitle[$i]=`echo "${subtitle[$i]}" | sed -e 's/"/\\\\"/g' | sed -e 's/\!/\\\!/g' `
		## check to see if we find any user-specified breaks \n
		it=`echo "${subtitle[$i]}" | awk -F'\\' '{print $2}' | cut -c 1`
		if [ "$it" == 'n' ] ; then
			logecho "[dvd-slideshow] Found \\n in subtitle"
			# user entered a \n to force line wraps
			# break lines at line wraps
			subtitle1=`echo "${subtitle[$i]}" | awk -F'\\' '{print $1}'`
			subtitle2=`echo "${subtitle[$i]}" | awk -F'\\' '{print $2}' | cut -c 2-`
		else	# no forced line wraps.  Check for long lines:	
			## make the subtitle break up into up to 4 different lines?
			font_width=15  # actually it's 14.4, but this should give us some margin
	#		characters=`echo "${subtitle[$i]}" | wc -c`
			characters="${#subtitle[$i]}"
			line_width=$(( $font_width * $characters ))
#			myecho "[dvd-slideshow] $i characters=$characters linewidth=$line_width"
			if [ "$line_width" -gt "$dvd_width" ] ; then # $dvd_width=720
				## need to split the line:
				characters2=$(( $characters / 2 + 1))
				# try cutting in the middle:
				subtitle1="${subtitle[$i]:0:$characters2}"
				subtitle2="${subtitle[$i]:$characters2:$characters2}" 
				# now re-join a potential broken word:
				if [ "${subtitle[$i]:$characters2:1}" != ' ' ] ; then	
					# break occurred in the middle of a word. re-join the word:
					wordend=`echo "$subtitle2" | awk '{print $1}'`
					wordend_length=${#wordend}
					subtitle1="$subtitle1$wordend"
					subtitle2="${subtitle2:$wordend_length}"
				fi
				logecho "[dvd-slideshow] Splitting long subtitle... New values:"
				logecho "[dvd-slideshow]  Line1=$subtitle1"
				logecho "[dvd-slideshow]  Line2=$subtitle2"
			else
				subtitle1=""
				subtitle2="${subtitle[$i]}"
			fi
		fi	
		myecho "[dvd-slideshow] $i subtitle1=$subtitle1 subtitle2=$subtitle2"
		
		## render subtitles, if necessary:
		if [ "$subtitle_type" == "srt" ] || [ "$subtitle_type" == "SRT" ] ; then
			## let spumux render subtitles internally
			## setup spumux fonts, etc?: (later)
			subtitle_number=$(( $subtitle_number + 1 ))		
		else
			## let dvd-slideshow render its own subtitles:
			subtitle1=`echo "$subtitle1" | sed -e 's/\\\!/\!/g' `
			subtitle2=`echo "$subtitle2" | sed -e 's/\\\!/\!/g' `
#			logecho "[dvd-slideshow]  Line1=$subtitle1"
#			logecho "[dvd-slideshow]  Line2=$subtitle2"
			transparent_color="ff0000"
			if [ "$low_quality" -eq 1 ] ; then
				f_subtitle_font_size=$(( $subtitle_font_size / 2 ))
			else
				f_subtitle_font_size=$(( $subtitle_font_size ))
			fi
	        	convert -size $resolution xc:red $font -pointsize "$f_subtitle_font_size" \
			-gravity South -fill white -stroke black -strokewidth 3 -colors 3 +antialias \
			-draw "text 0,105 \"$subtitle1\"" -draw "text 0,75 \"$subtitle2\"" \
			-stroke none -draw "text 0,105 \"$subtitle1\"" -draw "text 0,75 \"$subtitle2\"" \
			-quality 100 "$tmpdir/subtitle_$i.png"
		fi
	fi

	## let's assume the subtitle stays on the whole duration of the slide?
	subtitle_start=`hms "$slide_start_time"`
	subtitle_end=`hms "$slide_end_time"`
	subtitle_start_srt="`echo ${slide_start_hms} | tr '.' ','`"
	subtitle_end_srt="`echo ${slide_end_hms} | tr '.' ','`"

        ### Fix by AW.  Check to see if last subtitle was the same as this one!
	## if so, then display it continuously:
	if [ "$i" -gt 0 ] ; then
	        if [ "${subtitle[$i]}" != "${subtitle[$(($i-1))]}" ] ; then
			## subtitles different:
#			myecho "subtitles different i=${subtitle[$i]} i-1=${subtitle[$(($i-1))]}"
			# update times:
			## so, we have three cases here:  
		        if [ -n "${subtitle[$i]}" -a -z "${subtitle[$(($i-1))]}" ] ; then
				# Current subtitle is nonzero, and previous subtitle is empty:
				# Just update values, don't write out yet!
				write_last_subtitle=1
			else	## need to write out subtitle in all other cases:
#				myecho "Writing subtitle $continuous_subtitle_start --> $continuous_subtitle_end $previous_subtitle1 $previous_subtitle2 subtitle_$i.png"
				write_last_subtitle=0
				if [ "$subtitle_type" == "srt" ] || [ "$subtitle_type" == "SRT" ] ; then
#					myecho "writing srt subtitle"
					echo "$(( $subtitle_number - 1 ))" >> "$outdir/$subtitle_file"
					echo "$continuous_subtitle_start_srt"' --> '"$continuous_subtitle_end_srt" >> "$outdir/$subtitle_file"
					if [ -n "$previous_subtitle1" ] ; then
						# remove any backslashes
						previous_subtitle1=`echo "$previous_subtitle1" | sed -e 's/\\\!/\!/g' `
						echo "$previous_subtitle1" >> "$outdir/$subtitle_file"
					fi
					if [ -n "$previous_subtitle2" ] ; then
						previous_subtitle2=`echo "$previous_subtitle2" | sed -e 's/\\\!/\!/g' `
						echo "$previous_subtitle2" >> "$outdir/$subtitle_file"
					fi
					echo "" >> "$outdir/$subtitle_file"
#					echo "$subtitle_number $subtitle_start_srt --> $subtitle_end_srt $subtitle1 $subtitle2"
				else  ## let dvd-slideshow render its own subtitles:
					echo '		<spu start="'$continuous_subtitle_start'" end="'$continuous_subtitle_end'" transparent="'$transparent_color'" image="'$tmpdir/subtitle_$(($i-1)).png'">' >> "$tmpdir/$slideshow_name".spumux
					echo '		</spu>' >> "$tmpdir/$slideshow_name".spumux
					echo '		' >> "$tmpdir/$slideshow_name".spumux
				fi
			fi
			# set new subtitle starting point:
			continuous_subtitle_start="$subtitle_start"
			continuous_subtitle_start_srt="$subtitle_start_srt"
			previous_subtitle1="$subtitle1"
			previous_subtitle2="$subtitle2"
		else
			# subtitles are the same.  Don't write it out yet!
			# save the continuous_subtitle_end variable until done...
			if [ -n "${subtitle[$i]}" ] ; then
				write_last_subtitle=1
				# subtitles are the same AND the current one is not empty
			fi
		fi
		continuous_subtitle_end="$subtitle_end"  # update end point every time
		continuous_subtitle_end_srt="$subtitle_end_srt"  
	fi
	let i=$i+1
done

#######################################################################
####### End of loop over each line of input .txt file

if [ -f "$tmpdir/$slideshow_name".spumux ]; then
	if [ "$write_last_subtitle" -eq 1 ] ; then
		# write out last subtitle:
#		myecho "Writing subtitle $continuous_subtitle_start --> $continuous_subtitle_end $previous_subtitle1 $previous_subtitle2"
		if [ "$subtitle_type" == "srt" ] || [ "$subtitle_type" == "SRT" ] ; then
			echo "$(( $subtitle_number - 1 ))" >> "$outdir/$subtitle_file"
			echo "$continuous_subtitle_start_srt --> $continuous_subtitle_end_srt" >> "$outdir/$subtitle_file"
			if [ -n "$previous_subtitle1" ] ; then
				previous_subtitle1=`echo "$previous_subtitle1" | sed -e 's/\\//g'`
				echo "$previous_subtitle1" >> "$outdir/$subtitle_file"
			fi
			if [ -n "$previous_subtitle2" ] ; then
				previous_subtitle2=`echo "$previous_subtitle2" | sed -e 's/\\//g'`
				echo "$previous_subtitle2" >> "$outdir/$subtitle_file"
			fi
			echo "" >> "$outdir/$subtitle_file"
		else  ## let dvd-slideshow render its own subtitles:
			echo '		<spu start="'$continuous_subtitle_start'" end="'$continuous_subtitle_end'" transparent="'$transparent_color'" image="'$tmpdir/subtitle_$(($i-1)).png'">' >> "$tmpdir/$slideshow_name".spumux
			echo '		</spu>' >> "$tmpdir/$slideshow_name".spumux
			echo '		' >> "$tmpdir/$slideshow_name".spumux
		fi
	fi
	if [ "$subtitle_type" == "srt" ] || [ "$subtitle_type" == "SRT" ] ; then
		## write out bottom of .srt file:
		echo '		<textsub filename="'$outdir/$subtitle_file'" font="arial.ttf" horizontal-alignment="center" vertical-alignment="bottom" bottom-margin="30" movie-width="'$dvd_width'" movie-height="'$dvd_height'"' >> "$tmpdir/$slideshow_name".spumux
		echo '		/>' >> "$tmpdir/$slideshow_name".spumux
	fi
	## write the bottom of the subpictures file:
	echo '	</stream>' >> "$tmpdir/${slideshow_name}".spumux
	echo '</subpictures>' >> "$tmpdir/${slideshow_name}".spumux
fi

############################### Wait for mpeg2enc to finish

if [ "$yuvcat" -eq 0 ]; then
       ##  now we need to cat the mpeg files together:
       myecho "[dvd-slideshow] Joining each mpeg..."
       cat "$tmpdir"/slide_*.mpg > "$tmpdir/video.mpg"
else
       # just close the fifo and wait for the encoder to finish
       logecho "[dvd-slideshow] mpeg2enc process=$yuvpid"
       logecho "[dvd-slideshow] output from ps=`ps $yuvpid`"
	/usr/bin/lsof -a -u $USER -d 3 +c 0 -c dvd -c convert -c mpeg2 >> "$outdir/$logfile" 2>&1
	# close pipe to mpeg2enc
       exec 3>&-  
	myecho '[dvd-slideshow] waiting for mpeg2enc to finish...'
       wait $yuvpid
       yuvpid=0
	if [ "$mpegid" -ne 0 ] ; then
		## this should only happen when we encode video?
	       myecho "[dvd-slideshow] Joining each mpeg..."
	       cat "$tmpdir"/video_*.mpg > "$tmpdir/video.mpg"
	else
		mv "$tmpdir"/video_0.mpg "$tmpdir/video.mpg"
	fi
fi

## calculate total slideshow time:
#end_time=$(( $total_slideshow_frames * 1000 / $frames_per_sec ))  ## in seconds
end_time="$slide_end_time"
end_hms="$slide_end_hms"

############################################################################
# AUDIO section...
##########################################################################
myecho "[dvd-slideshow]#####################################"

## now do the audio for this slideshow ##########################
let i=0
total_audio_length=0
commandline_audio=0
if [ -n "${passed_audio[0]}" ] ; then  ## command-line passed audio
	myecho "[dvd-slideshow] Processing command-line audio..."
	for file in "${passed_audio[@]}"; do
		i_padded=`addzeros $i`
		myecho "[dvd-slideshow] Working on track 1 audio file $i"
		myecho "[dvd-slideshow] $file"
		fade_in_time="3000" # default 3 second
		fade_out_time="3000"
		fade_in_hms=`hms "$fade_in_time"`
		fade_out_hms=`hms "$fade_out_time"`
		myecho "[dvd-slideshow] fade_in_time=$fade_in_hms fade_out_time=$fade_out_hms"
		track=1
		song_length=`wavlength "$tmpdir/audio1_$i_padded.wav"`
		if [ "$song_length" -lt "$(( $fade_in_time + $fade_out_time ))" ] ; then
			fade_in_time=$(( ( $song_length - 1 ) / 2 ))
			fade_out_time="$fade_in_time"
		fi
		song_length_hms=`hms "$song_length"`
		total_audio_length="$(( $total_audio_length + $song_length ))"
		myecho "[dvd-slideshow] total_audio_length=`hms $total_audio_length`"
		sox -v 0.95 "$tmpdir/audio$track"_"$i_padded.wav" -w -s -c 2 -r 48000 "$tmpdir/audio1_$i_padded.raw" fade t "$fade_in_hms" "$song_length_hms" "$fade_out_hms"
		let i=$i+1
		myecho "[dvd-slideshow] ###############"
	done
	i_padded=`addzeros $i`
	## check to make sure the audio spans the video time:
	if [ "$total_audio_length" -lt "$end_time" ] ; then
		# video is longer than audio.  need to add silence to end.
		thetime_hms=`hms $(( $end_time - $total_audio_length + 1000 ))` #plus 10 so sox actually crops.
		myecho "[dvd-slideshow] Buffering end of audio file with silence for $thetime_hms"
		sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir/audio1_$i_padded.raw" trim 0 "$thetime_hms"
	fi
	
	## cat all the audio files together: 
	cat "$tmpdir"/audio1_????.raw | sox -t raw -w -s -c 2 -r 48000 - "$tmpdir/audio1.wav"
	## fade out at end of video:
	sox "$tmpdir/audio1.wav" "$tmpdir/audio_out.wav" fade t 0 "$end_hms" "$fade_out_hms"
	mv "$tmpdir/audio_out.wav" "$tmpdir/audio1.wav"
	## mpeg2 audio:
	## AC3 audio may be more compatible:
	if [ "$ac3" -eq 1 ] ; then
		checkforprog ffmpeg
		myecho "[dvd-slideshow] Creating ac3 audio for $file..."
		ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab 192K -acodec ac3 -ar 48000 -ac 6 "$tmpdir/audio1.ac3" >> "$outdir/$logfile" 2>&1
		if [ $? -ne 0 ] ; then
			## ffmpeg errored
			myecho "[dvd-slideshow] ERROR during ffmpeg execution!"
			myecho "[dvd-slideshow] see $outdir/$logfile for details"
			cleanup; exit 1
		fi
	else
		## toolame is way faster! (3x in my test)
		it=`which toolame`
		if [ -n "$it" ] ; then
			toolame_version=`toolame -h | head -n 4 | grep version | awk '{ print $3 }'`
			myecho "[dvd-slideshow] using toolame $toolame_version..."
			if [ "$toolame_version" == '0.2m' ] ; then
				toolame -s 48000 -b 128 "$tmpdir/audio1.wav" "$tmpdir/audio1.mp2" 
			else
				toolame -s 48 -b 128 "$tmpdir/audio1.wav" "$tmpdir/audio1.mp2" 
			fi
		else
			myecho "[dvd-slideshow] using mp2enc"
			mp2enc -v $verbosity -b 128 -r 48000 -s -o "$tmpdir/audio1.mp2" < "$tmpdir/audio1.wav"
		fi
	fi
	commandline_audio=1
fi  # end processing command-line passed audio

if [ -z "${audio_1[0]}" ] && [ "$commandline_audio" -eq 0 ] ; then
	## no audio file passed on command line or txtfile.  use silence:
	audio_1[0]='silence'  # no duration needed
	myecho "[dvd-slideshow] No audio files passed.  Using $end_hms silence."
	audio1_start=0 
	audio1_end="$end_time"
fi

## let's split this audio processing into two loops:  one just prepares the
## initial fadein/fadeout, and the next loop figures out the timing and cropping 

let i=0
skip_next_audio_file=0
if [ -n "${audio_1[0]}" ] ; then   ## audio track 1 files specified in .txt file
#	myecho "[dvd-slideshow] Processing track 1 audio from .txt file..."
	for file in "${audio_1[@]}"; do
		if [ "$skip_next_audio_file" -eq 1 ] ; then
#			myecho -n "i=$i myindex=$myindex  "
			if [ $i -eq $myindex ] ; then
				skip_next_audio_file=0
			fi	
			myecho "[dvd-slideshow] Skipping un-needed audio file $i"
			myecho "[dvd-slideshow] ###############"
			let i=$i+1
			continue
		fi
		i_padded=`addzeros $i`
		myecho "[dvd-slideshow] Working on track 1 audio file $i"
		myecho "[dvd-slideshow] $file"
		
		if [ "${audio1_end[$i]:-0}" -eq 0 ] || [ -z "$audio1_end[$i]}" ] ; then
#		if [ -z "$audio1_end[$i]}" ] || [ $audio1_end[$i] ] ; then
			## must be last audio track.  assume run til end
			audio1_end[$i]="$end_time"	
		fi

#		if [ ${audio1_start[$i]} -ge ${audio1_end[$i]} ] ; then
#			myecho "[dvd-slideshow] ERROR: Audio file endpoint is same or before start."
#			myecho "[dvd-slideshow] 	     This is sometimes caused by having two audio files"
#			myecho "[dvd-slideshow] 	     sequentially one after another with no slide between."
#			myecho "[dvd-slideshow] 	     Fix it and try again."
#			cleanup; exit 1
#		fi
	
		if [ "$file" == 'silence' ]; then   # create silence for the correct time:
			song_end_ms=$(( ${audio1_end[$i]} - ${audio1_start[$i]} ))
			[ "$song_end_ms" -lt 0 ] && song_end_ms=0
			song_end_hms=`hms $song_end_ms`
			song_start_hms="0"  # cannot modify starting point yet...
			myecho "[dvd-slideshow] Creating silence audio file for $song_end_hms"
			sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir"/audio1_$i_padded.raw trim "0" "$song_end_hms"
		else
			## file should only be wav format at this point since it was decoded before
			## all audio files are of the format "$tmpdir"/audio_1.wav
			# I found some "popping" in the audio for some tracks.
			# it turns out that this is caused by audio going
			# too low or too high and getting clipped.
			# reducing the volume a little should help.
			volume=0.95
			sox "$tmpdir/audio1_$i_padded.wav" -e stat 2> "$tmpdir"/trash.txt 
			## need to fix this so it's accurate to 0.01 sec, not just 1 sec
			## this will get floor(time) now.
#			myecho "$tmpdir/audio1_$i_padded.wav"
#			cat "$tmpdir"/trash.txt
			song_length=`cat "$tmpdir"/trash.txt | grep 'Length (seconds):' | awk -F: '{print $2}' | awk -F. '{print $1}'`
			rm "$tmpdir"/trash.txt
			song_length_ms="$(( 1000 * $song_length))"
			song_length_hms=`hms $song_length_ms`
			myecho "[dvd-slideshow] Original audio track length=$song_length_hms"

#			myecho "[dvd-slideshow] This audio plays in slideshow from `hms ${audio1_start[$i]}` to `hms ${audio1_end[$i]}`"

			if [ -z "${audio1_effect1_params[$i]}" ] ; then
				fade_in_time="0"
			else
				fade_in_time="$(( ${audio1_effect1_params[$i]} * 1000 ))" 
			fi
			if [ -z "${audio1_effect2_params[$i]}" ] ; then
				fade_out_time="0"
			else
				fade_out_time="$(( ${audio1_effect2_params[$i]} * 1000 ))" 
			fi
			fade_in_hms=`hms "$fade_in_time"`
			fade_out_hms=`hms "$fade_out_time"`
			myecho "[dvd-slideshow] Fade in time=$fade_in_hms Fade out time=$fade_out_hms"

			if [ "$song_length_ms" -lt "$(( $fade_in_time + $fade_out_time ))" ] ; then
				myecho "[dvd-slideshow] WARNING: Song length is shorter than the combined fadein and fadeout times"
				fade_in_time=$(( ( $song_length - 1 ) / 2 ))
				fade_out_time="$fade_in_time"
				myecho "[dvd-slideshow]          Setting fadein and fadeout time to `hms $fade_in_time`"
			fi

			song_end_ms=$(( ${audio1_end[$i]} - ${audio1_start[$i]} ))
			[ "$song_end_ms" -lt 0 ] && song_end_ms=0
			song_end_hms=`hms $song_end_ms`
			song_start_hms="0"  # cannot modify starting point yet...
#			myecho "[dvd-slideshow] audio1_start=${audio1_start[$i]} audio1_start+1=${audio1_start[$(($i+1))]}"
#			myecho "[dvd-slideshow] song_start_hms=$song_start_hms song_end_hms=$song_end_hms"
#			myecho "[dvd-slideshow] audio_start=`hms ${audio1_start[$i]}`. audio_end=`hms ${audio1_end[$i]}`."
			# check to see if we need to add multiple files together first:
			if [ -n "${audio1_start[$(($i+1))]}" ] && [ "${audio1_start[$i]}" -ge "${audio1_start[$(($i+1))]}" ] ; then
#				myecho " [dvd-slideshow] Multiple files found right after one another!"
				## User might add 10 audio files when only 2 are needed
				## to span the video...  check for this:
				## 1.  find next real audio start marker
				## 2. compare length of songs up to that point.
				myindex=$i
				while [ -n "${audio1_start[$(($myindex+1))]}" ] && [ "${audio1_start[$myindex]}" -ge "${audio1_start[$(($myindex+1))]}" ] ; do
					# grab last starting time:
					next_real_audio_start="${audio1_start[$(($myindex+2))]}"
					if [ -z "$next_real_audio_start" ] ; then
						## must be last audio track.  assume run til end
						next_real_audio_start="$end_time"	
					fi
#					myecho " [dvd-slideshow] next audio start=$next_real_audio_start myindex=$myindex"
					myindex=$(( $myindex + 1 ))
				done
				# set first file audio endpoint to the least
				# of the full length of song or the start of the next file:
				# (whichever comes first)
				if [ $next_real_audio_start -lt $(( ${audio1_start[$i]} + $song_length_ms )) ] ; then
					# this song is too long and needs to be cropped
					# set endpoint to starting point of next song
					audio1_end[$i]=$next_real_audio_start 
#					# ignore next audio files until $next_real_audio_start
					skip_next_audio_file=1
#					myecho "[dvd-slideshow] Next audio file not needed"
#					myecho "[dvd-slideshow] Setting audio1_end[$i]=${audio1_end[$i]}"
				else
					# song not long enough... need to add next audio file
					# or buffer with silence at end.
					audio1_end[$i]=$(( ${audio1_start[$i]} + $song_length_ms )) 
					# set second file audio startpoint to end of fist song:
					audio1_start[$(($i+1))]="${audio1_end[$i]}" 
#					myecho "[dvd-slideshow] Concatenating next audio file also"
#					myecho " [dvd-slideshow] Setting audio1_start[$(($i+1))]=${audio1_end[$i]} audio1_end[$i]=${audio1_end[$i]}"
				fi
			fi

			song_end_ms=$(( ${audio1_end[$i]} - ${audio1_start[$i]} ))
			[ "$song_end_ms" -lt 0 ] && song_end_ms=0
			song_end_hms=`hms $song_end_ms`
			song_start_hms="0"  # cannot modify starting point yet...
#			myecho "[dvd-slideshow] song_start_hms=$song_start_hms song_end_hms=$song_end_hms"

			if [ "$song_length_ms" -lt "$song_end_ms" ] ; then
#				myecho "Song length < song_end   `hms $song_length_ms` < `hms $song_end_ms`"
				# video is longer than audio.  need to add silence to end.
				# fade only to the end of song length now, because we may have to add silence:
				sox -v 0.95 "$tmpdir/audio1_$i_padded.wav" -w -s -c 2 -r 48000 "$tmpdir/audio1_$i_padded.raw" fade t "$fade_in_hms" "$song_length_hms" "$fade_out_hms"
				thetime_hms=`hms $(( $song_end_ms - $song_length_ms + 1000 ))` #plus 1s so sox actually crops.
				thetime2_hms=`hms $(( $song_end_ms - $song_length_ms ))` 
				myecho "[dvd-slideshow] Adding $thetime2_hms of silence to end of original audio file"
				sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir/silence.raw" trim 0 "$thetime_hms"
				cat "$tmpdir/audio1_$i_padded.raw" "$tmpdir/silence.raw" > "$tmpdir/audio.raw" 
				mv "$tmpdir/audio.raw" "$tmpdir/audio1_$i_padded.raw"
				# hopefully there won't be many times where the audio needs to be buffered 
				# at the end, so we'll add one extra step to make the coding easier:
				sox -t raw -s -w -c 2 -r 48000 "$tmpdir/audio1_$i_padded.raw" "$tmpdir/audio1_$i_padded.wav"
				rm "$tmpdir"/silence.raw
			fi
			## fade in by default... may change later
			sox -v 0.95 "$tmpdir/audio1_$i_padded.wav" -w -s -c 2 -r 48000 "$tmpdir/audio1_$i_padded.raw" fade t "$fade_in_hms" "$song_end_hms" "$fade_out_hms"
		fi
		if [ $i -eq 0 ] && [ "${audio1_start[$i]}" -ne 0 ] ; then
			## buffer beginning with silence:
			thetime_hms=`hms "${audio1_start[$i]}"`
			myecho "[dvd-slideshow] Adding $thetime_hms to beginning of audio file"
			sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir/silence.raw" trim 0 "$thetime_hms"
			cat "$tmpdir"/silence.raw "$tmpdir/audio1_$i_padded.raw" > "$tmpdir/audio.raw" 
			mv "$tmpdir/audio.raw" "$tmpdir/audio1_$i_padded.raw"
			rm "$tmpdir"/silence.raw
		fi
		myecho "[dvd-slideshow] This audio plays in slideshow from `hms ${audio1_start[$i]}` to `hms ${audio1_end[$i]}`"
		if [ "$debug" -ge 1 ] ; then
			length=`rawlength "$tmpdir/audio1_$i_padded.raw"`
			myecho "[dvd-slideshow] Actual length of .raw file=`hms $length`"
		fi
		let i=$i+1
		myecho "[dvd-slideshow] ###############"
	done
		
	myecho "[dvd-slideshow] Concatenating all audio files..."
	## cat all the audio files together: 
#	ls "$tmpdir"/audio1_????.raw | xargs -0 cat | sox -t raw -w -s -c 2 -r 48000 - "$tmpdir/audio1.wav"
#	find "$tmpdir" -name audio1_\?\?\?\?.raw -print0 | xargs -0 sox -t raw -w -s -c 2 -r 48000 - "$tmpdir/audio1.wav"
	cat "$tmpdir"/audio1_????.raw | sox -t raw -w -s -c 2 -r 48000 - "$tmpdir/audio1.wav"
	if [ "$debug" -ge 1 ] ; then
		length=`wavlength "$tmpdir/audio1.wav"`
		myecho "[dvd-slideshow] Actual length of .raw file=`hms $length`"
	fi
	## AC3 audio may be more compatible:
	if [ "$ac3" -eq 1 ] ; then
		myecho "[dvd-slideshow] Creating ac3 audio..."
		checkforprog ffmpeg
		check_rm "$tmpdir/audio1.ac3"
		ffmpeg -i "$tmpdir/audio1.wav" -vn -ab 192K -acodec ac3 -ar 48000 -ac 6 "$tmpdir/audio1.ac3" >> "$outdir/$logfile" 2>&1
		if [ $? -ne 0 ] ; then
			## ffmpeg errored
			myecho "[dvd-slideshow] ERROR during ffmpeg execution!"
			myecho "[dvd-slideshow] see $outdir/$logfile for details"
			cleanup; exit 1
		fi
	else
		## toolame is way faster! (3x in my test)
		it=`which toolame`
		if [ -n "$it" ] ; then
			toolame_version=`toolame -h | head -n 4 | grep version | awk '{ print $3 }'`
			myecho "[dvd-slideshow] Creating mp2 audio using toolame $toolame_version..."
			if [ "$toolame_version" == '0.2m' ] ; then
				toolame -s 48000 -b 128 "$tmpdir/audio1.wav" "$tmpdir/audio1.mp2" 
			else
				toolame -s 48 -b 128 "$tmpdir/audio1.wav" "$tmpdir/audio1.mp2" 
			fi
		else
			myecho "[dvd-slideshow] Creating mp2 audio using mp2enc"
			mp2enc -v $verbosity -b 128 -r 48000 -s -o "$tmpdir/audio1.mp2" < "$tmpdir/audio1.wav"
		fi
	fi
fi
		

#################################################################
## now do this all again for audio track number 2:
let i=0
skip_next_audio_file=0
if [ -n "${audio_2[0]}" ] ; then   ## audio track 2 files specified in .txt file
	myecho "[dvd-slideshow] #######################################"
	myecho "[dvd-slideshow] Processing track 2 audio from .txt file..."
	myecho "[dvd-slideshow] #######################################"
	for file in "${audio_2[@]}"; do
		if [ "$skip_next_audio_file" -eq 1 ] ; then
#			myecho -n "i=$i myindex=$myindex  "
			if [ $i -eq $myindex ] ; then
				skip_next_audio_file=0
			fi	
			myecho "[dvd-slideshow] Skipping un-needed audio file $i"
			myecho "[dvd-slideshow] ###############"
			let i=$i+1
			continue
		fi
		i_padded=`addzeros $i`
		myecho "[dvd-slideshow] Working on track 2 audio file $i"
		myecho "[dvd-slideshow] $file"
		
		if [ "${audio2_end[$i]:-0}" -eq 0 ] || [ -z "$audio2_end[$i]}" ] ; then
#		if [ -z "$audio2_end[$i]}" ] || [ $audio2_end[$i] ] ; then
			## must be last audio track.  assume run til end
			audio2_end[$i]="$end_time"	
		fi

#		if [ ${audio2_start[$i]} -ge ${audio2_end[$i]} ] ; then
#			myecho "[dvd-slideshow] ERROR: Audio file endpoint is same or before start."
#			myecho "[dvd-slideshow] 	     This is sometimes caused by having two audio files"
#			myecho "[dvd-slideshow] 	     sequentially one after another with no slide between."
#			myecho "[dvd-slideshow] 	     Fix it and try again."
#			cleanup; exit 1
#		fi
	
		if [ "$file" == 'silence' ]; then   # create silence for the correct time:
			song_end_ms=$(( ${audio2_end[$i]} - ${audio2_start[$i]} ))
			[ "$song_end_ms" -lt 0 ] && song_end_ms=0
			song_end_hms=`hms $song_end_ms`
			song_start_hms="0"  # cannot modify starting point yet...
			myecho "[dvd-slideshow] Creating silence audio file for $song_end_hms"
			sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir"/audio2_$i_padded.raw trim "0" "$song_end_hms"
		else
			## file should only be wav format at this point since it was decoded before
			## all audio files are of the format "$tmpdir"/audio_2.wav
			# I found some "popping" in the audio for some tracks.
			# it turns out that this is caused by audio going
			# too low or too high and getting clipped.
			# reducing the volume a little should help.
			volume=0.95
			sox "$tmpdir/audio2_$i_padded.wav" -e stat 2> "$tmpdir"/trash.txt 
			## need to fix this so it's accurate to 0.01 sec, not just 1 sec
			## this will get floor(time) now.
#			myecho "$tmpdir/audio2_$i_padded.wav"
#			cat "$tmpdir"/trash.txt
			song_length=`cat "$tmpdir"/trash.txt | grep 'Length (seconds):' | awk -F: '{print $2}' | awk -F. '{print $1}'`
			rm "$tmpdir"/trash.txt
			song_length_ms="$(( 1000 * $song_length))"
			song_length_hms=`hms $song_length_ms`
			myecho "[dvd-slideshow] Original audio track length=$song_length_hms"

#			myecho "[dvd-slideshow] This audio plays in slideshow from `hms ${audio2_start[$i]}` to `hms ${audio2_end[$i]}`"

			if [ -z "${audio2_effect1_params[$i]}" ] ; then
				fade_in_time="0"
			else
				fade_in_time="$(( ${audio2_effect1_params[$i]} * 1000 ))" 
			fi
			if [ -z "${audio2_effect2_params[$i]}" ] ; then
				fade_out_time="0"
			else
				fade_out_time="$(( ${audio2_effect2_params[$i]} * 1000 ))" 
			fi
			fade_in_hms=`hms "$fade_in_time"`
			fade_out_hms=`hms "$fade_out_time"`
			myecho "[dvd-slideshow] Fade in time=$fade_in_hms Fade out time=$fade_out_hms"

			if [ "$song_length_ms" -lt "$(( $fade_in_time + $fade_out_time ))" ] ; then
				myecho "[dvd-slideshow] WARNING: Song length is shorter than the combined fadein and fadeout times"
				fade_in_time=$(( ( $song_length - 1 ) / 2 ))
				fade_out_time="$fade_in_time"
				myecho "[dvd-slideshow]          Setting fadein and fadeout time to `hms $fade_in_time`"
			fi

			song_end_ms=$(( ${audio2_end[$i]} - ${audio2_start[$i]} ))
			[ "$song_end_ms" -lt 0 ] && song_end_ms=0
			song_end_hms=`hms $song_end_ms`
			song_start_hms="0"  # cannot modify starting point yet...
#			myecho "[dvd-slideshow] audio2_start=${audio2_start[$i]} audio2_start+1=${audio2_start[$(($i+1))]}"
#			myecho "[dvd-slideshow] song_start_hms=$song_start_hms song_end_hms=$song_end_hms"
#			myecho "[dvd-slideshow] audio_start=`hms ${audio2_start[$i]}`. audio_end=`hms ${audio2_end[$i]}`."
			# check to see if we need to add multiple files together first:
			if [ -n "${audio2_start[$(($i+1))]}" ] && [ "${audio2_start[$i]}" -ge "${audio2_start[$(($i+1))]}" ] ; then
#				myecho " [dvd-slideshow] Multiple files found right after one another!"
				## User might add 10 audio files when only 2 are needed
				## to span the video...  check for this:
				## 1.  find next real audio start marker
				## 2. compare length of songs up to that point.
				myindex=$i
				while [ -n "${audio2_start[$(($myindex+1))]}" ] && [ "${audio2_start[$myindex]}" -ge "${audio2_start[$(($myindex+1))]}" ] ; do
					# grab last starting time:
					next_real_audio_start="${audio2_start[$(($myindex+2))]}"
					if [ -z "$next_real_audio_start" ] ; then
						## must be last audio track.  assume run til end
						next_real_audio_start="$end_time"	
					fi
#					myecho " [dvd-slideshow] next audio start=$next_real_audio_start myindex=$myindex"
					myindex=$(( $myindex + 1 ))
				done
				# set first file audio endpoint to the least
				# of the full length of song or the start of the next file:
				# (whichever comes first)
				if [ $next_real_audio_start -lt $(( ${audio2_start[$i]} + $song_length_ms )) ] ; then
					# this song is too long and needs to be cropped
					# set endpoint to starting point of next song
					audio2_end[$i]=$next_real_audio_start 
#					# ignore next audio files until $next_real_audio_start
					skip_next_audio_file=1
#					myecho "[dvd-slideshow] Next audio file not needed"
#					myecho "[dvd-slideshow] Setting audio2_end[$i]=${audio2_end[$i]}"
				else
					# song not long enough... need to add next audio file
					# or buffer with silence at end.
					audio2_end[$i]=$(( ${audio2_start[$i]} + $song_length_ms )) 
					# set second file audio startpoint to end of fist song:
					audio2_start[$(($i+1))]="${audio2_end[$i]}" 
#					myecho "[dvd-slideshow] Concatenating next audio file also"
#					myecho " [dvd-slideshow] Setting audio2_start[$(($i+1))]=${audio2_end[$i]} audio2_end[$i]=${audio2_end[$i]}"
				fi
			fi

			song_end_ms=$(( ${audio2_end[$i]} - ${audio2_start[$i]} ))
			[ "$song_end_ms" -lt 0 ] && song_end_ms=0
			song_end_hms=`hms $song_end_ms`
			song_start_hms="0"  # cannot modify starting point yet...
#			myecho "[dvd-slideshow] song_start_hms=$song_start_hms song_end_hms=$song_end_hms"

			if [ "$song_length_ms" -lt "$song_end_ms" ] ; then
#				myecho "Song length < song_end   `hms $song_length_ms` < `hms $song_end_ms`"
				# video is longer than audio.  need to add silence to end.
				# fade only to the end of song length now, because we may have to add silence:
				sox -v 0.95 "$tmpdir/audio2_$i_padded.wav" -w -s -c 2 -r 48000 "$tmpdir/audio2_$i_padded.raw" fade t "$fade_in_hms" "$song_length_hms" "$fade_out_hms"
				thetime_hms=`hms $(( $song_end_ms - $song_length_ms + 1000 ))` #plus 1s so sox actually crops.
				thetime2_hms=`hms $(( $song_end_ms - $song_length_ms ))` 
				myecho "[dvd-slideshow] Adding $thetime2_hms of silence to end of original audio file"
				sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir/silence.raw" trim 0 "$thetime_hms"
				cat "$tmpdir/audio2_$i_padded.raw" "$tmpdir/silence.raw" > "$tmpdir/audio.raw" 
				mv "$tmpdir/audio.raw" "$tmpdir/audio2_$i_padded.raw"
				# hopefully there won't be many times where the audio needs to be buffered 
				# at the end, so we'll add one extra step to make the coding easier:
				sox -t raw -s -w -c 2 -r 48000 "$tmpdir/audio2_$i_padded.raw" "$tmpdir/audio2_$i_padded.wav"
				rm "$tmpdir"/silence.raw
			fi
			## fade in by default... may change later
			sox -v 0.95 "$tmpdir/audio2_$i_padded.wav" -w -s -c 2 -r 48000 "$tmpdir/audio2_$i_padded.raw" fade t "$fade_in_hms" "$song_end_hms" "$fade_out_hms"
		fi
		if [ $i -eq 0 ] && [ "${audio2_start[$i]}" -ne 0 ] ; then
			## buffer beginning with silence:
			thetime_hms=`hms "${audio2_start[$i]}"`
			myecho "[dvd-slideshow] Adding $thetime_hms to beginning of audio file"
			sox -t raw -s -w -c 2 -r 48000 /dev/zero -w -s -c 2 -r 48000 "$tmpdir/silence.raw" trim 0 "$thetime_hms"
			cat "$tmpdir"/silence.raw "$tmpdir/audio2_$i_padded.raw" > "$tmpdir/audio.raw" 
			mv "$tmpdir/audio.raw" "$tmpdir/audio2_$i_padded.raw"
			rm "$tmpdir"/silence.raw
		fi
		myecho "[dvd-slideshow] This audio plays in slideshow from `hms ${audio2_start[$i]}` to `hms ${audio2_end[$i]}`"
		if [ "$debug" -ge 1 ] ; then
			length=`rawlength "$tmpdir/audio2_$i_padded.raw"`
			myecho "[dvd-slideshow] Actual length of .raw file=`hms $length`"
		fi
		let i=$i+1
		myecho "[dvd-slideshow] ###############"
	done
		
	myecho "[dvd-slideshow] Concatenating all audio files..."
	## cat all the audio files together: 
#	find "$tmpdir" -name audio2_????.raw -print0 | xargs -0 sox -t raw -w -s -c 2 -r 48000 - "$tmpdir/audio2.wav"
	cat "$tmpdir"/audio2_????.raw | sox -t raw -w -s -c 2 -r 48000 - "$tmpdir/audio2.wav"
	if [ "$debug" -ge 1 ] ; then
		length=`wavlength "$tmpdir/audio2.wav"`
		myecho "[dvd-slideshow] Actual length of .raw file=`hms $length`"
	fi
	## AC3 audio may be more compatible:
	if [ "$ac3" -eq 1 ] ; then
		myecho "[dvd-slideshow] Creating ac3 audio..."
		checkforprog ffmpeg
		check_rm "$tmpdir/audio2.ac3"
		ffmpeg -i "$tmpdir/audio2.wav" -vn -ab 192K -acodec ac3 -ar 48000 -ac 6 "$tmpdir/audio2.ac3" >> "$outdir/$logfile" 2>&1
		if [ $? -ne 0 ] ; then
			## ffmpeg errored
			myecho "[dvd-slideshow] ERROR during ffmpeg execution!"
			myecho "[dvd-slideshow] see $outdir/$logfile for details"
			cleanup; exit 1
		fi
	else
		## toolame is way faster! (3x in my test)
		it=`which toolame`
		if [ -n "$it" ] ; then
			toolame_version=`toolame -h | head -n 4 | grep version | awk '{ print $3 }'`
			myecho "[dvd-slideshow] Creating mp2 audio using toolame $toolame_version..."
			if [ "$toolame_version" == '0.2m' ] ; then
				toolame -s 48000 -b 128 "$tmpdir/audio2.wav" "$tmpdir/audio2.mp2" 
			else
				toolame -s 48 -b 128 "$tmpdir/audio2.wav" "$tmpdir/audio2.mp2" 
			fi
		else
			myecho "[dvd-slideshow] Creating mp2 audio using mp2enc"
			mp2enc -v $verbosity -b 128 -r 48000 -s -o "$tmpdir/audio2.mp2" < "$tmpdir/audio2.wav"
		fi
	fi
fi


## check to make sure the output files exist before running mplex:
if [ ! -f "$tmpdir/video.mpg" ] ; then
	myecho "[dvd-slideshow] ERROR: no output .mpg file found!"
	myecho "[dvd-slideshow] This usually happens when mpeg2enc screws up something"
	myecho "[dvd-slideshow] or one image is messed up and the resulting video can't be created"
fi
	
myecho '[dvd-slideshow]############################################################'
myecho '[dvd-slideshow] Multiplexing audio and video...'
logecho '[dvd-slideshow] Some sequence marker warnings here are normal'

## now multiplex the audio and video:
## -M option is important:  it generates a "single" output file instead of "single-segement" ones
## if you don't use -M, the dvdauthor command will fail!
## total mplex bitrate = 128kBit audio + 1500 kBit video + a little overhead
verbosity=0
if [ -n "${audio_2[0]}" ] ; then
	## two audio tracks!
	if [ "$ac3" -eq 1 ] ; then
		mplex -V -v $verbosity -M -f 8 -o "$outdir/${slideshow_name}.vob" "$tmpdir/video.mpg" "$tmpdir"/audio1.ac3 "$tmpdir"/audio2.ac3 2>> "$outdir/$logfile"
	else
		mplex -V -v $verbosity -M -f 8 -o "$outdir/${slideshow_name}.vob" "$tmpdir/video.mpg" "$tmpdir"/audio1.mp2 "$tmpdir"/audio2.mp2 2>> "$outdir/$logfile"
	fi
else  # only one audio track used:
	if [ "$ac3" -eq 1 ] ; then
		if [ ! -f "$tmpdir/audio1.ac3" ] ; then
			myecho "[dvd-slideshow] ERROR: no output .ac3 file found!"
			myecho "[dvd-slideshow] Must be some error with your input audio"
			myecho "[dvd-slideshow] or the ac3 encoder"
		fi
		mplex -V -v $verbosity -M -f 8 -o "$outdir/${slideshow_name}.vob" "$tmpdir/video.mpg" "$tmpdir"/audio1.ac3 2>> "$outdir/$logfile"
	else
		if [ ! -f "$tmpdir/audio1.mp2" ] ; then
			myecho "[dvd-slideshow] ERROR: no output .mp2 file found!"
			myecho "[dvd-slideshow] Must be some error with your input audio"
			myecho "[dvd-slideshow] or the mp2 audio encoder"
		fi
		mplex -V -v $verbosity -M -f 8 -o "$outdir/${slideshow_name}.vob" "$tmpdir/video.mpg" "$tmpdir"/audio1.mp2  2>> "$outdir/$logfile"
	fi
	if [ $? -ne 0 ] ; then
		## mplex errored
		myecho "[dvd-slideshow] ERROR during mplex execution!"
		myecho "[dvd-slideshow] see $outdir/$logfile for details"
		cleanup; exit 1
	fi
fi

myecho "[dvd-slideshow]############################################################"

verbosity=0
## now run spumux only if the png was generated:
if [ "$has_subtitles" -eq 1 ] ; then   
	spumux -m dvd -v $verbosity -s 0 -P "$tmpdir/${slideshow_name}".spumux < "$outdir/${slideshow_name}.vob" > "$outdir/tmp.vob"  2>> "$outdir/$logfile"
	if [ $? -ne 0 ] ; then
		## spumux errored
		myecho "[dvd-slideshow] ERROR during spumux execution!"
		myecho "[dvd-slideshow] see $outdir/$logfile for details"
		cleanup; exit 1
	fi
	mv "$outdir/tmp.vob" "$outdir/${slideshow_name}.vob"
else
#	rm "$tmpdir/${slideshow_name}".spumux
	myecho "[dvd-slideshow] No subtitles... removing .spumux file"
fi

## build the chapters string for passing to dvdauthor:
myecho "[dvd-slideshow] total chapters=${#chaps[@]}"
total_chapters="${#chaps[@]}"
new_total_chapters="$total_chapters"
factor=1  ;  mod=1
while [ $new_total_chapters -gt 99 ] ;  ## 99 chapters max
do
	factor=$(( 2 * $factor ))
	new_total_chapters=$(( $new_total_chapters / 2 ))	
done
if [ "$new_total_chapters" -ne "${#chaps[@]}" ] ; then
	myecho "[dvd-slideshow] reduced total chapter markers to $new_total_chapters"
fi
a=0 ; b=0
for chap in "${chaps[@]}"; do
	if [ $a == 0 ] ; then  # no comma for first chapter
		## first chapter should always be at 0 time!
		chaps_string="0"
		chapter_thumbs[$b]="${thumbs[$a]}"
		b=$(( $b + 1 ))
	else
		# only do every $factor chapters
		if [ "$mod" -eq "$factor" ] ; then
			chaps_string="$chaps_string,$chap"
			chapter_thumbs[$b]="${thumbs[$a]}"
			b=$(( $b + 1 ))
			mod=1
		else
			mod=$(( $mod + 1 ))
		fi
	fi
	a=$(( $a + 1 ))
done

if [ "$write_chaps" -eq 1 ] ; then
	# write out chapters to file:
	echo "$chaps_string" > "$outdir"/"${slideshow_name}.chap"
fi

myecho "[dvd-slideshow] chapter markers at $chaps_string"
myecho "[dvd-slideshow]############################################################"

echo '		<vob chapters="'$chaps_string'" file="'$outdir/${slideshow_name}.vob'"  />' > "$outdir/${slideshow_name}".xml

cleanup

## now, just cleanup the logfile a little bit:
sed -e '/ bytes of data written[[:cntrl:]]INFO/d' "$outdir"/"$logfile" > "$outdir"/tmp.txt
sed -e '/ [[:cntrl:]]size= /d' "$outdir"/"tmp.txt" > "$outdir"/"$logfile"
\rm "$outdir"/tmp.txt
#mv "$outdir"/tmp.txt "$outdir"/"$logfile"

echo "[dvd-slideshow] More extensive logfile output is at:"
echo "[dvd-slideshow] $outdir/$logfile"
myecho "[dvd-slideshow] Done!"
myecho
exit 0

---

### Post by hogwartsnigel on 2007-11-25
Hi Toasty,
Thanks and if what I've just done "your 192 info" doesn't work I am just going to cut and paste your whole lot and be done with it.
I found this which has revolutionised my ability at working within root
[http://ubuntuforums.org/showthread.php?t=622627](http://ubuntuforums.org/showthread.php?t=622627)
it blew me away with what it can do and so simple......
The learning curve is steep but strangely enjoyable and what is great is the humility and humanity of the linux users as a whole...these forums of which your a good example are true confirmation of goodness.

Thanks

I'll post if any problems I am trying to create a slide show as I type


Nigel

---

### Post by hogwartsnigel on 2007-11-25
Thanks Toasty,
the 192 thing has worked beautifully:)

---

### Post by toastydave1 on 2007-11-25
Hi Nigel, glad to help, only worked this out myself yesterday!

Having said all that, I got it to work, but the AC3 sound is a bit naff!

for this problem DeVeDe recommends a different version of Mplayer/Mencoder (version 1.0rc2)

see here if you have this problem
[URL="http://www.rastersoft.com/programas/devede.html"]
http://www.rastersoft.com/programas/devede.htm[/URL]l

---

### Post by hogwartsnigel on 2007-11-26
Thanks,
Yeh the sound was a little blown out. I have some pressing things to do with renaming drive disks and partitions thats occupying me with more priority at present. The man dvd is for my wifes slideshow display as part of her photography. 
I thank you for the link as I will no doubt need to change it, of course the actual ubuntu rep. may well contain this by the time I get round to it.

Can I ask have you found your trying to convert everyone to Ubuntu, I've got 7 people trying it as dual boots and 2 already have made the change completely, just wanted to know if this is a symptom of the Ubuntu LURVE....LOL or just awakening from winDOSE.

Thanks again...I'll probably get to it in the next day via your link....otherwise it'll niggle at me.

Nigel

---

