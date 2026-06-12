---
title: "[SOLVED] The MP3 OGG problem"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-03-22
MP3 isn't fun because it isn't free to "use" - some guy somewhere says he owns it and wants to make money when people "use" it (I don't really know what that covers).

Problem is a lot of people do use it - especially podcasts. At the moment I listen to them on google reader - it puts them into a flash audio type player.

I was wondering what people thought of a firefox/rhythmbox plugin which converts mp3 to ogg without installing the elements which play mp3? Anyone seen anything similar?

---

### Post by gashcr on 2008-03-22
I don't know a lot about this, but I see it difficult as you'll need to implement the MP3 decoder in order to read the track and make it OGG. So you technically cannot avoid the use of the MP3 decoder.

---

### Post by kazamx on 2008-03-22
I would guess that in order to convert an mp3 file to an ogg file, your going to need the MP3 reader installed. 

I'm not sure why you need to take this step though. The MP3 format is free for users to download and use. As I understand it, the license just kicks in if your going to distribute it. If your worried you will need (should pay) for MP3 then don't worry, as an individual you don't. 

If however its for ethical reasons you don't want to, then I understand that too. <3 you freedom fighters.

---

### Post by unutbu on 2008-03-22
Both mp3 and ogg are lossy compression formats. That means that if you try to convert mp3s to ogg there will be some loss in sound quality. Discerning users will never be happy with that.

---

### Post by farueulogy on 2008-03-22
> **unutbu said:**
> Both mp3 and ogg are lossy compression formats. That means that if you try to convert mp3s to ogg there will be some loss in sound quality. Discerning users will never be happy with that.
Podcasts are frequently spoken word and frequently recorded at too high a bitrate for such. In this case it wont matter. *stricken from the record much*

---

### Post by Mulenmar on 2008-03-22
> **gashcr said:**
> I don't know a lot about this, but I see it difficult as you'll need to implement the MP3 decoder in order to read the track and make it OGG. So you technically cannot avoid the use of the MP3 decoder.

Well, I'm remembering this from the Windows version of the Audacity sound editor...but theres something called the LAME Mp3 Encoder that's free, opensource. You still have to download it separately though.

---

### Post by zvacet on 2008-03-22
```
sudo apt-get install mpg321 vorbis-tools
```

Go to the synaptic and install **nautilus-script-manager** and **nautilus-script-audio-convert**.After installing nautilus-script-audio-convert right click on in in synaptic and you will see other packages suggested for install so you can install them too if you want.In terminal type 

```
nautilus-script-manager enable ConvertAudioFile
```

and after that when you right click on audio file you will see option  ConvertAudioFile and from that you can choose to which format you want to convert.

---

### Post by artir on 2008-03-22
sudo apt-get install mp32ogg
then do mp32ogg *.mp3

---

### Post by namelessone on 2008-03-22
The methods of encasing audio in MP3 are patented, and technically, things like mpg123 are illegal in the united states due to patent laws, and the fact that even though they are under an open source license, they are still using patented methods, and really shouldn't be able to exist under the GPL.

But, according to Thomson, the company that owns the patent for MP3, the usage of such programs for home use is completely okay. They do want your money if you try to sell mp3s that you made with LAME, and in that case, you should probably get a commercial program that can encrypt it legally (unfortunately, these are all windows and osx based).

So the unofficial word from Thomson is that it is okay (you can email them yourself if you don't believe me) for home use. If you still have ethical qualms about using software that is under a license that it shouldn't be under, you can use the gstreamer fluendo plugins that are readily available in the ubuntu repos. Fluendo pays the licensing fees to Thomson, and has released a free mp3 decoder. Also, you can purchase decoders for other popular formats like real and windows media from their website.

---

