---
title: "MP3 Player recommendations - iTunes Style"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by johnmccracken on 2006-05-12
Hi,

I am lookin for an mp3 player / mp3 library in the style of iTunes.  Recommendations please.

Thanks

---

### Post by Gustav on 2006-05-12
If you are using gnome - rhythmbox or listen

---

### Post by johnmccracken on 2006-05-12
[QUOTE=Gustav]If you are using gnome - rhythmbox or listen[/QUOTE]


Okay, I am totally new to linux,  I have downloaded rhtythmbox from here : [http://linux.softpedia.com/get/Multimedia/Audio/Rhythmbox-3904.shtml](http://linux.softpedia.com/get/Multimedia/Audio/Rhythmbox-3904.shtml)

how do i install it,  I can open the archive and I can see all the files etc.  Coming from windows I would have looked for the setup.exe etc but what is the equivalent in linux ?

Sorry.

---

### Post by barbarian on 2006-05-12
Amarok

---

### Post by Kobalt on 2006-05-12
Rythmbox is already installed in Ubuntu, you don't have to download/install it. It's in Applications>Sound and Video>Music Player Rythmbox

---

### Post by Sutekh on 2006-05-12
I don't think there is any *real* alternative to iTunes, at least in terms of style.  Having said that, I think Rhythmbox, Listen and Quod Libet are much better than iTunes.

Are you using GNOME (Ubuntu) or KDE (Kubuntu).  Rhythmbox is installed by default in Ubuntu.  Check your Applications -> Sound and Video Menu

---

### Post by mostwanted on 2006-05-12
[QUOTE=johnmccracken]Coming from windows I would have looked for the setup.exe etc but what is the equivalent in linux ?[/QUOTE]

Take a look at this (for future enquiries):

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by johnmccracken on 2006-05-12
okay - ive found rhythm box.

When I try to import files I get  the error message that says the file is not an audio stream, I know they are as they are mp3 and I have played them before.

?

---

### Post by Sutekh on 2006-05-12
MP3s are a patent encumbered, non-free format and as such Ubuntu can't ship with support.

You can get the relevant codecs using this link

[Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats)

---

### Post by mostwanted on 2006-05-12
[QUOTE=johnmccracken]okay - ive found rhythm box.

When I try to import files I get  the error message that says the file is not an audio stream, I know they are as they are mp3 and I have played them before.

?[/QUOTE]

Mp3 is a patented format, Ubuntu is 100% free so it cannot include decoders for formats like Mp3 (it can in the EU/Japan/etc. but it wouldn't be allowed to be used by the users in the USA).

It is, however, possible to enable playback of restricted formats very easily if you have an Internet connection (and legal for Americans too if you've bought the needed licenses).

Because restricted formats are a bad idea to base a collection on, please consider supporting/using free formats!

Here's how you enable Mp3 and other restricted formats:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by johnmccracken on 2006-05-12
[QUOTE=Sutekh]MP3s are a patent encumbered, non-free format and as such Ubuntu can't ship with support.

You can get the relevant codecs using this link

[Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats)[/QUOTE]

okay i have installed the package using this :

sudo apt-get install  gstreamer0.8-mad

and it all seems to go okay but rhythm box still doesnt like my mp3s ;-(

---

### Post by johnmccracken on 2006-05-12
[QUOTE=johnmccracken]okay i have installed the package using this :

sudo apt-get install  gstreamer0.8-mad

and it all seems to go okay but rhythm box still doesnt like my mp3s ;-([/QUOTE]


correction it working

---

