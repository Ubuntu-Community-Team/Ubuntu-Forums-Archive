---
title: "I'm caving [mp3 help]"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by skeem on 2006-05-16
Hey, so I'm totally new to Ubuntu and Linux in general. I'm used to windows xp, but I'm over that platform. I like the way Ubuntu is. All day I've been trying to figure out how to play mp3's. I've checked the forum.

What I need because I am so new to this is a full on barebones tutorial. from beginning to end of how to get mp3's to play on this computer. Like, as if it were being said to a first grader, or something. Sometimes, I just don't get stuff. haha.

I am using the 5.10 ubuntu. I just got it today.
I'm hoping to understand this, because I really want to know everything about this and not just give up on it out of frustration!

-Kate

---

### Post by Sutekh on 2006-05-16
This is the only place I would send you

[[URL="https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970"]Ubuntu Wiki - Restricted Formats - MP3]("https://wiki.ubuntu.com/RestrictedFormats")
[/URL]

---

### Post by aysiu on 2006-05-16
A few things you should know, since you're new to Linux, too, not just Ubuntu:

1. Not all Linux distributions leave out MP3 formats. Ubuntu is committed to free software--not just cost-free software but non-proprietary software as well. MP3 is a proprietary format, so Ubuntu does not include it by default.

Other Linux distributions like PCLinuxOS, Mepis, Blag, and Linspire include MP3 playback and a lot of other proprietary codecs by default.

2. Both codecs and regular software programs are available in online "repositories." If you enable the proper repositories, you can get almost anything you need... including MP3 playback.

3. The easiest way to give instructions is through commands. Those are not as scary as they seem, especially since you can just highlight them (yes, even a first-grader could do this), copy and paste them into the terminal. No typing needed. No memorization needed.

4. There is a graphical way to do this as well.

[Here are the command-line instructions for getting MP3 playback](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

[Here's a graphical tutorial on how to enable the extra online repositories and install codecs and software from them](http://www.monkeyblog.org/ubuntu/installing.html)

There's also a script called [Automatix](http://www.ubuntuforums.org/showthread.php?t=138405), which will make it really easy to install a lot of popular software and proprietary codecs with the check of a few boxes.

Ask questions if you're confused.

For further reading on Ubuntu in general, go here:
[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

---

### Post by skeem on 2006-05-16
[QUOTE=aysiu]A few things you should know, since you're new to Linux, too, not just Ubuntu:

1. Not all Linux distributions leave out MP3 formats. Ubuntu is committed to free software--not just cost-free software but non-proprietary software as well. MP3 is a proprietary format, so Ubuntu does not include it by default.

Other Linux distributions like PCLinuxOS, Mepis, Blag, and Linspire include MP3 playback and a lot of other proprietary codecs by default.

2. Both codecs and regular software programs are available in online "repositories." If you enable the proper repositories, you can get almost anything you need... including MP3 playback.

3. The easiest way to give instructions is through commands. Those are not as scary as they seem, especially since you can just highlight them (yes, even a first-grader could do this), copy and paste them into the terminal. No typing needed. No memorization needed.

4. There is a graphical way to do this as well.

[Here are the command-line instructions for getting MP3 playback](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

[Here's a graphical tutorial on how to enable the extra online repositories and install codecs and software from them](http://www.monkeyblog.org/ubuntu/installing.html)

There's also a script called [Automatix](http://www.ubuntuforums.org/showthread.php?t=138405), which will make it really easy to install a lot of popular software and proprietary codecs with the check of a few boxes.

Ask questions if you're confused.

For further reading on Ubuntu in general, go here:
[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)[/QUOTE]


It's incredibly simple. I know I'm making it into a bigger issue than it is. I just keep getting "Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kate@ubuntuKate:~$ sudo apt-get install  gstreamer0.8-plugins gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg"

and i don't know what to do about that.

---

### Post by aysiu on 2006-05-16
That error usually occurs when you're trying to use *apt-get* or *dpkg* from the command-line, but you also have Synaptic Package Manager or Adept already open.

---

### Post by skeem on 2006-05-16
[QUOTE=aysiu]That error usually occurs when you're trying to use *apt-get* or *dpkg* from the command-line, but you also have Synaptic Package Manager or Adept already open.[/QUOTE]
I have that closed now and am setting up automatix. it's...been doing that for a bit. sitting at setting up automatix. okay  now i'm installing a lot of stuff through automatix.

i hope this works, because i like music. haha.

---

### Post by skeem on 2006-05-16
[QUOTE=aysiu]That error usually occurs when you're trying to use *apt-get* or *dpkg* from the command-line, but you also have Synaptic Package Manager or Adept already open.[/QUOTE]
I have that closed now and am setting up automatix. it's...been doing that for a bit. sitting at setting up automatix. okay  now i'm installing a lot of stuff through automatix.

i hope this works, because i like music.

---

### Post by Guns90 on 2006-05-16
Hey Skeem.  I dumped M$ and did a straight Ubuntu load three weeks ago.  I don't know jack about computers, but I do know that I really want to get away from all the money I was spending and all the systems crashes I was having.  

I MUST HAVE music and it MUST be in MP3 format for my player.  I have it now in Ubuntu!  I agree with Sutekh, the WIKI gives you what you need.  Just do exactly what it says and it will work.  Make sure you enable the multiverse and universe repositories first.  

If you don't know how to download and install a package, tell me and I'll walk you through it.  It's not hard.  Once you get the packages downloaded, you install them, and your done!  I've been spending the last four hours ripping my CD collection with Sound Juicer.  My MP3 player is recognized as a USB removeable drive.  I'm a happy camper.  Hang in there.

---

### Post by diego898 on 2006-05-16
I've used automatix, and filled in the gaps with the tutorials above. And yet, the sound quality is not that good at all...the BASS is all fuzzy, and on Windows its all so much better (sound quality wise). What can I do to fix this?

---

### Post by Guns90 on 2006-05-17
Hey Diego, I'm too new to Ubuntu to answer that, but I had a lot of trouble in general after I loaded Automatix. (It was probably because I didn't do it right.) Any way, I decided that I'm going to try and run everything strictly in Linux.  I am ripping into MP3 format with Sound Juicer and organizing my music with Rhythmbox, and I'm getting great reproduction.  It helps if your MP3 player (Creative Zen Nano Plus) is recognized as a USB detachable drive.  Just my words of encouragement.  Hang in there.  I promise it gets easier.

---

### Post by TeeAhr1 on 2006-05-17
(Just a suggestion)

Don't rip CDs to mp3 unless you really have to (mp3 players that don't read other formats, for example).  FLAC is just a way better option, you retain far more sound quality.

---

### Post by Lord Illidan on 2006-05-17
[quote=diego898]I've used automatix, and filled in the gaps with the tutorials above. And yet, the sound quality is not that good at all...the BASS is all fuzzy, and on Windows its all so much better (sound quality wise). What can I do to fix this?[/quote]

Type in alsamixer at the terminal.

Set master to 100%, PCM and WAVE anywhere from 80 to 75%.

Press q to exit.

Then type:

sudo alsactl store

and you're done.

---

### Post by skeem on 2006-05-17
Hey, everyone. I just wanted to tell you all that I figured it all out with automatix. Thanks for all your advice. It took a while, but I'm set.

-Kate

---

