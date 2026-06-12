---
title: "Sound Juicer Problems"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by jcr1 on 2008-03-21
Hello all,

This is my first post here so HI! This is my first time using linux, been on it now for about a week and so far I am loving it.

Been following all the tutorials for getting sound juicer to rip mp3, but I just cannot get it to work.

In my profiles, there was already a profile for CD Lossy, MP3, but I created another one anyway in the way described in the tutorials. 

Even when the MP3 profile format is selected, the track extracts to a .flac format. Even if I have unchecked flac as being active, it always goes to flac!

Very frustrating, and now no formats are available from the list, even though my 2 mp3 ones are checked as active.

Have installed many gstreamer plugins and have lost track a bit of what i have and havent tried.

Hope someone can help clear this up!

Cheers!

Jon

---

### Post by markharding557 on 2008-03-21
you could install ubuntu restricted extras and lame encoder

---

### Post by laidback on 2008-03-21
This is the Gstreamer pipeline I have in my Sound Juicer...it rips to mp3. Copy the line and paste might be best. 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

And by the way...welcome.

---

### Post by jcr1 on 2008-03-21
Nope to both I think. I have followed instructions and it don't work. The weird bit is that the mp3 profiles do not show up in the list of available output formats in preferences, even though they are the only two set as active.

Just rips as flac with no format selected...

---

### Post by laidback on 2008-03-22
What version of Ubuntu are you running?

---

### Post by jcr1 on 2008-03-22
Gutsy Gibbon (not sure what that means) 7.10

---

### Post by GrokIt on 2008-03-22
I've got the same type of problem.  The only formats available to rip are flac, ogg, wav & spx.  I have mp3 & acc available when I edit the profiles but they both never show up in the drop down list.  When I unclick available on the ogg & flac profiles they still show in the drop down list.  Very confusing.  I used this on another pc and it worked just fine.  I'm running ver 2.20.1 on gutsy.  I am guessing that sound juicer keeps this list in a config file somewhere but where would I look to find it?

---

### Post by laidback on 2008-03-22
I have 7.10 running and my notes indicate that I simply added the Multiverse repository and Codecs via Synaptic to get Sound Juicer working with mp3s, also worked for Amarok. For 7.04 the process was somewhat more elaborate but still worked first time. I'm lost as to what your problem could be. Sorry.

---

### Post by jcr1 on 2008-03-22
OK well thanks anyway.

Is there a way to remove all the plugins i may have tried to do with this in order to start from fresh again?

---

### Post by laidback on 2008-03-23
Could try a Search in Synaptic for Plugins. The ones you have installed are identified, so you uninstall them too.

---

### Post by jcr1 on 2008-03-23
Well I am at a loss...

What other alternatives are there seeing as juicer won't work for me?

---

### Post by Auslegung on 2008-03-25
I recently did a fresh install of Gutsy and forgot what I had gone through to tweak my Sound Juicer.  However, I found this time that all I had to do was install those multiverse packages mentioned on the previous page, restart Sound Juicer, and make the mp3 profile active.  If that doesn't work, restart Sound Juicer again.  If that doesn't work, make your own profile with this as the pipeline:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

and again restart Sound Juicer.  

I'm having a totally different problem where Sound Juicer will rip the first song and part of the second, and just freeze.  I'm beginning to think, however, that the problem lies in the CD and not the program.  Ah well.

---

### Post by laidback on 2008-03-29
jcr1,
You might like to try Linux Mint (an Ubuntu derivative) as I believe it comes with codecs (mp3) preinstalled.

Laidback

---

### Post by GrokIt on 2008-04-01
Problem solved!
I did not look too hard at what exact packages were installed.  I did have soundconverter 0.9.6-1 installed and I thought that I had other lame packages installed.  That is my guess as to why I could see and make an mp3 profile but not have it be able to actually burn this file type!  
I found a readme file in /usr/share/doc/sound-juicer which said "To encode to MP3 you need the GStreamer Lame plugin.  Most distributions don't ship this...".  So I searched in synaptic for 'GStreamer Lame' and found that 'ubuntu-restricted-extras 10' was not installed.  For good measure I installed 'libgstreamer-perl 0.09-1' too.
When I restarted sound juicer, every type was available to burn and I made a good copy of Queen's News of the World !  Next up, Metalica.

---

### Post by Crafty Kisses on 2008-04-01
> **laidback said:**
> jcr1,
You might like to try Linux Mint (an Ubuntu derivative) as I believe it comes with codecs (mp3) preinstalled.

Laidback

Yeah, it does.

---

