---
title: "video slideshow"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by Incite on 2008-03-15
I need to make a movie compiled of pictures and I have to have music and a voice recording play over the slideshow.
 
i have 3 different movie making software and i cant drop any pictures into them. Also i need a software that i can record my voice then use that recording in the movie.

So basically i need a way to make a slideshow with two audio tracks playing over it.

---

### Post by Incite on 2008-03-16
up

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-16
well do you wanna play the music and your voice at the same time?
if you don't then you could just uses a play list 
if you do ..... well i will look in to it and get back to you

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-16
Audacity looks like it should do this for you
sudo apt-get install audacity
i didn't get to play with it to much sound card trubles over here but it can defantly play to differant sound files at the same time

---

### Post by Incite on 2008-03-16
What im doing is making a video slideshow for a school project. my teacher assumed everybody had windows movie maker. So im SOL. I have to be able to record my voice and have music playing while my speech is going. and have both the music and the voice recording (which i dont know hoe to do) while the pictures go. And i have to sync the pics to what im saying.

---

### Post by skrimpy on 2008-04-04
Hi Incite,

i was looking for the same thing you are for a narrated slide show I'd like to do and I found this - it's called LiVES.  If you read this page under 'extras" it says it can load single images or entire albums.  And it says it can do audio.  [http://lives.sourceforge.net/index.php?do=features](http://lives.sourceforge.net/index.php?do=features)

I haven't tried it yet so I don't know how well it works.  It's not in the repositories so you have to download it from the site and install.  It's the only one I've seen that specifically says you can do the still images.

For recording sound I'm just going to use Sound Recorder that comes with Ubuntu and lay that track down over my images.

---

### Post by shane2peru on 2008-05-12
Do yourself a favor and install Digikam and kipi-plugins  those two will do exactly what you need. :)  They are the easiest.  Also, you can use Kino, however kino uses some serious disk space for it's files!  
If you want to use kino, here is a command line for dumping the pictures to a .dv file: 
> 
image2raw -a -r <enter digits for the number of times you wish it to repeat each image>*.jpeg > file.dv

eg. image2raw -a -r 25 *.jpeg > file.dv

If you had 20 files, this will give you raw video showing 20 images, each of one second long (25 frames per second for PAL).
  

I copied this from e2beees or someone of that name here in the forums from another thread (don't remember where) and jotted it down in my notes for future reference.  I have used this method and right now and trying the digikam method.  Of the two, I think I recommend the digikam method even if you are using Gnome!  Kino as I said before make very large files with the .dv extension, if you have the space to spare, you can take your pick. :)

Shane

---

### Post by mavi_yelkenler on 2008-05-23
> Do yourself a favor and install Digikam and kipi-plugins

thank you much Shane, I needed such an application

regards

---

### Post by shane2peru on 2008-05-23
> **mavi_yelkenler said:**
> thank you much Shane, I needed such an application

regards

No prob glad to be of help!  :popcorn:

Shane

---

