---
title: "[SOLVED] Amarok and iPod"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by mubelhor on 2007-11-21
I apologize for asking a question that someone has already posted, but it takes hours to hunt through these message threads!

I installed Amarok, plugged in my iPod, my iPod was quickly recognized, all its files were listed, but they don't seem to be playable.  I get a message about missing codecs.  I tried "help" within Amarok, but get a message about missing kde something or other.

Rhythmbox sees the iPod,too, but doesn't seem to be able to play the files either.

What am I missing?

---

### Post by victorgreen on 2007-11-21
You are probably missing codecs to play most media files. These codecs are not open source as as such are not included in default installation. The easiest way to get lots of these types of programs is to download and install a program called automatix- you can get the .deb from their website. It can get you tons of codecs and other useful programs. 

You can also get the codecs manually if you find a thread on how/where to get them.

---

### Post by Incense on 2007-11-21
Installing the ubuntu-restricted-formats package should get you everything. Try that and see if it helps. 

```
sudo apt-get install ubuntu-restricted-extras
```

You can also check this page for more info. 

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by mubelhor on 2007-11-21
Thank you for the quick response.  (It took me a while to load in the packages you suggested).

I think your suggestions basically fixed the problem.  The podcasts and the music I uploaded to the iPod from cds seem to play fine.  Most of my music, however, was downloaded from the iTunes store.  I have a vague recollection of something in iTunes about doing something about those downloads, so I maybe need to hold my nose and fire up Windows XP again and launch iTunes.  Of course, then I'll probably need to wait at least 12 hours for the security software to update and for Windows to do a virus scan.

Does something about music downloaded from the iTunes store trigger any memory for you, or is my attention focused on the wrong thing?  My next question in the appropriate forum is probably going to be about virtualization (I spotted the option to install "wine" during the Automatix installation, but thought I should focus on one problem at a time.)

---

### Post by Incense on 2007-11-22
> **mubelhor said:**
> Thank you for the quick response.  (It took me a while to load in the packages you suggested).

I think your suggestions basically fixed the problem.  The podcasts and the music I uploaded to the iPod from cds seem to play fine.  Most of my music, however, was downloaded from the iTunes store.  I have a vague recollection of something in iTunes about doing something about those downloads, so I maybe need to hold my nose and fire up Windows XP again and launch iTunes.  Of course, then I'll probably need to wait at least 12 hours for the security software to update and for Windows to do a virus scan.

Does something about music downloaded from the iTunes store trigger any memory for you, or is my attention focused on the wrong thing?  My next question in the appropriate forum is probably going to be about virtualization (I spotted the option to install "wine" during the Automatix installation, but thought I should focus on one problem at a time.)

It's called DRM. If you bought songs from the iTunes music store, it will play on nothing more then an iPod, or iTunes that have been authorized to play music from your account. You need to remove the copy protection before you can play those files on linux. The best way (IMO) to do this, is to burn the tracks to a CD in itunes as an audio CD. Then rip the tracks again back to MP3. The tracks will be just plane jane mp3's and can run on any system (with the right codecs). I like this way because you then have a backup of your music. Until you remove the DRM though, they will not play in Amarok. Lucky for us Apple and Amazon are starting to move away from DRM.

---

### Post by mubelhor on 2007-11-22
Ah!  I should have remembered that.  Thanks again.

---

