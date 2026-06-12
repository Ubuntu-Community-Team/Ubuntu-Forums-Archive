---
title: "ripping cds, and preferred audio formats,tools"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by byen on 2005-08-21
hey fellas,
I know you guys must have heard this before but oh well...here goes..
I have a 100+ audio cd collection and after upgrading my HD I though it would be a good idea to backup my cds on my HD. I used to use an mp3 convertor on windows but while looking around heard a lot about...ogg and other file formats. so my question to you is...which is the best format? All I want is to keep the quality, be able to easily burn them into audio cds and should be playable on a windows based pc (I know I know..but my brother needs games and has to have windows...(we are planning to have a common storage drive for both pcs).

So which file format do you suggest? and which is the best app for it?

thank you guys... appretiate the help.

---

### Post by qalimas on 2005-08-21
For what you need, use Grip and encode with MP3

---

### Post by byen on 2005-08-21
[QUOTE=qalimas]For what you need, use Grip and encode with MP3[/QUOTE]
 and which encoder should i use? lame?  can someone please help me out here. Im looking around as well as we speak..just wondering....if there was a hardcore music guy who must have converted tons of music and is pleased....

---

### Post by wmcbrine on 2005-08-21
LAME, yes. I use "--preset fast standard"; in the ripper config, I disable paranoia, extra paranoia, scratch detection and repair. This works fast, does a good job, and works with almost all media -- the tracks I can't rip usually aren't helped by enabling paranoia anyway.

I have grip associated with audio CD insertion, so I can just pop a disc in, click three times, and have it converted in about five minutes. Actually I had to make a script I called "regrip", and associate the event with that instead, because I kept getting false insert events, leading to multiple instances of grip. I dunno if it's my drive, or what. regrip:

if [ "`ps -C grip -o pid=`" == "" ] ; then grip ; fi

I've done about 150 discs so far.

---

### Post by byen on 2005-08-21
ok... having a lil trouble here...i tried ripping into mp3 but the files just get copied.... :(

here are my options..please tell me of i should change em:
Rip>Ripper:
Ripper : grip (cd paranoia?)
Selected: Disable paranoia
Selected:Disable extra paranoia
Disabled scratch
gain adjustment: not selected
rip file format:~/mp3/%A/%d/%n.wav (shouldnt it be mp3?)
Generic SCSI device: empty
rip nice value = 0

ENCODE:
Encoder: lame?
Encoder command-line:-h -v -V 0 %w %m
Encoder file extension:mp3
Encoder file format: ~/mp3/%A/%d/%n.%x

Options:
selected: delete .wav after encoding
selected: create .m3u files
selected: use relative paths in .m3u files
M3u file format: ~/mp3/%A-%d.m3u

Encoding bit rate: 128 (can i change this to 256?)
no of cpus to use 1
nice value:0
enter filer command : empty?


can someone please help me here.... sorry for being so rudementary in my questions.

---

### Post by wmcbrine on 2005-08-22
[QUOTE=byen]ok... having a lil trouble here...i tried ripping into mp3 but the files just get copied.... :([/quote]You have to click on the "Rip + Encode" button rather than the "Rip Only" button.

> rip file format:~/mp3/%A/%d/%n.wav (shouldnt it be mp3?)Nope. To rip is to pull the data off. "Rip Only" creates WAV files. ("Rip + Encode" also creates them, but only as an intermediate step.) To go from WAV to MP3, you must Encode.

And yes, it is actually sometimes useful to rip without encoding. But if you don't know why, then don't worry about it for now. :)

Edit:

> Encoder command-line:-h -v -V 0 %w %m

Encoding bit rate: 128 (can i change this to 256?)With your current encoder command line, you're creating a variable bit-rate file, and the grip-specified bit rate isn't even being passed on to LAME. You could change this by adding "-b %b", but with a variable bit-rate, that just sets the minimum (-B for the max). If you want a constant bit-rate (not recommended), you can take out the -V. See man lame for all the options.

I use "--preset fast standard %w %m" as my encoder command line in grip, and I set the bit-rate in grip to 192 -- purely for purposes of getting the encoder progress bar somewhere close to reality; it doesn't control the encoding, since I'm not passing the value in the encoder command line.

---

### Post by xequence on 2005-08-22
Choose ether MP3 or OGG.

MP3 works with almost ANYTHING. It has good quality.

OGG doesent work with many mp3 players but should work on most audio players on your computer. It is said to have better quality and it is open source.

---

### Post by byen on 2005-08-23
thank you for your reply guys. Looked around and tried a lot but nothing seems to work. I cant get grip to convert cd to mp3...it just changes to wav and thats it!.... when i try to convert to ogg..it tries to convert it at a speed of <1x..i gave up after 60mins. nothing seems to work and After trying for 3 hours...im giving up.... im tired and so pissed off. Will make a fresh attempt tommorow.wish me best! I hate to have to ask my brother to rip the cds on his xp computer just because I was lame enough to not get things working...but looks like im heading there...
hope i work it out tomm. Please suggest anything if you can.thanks,

---

### Post by byen on 2005-08-23
ok..fresh start again...so i need lame to rip mp3s right? how can i find out if i have it or not? where do i look for it..and if i dont have it how do i get it? 

thanks for the help  guys.

---

### Post by Jenda on 2005-08-23
[QUOTE=byen]ok..fresh start again...so i need lame to rip mp3s right? how can i find out if i have it or not? where do i look for it..and if i dont have it how do i get it? 

thanks for the help  guys.[/QUOTE]
 Even I can tell you: Synaptic. Just look for it, it's there.

---

### Post by senn on 2006-09-24
> **byen said:**
> ok..fresh start again...so i need lame to rip mp3s right? how can i find out if i have it or not? where do i look for it..and if i dont have it how do i get it? 

thanks for the help  guys.

hi byen, i've just bought a samsung i6 camera which has a PMP and a mp3 download and play back on it:D . in order to get the mp3 to work ( after i read this thread cheers chaps) i searched in synapitics for "lame" which came back with "ripper X". this is also in "add/remove" under the applications tab at the top left of the screen and is always visible. i used "add/remove to install this app and it work a treat, is simple to use (even for me !!!:oops: ) it launches from "Sound&video" comes up with a simple interface with which you can rip straight from the cd and encode it to mp3 in your home folder. when that is done (takes about 30 mins dont beleive the 359 mins that first comes up) you can open up rhythembox to "scan removable drives" open up your home folder and drag an drop files straight into the i6 or any other removeable drive that uses the mp3 format. oh im running dapper 6.06. you should check this one out as it is very easy to use.

---

### Post by wavesound on 2006-10-02
HI All 8) 
Just been trying Ubuntu for this very thing (from Redhat)
The only thing I found that worked on my system was ripperX which seems to work on anything!!! well done to the developers.

I wanted to rip my CD collection to wav to run on my I-river, with about 30gigs on this there is no need for Mp3 or Ogg (Ogg sounds much better than mp3 at the same size)

Sound Juicer just complained about a pipeline when I tried wav.
I installed easyubuntu to get the proprietry stuff but it now complains that there is stuff on here it cant remove (?)

Is wav a windows thing? or is it free for deveoplers to use, I thought wav predated windows.

All working now though apart from I seem to have installed the KDE desktop instead of gnome, I dont suppose there is an easy way out of this?;) 

Cheers
Bob

---

