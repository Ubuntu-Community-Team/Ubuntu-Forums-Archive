---
title: "Old itunes music"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-04-20
Back when I used windows I used the itunes store and backed it up by burning albums to CDs. So now I have CDs with the quality of 128kbps burnt as wav I assume (not an "mp3" CD). 

I want to know if I rip these CDs at 128kbps AAC if they'll be the same as what they were when I had them downloaded from itunes or if they'll be a lesser quality?

If I rip them as wav will they be the same or lesser quality? Will the files be huge?

---

### Post by Hieronymus on 2008-04-20
Farueulogy,

When you have audiofiles ripped at 128kbps the audio quality is less than normal CD quality in order to make the filesize smaller. 
When you then re-create an audiocd from these files and rip it again the quality will be even worse. 

You have a downgrade of an already downgraded file. 

The thing you should do is just try and see if you are happy with the result. Yeah, the quality is less but maybe you won't notice it. 

If you want to keep (almost) the same quality you should rip the CD in better quality, resulting in larger files. 

Regards, 

Jeroen

---

### Post by farueulogy on 2008-04-20
If I rip the files as .wav then - will they not be the same quality because they haven't been compressed further?

---

### Post by Hieronymus on 2008-04-20
Yep, they should be as good as the 128kbps files you burned to a cd.
Though each time you convert a file there is loss, in this case you will probably not notice it.

Jeroen

---

### Post by daengbo on 2008-04-20
If you want to store as a loosless file (WAV), you should at least look at storing as FLAC. It's lossless and it will save you about 40% on space. If you rip to 256Mb AAC, you probably won't be able to notice the difference between the CDs you have and the files.

---

### Post by farueulogy on 2008-04-20
> **daengbo said:**
> If you want to store as a loosless file (WAV), you should at least look at storing as FLAC. It's lossless and it will save you about 40% on space. If you rip to 256Mb AAC, you probably won't be able to notice the difference between the CDs you have and the files.

I think I'm being giving a lot of misinformation and some not applicable generic responses.

256 from 128? That's just going to use space to store lots of 00000000s

---

### Post by aysiu on 2008-04-20
If they were originally AAC files and get re-ripped to AAC (supposedly using the same compression method), would it really lose *more* information?

---

### Post by farueulogy on 2008-04-20
> **aysiu said:**
> If they were originally AAC files and get re-ripped to AAC (supposedly using the same compression method), would it really lose *more* information?

Good summary I think - does anyone know?

Also I just tried ripping to aac and it's all fragments - songs of 4 minutes are 16 minutes with bits of silence in between blips of the music.

---

### Post by Hieronymus on 2008-04-20
If you rip an audiocd to say 128kbps it loses some data. 
When you then write them to a cd making it and audio cd it can not re-create the lost data and you will have and audio cd with 128kbps quality.

When you the again rip this CD it will again lose data because it will downcovert the audio content to 128 kbps. 

So the answer is YES you will lose more data and in effect more quality

Jeroen

---

### Post by vanadium on 2008-04-20
Your files purchased through itunes are protected by digital rights management. This means you cannot play them with anything else than itunes on your particular computer and your particular ipod. Backing these up to audio CD is therefore the best you could have done in the given circumstances.

In order to convert your purchased files to formats you can use where *you* want, you indeed should re-rip the audio CDs you created to compressed audio files. If you use a good codec with sufficiently high quality settings, you won't notice any quality deterioration, although technically, there is.

For the most widespread compatibility, I am afraid mp3 is the only choice, although it is an unfree, patent encumbered format. Use lame to do the encode, and encode with variable bitrate. You will have very good quality and fast encoding using

lame -V 2 --vbr-new yourmusic.wav

The "2" gives variable bitrate files corresponding in file size with files of about 192 kbps. However, probably you won't even notice a difference using a somewhat lower quality of 3, 4 or even 5. So if disk space is at premium (portable audio player), test the same command substituting a higher number and listen to the result.

Otherwise, if compatibility is less of an issue (you use your PC or have an ogg compatible player), nothing beats the free open source format ogg.

Do not use AAC: it has limited support and is not free.

---

