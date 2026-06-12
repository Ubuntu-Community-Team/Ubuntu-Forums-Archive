---
title: "dvd authoring .. can't quite make up my mind .."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-08-20
i've got an AVI file, encoded (i think) in XViD, and what I basically want to do is to do nothing more than to add some chapters and burn it in DVD format so I can watch it on my DVD Recorder. 

I don't want any menus or anything like that, just the film, with chapters, on a disc.

In Nero on Windows, I could do just that - create your own dvd video, chapter it up and burn away.

So ideally, i'd need the equivalent in Linux.

I've looked at tovid, and qdvdauthor but can't quite make up my mind which is the best one - I don't ideally want to fanny around with command line stuff, but if I have to, i guess i'll have to.

has anyone had any experience in basic authoring such as this ?.  If so, what's been the easiest method you've found ?

it's not something I do all that often, but it would be useful to know.  Thanks.

---

### Post by vanadium on 2007-08-20
DeVeDe is a graphical app specifically designed to convert AVI video to video-dvd in one step. You probably should look at it first.
With Qdvdauthor, you can authoring existing DVD-compliant video to DVD. However, your video needs to be converted to DVD compliant mpg first. The latter can be achieved using Avidemux. Besides these graphical tools, there are many command line possibilities to do this.

---

### Post by Amazona aestiva on 2007-08-20
See this thread:
[http://ubuntuforums.org/showthread.php?t=529759]("http://ubuntuforums.org/showthread.php?t=529759")

---

### Post by jasonwatkins on 2007-08-20
> **vanadium said:**
> However, your video needs to be converted to DVD compliant mpg first. 

I actually wonder if this is what is causing the glitch that I have with the DVD.

I downloaded and installed DeVeDe and it worked like a dream - did exactly what I want, how I want, but I was left with a picture like this ..

[IMG]http://i79.photobucket.com/albums/j145/jasonwatkins/screenie.png[/IMG]

If you look, you can see visible lines running down the screen, and if it's a black screen, there's also a noticeable flickering green line at the bottom of the picture.

But i'm going to convert it to MPEG format and see if that makes a difference.

Just wondering - can DeVeDe be installed through the package manager ??.

I'd ideally like it set up properly so I can access it through the desktop if possible.  Cheers.

---

### Post by gn2 on 2007-08-20
I used to get lines like that with DVD's on PCLinuxOS. 
Cured it by using VLC for playback.
.
Have you got all the extra codecs/libdvdcss2 installed?
.
Devede is in the repos and available through Synaptic.

---

### Post by jasonwatkins on 2007-08-20
> **gn2 said:**
> I used to get lines like that with DVD's on PCLinuxOS. 
Cured it by using VLC for playback.
.
Have you got all the extra codecs/libdvdcss2 installed?
.
Devede is in the repos and available through Synaptic.

i think i have all the codecs - but i'm not interested in playing it back on my PC - I want it on a disc I can play on my TV.

I'm nearly finished converting the file to MPEG so i'll give that a whirl.

---

### Post by jasonwatkins on 2007-08-20
well my first attempt at mpeg conversion was a bit .. um .. wrong :)

anyway, i've just tried again and converted the first 3 minutes of the film in avidemux, using the DVD(mpeg2enc) video setting - with nothing altered I might add - and the audio setting of AC3(lavc) and I just increased the bitrate to 192.

I chose the format of "MPEG-PS(A+V)" - assuming "A+V" means Audio + Video .. durrrr 

anyway, the 3 minute file played fine with no glitches or lines or anything like that, so i'm running the whole thing through now.

according to avidemux, it'll be done in 2 and a half hours .. :(

Thought it would be quicker considering i've got 1GB of RAM.  Oh well .. i'll report back with the result ..

---

### Post by jasonwatkins on 2007-08-20
Outstanding! Worked like a charm.

Took a screen grab directly from the DVD that i'd burnt - I played it in SMPlayer and just used the 'take screenshot' program.  It's about 5 seconds after the original screenie I took, but the comparison is there to see.

[IMG]http://i79.photobucket.com/albums/j145/jasonwatkins/screenie2.png[/IMG]

And the auto chaptering was spot on as well.  All in all, very happy.  At least I now know what to do in the future as well.

If the mods want to mark this as "solved" then that's cool - maybe someone else will find the settings I used for avidemux useful.

---

