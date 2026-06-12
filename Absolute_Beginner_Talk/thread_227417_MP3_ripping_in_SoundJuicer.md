---
title: "MP3 ripping in SoundJuicer"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by becominglumberg on 2006-08-01
Even though I have installed Automatix, I cannot rip CDs directly to MP3s via Sound Juicer (it doesn't show the option). I would use ogg, but support for it isnt on my DAP.

Where should I look to fix this?

---

### Post by Metacarpal on 2006-08-01
Using SoundJuicer, I've never been able to get MP3 ripping working right.

I recommend using Grip.  If you don't already see Grip in your Applications > Sound & Video menu, here's how to install it:  Go to System > Administration > Synaptic Package Manager.  Search for Grip, then click the box next to it and select "Mark for Installation".  Then search for LAME, and mark it for installation as well. (If the box next to either is already dark gray, that means it's already installed.) Then click Apply, and Synaptic will download and install the packages.

Now, open Grip and click the Config tab.  Below it, more tabs will appear.  Click the Encode tab (should be right under the Config tab).  There is a drop-down menu marked "Encoder" - oggenc is the default.  Select Lame.

Now you'll be able to rip CDs to MP3.  Load a CD, open Grip, and select the tracks you want to rip.  Then click the Rip tab, click "Rip+Encode", and it'll take it from there.


**Edit:** if you want ID3 tags on your files (the data used by MP3 players and such to display band, album, and track information) you'll need to check that box on the ID3 tab under Config.

---

### Post by deadgobby on 2006-08-01
> **becominglumberg said:**
> Even though I have installed Automatix, I cannot rip CDs directly to MP3s via Sound Juicer (it doesn't show the option). I would use ogg, but support for it isnt on my DAP.

Where should I look to fix this?
 Ok that is going to take some editing to get the ripper to burn MP3's. I use grip to rip Cd to mp3's. There is a couple of thing you can do. Open the wav or ogg file in Audacity and convert the ogg to mp3. That can take time. Or you can config Grip to rip with. You will need to do some tweeking once you install grip from synaptic. Ok once you installed grip this should work. If not I will edit this later. You need to install lame as well too if not installed. Or you can do it easy and open up the terminal and install.

sudo apt-get install lame grip cdparanoia

Open up Grip
Go to the Confugure tab. The select Ripper tab
Select Ripper: to cdparanoia
( Copy and past the following )
The Ripping executable could be /usr/bin/cdparanoia
Rip command line: -d %c %t[.%b]-%t[.%e] %w
Rip File Format: ~/mp3/%A-%d/%t_%n.wav
  The next step is now go to the "encode" tab and select "encoder" tab. 
Here is some more copy and paste fun.
Encoder Excutable could be /usr/bin/lame
Encoder command-line: -V 2 --vbr-new --add-id3v2 --pad-id3v2 --ta "%a" --tt "%n" --tl "%d" --ty "%y" --tn "%t" %w %m
Encode File Extention: mp3
Encode file formate: ~/mp3/%A-%d/%t_%n.%x
  Now go and click on the "options" tab next to the "encoder" tab. 
Check on Delete .wav after encoding... You can keep iton, but you just are making a wav file along with the mp3 file.
Click on Create mpu files
Click on Use relative paths in mpu files
 now copy and paste in the "mpu file formate" ~/mp3/%A-%d.m3u
   You should be able to rip away on using grip. People may have all ready relply to you message. But at least you have a 2cd option. Please let me know if this works are not. I'll do my damn best to help There is some links to help you on your quest
[http://ubuntuforums.org/showthread.php?t=189140&highlight=ripping+mp3%27s](http://ubuntuforums.org/showthread.php?t=189140&highlight=ripping+mp3%27s)
[http://ubuntuforums.org/showthread.php?t=99115&highlight=ripping+mp3%27s](http://ubuntuforums.org/showthread.php?t=99115&highlight=ripping+mp3%27s)


Gobby

---

### Post by Uncle Spellbinder on 2006-08-01
> **Metacarpal said:**
> ...I recommend using Grip.

Thanks. I've been searching for something like this. I did not even know Grip existed. Works *flawlessly*. Thanks so much for the info. 

I LOVE this forum!  :D

---

### Post by deadgobby on 2006-08-01
> **Uncle Spellbinder said:**
> Thanks. I've been searching for something like this. I did not even know Grip existed. Works *flawlessly*. Thanks so much for the info. 

I LOVE this forum!  :D
Hell ya, I love using Grip and Love this forum too.

---

### Post by becominglumberg on 2006-08-02
Okay, I have tried grip, and it worked... I still prefer SoundJuicer (personal pref). Anybody know how to do it?

---

### Post by reclusivemonkey on 2006-08-03
> **becominglumberg said:**
> Okay, I have tried grip, and it worked... I still prefer SoundJuicer (personal pref). Anybody know how to do it?

As long as you can hear MP3s (meaning you have the mp3 codec working) all you need to do is;

In Sound Juicer, go to "Edit" --> "Preferences", then down by "Output Format" click on "Edit Profiles". Add a "New" profile with the following;

Profile Name: MP3
Profile Description: MPEG Layer 3
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
File Extension: mp3

and tick the active box. You should now be able to rip in MP3.

---

### Post by becominglumberg on 2006-08-03
Thanks, works like a charm!

---

### Post by reclusivemonkey on 2006-08-03
> **becominglumberg said:**
> Thanks, works like a charm!

No problem, glad you got it working. If I read your username correctly, you might also like this...

[http://www.phydiux.com/bill_lumbergh_soundboard.cfm](http://www.phydiux.com/bill_lumbergh_soundboard.cfm)

;)

---

### Post by BatteryCell on 2006-08-10
Hmm, I do all that but when I try to encode them they encode and everything but dont sound like music when I play them, lots of high pitched noises and such though.

---

### Post by reclusivemonkey on 2006-08-11
> **BatteryCell said:**
> Hmm, I do all that but when I try to encode them they encode and everything but dont sound like music when I play them, lots of high pitched noises and such though.

Not sure why that should be. Do mp3s play normally? Do you have all the requisite software installed?

---

### Post by chuckn on 2006-08-19
Thanks for the info on ripping with sound juicer. I followed all the instructions, and when I try to extract it just closes. Am i missing something.

Thanks,

Chuck

---

### Post by dislocated on 2006-08-24
> **reclusivemonkey said:**
> 
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux.
Not sure how a layman like myself would ever find out what pipeline parameters to use, but yours sure did the trick for me as well! Thanks!

---

### Post by nothi on 2006-08-24
I've posted in another thread, but it seems to be dead. I'll paste here it:

I have a problem with my Grip and Sound Juicer. the first one ripps my cds very slow, and quality is ok, but it cuts 4-5s from each file. What's the problem?

SJ ripps my cds faster, but files are broken, and they'r very big - 3 minutes = 22mb. What's wrong?

During configuring both of programs i followed all steps from this thread. There is olso one more problem with SJ. It starts olny once. I needto reboot my system to run SJ one more time.
Can you help me, please?

---

### Post by heikrnen on 2006-08-27
> **reclusivemonkey said:**
> 
Profile Name: MP3
Profile Description: MPEG Layer 3
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
File Extension: mp3


Thanks for the settings. I modified GStreamer Pipeline: > audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 xingheader ! id3v2mux
and got also ID tags correctly. I'am using Ubuntu Dapper.

---

### Post by reclusivemonkey on 2006-08-27
> **heikrnen said:**
> Thanks for the settings. I modified GStreamer pipeline and got also ID tags correctly. I'am using Ubuntu Dapper.

Thanks for sharing heinkren. :)

---

### Post by pstenman on 2006-09-04
I have tried to get to work both grip and SoundJuicer. Seems to be so that lame is missing from my installation. Also, I'm not able to find it from the standard Ubuntu repositories. Any help for beginner?

---

### Post by pstenman on 2006-09-04
I got it working when I added all possible package repositories that Synaptic proposed. Now both grip and SoundJuicer work fine.

---

### Post by Zmija on 2006-09-10
Can I have VBR mp3 rip? ex min: 128 avg: 192 max: 320 kbps ? :cool: 


THNX

---

### Post by Lemur on 2006-09-10
> **Metacarpal said:**
> Using SoundJuicer, I've never been able to get MP3 ripping working right.

I recommend using Grip.  If you don't already see Grip in your Applications > Sound & Video menu, here's how to install it:  Go to System > Administration > Synaptic Package Manager.  Search for Grip, then click the box next to it and select "Mark for Installation".  Then search for LAME, and mark it for installation as well. (If the box next to either is already dark gray, that means it's already installed.) Then click Apply, and Synaptic will download and install the packages.

Now, open Grip and click the Config tab.  Below it, more tabs will appear.  Click the Encode tab (should be right under the Config tab).  There is a drop-down menu marked "Encoder" - oggenc is the default.  Select Lame.

Now you'll be able to rip CDs to MP3.  Load a CD, open Grip, and select the tracks you want to rip.  Then click the Rip tab, click "Rip+Encode", and it'll take it from there.


**Edit:** if you want ID3 tags on your files (the data used by MP3 players and such to display band, album, and track information) you'll need to check that box on the ID3 tab under Config.

I've been looking for a solution for this problem.  Your suggestion worked really well.  Thanks!:D

---

### Post by cvmostert on 2006-09-11
> **pstenman said:**
> I have tried to get to work both grip and SoundJuicer. Seems to be so that lame is missing from my installation. Also, I'm not able to find it from the standard Ubuntu repositories. Any help for beginner?

ripping in ubuntu has always been slow for me... but as i am hooked to linux, i will suffer the cons. :-)

you need to refer to the ubuntuguide to get the repositories you should add to be able to install lame through synaptic or..

$ sudo apt-get install lame

take care,
C

---

### Post by reclusivemonkey on 2006-09-11
> **cvmostert said:**
> ripping in ubuntu has always been slow for me... but as i am hooked to linux, i will suffer the cons. :-)


I just ripped with SoundJuicer this morning at 10X... what sort of speeds are you getting?

---

### Post by 3rdalbum on 2006-09-11
Thanks for the tips regarding getting Sound Juicer to encode to MP3, but I'm already very very happy with Grip :-)

Grip is also good for if the CD Player and Sound Juicer won't play CDs in your drive. Plus, you get more control over encoding and ripping settings.

---

### Post by bubbjane on 2008-04-12
1.  open synaptic and search for gstreamer.  
2.  select all of the gstreamer codecs for installation.  
3.  After install, open soundjuicer 
4.  preferences will now have cd quality mp3 as one of the pull down options.  

:guitar:No need to create profiles or edit any source code.

---

### Post by BUSHYBOB on 2008-04-13
I've got CD Quality, MP3 profile and the active box is ticked, but it doesn't appear in the dropdown menu on the preferences. Can any one suggest a remedy?

---

