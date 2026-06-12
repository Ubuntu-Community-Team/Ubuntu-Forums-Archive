---
title: "[SOLVED] Best MP3 Ripper for Ubuntu?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-17
I did a Synaptic search and found many options as well as in this forum.  I am wondering what, in everyone's opinion, is the best app for ripping Audio & Music CDs into MP3 format.  This Sound Juicer guy doesn't seem to have an option to extract as MP3.  (Sound Juicer is the default app that comes up when I put a CD into the CDROM drive.)

I also see this Serpetine Audio Creator in my Apps Menu.  Haven't used it yet.

I like Winamp, but I always used to use Windows Media Player to RIP CDs simply because I liked the way it ripped.  Then I would play them in winamp or in VLC.  I was thinking that VLC would rip, cause I have it installed on Ubuntu, but I don't see where it will.

---

### Post by Razorback on 2007-04-17
If you install lame and other codecs you can make mp3s with sound juicer.  Hold a minute and I will post the link.

[http://ubuntuforums.org/showthread.php?p=1732341#post1732341](http://ubuntuforums.org/showthread.php?p=1732341#post1732341)

---

### Post by Razorback on 2007-04-17
Here is another link - I believe it is the one I used:

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by kc5hwb on 2007-04-17
Perfect, I'll try that.  Thanks.

---

### Post by kc5hwb on 2007-04-17
ok, this worked...however, the files are HUGE.  30-50MB each.  Kinda defeats the purpose of MP3.  I changed the bitrate from 196 to 96 and it didn't seem to make a difference.

This is the stream I am using...

```
audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux
```

---

### Post by ardchoille42 on 2007-04-17
An app to rip cd's to mp3?
```

sudo apt-get install grip lame

```

And if you want a nice gui mp3 tag editor
```

sudo apt-get install easytag

```

---

### Post by kc5hwb on 2007-04-17
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate
```

---

### Post by MetalMusicAddict on 2007-04-17
Give my HOW-TO a try. [Convert audio CDs with Grip and understand what you are doing.]("http://ubuntuforums.org/showthread.php?t=183125hp%3ft=25151")

---

### Post by joeblow1102 on 2007-04-17
> **ardchoille42 said:**
> An app to rip cd's to mp3?
```

sudo apt-get install grip lame

```

And if you want a nice gui mp3 tag editor
```

sudo apt-get install easytag

```

I recommend this setup too as this is my exact setup.  Follow MetalMusicAddict's like to the how-to.

---

### Post by kc5hwb on 2007-04-18
I got grip from the Add/Remove menu under Applications.  But the SUDO command for LAME didn't seem to work and when I try and encode with Grip, it tells me LAME isn't installed.

```
jason@SAMSON:~$ whereis lame
lame:
```

---

### Post by ardchoille42 on 2007-04-18
> **kc5hwb said:**
> I got grip from the Add/Remove menu under Applications.  But the SUDO command for LAME didn't seem to work and when I try and encode with Grip, it tells me LAME isn't installed.

```
jason@SAMSON:~$ whereis lame
lame:
```

lame is in the multiverse repo. Do you have multiverse repo enabled? If not, enable multiverse and try installing again.

---

### Post by Razorback on 2007-04-18
> **kc5hwb said:**
> ok, this worked...however, the files are HUGE.  30-50MB each.  Kinda defeats the purpose of MP3.  I changed the bitrate from 196 to 96 and it didn't seem to make a difference.

This is the stream I am using...

```
audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux
```

You will need lame.  Then replace "ugly" in the pipeline with "lame".  I converted a whole CD with 18 songs for 200 MB at 192.

---

### Post by stchman on 2007-04-19
> **kc5hwb said:**
> ok, this worked...however, the files are HUGE.  30-50MB each.  Kinda defeats the purpose of MP3.  I changed the bitrate from 196 to 96 and it didn't seem to make a difference.

This is the stream I am using...

```
audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux
```

That is because your gstreamer pipeline is incorrect.

Go to my website and lood at my procedure.  It works.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Gstreamer pipeline
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! xingmux ! id3v2mux

The .mp3 file will be around 5MB each.

---

### Post by kpkeerthi on 2007-04-19
> 
That is because your gstreamer pipeline is incorrect.

Go to my website and lood at my procedure. It works.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Gstreamer pipeline
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! xingmux ! id3v2mux



Is it VBR? CBR? What bit rate? What is the pipeline to rip at VBR? I couldn't find that in your website. Can you please tell me?

---

### Post by stchman on 2007-04-19
> **kpkeerthi said:**
> Is it VBR? CBR? What bit rate? What is the pipeline to rip at VBR? I couldn't find that in your website. Can you please tell me?

It uses the LAME encoder.  LAME decides the bit rate for you.  It analyzes the music and decides the best bitrate throughout the song.  Think of it as variable bit rate.

Thank you, I should update my page to tell people that the bitrate is variable.

---

### Post by shirilover on 2007-04-19
If you use the appropriate command line switches, you can determine the bitrate yourself.
```

-b 320 will encode at 320 kbps CBR
-V n uses variable bitrate. where 0 <= n <= 9. low values of n represent higher bitrate

```

More information on LAME can be found at [LAME - Hydrogenaudio Knowlegebase]("http://wiki.hydrogenaudio.org/index.php?title=LAME")

---

### Post by kpkeerthi on 2007-04-19
Thanks. My favorite is abcde.

---

### Post by kc5hwb on 2007-04-19
> **stchman said:**
> That is because your gstreamer pipeline is incorrect.

Go to my website and lood at my procedure.  It works.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Gstreamer pipeline
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! xingmux ! id3v2mux

The .mp3 file will be around 5MB each.


I just got that code from the first reply to my original post in this thread.


Honestly, I think I would rather use Sound Juicer anyway, it looks easier.  GRIP looks like it will do alot, but too many settings...I just wanna rip to MP3 at 96-128k bit rate.

I'll try that code on your site

---

### Post by stchman on 2007-04-20
> **kc5hwb said:**
> I just got that code from the first reply to my original post in this thread.


Honestly, I think I would rather use Sound Juicer anyway, it looks easier.  GRIP looks like it will do alot, but too many settings...I just wanna rip to MP3 at 96-128k bit rate.

I'll try that code on your site

In order to rip MP3s at a constant bit rate you will need to modify the Gstreamer pipeline.  This will result in poorer audio quality.  Let LAME do the VBR thing.  The files are still a manageable size.

---

### Post by andrew.46 on 2007-09-29
Hi,

 Have you tried abcde? I see others have suggested it, I wrote a guide a while ago:

[http://ubuntuforums.org/showthread.php?t=535950&highlight=howto+abcde+command+line](http://ubuntuforums.org/showthread.php?t=535950&highlight=howto+abcde+command+line)

              Andrew

---

### Post by n3tfury on 2007-09-29
hand down (although you have to use wine, but works perfectly) it's Exact Audio Copy.  see this thread.  NOTHING beats EAC.  take a trip to hydrogenaudio forums for proof of how configurable and accurate it is.  here's a link to a how-to under ubuntu"

[http://ubuntuforums.org/showthread.php?t=142784](http://ubuntuforums.org/showthread.php?t=142784)

---

### Post by koleoptero on 2007-10-12
I use Grip, it's the best of all linux cd rippers. I don't know about EAC but I didn't throw away windows to start using wine for everything I need. Grip worked fine with lame. It's superbly configurable and is very convenient when filling disk data by hand for custom disks. Plus lame prouces very good quality mp3s.
And sound juicer sux, they should throw it away and replace it with grip in the future.

---

### Post by kc5hwb on 2007-11-11
Sound Juicer with the proper stream configured is the easiest.

---

### Post by BradwJensen on 2007-11-12
I actually found I Love using 'k3b' to rip my CD's to Ogg Quality 8

I tried Sound Juicer but i hate its interface and all the tags come up with lowercase first letters very often..

In k3b the tags are usually a whole lot nicer, and i can quickly double click a song tag fix it and click enter to have it take me to the next song tag to fix..  Also i can tell it to rip my CD's to  /Artist/Album/Title.ogg for me :-)

I actually have this New CD that i got last year for Xmas that has no scratches but always skipped when played or ripped in iTunes or anything on Windows. BUT when i ripped it with k3b with the Paranoia setting turned on i got a perfect rip with NOT ONE skip!!

I'm rambling on... but i'm just saying, i really like that app, man.

---

### Post by david tutton on 2007-11-15
Use the Synaptic package manager: reload. then in Terminal use sudo apt-get install lame.

---

