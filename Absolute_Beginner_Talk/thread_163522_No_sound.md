---
title: "No sound??"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-04-21
Hi all! :D 

I have installed all the codecs for audio and video and the videos play, no problem.  The only thing is THERE IS NO SOUND!  :confused: 

Even when I play mp3's, wma's etc., there is nothing. What could possibly be wrong?  I have windows on this machine and I have no trouble with sound there, so it is not the speakers.  When I watch TV or listen to the radio through my TV card there is sound.

Can anyone help.:( 

Russty.

---

### Post by shaqan on 2006-04-21
Hey. I'm a newbie myself, so go easy with me :)

Have you selected the right engine to play the sound ? Usually somewhere in "settings"? If you are using the aRTS engine be sure to check in Adept that you have the nessecary packages installed for aRTS MP3 support.

---

### Post by Sef on 2006-04-21
Could you give us some system specs, especially your sound card.

---

### Post by Russty of Oz on 2006-04-21
Hmmm, you are obviously further advanced than me.  I can't seem to find what engine I am using, but have started downloading the Adept package.  Will keep you posted as to what (if anything) happens.

---

### Post by Russty of Oz on 2006-04-21
I think the sound card is Intel 82801DB-ICH4.  If that makes any sense.  
In fact, I was able to get sound from web sites before, but not now.

---

### Post by Russty of Oz on 2006-04-21
I have installed Adept but it has made no difference.  Where can I find what "engine" I am using?  Where are the "settings"?

---

### Post by xyz on 2006-04-21
You may find this link useful
[http://www.ubuntuforums.org/showthread.php?t=101125](http://www.ubuntuforums.org/showthread.php?t=101125)

---

### Post by Russty of Oz on 2006-04-21
Thanks xyz, I will have to go through that later, it' time to eat now.

---

### Post by Russty of Oz on 2006-04-21
Well, I have tried all that and still no sound.  It says that the sound is AC97.  

I used to get sound at startup and could get sound from streaming internet but now nothing!  The only thing I did yesterday was to install the multimedia pack for mp3 etc.

Is there something like windows system restore in ubuntu?

---

### Post by xXx 0wn3d xXx on 2006-04-21
[QUOTE=Russty of Oz]Well, I have tried all that and still no sound.  It says that the sound is AC97.  

I used to get sound at startup and could get sound from streaming internet but now nothing!  The only thing I did yesterday was to install the multimedia pack for mp3 etc.

Is there something like windows system restore in ubuntu?[/QUOTE]
In terminal type "sudo alsamixer" and make sure everything is enabled and nothing is muted.

---

### Post by Russty of Oz on 2006-04-21
Well, it seems Ok.  Master is 61, Master M is 0, Headphone is 71. PCM is 90, Line is 68 and CD is 81.

---

### Post by Russty of Oz on 2006-04-21
My sound works again now.

It had something to do with the Winfast TV card I installed.  I removed it and the sound returned.  But then another problem.  Now windows keeps rebooting!  Even in Safe Mode!  So it looks as though I will HAVE to use Ubuntu only now.  Not a bad thing, but I am still learning how to use it.  

Oh well, I will have to learn FAST!!!

---

