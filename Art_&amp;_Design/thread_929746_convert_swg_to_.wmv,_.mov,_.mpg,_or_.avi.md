---
title: "convert swg to .wmv, .mov, .mpg, or .avi"
date: 2008-09-25
forum: Art &amp; Design
---

### Post by lyceum on 2008-09-25
I am using Flash 8 via Wine-Doors to make videos, now I want to put them on YouTube. Does anyone know of a good way to do this on Ubuntu?

---

### Post by lyceum on 2008-09-26
Okay... does anyone know of a good way I can start over and make a video for YouTube from scratch? I am very new at this.

---

### Post by SuperSonic4 on 2008-09-26
FFMpeg is considered to be a good program to use to transcode video.

I'm not sure what you mean, do youmean full on video editing like Windows Movie Maker?

---

### Post by lyceum on 2008-09-26
I am an idiot! I tried to export it and realized there are options to save as .mov for quicktime in flash :)

I would still like to know the best way to make movies for YouTube on Ubuntu though if anyone knows.

---

### Post by lyceum on 2008-09-26
> **SuperSonic4 said:**
> FFMpeg is considered to be a good program to use to transcode video.

I'm not sure what you mean, do youmean full on video editing like Windows Movie Maker?

To be honest I do not know what I mean, I have never done this before and do not know where to start. Here is a list of what I want to do:

1. make animated videos 
2. make videos with my web cam
3. make videos with a very expensive camera a guy is loaning to me and edit them. I have a green screen and want to do some cool stuff.

I may need to learn a few new programs, but wanted to see if anyone recommended anything. I have never done any of this before. I work for an economic news (blog) website as the web designer, now my boss wants me to make news videos and animation. I can get him to buy Windows or Mac programs, but I would rather use as much FOSS as I can. I only use Flash as it is the best way to make Flash videos. I make one and now I get to be a producer :|

---

### Post by lyceum on 2008-09-28
Does anyone here do anything with movies of any kind? (other than watch them)

---

### Post by lyceum on 2008-09-28
So far I have found that DVDStyler is great for taking your finished product and making a DVD. You can make a menu and time line, but you cannot edit.

---

### Post by justsomedude on 2008-09-28
You might want to check out Blender, which comes with a very powerful video sequence editor (among many, many, many other things):

[http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing)

Be prepared to spend a lot of time learning Blender, it's worth it though. :)

---

### Post by lyceum on 2008-09-29
> **justsomedude said:**
> You might want to check out Blender, which comes with a very powerful video sequence editor (among many, many, many other things):

[http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing)

Be prepared to spend a lot of time learning Blender, it's worth it though. :)

I have already started learning Blender. I would to use a camcorder though for this, Blender, as far as I know, does not work with camcorders. Thanks though :)

---

### Post by lyceum on 2008-09-29
Okay, new news on my plight: the stuff I am going to make for YouTube will also be going on a local cable TV network. If this getting too professional for FOSS? I am hoping not.

---

### Post by forger on 2008-09-29
Please stop bumping, at least give it a day's rest..
> 
$ apt-cache show ubuntustudio-video
[...]
Description: Ubuntu Studio video Package
 Ubuntu Studio is a multimedia creation flavor of Ubuntu for the
 Linux audio, video, and graphic enthusiast or professional.
 .
 A collection of applications aimed at video creation and editing.

$ apt-cache depends ubuntustudio-video
ubuntustudio-video
  Depends: dvgrab
  Depends: ffmpeg
  Depends: ffmpeg2theora
  Depends: kino
  Depends: openmovieeditor
  Depends: stopmotion



To install ubuntustudio-video related software for video, head to menu Applications > Accessories > Terminal and execute:
```
sudo apt-get install ubuntustudio-video ubuntustudio-audio-plugins ubuntustudio-audio
```

Type in your password and press Enter.
It will install several application for video and audio management/creation/edit

---

### Post by lyceum on 2008-09-30
> **forger said:**
> Please stop bumping, at least give it a day's rest..


To install ubuntustudio-video related software for video, head to menu Applications > Accessories > Terminal and execute:
```
sudo apt-get install ubuntustudio-video ubuntustudio-audio-plugins ubuntustudio-audio
```

Type in your password and press Enter.
It will install several application for video and audio management/creation/edit

Sorry, didn't mean to bump, just taking notes, it looks like there are not too many people using FOSS video software. I know how to load programs, I am looking for recommendations. As I start using software, I am going to note here how well it works so if someone else looks on the forums they will find some info.

---

