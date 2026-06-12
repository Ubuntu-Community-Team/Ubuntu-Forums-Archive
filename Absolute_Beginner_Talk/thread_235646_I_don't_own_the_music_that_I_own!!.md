---
title: "I don't own the music that I own!!"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2006-08-13
So I've purchased some music from Musicmatch on a M$ XP machine.  I'm sure some of you have been through the absolutely INFURIATING process of having to log in to the music store (itunes and the rest of them do the same thing, I believe) to "license" your right to listen to, burn or upload to an MP3 player the music you rightfully own *^$%#>!!!  Who REALLY owns it?  :-k (climbing down off my soapbox)...

I have transfered these .wmv files to my Ubuntu OS machine, and I need to convert them to ogg/vorbis or flacs.  How do I do that?  I tried importing them with Rhythmbox, but it says "not an audiostream file".

---

### Post by Tomosaur on 2006-08-13
As far as I am aware, linux does not support DRM audio, nor will it in the future. Thus, audio with DRM embedded will simply not play, since linux thinks they're corrupt or something. I may be way off base here, but I think that's the situation.

---

### Post by Jasper Houtman on 2006-08-13
You need the win32codecs to play that, the easiest way to install those is using automatix.

I installed them by editing my sources list (adding multiverse and non-free) and used synaptic package manager to install them.

I have no problem playing wmv files now.

---

### Post by telegramsam on 2006-08-13
Hey--thanks for the tip...

I've enabled all of the repositories, but I can't find the Win32codec.  Could you tell me what category to look in?  I tried searching under "ALL", but didn't see that name.

---

### Post by nalmeth on 2006-08-13
Try automatix or easy ubuntu

---

### Post by telegramsam on 2006-08-13
Just found it in Automatix

Thanks for your help!!

---

