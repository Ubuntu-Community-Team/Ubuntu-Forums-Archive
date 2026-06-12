---
title: "Splitting/Joining mpeg-2 Video"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by diogenes_3 on 2006-07-11
Hiall,

I seem to be running into a brick wall ](*,) while trying to solve a seemingly simple task. I have a machine with a DVB-T card (no, it's not the Ubuntu machine, it's XP...) which I use to tape episodes of some kids' programme for showing it to my lil' ones later. The output is .mpg files, mpeg-2 as I understand. The automatic recording (EPG) always gets the beginnings and ends wrong.

So I have a number of .mpg files on which I want to crop (split) the beginnings or ends, and some I want to join, because the beginning of one show is on the end of the other file. I don't want another file format, or file size. As far as I am concerned, I don't even need to transcode the things (the Ubuntu thingy is not *that* fast), but if that's just the way mpeg works, OK...

It should be a simple task, but I fail to find the proper tool for it. I have tried various gadgets, on either OS, but none did the job properly.

---

### Post by mister_p_1998 on 2006-07-11
Try Project-X that works Im using it now, you'll need Java installing first though.
Steve

---

### Post by xrchris on 2006-07-11
Have you tried Womble MPEG-VCR v3.14 it is a windows program which i have used to stitch files together with in the past. 

[http://www.afterdawn.com/guides/archive/womble_mpeg_join_tutorial.cfm](http://www.afterdawn.com/guides/archive/womble_mpeg_join_tutorial.cfm)

---

### Post by mazirian on 2006-07-11
You may avidemux suits your needs.  It is in the plf repo.

---

### Post by diogenes_3 on 2006-07-11
@xrchris,
I'm almost ashamed to say, wow, thanks, this one did it greatly! But - it's a closed-source Windows application... they'll kill us both around here... Plus it'll be 50$ in 30 days.

@mazirian,
thanks, I've read a lot about avidemux, but so far couldn't get it to run, I'll keep trying though, I guess it's worth it.

---

### Post by keith whitehouse on 2006-07-11
hi diogenes_3,

go back onto your windows drive and install PojectX and also java to run it. Then install Mpeg2scnitt and finally Remuxer. All of these programs are free.

Run the files through ProjectX, and this will make a single output file that has been split into video and audio. The reason that you run ProjectX is to make sure that you get no lip-sync problems.

Open Mpeg2scnitt and open the video file, this will also open the audio file as well. Edit out the bits that you do not want and save the rest as seperate episodes.

Open Remuxer and click the episodes, and remux. That will put the audio and video back together again and give you the various episodes to keep, still in the mpeg format.

Then use a burner of your choice and put them on dvd's for the kids

best regards keith

---

### Post by xrchris on 2006-07-11
> **diogenes_3 said:**
> @xrchris,
I'm almost ashamed to say, wow, thanks, this one did it greatly! But - it's a closed-source Windows application... they'll kill us both around here... Plus it'll be 50$ in 30 days.
. 

HA HA yes - sometimes i have to revert back for the odd program for which i do not know of an alternative. It is a damned good program though. If there is an ubuntu version that works as well as this then i would like to know. 

I dont mind dual booting as i see it as getting the best of both worlds until something better comes along in ubuntu. 

By the way the AfterDawn website/forum is one of the best if you want to know about dvd/mpeg/avi (etc etc) encoding.

---

### Post by aysiu on 2006-07-11
How about *mpgtx*? It's in the repositories.

---

### Post by mazirian on 2006-07-12
Give the native linux solutions a try first.  Avidemux2 is a fine application I have used for this very purpose on several occasions in th epast.  Admittedly, I have never used the ubuntu packages, so I am not sure how well they work, but it should be very doable.  You will probably need to have the whole array of non-free codecs in place.  

You might also try Kino and its related plugins (sudo aptitude install kino kinoplus kino-timfx kino-dvtitler).  Again, you'll need the non-free community and plf repositories set up in your sources.list.  I understand Kino can do the same thing and is more sophisticated than Avidemux (although I have never used it).  There are instructions for installing Kino at ubuntuguide.org and probably elsewhere on the forums. 

There is also Cinelerra (or something similar sounding to that). I don't know anything about that project, but I understandit is in development.

If you have troubles installing or using any of those, post back in the forums here, or in the forums of the respective projects.  The guy who runs avidemux answered my annoying email questions very promptly.  You won't get that kind of community assistance with a windows app I bet.

---

### Post by chinaski on 2006-10-02
> **aysiu said:**
> How about *mpgtx*? It's in the repositories.

it's great, thank you ;)

---

