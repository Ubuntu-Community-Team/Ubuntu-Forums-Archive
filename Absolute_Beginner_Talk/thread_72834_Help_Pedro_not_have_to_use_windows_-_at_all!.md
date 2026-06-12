---
title: "Help Pedro not have to use windows - at all!"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by Pedricko on 2005-10-07
Hey Hey Ubunturino's!

I'm steadily learning the ropes of Ubuntu, and Linux in general, and it is quite possibly the most sublime OS I've ever come across! 

Just a few things I need - 

1. To make my Canon PIXIMIA io200 printer to work (hopefully Breezy supports more printers...)

2. I have a bog standard Labtech Webcam that I hope to have working.

3. Please reccomend an mp3 player (external, 2G+ capactiy, quite cheap british pounds) that works well under Ubuntu (USB please)

4. The same as 3 except for a webcam, and if it runs on memory cards, a reader that is also compatible.

and finally...

5. Is the Audigy series of soundcards by creative supported?

---

### Post by Ampersand on 2005-10-07
Hi

Not sure about the printer. Couldn't find it in the printer configuration utility, but it might be installable.

Try installing xawtv or camstream (using synaptic or apt-get). I've not had experience with that particular webcam, but mine was detected automatically.

I'll leave 3 and 4 to someone else for now...

Some of the audigy cards are supported, details here:

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

---

### Post by Pedricko on 2005-10-07
Great, I installed the camstream package, I'm away from my Linux box for now so I didnt get a chance to try it...

I'll attempt to use the ip3000 drivers on my printer next time on my Ubuntu machine.

---

### Post by TheAreopagite on 2005-10-08
HI Pedro

I'm looking for an MP3 player too - this is what I found out so far.

First of all, you're not limited to MP3 formats. One alternative is a file format called Ogg Vorbis. I've heard it claimed that Ogg Vorbis files are half the size of MP3 files, but the sound quality is better. I have no idea if that is true, but if it is, then a 1Gb player would hold about as many tracks in Ogg Vorbis format as a 2Gb player holding tracks in MP3.

Ogg vorbis also has the advantage of being fully supported by ubuntu. Ubuntu doesn't come with MP3 support, because MP3 is not free, but you can add MP3 support to ubuntu through synaptics - see the RestrictedFormats wiki page for instructions on how to do this in warty and hoary. I don't know how easy it will be to do it in breezy, I read here somewhere that breezy won't have an equivalent of the 'hoary-extras' repository because of legal threats.

Unfortunately, only a handful of portable players will play Ogg Vorbis files. Also apparently some MP3 portable players (notably the ipod series, but others as well) organise the music in their own special file system, and this means difficulties with linux, as special software is needed to get the music files onto the player, and of course the manufacturers only make that stuff available in Windows/Macintosh binaries.

If you want an ipod, there are programs available to enable you to use it with linux:- gtkpod for hoary and banshee for breezy. You can find out more about these at the ipodHowto wiki page.

For other players, I guess the thing to do would be to ask the guy in the shop whether the player comes with any computer software, and if it does, do you *have* to install it or can you just stick the player into a usb port and drag mp3 files to it like you would a memory stick? if the answer is that it won't work without the bundled software, then leave it.

The latest iRiver players do play Ogg Vorbis as well as MP3, and they look pretty good - I like the T10 and the T30. The Cowon iaudio G3 looks ok too, and is marketed as linux friendly. Checkout the manufacturer's sites [www.iriver.com]("http://www.iriver.com") and [http://eng.iaudio.com]("http://eng.iaudio.com")

Incidentally, a standard install of ubuntu comes with a program called sound juicer (no need to even go to synaptics, it's right there on your applications menu!). Sound juicer will take tracks from an audio cd and convert them to Ogg Vorbis before storing them on your hard drive. I just tried it, it's really really easy. Sound juicer will also convert cd tracks to MP3's , but first you have to find and install the extra software to enable it to do this.

I converted a 3minute49second track to Ogg Vorbis. The Ogg file is 4mb - does anyone know how that compares in size to an MP3 of similar length? Playing the Ogg track on my modest system (Intel 865GBF motherboard with built-in sound chips, Altec Lansing 2100 speakers) it sounds just as good as the cd original.

So at the moment, I'm looking at buying either:

1. an ipod shuffle, (to be used with banshee but only if I can get the MP3 stuff for sound juicer, as ipods don't play OggVorbis)
2. an iRiver T30 (plays Ogg Vorbis, pretty sure it'll play nice with linux) or
3. a Cowon iAudio G3 (Ogg friendly and linux friendly, but hard to find in the uk and maybe not that competitively priced)

If anyone has tried any of the recent iRiver players and can confirm that they'll work in linux without tears, please let me know!

Good luck with finding alternatives to the windows stuff Pedro. My windows machine broke last December and I've used linux exclusively since then. I haven't missed windows, but it would be nice to be able to just buy peripherals and know that they'll work, the way that you can with windows.

---

### Post by Pedricko on 2005-10-09
Thank you for the indepth advice. I was thinking of the drag and drop approach but still had my doubts about it working in linux, thanks for veryfing that for me.

I'm thinking of going for Iriver as they do look good, and are quite small.

I already have the mp3 player support and all my rather bounteous music collection is in mp3 format.

Anyone got any tips for the printer?

(I just upgraded to breezy)

---

### Post by Myglaren on 2006-12-15
I bought an iRiver T30 for exactly the reasons above - it played Ogg Vorbis files and the assumption I made was that it would be Linux-friendly.

Not so.

You have to do a firmware upgrade to even get it to play Ogg Vorbis files, also they have to be dragged into the "Data" folder, unlike MP3's.

Ubuntu "Dapper" didn't recognise the player at all.
"Edgy" thinks it is a camera.

---

### Post by macogw on 2006-12-15
There's always Rockbox, guys.  It's Linux-based firmware for the mp3 player.  For iPod, there'd Podzilla, too.  They're guaranteed to work with your Linux computer, though you will have to copy the mp3s and oggs back onto the mp3 player after you install Rockbox or Podzilla.

---

