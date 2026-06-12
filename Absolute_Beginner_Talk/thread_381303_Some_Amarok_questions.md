---
title: "Some Amarok questions"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Chadwick17 on 2007-03-10
Ok, so I got Amarok installed and it recognizes my Zen Vision:M. I have a couple of quick questions now. 

Somehow I lost the menu bar at the top of Amarok - how do I get that back?

Also, is it safe to delete the folder that has all the files that I compiled Amarok from?

And lastly, is it possible for me to rip CDs to mp3 format from Amarok? If not, whats the best piece of software I can do this from?

Thanks! 
Chad

---

### Post by groeswenphil on 2007-03-10
I use Sound Juicer to rip CDs.
I rip into Ogg Vorbis format though.
Once they're stored, I use Amarok to play the files.
All in all, the system works well.
I love the way Amarok shows the CD covers.

Phil

---

### Post by Chadwick17 on 2007-03-10
I would rip to Ogg but I'm new to this open source scene and I'm not sure what it is compatible with. I'd like to create MP3 cds for my car, use them on other comps, etc. 

Thanks though

---

### Post by laidback on 2007-03-10
Sound Juicer can create mp3 files. You need the extra codecs though. Standard Ubuntu doesn't do it.

see
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Chadwick17 on 2007-03-10
I've installed those codecs according to that page (had to in order to get Amarok to play mp3s) but when I open Sound Juicer the only options I have are Ogg, FLAC, and WAV formats.

---

### Post by laidback on 2007-03-11
Oh, I have FLAC, Ogg, WAV and MP3. Now it's quite a time since I set this up, was there something else I had to do to get Sound Juicer to run with MP3s? My notes aren't what one would like but  I'll search back and see what I can find. You can be sure that it came from some book or How to type reference. There's no way I would have known.

Hopefully more later.

Laidback

---

### Post by laidback on 2007-03-11
Ok here we go, MP3 in Sound juicer (assuming all Codecs preinstalled, (gstreamer))

Start Sound Juicer
EDIT>Preferences, in the dialogue box that appears click Edit Profiles
Choose New, call it MP3 and click create.
Select the new MP3 entry from the list and click Edit
In Profile Name box type MP3
In Description box type MP3
In the Gstreamer pipeline box type:-

     audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux

(suggest you cut and paste that line, no spaces at the front)

In file extension type mp3
Check Active box
Click OK
Restart Sound juicer
Click Edit> Preferences again and select MP3 from the dropdown list. This will set the extracted file type for next time you rip.

Only slight question I have is that I've also seen this:-
     audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
as the Gstreamer pipelining box entry. Note just last part missing, i.e. ! id3mux

I don't know if it matters. I have the first longer line on my system.

Hope you have success.

Laidback

---

### Post by frotzed on 2007-03-11
This worked perfectly for me!  Thank you so much!  For what it's worth, I used the longer line too, as you indicated.

---

### Post by Chadwick17 on 2007-03-14
I apologize for not thanking you sooner, but this worked great for me as well. I takes awhile (about 15 min. per disc) but it gets the job done. I noticed that sometimes Sound Juicer think the disc is another and name it completely wrong. 

Thanks again!

---

### Post by lamalex on 2007-03-14
buddy amarok rips cds, in the side bar type in audiocd:/ then select what you want and copy them to your collection. don't bother with another program, amarok does it all, including our sick zen vision:m. Best player on the market :guitar:

---

### Post by chavo on 2007-03-14
To answer your other questions, yes you can delete the source folder. And hit Ctrl-M to show and hide the menubar.

---

