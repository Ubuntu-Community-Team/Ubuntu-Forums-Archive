---
title: "DVD creation - AVI file woes!"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by zachthejones on 2007-12-26
I'm trying to make a DVD from some AVI files I edited on Adobe Premiere as well as Windows Movie Maker (I couldn't get Kino to detect my DV Camera - some sort of IEE1394 error which no one can figure out...).

Anyways, I've tried using Avidemux to convert these to MPEG file types - I spent an entire evening doing so. But when I tried to created the DVD via QDVDauthor, it spent **11 hours** re-encoding the mpeg videos (yeah, I did get a little over-zealous - I had almost 3 hours of video...). I ended up with some files which I assume I can burn to a DVD...

Is there a way to render/encode each AVI file so that QDVDauthor doesn't have to do 'em all at once?

Why can't I get much more than 2.5 hours worth of Video on a regular DVD? I thought I was supposed to be able to get almost 4 hours worth on there!

a few posts suggested using Avidemux's "Auto" functions to encode the AVI file properly...I tried using the Auto->DVD function for one AVI file just to see what it did...but it didn't even provide a correct ending on the file....no ".mpeg2" or ".vob" or anything. Can I just add that 'ending' in the field where I name the file?

---

### Post by taurus on 2007-12-26
I usually use devede (it's in the repos so you can install it with synaptic) to convert the .avi to .iso.  Then, I use k3b to burn that .iso image as a DVD Image to a DVD media and it can play just fine on a stand alone DVD player.

---

### Post by Hospadar on 2007-12-26
You probably didn't code them properly in avidemux, most likely that the settings in the encoding weren't properly set for PAL or NTSC.  You might want to check out avidemux's wiki for more info on that, and make sure if you code them to be PAL or NTSC, that Qdvdauthor is looking for the same format. (PAL/NTSC has to do with framerate and aspect ratio)

avidemux wiki for dvds: [http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD](http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD)

especially the "Preparing the Video" segment

As for how much video you can fit on a dvd, it's all about the bitrate.  Standard dvds use an average bitrate of 5000kb/s.  If you have movie you shot from a home camera, or let's say a legally downloaded feature length film ;-) that was ripped to an avi, you're probably looking at a much lower bitrate, maybe as low as 800-1500kb/s (which still looks fine on a big screen hdtv I might add)  so when you encode the mpegs, mind that you set the bitrate to something similar to the bitrate of the AVI (I think if you right click a video and go to properties it will give you the video bitrate) there's not much sense in transcoding a 800kb/s avi to a 5000kb/s mpeg, obviously you won't magically get 5 times the quality.

So, Mind your format (PAL/NTSC), and try and set the target bitrate to something sensible for the source video (I've got a homemade dvd with 9 hours of video on it, I'm sure you can fit four hours)

That said, if you've just got one or two video files and arn't dying for a menu, I think devede is a much easier option that avidemux+qdvdauthor, although I realize for somethings it can't be avoided

Hope this helps!

---

### Post by zachthejones on 2007-12-27
Thanks a bunch Hospadar! That link really helped me a bunch. I think I may be on the right track now...we'll see by this weekend when I retry the DVD.

I've really enjoyed using QDVDauthor, but their website is rather lacking in the documentation area. I'd really like to learn more about what the different commands and/or settings mean - in both Avidemux and QDVDauthor.  Most of it is terminology I'm not too familiar with. You know any good resources or websites which might help me out with understanding all that?

---

