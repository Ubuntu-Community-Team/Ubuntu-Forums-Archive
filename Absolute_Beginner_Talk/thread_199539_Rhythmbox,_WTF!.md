---
title: "Rhythmbox, WTF?!"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Mr_Vercetti on 2006-06-18
Today I had an urge to listen to my music and I noticed that Xubuntu didn't have a Music player. I decided to switch back to good ol' Ubuntu and now Rythem box says my MP3s "aren't audio stream files". I never had a problem with playing my music on Linux until now and I really would appreciate any help anyone could give me. Thank in advance.

---

### Post by TheRingmaster on 2006-06-18
try installing automatrix. This program can install MP3 codecs. If this isn't your problem, then I don't know what to do.

sudo apt-get install automatrix

---

### Post by Raavea on 2006-06-18
I had to re-install all my codecs and non-free formats after upgrading to Dapper. Perhaps that's what caused your problem?

 If so, automatix is a nice quick way to put them back in.

 However, I couldn't get my .wma to work again after the update - if you want to translate your music into a format that will work on all your installations, hunt in synaptic for soundKonverter and install that. Then translate all your music to .ogg (its like free mp3).

 Hope this was helpful. :)

---

### Post by Mr_Vercetti on 2006-06-18
Thank you both of you, yet soundkonverter doesn't want to convert my MP3s. I tell it what to convert, hit start, and nothing happens it just sits there. Any suggestions?

---

### Post by nalmeth on 2006-06-18
Did you go get the codecs?

---

### Post by Raavea on 2006-06-18
Strange... I just installed the codecs, installed SK, then I just open it up, tell it I want good quality, .ogg, click and drag all the files I want changed into the SK window, click start (down near the err... southeast(top of the screen being north) corner of the SK window) and wait. It decodes, encodes, and there's my stuff.

It took me a while to notice the start button - have you clicked it, or missed it like I did?

---

### Post by Mr_Vercetti on 2006-06-18
[QUOTE=Raavea]Strange... I just installed the codecs, installed SK, then I just open it up, tell it I want good quality, .ogg, click and drag all the files I want changed into the SK window, click start (down near the err... southeast(top of the screen being north) corner of the SK window) and wait. It decodes, encodes, and there's my stuff.

It took me a while to notice the start button - have you clicked it, or missed it like I did?[/QUOTE]I clicked it and it started my first song and it just sat there. Let me try going through it again.

EDIT:: Nope still the same. I click start and at the very bottom box it says:

[QUOTE=soundkonverter]mplayer -vo null "/home/tom/Music/01 It's A Long Way To The Top (If You Wanna Rock 'N' Roll).mp3" -ao pcm:file="/home/tom/Music/01 It's A Long Way To The Top (If You Wanna Rock 'N' Roll).mp3.wav"[/QUOTE]

Then it just sits there. No remaining time, no speed, nothing. It just sits there.

---

