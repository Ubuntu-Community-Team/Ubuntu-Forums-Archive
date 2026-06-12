---
title: "Possible cure for audio lag when burning vcd"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2007-01-17
Hi all,
     after some experimenting (ie making badly out of synch vcd's). I think I may have found a solution.
using FFMPEG  (in the repositories ) command line but dont worry
take your avi. file and in a terminal type

ffmpeg -i  yourfilename.avi  -target pal-vcd outputfilename.mpg  

EDIT 14th May 2007 *******************************************
for 16:9 avi's use

ffmpeg -i yourfilename.avi -target pal-vcd -s 352x192 -padtop 32 -padbottom 32 outputfilename.mpg

this will preserve 16:9 aspect

END OF EDIT*****************************************************



yourfilename and outputfilename are of course the names of the files you wish to convert and pal is the tv system type .Check for your own region ie ntsc in ffmpeg man and substitutie it for pal

if the resulting file is larger than 700mb for a vcd then you will have to split the file 
e.g a 1.3gig mpg needs to be split into 2 parts to fit on 2 vcd 

using mpgtx (also in the reps) type the following

mpgsplit -2 filename.mpg -b outputfilename.mpg
or 
mpgsplit -2 filename.mpg (which will split the file into 2 giving you 2 files named  chunk1 and chunk2 )

get DEVEDE from Ubuntu Click and Run making sure you get the right distro and choose VCD from the menu. Choose the first chunk to encode and in the ADVANCED options  under MISC choose 
THIS FILE IS  MPG -PS  to stop devede re encoding

EDIT MAY 2007

If you are familiar with vcdimager command line you can use instead of DEVEDE

vcdimager -t vcd2 -l "name of disc" -c nametocall.cue -b nametocall.bin  filename_to_use_from_mgpsplit.mpg

END OF EDIT MAY 2007

repeat for the second chunk. This will give you the bin and cue files for each part .

start the burn using  Gnomebaker or kb3 to burn cd image

Devede uses Mencoder toi encode and I think this may be part of the problem , so using FFmpeg instead seems to work 

these are the simpleist commands from ffmpeg and mpgtx there are more complicated options you will have to read thru the man,but these should get you started.
SVCD's will have to be broken down into more parts and change the ffmpeg command to -target pal-svcd . Of course if you are not in a pal region use -target ntsc-vcd. Check for your region setting in man ffmpeg

Phil

ps should work for other filetypes to vcd

---

### Post by PhilJ on 2007-01-17
just completed another trial avi movie conversion on a downloaded bit torrent file

seems to be ok fast forward and reverse dont seem to upset it.

Phil

---

### Post by PhilJ on 2007-01-17
bump.

missed a step out of the instructions
edited it

---

### Post by PhilJ on 2007-01-17
just completed and tested 2nd avi to vcd using above method.

fingers crossed I think I've cracked it this one is ok too

hope this is of some help

Philj

edit   I burned on slowest speed   4

dont use your computer for anything else whilst ffmpeg and devede are doing their stuff

---

### Post by PhilJ on 2007-01-26
just an update.
have now burned 4 vcd's using this method and the audio is correct on all of them they were burned at faster speed  x12 and still ok

Phil :D

---

### Post by PhilJ on 2007-05-14
edited first post adding alternative method for making bin and cue files

philj

---

### Post by PhilJ on 2007-05-27
Also checkout this thread for info on cdrecord and wodim 

[http://ubuntuforums.org/showthread.php?t=448453](http://ubuntuforums.org/showthread.php?t=448453)


Philj

---

