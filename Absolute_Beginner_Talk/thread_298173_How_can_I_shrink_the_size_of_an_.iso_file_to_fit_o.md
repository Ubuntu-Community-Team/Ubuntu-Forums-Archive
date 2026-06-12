---
title: "How can I shrink the size of an .iso file to fit on a CD?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-11-12
Hello all!

I have an .iso file of size 1,1GB.

I would like to shrink it to size 650MB to fit on a CD-Rom.

What program can I use to shrink the size of the .iso?

Thanks.

P.S.> Please do not suggest me to write on a DVD - I do NOT have a DVD burner.

---

### Post by bodhi.zazen on 2006-11-12
> **dvarsam said:**
> Hello all!

I have an .iso file of size 1,1GB.

I would like to shrink it to size 650MB to fit on a CD-Rom.

What program can I use to shrink the size of the .iso?

Thanks.

P.S.> Please do not suggest me to write on a DVD - I do NOT have a DVD burner.

I do not think you can shrink it per se. You can remove stuff from it.

Mount the .iso and do what you will:
```
mkdir ~/ISO
mount -o loop -t iso9660 filename.iso ~/ISO
```

---

### Post by dvarsam on 2006-11-12
Dear "bodhi.zazen",

Thanks for your reply!

> 
I do not think you can shrink it per se. You can remove stuff from it.

Mount the .iso and do what you will:
```
mkdir ~/ISO
mount -o loop -t iso9660 filename.iso ~/ISO
```

Actually, the file is a Video File - similar to DVD, only smaller in size.

So, there is no way I can remove stuff from it...

I can only reduce its size...

How can I do that?

What program should I use?

Thanks.

---

### Post by bodhi.zazen on 2006-11-12
You will need to edit the video file, possibly break it into several sections.

I am mot sure, but you could try this: [LiVES](http://lives.sourceforge.net/)

Or this: [DVD Editing/Authoring/Burning with Linux](http://gecius.de/linux/dvd.html)

---

### Post by migla on 2006-11-12
If you don't want to be able to play the video-cd in your dvd-player, but only wish to store the .iso on the cd, then archive manager should be able to shrink it. (No?)

edit: on the other hand, video is usually allready very compressed, so this might not help at all

---

### Post by dvarsam on 2006-11-13
> **migla said:**
> If you don't want to be able to play the video-cd in your dvd-player, but only wish to store the .iso on the cd, then archive manager should be able to shrink it. (No?)

edit: on the other hand, video is usually already very compressed, so this might not help at all

I find it very convienient to be able to play the CD on a DVD player.
And therefore: I would like to retain that ability!

There is something I do not understand here:

> Isn't there a way to decrease the quality of the video automatically - e.g. to decrease the number of frames per second, or the quality of the picture?

How would somebody work if he was dealing with a DVD?
How would somebody decrease the size of the .iso if we were talking about a DVD Film Backup?

Maybe the same program could work also for my needs too!!!...?

Thanks.

---

### Post by sml on 2007-09-03
And your solution was ... ? .....

---

### Post by insane_alien on 2007-09-03
you could always go get a DVD writer(they'e cheap now and very useful). otherwise you're going to need multiple CD's.

---

### Post by jay4e on 2007-09-03
there are a lot of options for video format that will make it smaller.  h.264, xvid and the like.  however if you want to be able to play it in most dvd players you will have to use the video cd format and your only option will be to split the video into two parts.  video cd format can be shrunk some with settings but there is no way your going to cut it in half with out going with a much more efficient codec.

so either split it in two or invest in a dvd burner (you can get em for 25-30 bucks on newegg)

---

### Post by southernman on 2007-09-03
You'll need to use a tool called (or similar to) memcoder. I've cut dvd movies (read as 4.7GB files) down to fit on one cd (695-705mb is usually my target range) with VERY little loss of quality in the audio or video of the movie. It takes a lot of trial and error to keep the quality there... you've been warned! ;)

The only thing, it took me many days of reading various wiki's, lots of processor hours, and more hair loss than I could stand.

[http://www.mplayerhq.hu/DOCS/tech/encoding-tips.txt]("http://www.mplayerhq.hu/DOCS/tech/encoding-tips.txt")
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide")
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html")
There are a few guides to get you going...

---

### Post by Duck2006 on 2007-09-03
DVD shrink mite be what your looking for

---

