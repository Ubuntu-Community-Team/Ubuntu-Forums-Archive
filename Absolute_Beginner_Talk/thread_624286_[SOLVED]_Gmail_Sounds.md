---
title: "[SOLVED] Gmail Sounds"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-11-26
Why don't the Gmail Chat sounds work in Gutsy? They worked in Feisty, but not in Ubuntu's latest release.

---

### Post by Nano Geek on 2007-11-27
> **shanepardue said:**
> Why don't the Gmail Chat sounds work in Gutsy? They worked in Feisty, but not in Ubuntu's latest release.Is the on their website or a downloaded program?

---

### Post by shanepardue on 2007-11-27
On Gmail's website within the built-in chat, the notification sounds don't play at all.

---

### Post by Nano Geek on 2007-11-27
> **shanepardue said:**
> On Gmail's website within the built-in chat, the notification sounds don't play at all.If it's just that one site that won't play sound, then it might be that it was either accidentally disabled by you, or they turned it off themselves. Can you confirm that other sites play sound files correctly?

---

### Post by shanepardue on 2007-11-27
Yes. I'm confirmed it's only this website and it plays fine now that I've reverted back to Feisty on my laptop. It didn't work when I ran Gutsy and to further confirm this is an issue with Gutsy, I've got it running on my desktop experiencing the same exact problem.

---

### Post by Nano Geek on 2007-11-27
One more thing if you still are interesting in fixing it, do you have ubuntu-restricted-extras installed?

---

### Post by shanepardue on 2007-11-27
> **asjdfwejqrfjcvm msz34rq33 said:**
> One more thing if you still are interesting in fixing it, do you have ubuntu-restricted-extras installed?
Yes, I have ubuntu-restricted-extras installed on both the gutsy machine and the feisty one.

---

### Post by Nano Geek on 2007-11-27
Interesting.
I might try to look into this further and see what I can find.

---

### Post by shanepardue on 2007-11-27
Alright, I don't know if this is because of the recent firefox update, but it seems to be 
working properly for me now. I am however still not able to use the file I've attached 
within pidgin. This may be a bug to file with Pidgin since I can play the file 
within Mplayer, just not within Pidgin.

Sorry for being such a diva! haha

:edit - I found the gmail sound within firefox doesn't work when I'm playing music..that 
was my problem..d'oh! I'll have to look into the latest pidgin version and see what's wrong 
there. Thanks for your help!

Here's the error message I get in the terminal when I test the sound file...
```
JACK tmpdir identified as [/dev/shm]

(pidgin:15497): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start <= stop' failed
```

---

### Post by Nano Geek on 2007-11-27
I looked up that error, and I could not find anything in English (which is the only language I speak atm). You could try changing the file to a *.wav. It's (remotely) possible that that's all Pidgin supports.

---

### Post by shanepardue on 2007-11-27
> **asjdfwejqrfjcvm msz34rq33 said:**
> I looked up that error, and I could not find anything in English (which is the only language I speak atm). You could try changing the file to a *.wav. It's (remotely) possible that that's all Pidgin supports.
That was it! I didn't think about that considering I'm running and open-source OS that loves .ogg, but that was it. Pidgin just needed a .wav file. It didn't in it's previous releases, but it does now.

Thank you very much for your help and I greatly appreciate your time in resolving this issue!

---

### Post by Nano Geek on 2007-11-27
Wow, I was almost sure that Pidgin would support ogg. Weird
And you're welcome.

---

### Post by shanepardue on 2007-11-27
Yeah, it used to. Maybe I should open a ticket or something. An open-source app should support .ogg!!!

---

### Post by Nano Geek on 2007-11-27
Really, it should. In my mind it should support any format that your computer can play. But yea, you could ask in the mailing lists or as you said open up a bug report.

---

