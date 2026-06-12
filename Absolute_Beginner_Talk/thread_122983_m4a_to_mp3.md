---
title: "m4a to mp3"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Downtown on 2006-01-28
I know it's been covered before, but I'm getting mixed results.  I read the posts on [this]("http://ubuntuforums.org/showthread.php?p=630881#post630881") and [url="
http://ubuntuforums.org/showthread.php?p=589315#post589315"]this[/url] thread and I've tried both the scripts suggested.

If I try the first one, I conserve the ID3 tags, but the file is corrupted and the file is just static, and if I use the second one, I lose ID3 tags, but the file plays correctly.  I don't know much about scripts, so does anybody know how I can combine the two so that I can convert an m4a to mp3 while conserving my ID3 tags.

For quicker reference, these are the two scripts, in order of the links provided above...

```

#!/bin/bash
for i in *.m4a
do
base=`basename "$i" .m4a`
info=`faad -i "$i" 2>&1`
artist=`echo "$info" | grep artist: | sed s/artist:\ //g`
album=`echo "$info" | grep album: | sed s/album:\ //g`
song=`echo "$info" | grep title: | sed s/title:\ //g`
track=`echo "$info" | grep track: | sed s/track:\ //g`
year=`echo "$info" | grep date: | sed s/date:\ //g`
genre=`echo "$info" | grep genre: | sed s/genre:\ //g`
faad -w "$i"| lame -h -b 128 - "$base.mp3"
#id3 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
id3v2 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
done

```

```

#!/bin/bash
for i in *.m4a
do
	NO_SPACE=`echo $i | sed -e "s/ /_/g"`
	mv "$i" "$NO_SPACE"
done

for i in *.m4a
do
	faad $i
	lame *.wav
	rm *.wav
	rm "$i"
done

for i in *.mp3
do
	NO_WAV=`echo $i | sed -e 's/.wav//g' -e 's/_/ /g'`
	mv "$i" "$NO_WAV"
done

```

---

### Post by Kethinov on 2006-01-29
Well, I don't know about preserving ID3 tags, but I wrote a few quick scripts to convert all the m4as in a directory to mp3s. You will need mplayer and lame installed for this.

Convert m4a to wav:
```

for i in *.m4a
do
mplayer -ao pcm "$i" -ao pcm:file="$i.wav"
done

```

Convert wav to mp3:
```

for i in *.wav
do
lame -h -b 192 "$i" "$i.mp3"
done

```

Fix filenames:
```

for i in *.mp3
do
x=`echo "$i"|sed -e 's/m4a.wav.mp3/mp3/'`
mv "$i" "$x"
done

```

To get your id3 tags back, you might want to try using a program to assist you like Easytag or Ex Falso.

---

### Post by dmartin on 2006-02-05
I have been using SharpMusique to get my music from ITunes Music Store, and I wanted to put it on a Zen Touch which can't use aac.  None of the scripts I could find seemed to be a complete solution, so I've spent some time making it work this weekend.  I used code from somebody named Gimpel, found [here]("http://gimpel.gi.funpic.de/Howtos/convert_aac/"), and the code you posted (I think the credit originally belongs to sciurus for that).  I also had to fix a number of things that weren't working in both scripts.

Here's the steps:

1) Install all dependencies:
```
sudo apt-get install mplayer-386 faad lame libfaad2-0 id3v2
```

2) Download the attachment: [ATTACH]5874[/ATTACH]

3) Set the script up the way it needs to be:
```
sudo mv aac2mp3.txt /usr/local/bin/aac2mp3
sudo chmod +x /usr/local/bin/aac2mp3
```

Now you are good to go. Just type "aac2mp3 myfile.m4a", or "aac2mp3" to convert all m4a files in the current directory.   For command line arguments, use "aac2mp3 --help".

Some notes on this:

1) I set the default bitrate to 128.  This is because ITunes is set at 128, and it doesn't make sense for me to encode any higher.  You can pass it another bitrate using the -b command, or you can edit the script and change the default.

2) This script uses faad to get the tag information.  The tag information isn't always great.  Not sure if this is a shortcoming of faad, or if ITMS doesn't supply good tag data.  The worst part is that it seems to never have the album.  Some files have no tag data at all.

3) You can run this script in Nautilus (the file-browser in Ubuntu).  Just right click on the m4a file and choose "Open With >> Open With Other Application".  Then click the arrow for "Use a custom command" and put "aac2mp3" in the box, and click "Open".  From then on, it should show up automatically in the "Open With" dialog.

---

### Post by zombie.daemon on 2006-02-14
change your faad line to

faad -o - "$i" | lame -h -b 192 - "$base.mp3"

---

### Post by fletc900 on 2006-08-13
Thanks dmartin! =D>
I created a Python program that adds some extra functionality to  your bash script for converting *.m4a format to *.mp3:

1- The python script now recursively searches  through all the folders of the working directory to find the *.m4a files...once the m4a files are found they are converted into mp3 files.

2- The user can also select an option to delete the *.m4a files once the file is converted to mp3.

See the message attachment to download the code. Installation instructions are presented in the README file.

Cheers,
B.F.

---

