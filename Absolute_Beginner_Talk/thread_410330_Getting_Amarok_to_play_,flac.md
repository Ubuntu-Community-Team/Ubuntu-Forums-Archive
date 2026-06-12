---
title: "Getting Amarok to play ,flac"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2007-04-15
I used automatix to install all the multimedia codecs.  My default player will recognize and play a flac but amarok will not.  How can I enable amarok to play flacs?

---

### Post by Happy_Man on 2007-04-15
Well, a flac file is the same as an mp3, so just go and rename all of them to .mp3 extension and you're good!

---

### Post by tdrusk on 2007-04-15
> **Happy_Man said:**
> Well, a flac file is the same as an mp3, so just go and rename all of them to .mp3 extension and you're good!

I don't think this is correct. MP3 is different than flac.

---

### Post by Happy_Man on 2007-04-15
Well, when I go and experimentally rename one of my .flac files, it works perfectly.

---

### Post by christhemonkey on 2007-04-15
> Well, a flac file is the same as an mp3, so just go and rename all of them to .mp3 extension and you're good!
That is complete rubbish i hate to say... Flac being lossless and Mp3 being lossy being just the start of the differences.
Maybe the music playing program recognises the flac files by mime type and not extension?
This is a possibility.

**@dreadh3ad** amarok uses the xine output engine, maybe try installing libxine-extracodecs?
Allso try running amarok from a terminal and see if there is any nice helpful output!

---

### Post by qamelian on 2007-04-15
> **Happy_Man said:**
> Well, a flac file is the same as an mp3, so just go and rename all of them to .mp3 extension and you're good!
Not even close! flac and mp3 share nothing in common except that they are compressed audio data. The flac codec allows you to reduce the size of stored audio data without losing any quality..hence **F**ree **L**ossless **A**udio **C**odec. The mp3 codec allows you much greater compression but it does so by reducing the quality of the audio. You can just change the filename becasue they aren't interchangeable.

---

### Post by qamelian on 2007-04-15
> **Happy_Man said:**
> Well, when I go and experimentally rename one of my .flac files, it works perfectly.

That just means you have both codecs installed. Well written Linux/Unix software doesn't use or care about file extensions. It uses the header information in the file to determine its type. Sos you changed the extension in the filename, but linux was smart enough to know better. Can't fool the Penguin!

---

### Post by n3tfury on 2007-04-15
> **fuzzyhair said:**
> MP3 is different than flac.

absolutely correct.

---

### Post by Apollo17 on 2007-04-15
Hello,

I'm a very new newbie - only been running Ubuntu 6.10 Edgy for about a month now, but I did find this at the Amarok website - maybe it will help.

The help at Amarok's web site said to:

sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs

Also, another help message at their site regarding playing .flac files reads:

---------------------------------------------
 Sakumatti Luukkonen said on 2007-04-11:

You need to install libxine-extracodecs.
 PaulE said on 2007-04-12:

Thanks for the response!

The multiverse repository was selected, but when I searched for libxine-extracodecs it did not appear.I then searched for and found a page that put me on the trail of the libxine-extracodecs ([http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs).) I downloaded and installed (dpkg --install libxine-extracodecs_1.1.1+ubuntu1-2_i386.deb) the codecs, started Amarok, attempted to play a flac file and received the same error message.

I have the following libraries loaded:
libxine-extracodecs, libxine-main1, libxine1 and libxinerama1.

If there is any other information I can offer, please let me know.
Best  PaulE said on 2007-04-12:

I did a little more and closer looking and found that I downloaded and installed the wrong version. I installed the correct version and it works.

THANKS again for your help. It got me to the solution!
-----------------------------------------------------------

I must have installed all necessary codecs before - probably when I was working with gxine - because Amarok plays .flac files for me, however, for some strange reason, they are very low in volume during playback. Not sure what is up with that. In Windows I use a program called WinAmp with a flac plug in to play flac files. I also tried to play the .flac file (a Decemberist live show song from etree.org as a test) in Rhythmbox Music Player and it played fine, but once again, at a very low volume, even with the system volume and the application volume controls full up.

Yeah, the FLAC codec is quite different than lossy mp3...that's why it is great for archiving lots of live shows, and with it being FREE Lossless Audio Codec, we don't have to pay needless licensing fees thanks to all the great folks that developed it.

Good luck,

Ross

---

### Post by Apollo17 on 2007-04-15
Hello again,

Just a quick note to say that MPlayer (my default player) plays the .flac file I mentioned at a good, much louder volume than Amarok or Rhythmbox does. Not sure why that is...strange.

I can't wait to try out Feisty Fawn - it is supposed to get most all the codecs you need automatically, so perhaps  issues like these will be a thing of the past. If so, I can see Ubuntu becoming ready for prime time with the masses out there. We'll see. 

After Microsoft strong armed PC suppliers like Dell and HP into not selling XP after December, I can see how many people will be looking for an alternative. I'm not "anti" Microsoft, it's just that after reading many trade magazines reports on Vista such as PC World, Info World, and others I've found that to really run Vista effectively you need a new, top of the line PC (i.e one more approaching $1500 or more USD). I'm not sure many businesses or even individual consumers are willing to throw away a perfectly good computer just to be able to run an new operating system, even with all the "eye-candy" and benefits that Vista offers. So, it might be a good time for all of us using Ubuntu to start making noise. 

Where I work, if it were not for about 30 seats needing to run AutoCAD, I'm sure the majority of our 100 PC users could do very well with Ubuntu alone.

Good luck, and if anyone comes up with why the volume of the .flac files is so different in the different programs please post your analysis or solution.

Thanks,

Ross

---

### Post by dreadh3ad on 2007-04-15
Thank you everyone for your support, you are making the switch from XP to ubuntu a lot less painful.  

As suggested I went to make sure i had the extracodecs:
whoracle@TOOL:~$ sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-plugins-ugly is already the newest version.
libxine-extracodecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I attempted to play the flac in amarok:

This is the error message i get when i attempt to play a flac:
Error Loading Media
There is no audio channel!
file:///media/mount/storage/Music/Rage Against The Machine/The Battle Of Los Angeles/04 - Mic Check.flac

Thoughts?

---

### Post by Apollo17 on 2007-04-15
Hey there dreadh3ad,

In doing a Google search for your error message I found this link:

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/56475](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/56475)

You may want to read it. Unfortunately, I never asked which version of Ubuntu or Amarok you were running.

As you can read, this is a "known bug" that hasn't yet been squashed - at least as of August 2006. Perhaps some of the more knowledgeable people on the forum here can offer other solutions. 

I'm running Edgy and like I said, my Amarok will play the .flac files, but at a very lower volume level than MPlayer does. For a work around, you may have to convert the flac files to .wav files. I know that takes up hard drive space, but it might be the only solution at the moment.

Sorry you are having problems. Perhaps you should give Rhythmbox a try.

Good luck,

Ross

---

