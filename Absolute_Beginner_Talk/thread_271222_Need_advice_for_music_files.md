---
title: "Need advice for music files"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by tricky76 on 2006-10-04
....

---

### Post by Anonii on 2006-10-04
> **tricky76 said:**
> I like Ubunutu a lot and am starting to use it more than XP.  One problem I have is that I have all of my music files in WMA format.   I choose this format simply because of size and I think it sounds pretty good at 128k.

Anyways, I use windows media player to rip cds to wma and dbpoweramp to convert mp3s, shns or flac files to WMA and that works pretty well for me in Windows.

Is there something like dbpoweramp that would let me easily convert files to WMA?  

Would it be more realistic to just abandon wma and start using mp3s?  If I go this route, whats the best way to convert all my files from 128k wmas to mp3s? wma -> wave -> mp3?

thanks,
-tricky
**sudo apt-get install soundconverter**

>:3

---

### Post by Bizmac on 2006-10-04
Look there, it' a script to convert wma with mplayer.

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3)

My advice: give up wma, use ogg or mp3, and amarok ;) 

Enjoy!

---

### Post by phranx on 2006-10-04
You can solve this and other problems with Automatix
[http://getautomatix.com/wiki/index.php?title=Main_Page&Itemid=30](http://getautomatix.com/wiki/index.php?title=Main_Page&Itemid=30)

It will install all the proprietary codecs you need and much more

However, i agree with Bizmac 

> **Bizmac said:**
> 
My advice: give up wma, use ogg or mp3, and amarok


bye bye

---

### Post by gvgerman on 2006-10-04
I'm a noob on Ubuntu but familiar with wma and MP3 and ripping and converting.

Each time you convert a song file, i.e.- original source to wma is the first conversion, wma to MP3 would be a second conversion, you have loss of information, i.e- the sound quality degrades.  I know ogg is supposed to be "lossless" but there is indeed compression of the file.  This can be understood by comparing the size of the file with the wav rip of the song, which is usually the first step in the rip process.  The wav rip has no loss and the file size is huge compared with wma, mp3 and ogg formats, which compress the wav file to provide a trade-off between sonic quality and file size. 

So, depending on the number of songs that you have and the quality of the original "rip", you may not want to convert your wma files at all or, alternatively, you may even want to re-rip all of the original sources to ogg or to MP3 (using Lame).  

There are several things to consider:
- original wma rip quality setting: was it extemely high or was it very low?
- know that the quality of the sound will never be better than the wma file (it is now the source for the second conversion)
- the size of the new file (the second conversion) may be quite different than the wma file

You should experiment with one song using several conversion settings and different formats before you go off to the races and convert with a batch process.

Three things can happen:
- Second conversion results in satisfactory sound and an agreeable file size
- Second conversion results in poorer sound (file size is then a moot point)
- Second conversion results in huge files with same sound

---

### Post by Anonii on 2006-10-04
I'd propose ogg if you are not bored to convert every song you download/buy. Else, all the way to mp3. 

ogg is superior, because its open-source etc. But still, boring as hell to convert. And I have many painful experiences of clearing out the converted files and accidentaly deleting the entire music folder (5GB of music lost, hooray!)

---

### Post by crispy_420 on 2006-10-04
Here is a link to a script for nautilus to convert audio files:

[http://doc.gwos.org/index.php/Audio-convert](http://doc.gwos.org/index.php/Audio-convert)

Then all you do is right click -> scripts -> audio convert, now you converted file will show up in the same directory in just a minute.

---

### Post by jaboua on 2006-10-04
> **gvgerman said:**
> I know ogg is supposed to be "lossless"
OGG is just a container format for different audio and video formats. You were probably thinking of OGG Flac, the lossless format, but the more widely used is OGG Vorbis, which is a lossy format.

Just my two cents: as WMA works in most audio players on linux, I don't see the need to convert them (and loose either quality or diskspace at the same time, as mentioned). However when ripping new CDs you should choose some other format though, as I don't even think it's possible to rip to WMA on linux. Personally I use MP3 as my MP3-player doesn't support OGG vorbis :/ - however AFAIK ogg vorbis provides better compression, in other words better quality with the same bitrate.

---

### Post by tricky76 on 2006-10-04
...

---

### Post by gvgerman on 2006-10-04
jaboua -

Thanks for the clarification.

I also use MP3 but being new to Ubuntu, I've never used the tools within.  In Windoze, I've used EAC v0.95 and Lame v3.97b2 with alt presets and have been very pleased with the results.

What are you using in Ubuntu to rip to MP3?

Thx,

---

