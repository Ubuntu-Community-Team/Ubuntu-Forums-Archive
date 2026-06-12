---
title: "[SOLVED] ripping cd to 'mp3'"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by bignelly on 2007-08-23
i have been using ubuntu for a couple of weeks now, i have had trial and tribulation and have worked through some problems myself and also gained some help where needed. 
i use my computer mostly for ripping cd's then transferring them on and off an mp3 player,
i like the sound juicer but it rips cd's to 'ogg' is there a similar easy to use program that will rip mp3's for me?
i have tried looking in the "add/remove programs" and tried one or two programs but foind them either cumbersome or glitchy or just a bit too techie for a noobie to linux. 
i don't particularly want to start trying to convert them from 'ogg' to 'mp3' . 
iether that or a fully functional meadia player like 'realplayer' that burns plays syncs and rips would be good.
i would be grateful if some of you could leave suggestions comments or tell all about the mediea programs that you prefer   

bignelly

:guitar:

---

### Post by ThrobbingBrain66 on 2007-08-23
Sound Juicer lets me rip to mp3.

Edit > Preferences > Format
There is an option for mp3...maybe that just started in Gutsy though?

You can also take a look at Grip and Goobox

---

### Post by Jimmyfj on 2007-08-23
Well I don't use the MP3 format on my computer, only Ogg-Vorbis. But I think that RipperX could be what you are looking for. Look for it in Programs/Add/Remove/Music and video.

---

### Post by sumguy231 on 2007-08-23
I've never really used sound juicer before, but you'll definately need to install lame or something else that can encode mp3s from the repositories to be able to encode to mp3. From there go to Edit -> Preferences in Sound Juicer, and see if mp3 is listed in the dropdown box at the bottom. I have LAME and all other manners of encoders installed, but it still doesn't list mp3 as an option for some reason.

I use KAudioCreater myself (and think it's better) but that's because I use KDE.

---

### Post by jingo811 on 2007-08-23
I just discovered this link that someone posted today it seems good.  I haven't tested the tutorial though.  However I've used **Sound Juicer for Feisty** and let it convert my CD album just by following the programs simple directions.  It converted things to 160 kbps *.ogg it sounds just as great as my 256 kbps *.mp3 files.  Sound Juicer from my old Dapper time wasn't as nice and easy though.

But with that tutorial link you might be able to control the kbps like you want it.....
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by bignelly on 2007-08-23
how?  

it only gives options wav or ogg ?

have i missed something?   a plug in maybe 

i will go and have another look, thaks for your comment 


bignelly

---

### Post by bignelly on 2007-08-23
> **jingo811 said:**
> I just discovered this link that someone posted today it seems good.  I haven't tested the tutorial though.  However I've used **Sound Juicer for Feisty** and let it convert my CD album just by following the programs simple directions.  It converted things to 160 kbps *.ogg it sounds just as great as my 256 kbps *.mp3 files.  Sound Juicer from my old Dapper time wasn't as nice and easy though.

But with that tutorial link you might be able to control the kbps like you want it.....
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Excellent link, thankyou for you help jingo

---

### Post by bignelly on 2007-08-23
> **Jimmyfj said:**
> Well I don't use the MP3 format on my computer, only Ogg-Vorbis. But I think that RipperX could be what you are looking for. Look for it in Programs/Add/Remove/Music and video.

Cheers jimmy, i downloaded ripperX, I'll give it a whirl and see what happens.:)

---

### Post by laidback on 2007-08-23
Sound Juicer can rip to mp3, mine does but it needs an additional Output Format to be added. I don't have the time right now to give the details so I'll do it tomorrow evening. Hope that's OK.

Correction I'll do it now:

Here's the line you need to add in a new Output format:-

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

(I'd copy it rather than retype)

In Sound Juicer Edit>Preferences>Edit Profiles>Add  ..now put in an entry for mp3. The above line is the critical one. 
There is a bug that prevents further editing on an existing entry, but you can edit it via the CML

I will leave that until tomorrow.

---

### Post by laidback on 2007-08-24
This is what you need to edit via the command line:-

 just open 'gnome-audio-profiles-properties' from the CLI. It doesn't freeze doing it this way.

(You may be able to do the entire operation via this route, but I haven't tried that)

You'll also need Restricted formats installed to rip or play mp3s.

---

### Post by bignelly on 2007-08-24
i got sound juicer to make mp3's for me, i used the link that was posted earlier, only niggle now is that i don't know how to adjust the bit rate. i tried out the ripperX and it worked quite nicely, and allowed me to select my chosen bit rate from a menu

thankyou for your help laidback i would like to have a go at what you suggested,( as a learning experience), but i only vaguely understand what you are saying  What is a 'CLI'  ? and a CLM ?

---

### Post by laidback on 2007-08-24
CLI = Command Line Interface = CLM= CML later is probably an error on my part. It's the Terminal that takes you to a Command Line Screen, where you get a Shell prompt:-

Applications>Accessories>Terminal in 7.04 (Feisty). 

I'm very sorry to have confused you, that wasn't the intention
Pleased to hear that you have mp3 working now, I've never altered the bit rate although no doubt somewhere within this is the key to that:-

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

you'd just need to know what it all means I guess.
There is a CD quality Lossless setting in Sound Juicer, but it's not mp3 format.

Maybe I should look at ripperX as I've never used it, so thanks for that.

---

### Post by marty922 on 2007-08-24
G'day guys,

> I've never altered the bit rate although no doubt somewhere within this is the key to that:-

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

I've just found this on another thread.

Here's my GStreamer pipeline setting for 256kbps.

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=256 ! id3v2mux
```

The standard setting is for variable bit rate (vbr).  The line I use above sets it to a constant 256.  If you want higher or lower, just change that value.

Hope that helps,

Cheers,
Marty

---

### Post by bignelly on 2007-08-24
thank you for explaining that for me, :)
My dificulty is, that i am not only new to linux, but fairly new to computers. It has been a sharp learning curve so far but i think i am picking it up quite quickly, it's just the tech speak sometimes throws me off track a bit.
i see what you mean about it locking up, witch is why we used 'Terminal' (the CLI:)) to go in and change the line of code in sound juicer.

I am having a new problem. i downloaded a couple of themes to try from the Synaptic package manager but i cant seem to use them,  they are not in 'SYSTEM/PREFERENCES/THEMES' where i expected them to be? 

do they need to be activated, or perhaps i need to download an other program to run them?
it's no big deal really, but it is bugging me that i couldn't get it to work

many thanks

---

### Post by bignelly on 2007-08-24
> **marty922 said:**
> G'day guys,



I've just found this on another thread.

Here's my GStreamer pipeline setting for 256kbps.

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=256 ! id3v2mux
```

The standard setting is for variable bit rate (vbr).  The line I use above sets it to a constant 256.  If you want higher or lower, just change that value.

Hope that helps,

Cheers,
Marty


it does help thanks, i have just learned how to change that comand,  and now i know what to change it to :)

---

### Post by laidback on 2007-08-25
Thanks to all for the bit rate info, another step forward.

---

### Post by laidback on 2007-08-25
I'd put up another thread re your themes query

---

### Post by andrew.46 on 2007-08-29
Hi,

 If you are confident in using the command line you could try abcde:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

 If not just file the link away for another day. 

                Andrew

---

### Post by vanadium on 2007-08-29
The hydrogenaudio forum recommends 

lame -V 2 --vbr-new

as settings to obtain a high quality vbr mp3 ("transparent") with a minimum file size for that quality. -V 2 means vbr at quality level 2 (yields files with an average bitrate between 170 - 190 kbps) and --vbr-new means: use the "new" algorithm. Currently, this is considered to be equal, quality wise, to the "old" algorithm, but is about two times faster (refs: "man lame" and the hydrogen audio pages)

This would translate in gstreamer syntax as:

```

lame name=enc vbr=4 vbr-quality=2

```

vbr=4 means "Lames' new VBR algorithm" and is the equivalent of --vbr-new
vbr-quality is equivalent to the quality level in the -V option.

According to the lame documentation, joint-stereo is by default used for V > 4, and stereo for higher quality settings. The "mode=0 " option (use "stereo) could therefore probably be omitted.
This info can be found typing "gst-inspect-0.10 lame | less" at the command line.

---

### Post by Giggity on 2007-09-01
This is all good stuff.  I still have a problem, though... when I create a new ripping profile via the CLI method, the profile does not appear in SoundJuicer's list.  How do I go about fixing this?

Edit:  I have MP3 playback support, as well as liblame0 libraries installed.  Is that the correct library?

---

