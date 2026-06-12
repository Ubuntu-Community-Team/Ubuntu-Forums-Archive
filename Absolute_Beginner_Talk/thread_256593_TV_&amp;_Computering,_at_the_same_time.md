---
title: "TV &amp; Computering, at the same time?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by rickybee on 2006-09-13
Sorry if this has been answered before but I can't find anything recent on this exact subject.

I am an XP user on the edge, building a new box and ready to make the jump to full time Ubuntu. I have done some test installs on my current hardware and it looks like I'll be able to do everything I need, I do my gaming on an xbox, until I come to the multimedia part.

90% of my tv viewing is done in a window on my XP box using BeyondTV. And I must be able to continue to do this in Linux otherwise its a no go.

I looked at MythTV which seems to be the most comprehensive PVR solution but I don't see any screenshots of it being used in a window. This looks to be a great solution if your dedicating a box to a HTPC but what if you need to do all the things it does AND be able to surf the web, work on documents etc. at the same time?

I see that TVtime allows watching in a window but doesn't do recording.

Putting aside all hardware concerns as I am building this box to suit Ubuntu, is there software that will do what I need? Watch TV, have a guide, record shows all the usual TIVO type stuff.

Any suggestions would be appreciated, TIA.

---

### Post by Kobalt on 2006-09-13
Hello,

There is a great HowTo thread about using MythTV with a Hauppauge video card, you might want to check it out and ask questions in this thread to get more accurate answers : 
[http://www.ubuntuforums.org/showthread.php?t=186747](http://www.ubuntuforums.org/showthread.php?t=186747)

Cheerio !

---

### Post by rickybee on 2006-09-13
Sorry but that wasn't the question, I am not having problems installing MythTV, yet. The question is what software would best suit my needs? MythTV and Freevo seem to be more suited for dedicated HTPC's, what I need is that functionality but still be able to use my computer as a computer for everything else.

---

### Post by teddy879 on 2006-09-13
I'm not too familiar with Linux PVR software but I know that the two you mention are very robust.  A quick search through the [MythTV Documentation]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.4") reveals that you can run the MythTV GUI in full screen or as a desktop application.

I know it's tempting to try and get a quick and easy answer to your questions but you'll gain a far better understanding of Linux (or anything else for that matter) if you try to find the answer yourself at first.  Sorry for the lecturing...   :-#

---

### Post by rickybee on 2006-09-13
Yes, your right. I looked throught the docs and found what you were talking about, thanks for pointing me in the right direction. However, in my defense, that's why this forum is called 'Absolute Beginner Talk' :)

---

### Post by teddy879 on 2006-09-13
You know... I would hate it if someone responded the way I did to a request for help... especially since I'm only a newb too and this IS the "Absolute Beginner Talk" forum... my apologies, rickybee.  #-o

---

### Post by thomasando on 2006-09-13
There's definitely an option to view in a window. And it works, very well. I have a dedicated MythTV PVR in my living room, and I often stream SD digital TV over the network to a frontend, running in a window on my workstation.

---

### Post by rickybee on 2006-09-14
Thanks for the info. It looks like MythTV is the way to go then. My new Core 2 Duo processor is here, a PVR350 is on its way, I just have to make a final decision on a motherboard before picking up the last components.

---

### Post by megamaced on 2006-09-19
> **rickybee said:**
> MythTV and Freevo seem to be more suited for dedicated HTPC's, what I need is that functionality but still be able to use my computer as a computer for everything else.

Use Kaffeine - comes with Kubuntu by default

---

### Post by Brunellus on 2006-09-19
> **megamaced said:**
> Use Kaffeine - comes with Kubuntu by default
Kaffeine is only a media player.  It won't tune your TV card.

to Original Poster: Assuming your TV card can work in Linux, the application you want is 'tvtime'

---

### Post by megamaced on 2006-09-19
> **Brunellus said:**
> Kaffeine is only a media player.  It won't tune your TV card.

Oh really?

Well why is it that I can tune all of the DVB stations on my Hauppauge Nova-T card? :confused:

---

### Post by Brunellus on 2006-09-19
> **megamaced said:**
> Oh really?

Well why is it that I can tune all of the DVB stations on my Hauppauge Nova-T card? :confused:
Kaffeine is a frontend for the xine media player (and others beside).  The actual backend stuff--interacting with your TV card--is handled by other programs on which kaffeine itself depends.

---

### Post by megamaced on 2006-09-19
Yes I am aware of that. But the fact remains that kaffeine (be it through backends or whatever) WILL tune a DVB card :tongue:

---

