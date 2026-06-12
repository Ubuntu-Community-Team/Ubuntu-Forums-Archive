---
title: "Help rip to mp3,Thanks...."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Apple Pie on 2007-02-11
Hey everyone,this is my first posting.I am new to Ubuntu(about 1 week)and any and all help would be great.I would like to know how to get Sound Juicer to rip to mp3 or a format i can use on an ipod?
Please include every step even the most basic because i do not know much about Ubuntu.
Thanks again..
Pie...

---

### Post by AndyCooll on 2007-02-11
Open up Soundjuicer then go to Preferences.

Under format click "Edit Profiles" then click "New". Call it "mp3".

Now click on your new profile, and "Edit".

You can add a comment such as "Converts to mp3 format" under profile description.
Add the following "audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux" (without the quotes) to the GStreamer pipeline.
Add "mp3" to file extension and click ok.
Done.

:cool:

---

### Post by kevinlyfellow on 2007-02-11
Wouldn't you need to get the gstreamer codecs first?

---

### Post by AndyCooll on 2007-02-11
Yep. Sorry forgot to mention that bit!

:cool:

---

### Post by Apple Pie on 2007-02-11
Open up Soundjuicer then go to Preferences.

Under format click "Edit Profiles" then click "New". Call it "mp3".

Now click on your new profile, and "Edit".

You can add a comment such as "Converts to mp3 format" under profile description.
Add the following "audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux" (without the quotes) to the GStreamer pipeline.
Add "mp3" to file extension and click ok.
Done.

Thanks for the reply.I tried what you said,however i can not select mp3 from the output format in preferences??Did I need some other software first??
Thanks again..
Pie...

---

### Post by pay on 2007-02-11
You probably need lame installed. Look at [this](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html).

---

### Post by Apple Pie on 2007-02-11
Can you please tell me where i can get this other software.
Thanks again.
Pie...

---

### Post by deadgobby on 2007-02-11
There is Grip too.
[http://ubuntuforums.org/showthread.php?t=99115&highlight=grip](http://ubuntuforums.org/showthread.php?t=99115&highlight=grip)
Gobby

---

### Post by Apple Pie on 2007-02-11
You probably need lame installed. Look at this.

Sorry but i don't understand what they are saying in the link you sent me.Any more info would be great.
Thanks.
Pie...

---

### Post by pay on 2007-02-11
Open up the universe (and maybe some others) repositories and type ```
sudo aptitude update
sudo aptitude install gstreamer8.0-lame
sudo aptitude install gstreamer8.0-mad # for playback
gnome-audio-profiles-properties
```and create a new profile with> Profile name: CD Quality, Lossy
Profile Description: Test
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
File Extension: mp3

---

### Post by Apple Pie on 2007-02-12
There is Grip too.
[http://ubuntuforums.org/showthread.p...highlight=grip](http://ubuntuforums.org/showthread.p...highlight=grip)
Gobby


Thanks for the info but i would like to continue to use Sound Juicer for ripping.Can you tell me how to get Sound juicer to rip to mp3????.
Thanks for the info.
Pie...

---

### Post by Apple Pie on 2007-02-12
Re: Help rip to mp3,Thanks....
Open up the universe (and maybe some others) repositories and type
Code:

sudo aptitude update sudo aptitude install gstreamer8.0-lame sudo aptitude install gstreamer8.0-mad # for playback gnome-audio-profiles-properties

and create a new profile with
Quote:
Profile name: CD Quality, Lossy
Profile Description: Test
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
File Extension: mp3

IT WORKS!!!!!.Thanks to everone for the help!!!!
THANKS AGAIN!!!!!!!
Pie.....

---

### Post by Apple Pie on 2007-02-12
On last question please,what quality is the mp3 and can that setting be changed.
Thanks.
Pie......

---

### Post by pay on 2007-02-12
> **Apple Pie said:**
> On last question please,what quality is the mp3 and can that setting be changed.
Thanks.
Pie......I think that it is 128kbps by default
You can change it with```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=128
```that's for cbr

---

### Post by Apple Pie on 2007-02-12
PAY,Thanks for the help!!!Thats it for today.Take care...
Pie...

---

### Post by Apple Pie on 2007-02-12
Hello everyone,last night(or should i say 2:00am) with your help i got sound juicer to rip to mp3.Today i tried to rip a cd and sound juicer just shuts down.Any help please...
Thanks Again for your time and patience...
Pie......

---

### Post by MetalMusicAddict on 2007-02-12
Ill look into the Soundjuicer issue but Grip is really the best we have. Please see my sig for my up-to-date How-To.

---

### Post by Apple Pie on 2007-02-12
Thanks for the reply,i will also look into Grip...
Pie.....

---

### Post by Cobikegeek on 2007-02-12
Soundjuicer can be setup to rip mp3's just fine.  Follow these steps (check out the soundjuicer help file under preferences for similar info)--

1. install "Lame" codecs using synaptic.  Just type Lame in the search box and check it to install. Click apply.  Make sure you have the multiverse repositories (I think) available or Lame might not be found.

2. Open soundjuicer.  Go into edit->preferences and click on the Edit Profiles box at the bottom of the window.  Click on "New" in the profile window. Enter the following in the appropriate text box:

Profile name:  MP3

Profile Description: LAME

Gstreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux

File extension: mp3

Check the "Active?" box at the bottom of the window and then click OK.

In the edit->preferences window use the drop down box to select the MP3 profile you just created for the Output Format.

You should be good to go.  If you want a higher or lower bitrate (sound quality and mp3 file size) enter a higher or lower number for "bitrate=160" in the Gstreamer pipeline code.  Common choices are 192, 160, 128.

I find that soundjuicer rips much faster than grip or the kde ripper.  At least on my system

Good luck.

---

### Post by Apple Pie on 2007-02-12
Thanks i will try the settings in sound juicer and get back to you with what happened.

Pie...

---

### Post by MetalMusicAddict on 2007-02-12
> **Cobikegeek said:**
> I find that soundjuicer rips much faster than grip or the kde ripper.  At least on my system.
Thats because Soundjuicer doesnt use cdparanoia. Using it helps to create a accurate rip. It also slows down the rip process.

---

### Post by Apple Pie on 2007-02-12
I tried the steps you said Cobikegeek,and I'm RIPPING again.Thats it for now.
Thanks again....
Pie...

---

### Post by kinematic on 2007-02-12
soundjuicer sucks people!
first of all it doesn't use cdparanoia....the best ripper on linux.
and secondly....why in godsname are you soundjuicerusers telling people to encode in constant bitrate?
it's a waist of space and if you go to [this](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings) page you'll see that the people who created lame recommend that you use variable bitrate for the best quality.

---

### Post by pay on 2007-02-13
> **kinematic said:**
> soundjuicer sucks people!
first of all it doesn't use cdparanoia....the best ripper on linux.
and secondly....why in godsname are you soundjuicerusers telling people to encode in constant bitrate?
it's a waist of space and if you go to [this](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings) page you'll see that the people who created lame recommend that you use variable bitrate for the best quality.Are VBR mp3's compatible with mp3 players though? If they are then go for it but if they aren't, but you want to use vbr anyway, then I see no reason to use the mp3 format at all. If you want the best quality for size ratio, use Vorbis :) As an added bonus it has the best compatibility under Ubuntu.

---

