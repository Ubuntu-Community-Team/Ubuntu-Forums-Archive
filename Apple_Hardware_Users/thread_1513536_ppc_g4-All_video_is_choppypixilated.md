---
title: "ppc g4-All video is choppy/pixilated?"
date: 2010-06-19
forum: Apple Hardware Users
---

### Post by mwilkinson71 on 2010-06-19
I'm generally non-techy, but was able to do the install of Lucid on my iBookg4 ppc, and use terminal to cut/paste the fix for my airport extreme card off the ubuntu wiki. my current vexing problem is this: ALL video playback (mp4, .mov, swirly display thing when musicplayer is going, etc) is choppy looking. not pixilated, but kind of messily choppy & grated looking. I've searched all the forums & wikis ('natch) and cant find anything that describes this exact problem. is there a fix that dosen't involve confusing command line judo? something that wont require too much hand-holding? (I am def one of, "the rest of us" that ubuntu is for...) THX!

---

### Post by shawnhcorey on 2010-06-19
Does it look [something like this]("http://sites.google.com/site/shawnhcorey/Home/stuff/DSCN0349.JPG?attredirects=0")?  It appears as the odd & even columns of pixels are swapped.  If you look closely at the curves in the letters, it's as though thin strips were cut vertically and replaced with their mirror image.

I have the same problem and, no, I don't know how to fix it.  :( :confused: :(

---

### Post by mwilkinson71 on 2010-06-19
YES! thats exactly it.. looks like the image has gone thru a[SIZE=1] Ronco® Veg-O-Matic! so the problem seems clearly defined now... If only there were someplace on the internets where some sort of knowledgable unix pro could read this and possibly have an answer..;)
[/SIZE]

---

### Post by linuxopjemac on 2010-06-20
Can you guys test Debian? Debian has a multimedia repo with a lot of non free codecs.

[http://debian-multimedia.org/](http://debian-multimedia.org/)

---

### Post by oswaldkelso on 2010-06-20
Change the video out option. On my current g4 800mhz  machine I set my vo for mplayer to x11 (from xv). ymmv

---

### Post by shawnhcorey on 2010-06-20
> **linuxopjemac said:**
> Can you guys test Debian? Debian has a multimedia repo with a lot of non free codecs.

[http://debian-multimedia.org/](http://debian-multimedia.org/)

I don't think it has anything to do with the codecs.  The VLC player has the ability to take a screenshot and when I do, it renders it correctly.  I think it's using an internal engine for this, rather than the GPU.  So, I think the problem is in X Window but I have been able to track down why (yet).

---

### Post by mwilkinson71 on 2010-06-20
is the "video out option" something in Debien? (I also need to figure out what debien is too)

---

### Post by shawnhcorey on 2010-06-20
No, it's a preference in the media (or movie) player.

I tried changing it to X11 in VLC and it work for fullscreen and 2x but not for normal size.  I haven't tried mplayer yet.

[Debian]("http://www.debian.org/") is a [distro]("https://secure.wikimedia.org/wikipedia/en/wiki/Linux_distribution") of [Linux]("http://www.linux.org/").

---

### Post by mwilkinson71 on 2010-06-21
YES! this worked for me too using the VLC application. I couldn't find the settings in movieplayer.

---

### Post by mwilkinson71 on 2010-06-21
now all I need is some way to play flash, so I can do 85% of the things on the internets...

---

### Post by mwilkinson71 on 2010-06-21
now I love VLC, but I cant make it my default video player.

---

### Post by shawnhcorey on 2010-06-21
Default as in it doesn't start when you put a DVD in or as in when you double-click a video file?  For the first one, it's one of the system parameters you can set.  How you do so depends on whether you're running Ubuntu, Kubuntu, Xubuntu, etc.  It should be under System->Preferences, System->Administration, or Settings.

For the second one, right click on the file and choose Properties.  Under one of the tabs, it will say "Open with..."  Choose it and choose the option to open all files with the same extension with the same application.

---

