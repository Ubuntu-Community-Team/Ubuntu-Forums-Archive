---
title: "From .mp3 to .m4a conversion"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by bigboyman2 on 2007-12-15
Okay, my phone is able to receive and send files via bluetooth (browsing it is a whole other story). But in order for my ringtones to be playable as callertones and an official ringtone (Samsung t169), the files have to be converted to .m4a format, and -renamed- as 3gp (don't ask how I found that out, it took forever)

I recently made the switch to Ubuntu Gutsy. In windows, I used wavepad to cut the song down, so now I use audacity in Gutsy. Problem is, to convert it to m4a, I used iTunes and converted the files there. Which presents a sort of problem, as I don't have Vista on my computer anymore, to Wine is out of the question, and since iTunes doesn't exactly carry support on Linux ubuntu, I can't open it up.

tl;dr: I need something on Gutsy that is able to convert from .mp3 to .m4a 
Backwards, maybe, but necessary if I ever want to make a video game ringtone :)

---

### Post by staticvoid on 2007-12-15
does soundconverter or soundkonverter do that?

if gstreamer supports .m4a then soundconverter should be able to convert it


sv

good luck :)

---

### Post by bigboyman2 on 2007-12-15
> **staticvoid said:**
> does soundconverter or soundkonverter do that?

if gstreamer supports .m4a then soundconverter should be able to convert it


sv

good luck :)

No, neither of those are able to encode into m4a. Just tried both of them

---

### Post by ozzyprv on 2007-12-15
**bump**

I have the same question. I need to convert quite a few files from .mp3 and .ogg to .m4p

Any help?

Thanks.

---

### Post by ozzyprv on 2007-12-15
> **ozzyprv said:**
> **bump**

I have the same question. I need to convert quite a few files from .mp3 and .ogg to .m4p

Any help?

Thanks.

I did some more reading. It seems like gtkpod is what we need.
What can gtkpod do?

gtkpod allows you to

    * Read your existing iTunesDB (i.e. import the existing contents of your iPod including playcounts, ratings and on-the-go playlists).
    * Add MP3, WAV, M4A (non-protected AAC), M4B (audio book), podcasts, and various video files (single files, directories or existing playlists) to the iPod. You need a third party product to download podcasts, like 'bashpodder' or 'gpodder'

---

### Post by High Camp on 2007-12-15
Try [www.media-convert.com](www.media-convert.com). It's not 100% reliable but it's fast and safe with no install necessary. It seems to be able to convert almost anything. I used it to convert .wmv podcasts to .mp3 to listen to on my phone.

Hope that helps,

---

### Post by bigboyman2 on 2007-12-15
I guess that'll have to do. I was actually gonna use Zamzar. That other one that you gave me can't convert mp3 to m4a, I selected input as mp3, and the output, it wouln't let me select m4a. [www.zamzar.com](www.zamzar.com) will work, though. I just wish I had a way of doing it myself without the hastle of going through a site =p

---

### Post by Azakus on 2007-12-16
I made a little script to do this. I'm working on getting all the tags transferred too.
It uses mplayer and faac. Basically, the script uses mplayer to dump the .mp3 to .wav, and then uses faac to encode the .wav into a .aac (tags need .m4a format).
This is very beta, but it works for me.
I'm working on getting it to do a batch convert, so if you know how, just post an updated copy.
EDIT: added line to remove .wav file created. Who needs that?
Contents:
```

#!/bin/bash
# Azakus 2007
# Requires mplayer, faac, and id3v2
echo "Input name of mp3 file, excluding .mp3"
echo -n ">"
read IN
OUT="`ls | grep $IN.mp3`"
echo "Dumping mp3 to wav"
mplayer -vo null -vc null -ao pcm:fast:file=$IN.wav $OUT
echo "Converting id3v1 tags to id3v2 for easier transition to m4a tags" 
id3v2 -C $OUT
#"Coverting id3 tag from mp3 to m4a tag" --requires id3v2 tags.
TITLE="`id3v2 -l $OUT | grep TIT2 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
ARTIST="`id3v2 -l $OUT | grep TPE1 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
ALBUM="`id3v2 -l $OUT | grep TALB | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
TRACK="`id3v2 -l $OUT | grep TRCK | awk '{ORS=" "} {for (i = 6; i <= NF; i++) print $i}'`"
YEAR="`id3v2 -l $OUT | grep TYER | awk '{ORS=" "} {for (i = 3; i <= NF; i++) print $i}'`"
faac -b 128 -c 44100 -w --title "$TITLE" --artist "$ARTIST" --year "$YEAR" --album "$ALBUM" --track "$TRACK" $IN.wav
rm $IN.wav
echo "AAC transcode complete!"

```

---

### Post by IcarusR on 2007-12-16
Hi
I believe there is a script for Amarok that will do this. Not tried it since edgy, now on feisty.

Icarus

---

### Post by rflight79 on 2008-03-01
Inspired by one of the above posts, I created this script to convert an entire directory of MP3's to M4b files (essentially audiobook), to allow bookmarking of my podcasts. I had a lot downloaded, and this does all of the ones in the directory, and I can add the command to IcePodder to do each time it downloads a new podcast, without having to actually supply a filename argument.

What I did learn, is that if you want bookmarkability, you should actually designate an output filename for faac with the "m4b" suffix, going in and renaming the file does not seem to work, or at least it didn't work with my 2nd gen nano. Hope this helps others trying the same thing.

```
#!/bin/bash
# mp3tom4b.sh
# bulk mp3 to m4b converter to generate bookmarkable aac files for ipod

mp3files="*.mp3"
wavend=wav
aacend=m4b
GENRE=Podcast
tmpdir=~/.backup_podcasts/ #change this depending on what you want to do with the old files

for file in $mp3files
do
  
  basenam=${file%.*3} # Get the first part of the filename, without the mp3 part

# Then run mplayer on the file, generating a wav file, using the mp3 file
  mplayer -vo null -vc null -ao pcm:fast:file=$basenam.$wavend $file

  id3v2 -C $file

  TITLE="`id3v2 -l $file | grep TIT2 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
  ARTIST="`id3v2 -l $file | grep TPE1 | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
  ALBUM="`id3v2 -l $file | grep TALB | awk '{ORS=" "} {for (i = 4; i <= NF; i++) print $i}'`"
  TRACK="`id3v2 -l $file | grep TRCK | awk '{ORS=" "} {for (i = 6; i <= NF; i++) print $i}'`"
  YEAR="`id3v2 -l $file | grep TYER | awk '{ORS=" "} {for (i = 3; i <= NF; i++) print $i}'`"
  
  faac -b 32 -c 44100 --title "$TITLE" --artist "$ARTIST" --year "$YEAR" --album "$ALBUM" --track "$TRACK" --genre "$GENRE" -w -o $basenam.$aacend $basenam.$wavend

  rm $basenam.$wavend
  mv $file $tmpdir
  
done
```

---

