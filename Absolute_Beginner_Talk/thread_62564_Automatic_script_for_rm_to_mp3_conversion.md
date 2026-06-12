---
title: "Automatic script for rm to mp3 conversion"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by Dafydd on 2005-09-05
Hello everybody,

I installed Ubuntu 5.04 a couple of a week or two ago after trying out several live CDs (Aurox 10, Knoppix 3.9, Linux+ Live, etc). It's great. After trying to use Mandrake 8.2 (couldn't get Internet to work) and then Suse 9.1 (could get the sound to work), Ubuntu is great... Thanks (despite a few problems - this is my first post).

Anyway, one thing I used to do with Windows was use Streambox to  batch convert a downloaded realmedia files into mp3 and bung them on my mp3 player. I've learnt how to do that one by one by copying some script found on a forum:

But how do I automate the process? How can I make it just batch convert all rm files in a single directory and put them on my mp3 player? Thanks a million to anyone who can help.

Best 
Dafydd

-------------

mplayer /home/dafydd/Desktop/Radio/polish.rm -ao pcm -aofile /home/dafydd/Desktop/Radio/polish.wav
mplayer /home/dafydd/Desktop/Radio/polonais.rm -ao pcm -aofile /home/dafydd/Desktop/Radio/polonais.wav
mplayer /home/dafydd/Desktop/Radio/polonais2.rm -ao pcm -aofile /home/dafydd/Desktop/Radio/polonais2.wav

lame -f /home/dafydd/Desktop/Radio/polish.wav /media/usbdisk/polish.mp3
lame -f /home/dafydd/Desktop/Radio/polonais.wav /media/usbdisk/polonais.mp3
lame -f /home/dafydd/Desktop/Radio/polonais2.wav /media/usbdisk/polonais2.mp3

-------------

---

### Post by Arjen on 2005-09-05
Hey Dafydd,

the easiest solution would probably be to write a short script that does it for you. I'm working on it now, but I don't actually have any rm files to test it on :-). Could you perhaps point me to some? Once I know the script works I'll post it here and you can use it.

---

### Post by Arjen on 2005-09-05
Never mind, I found some. The following script works. All you have to do is save it in a new file (copy-paste into gedit for example). A good name for it is probably rm2mp3 which is the name I used.

Once you have saved the file you must give it executable rights. You do that like this:
```
$ cd *(directory where you saved the file)*
$ chmod +x rm2mp3
```

The code for the file itself:
```
#!/bin/bash
# transcodes realmedia (RM) audiofiles to MP3 audio files.
# Version 0.1
# Author: Arjen
# Usage: rm2mp3 <input-dir>

### Configuration

#This is where the temporary wav files will be stored
TMPDIR="/tmp"

#This is where the MP3 files will end up
OUTPUTDIR="/media/usbdisk"

#Path to mplayer binary. Don't change unless you know what you're doing.
MPLAYER="/usr/bin/mplayer"

#Path to lame binary. Don't change unless you know what you're doing.
LAME="/usr/bin/lame"

#Options for rm to wav decoding
MPLAYER_OPTS="-ao pcm -aofile"

#Options for lame encoding
LAME_OPTS="-f"

#Define working directory
WORK="$TMPDIR/rm2mp3.$$"

#Define working name for tracks
WAV="$WORK/track.wav"

### End configuration

# Get absolute directory paths
INPUTDIR="$1" #you can change this to an absolute path
cd "$INPUTDIR"
INPUTDIR="$PWD"

# Setup work directory, clean and create
rm -rf "$WORK"
if [ -e "$wORK" ]; then
	echo "Couldn't delete $WORK"
	exit 1
fi
mkdir "$WORK"
	if [ ! -d "$WORK" ]; then
	echo "Couldn't create $WORK"
	exit 1
fi

# Transcode the files
cd "$INPUTDIR"
OLDIFS="$IFS"
IFS=$'\n'
for filepath in $(find . -type f -name '*.rm' -print \
	| sort | sed -e 's/^\.\///' -e 's/\.rm$//'); do
	IFS="$OLDIFS"
	filedir="$(dirname "$filepath")"
	filename="$(basename "$filepath")"
	if [ ! -d "$OUTPUTDIR/$filedir" ]; then
		mkdir -p "$OUTPUTDIR/$filedir"
	fi
	if [ ! -f "$OUTPUTDIR/$filepath.mp3" ]; then
		#Create wav file
		$MPLAYER "$INPUTDIR/$filepath.rm" $MPLAYER_OPTS "$WAV"

		# Encode MP3
		$LAME $LAME_OPTS "$WAV" "$OUTPUTDIR/$filepath.mp3"
	fi
done

# Clean up
rm -rf "$WORK"
exit

```

Using the script is very easy. Right now it is configured for all the MP3 files to go to your USB disk, but you can change that if you want.
```
$ rm2mp3 /home/dafydd/Desktop/Radio/
```
is all you need to type in a terminal to use it. Although you should browse to the rm2mp3 directory first.

Everything with a # in front of it is a comment and should tell you what is being done. For example you might want to check the lame options. -f gives you pretty low quality and you might want to get better quality.
```
$ man lame
```
Will show you all possible options.

If you have any questions don't hesitate ask them.

---

### Post by xmastree on 2005-09-05
[QUOTE=Dafydd]mplayer /home/dafydd/Desktop/Radio/polish.rm -ao pcm -aofile /home/dafydd/Desktop/Radio/polish.wav
lame -f /home/dafydd/Desktop/Radio/polish.wav /media/usbdisk/polish.mp3[/QUOTE]Assuming those are the commands you run to convert the rm to mp3, via wav format, then you could make a simple script and save it in ~/.nautilus/scripts
You could invoke it from within nautilus by selecting the files you wish to convert, right clicking and selecting the script.
```
#!/bin/sh
for arg 
do
mplayer "$arg" -ao pcm -aofile temp.wav
lame -f temp.wav "$arg"
done
```As it is, that wouldn't work.
$arg will be the input filename, so the output filename produced by lame would be the same, including the extension. There may well be a way to pass the filename to the script without the extension, but I haven't figured that out yet.

More options [here](http://g-scripts.sourceforge.net/cat-multimedia.php)

---

### Post by Arjen on 2005-09-05
Interesting. I didn't know nautilus could deal with scripts like that.
As to how to strip the extension from the file name, couldn't that be done by using sed?
You could probably do a search and replace on $arg that stripped it of its extension, and then carry out the other commands.

---

### Post by UbuWu on 2005-09-05
Or alternatively you could install soundconverter (from breezy repo's) and gstreamer-lame (backports extra's?) and not mess with scripts at all...

---

### Post by xmastree on 2005-09-05
[QUOTE=Arjen]Interesting. I didn't know nautilus could deal with scripts like that.[/QUOTE]Neither did I until the other day, when I saw [this thread](http://www.ubuntuforums.org/showthread.php?t=60975) and jumped in as I was interested in the idea.

---

### Post by Dafydd on 2005-09-07
[QUOTE=Arjen]Hey Dafydd,

the easiest solution would probably be to write a short script that does it for you. I'm working on it now, but I don't actually have any rm files to test it on :-). Could you perhaps point me to some? Once I know the script works I'll post it here and you can use it.[/QUOTE]
 Thanks a million Arjen and everybody!


Tried the script out and it worked fine, converting the sound. That's saved me such a lot of fiddling. The script actually works just a well as the little program I used in Windows (Streambox Ripper).

I've had to reinstall Ubuntu (after a stupid messed up install of Puppy Linux - just to try). And now I've got problems with the repositories... But hopefully tomorrow, I can test out the script (I need to reinstall mplayer).

---

### Post by bhuvankrishna on 2008-03-31
a small change in the code for an updated mplayer. this edited code will work with the new version of mplayer which prefers -ao pcm:file= as an ouput option to the old one which takes -ao pcm -aofile

#!/bin/bash
# transcodes realmedia (RM) audiofiles to MP3 audio files.
# Version 0.1
# Author: Arjen
# Usage: rm2mp3 <input-dir>

### Configuration

#This is where the temporary wav files will be stored
TMPDIR="/tmp"

#This is where the MP3 files will end up
OUTPUTDIR="/home/bhuvan/Desktop/songs/mp3"

#Path to mplayer binary. Don't change unless you know what you're doing.
MPLAYER="/usr/bin/mplayer"

#Path to lame binary. Don't change unless you know what you're doing.
LAME="/usr/local/bin/lame"

#Options for rm to wav decoding
MPLAYER_OPTS="-ao pcm:file"

#Options for lame encoding
LAME_OPTS="-f"

#Define working directory
WORK="$TMPDIR/rm2mp3.$$"

#Define working name for tracks
WAV="$WORK/track.wav"

### End configuration

# Get absolute directory paths
INPUTDIR="$1" #you can change this to an absolute path
cd "$INPUTDIR"
INPUTDIR="$PWD"

# Setup work directory, clean and create
rm -rf "$WORK"
if [ -e "$wORK" ]; then
echo "Couldn't delete $WORK"
exit 1
fi
mkdir "$WORK"
if [ ! -d "$WORK" ]; then
echo "Couldn't create $WORK"
exit 1
fi

# Transcode the files
cd "$INPUTDIR"
OLDIFS="$IFS"
IFS=$'\n'
for filepath in $(find . -type f -name '*.rm' -print \
| sort | sed -e 's/^\.\///' -e 's/\.rm$//'); do
IFS="$OLDIFS"
filedir="$(dirname "$filepath")"
filename="$(basename "$filepath")"
if [ ! -d "$OUTPUTDIR/$filedir" ]; then
mkdir -p "$OUTPUTDIR/$filedir"
fi
if [ ! -f "$OUTPUTDIR/$filepath.mp3" ]; then
#Create wav file
$MPLAYER "$INPUTDIR/$filepath.rm" $MPLAYER_OPTS="$WAV"

# Encode MP3
$LAME $LAME_OPTS "$WAV" "$OUTPUTDIR/$filepath.mp3"
fi
done

# Clean up
rm -rf "$WORK"
exit

---

