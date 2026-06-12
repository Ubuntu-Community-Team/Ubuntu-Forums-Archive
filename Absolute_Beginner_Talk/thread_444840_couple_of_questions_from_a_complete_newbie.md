---
title: "couple of questions from a complete newbie"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by ludepu on 2007-05-15
Hi all,
i am very new to linux & ubuntu (to the tune of 4 days). i have a couple of basic questions for you:
 1   i have downloaded and a driver from ait's website form my radeon 9200 card but i get an error when trying to install (./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install) i have dual monitors which i have working but not with the ati driver.

2   i was given a folder of music which is in .wv format. (i am told it is a compressed wave file?) that i would like to convert to mp3 or uncompress to wave or even wmp. any ideas or software to use?

thank you all very much

---

### Post by nereid on 2007-05-15
Hi,

can't help you about your second question, but you don't need to download the ATI driver. Just install it from the repositories

```

sudo aptitude install fglrx-driver

```

---

### Post by crimesaucer on 2007-05-15
Maybe try this for converting WAV to mp3 or ogg.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-118-1.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-118.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-118.png)

I used this when I had some scratched CD's that wouldn't rip using the Grip ripper. 

I had made most all of my CD's into ogg vorbis with a variable bit rate near 192 (q6), and I was missing a few songs from some CD's that would not rip properly in Grip. 

For some reason those songs wouldn't rip in Linux, but could be ripped using WMP10 in Windows, so I ripped them to WAV at the highest possible bit rate (just like Grip does), and then used this script to convert them from a .wav file, into a .ogg file near 192 kbps.

All you have to do is right click on the wav file, and select "nautilus audio converter script" in the drop down menu, and then follow the instructions of the easy to use GUI (graphical user interface). Then just rename the file so that it is in the correct album order and it will play in order with the rest of the CD.

Now you can use Synaptic to install it, or you can use Terminal to install it:

```
sudo aptitude install nautilus-script-audio-convert
```

You also need to install the proper codecs for ogg vorbis, called vorbis tools from Synaptic:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-119.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-119-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-119-1.png)

---

