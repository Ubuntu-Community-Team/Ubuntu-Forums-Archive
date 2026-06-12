---
title: "can't rip CDs into MP3 format"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by markfasano on 2006-05-25
I cannot for love or money locate the gstreamer0.8-lame package in order to enable MP3 encoding for my Sound Juicer. I have enabled every repository in universe and multiverse on Synaptic and still no file is available. Help please.

---

### Post by mostwanted on 2006-05-25
You need to make an mp3 profile for gstreamer:

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

This extra step has to be taken because (I guess) Ubuntu doesn't want to make it obvious to people that they can rip their music into mp3. Mp3 is not a free format, supporting it isn't exactly helping out the world free format situation.

Personally I think you should start building an ogg vorbis collection next to your mp3 collection (which can be kept for compatibility with portable music players). Some day you'll be grateful for having done that. Ogg Vorbis is also the better format of the two.

---

### Post by az on 2006-05-25
[QUOTE=mostwanted]This extra step has to be taken because (I guess) Ubuntu doesn't want to make it obvious to people that they can rip their music into mp3. [/QUOTE]


That is absolutely not the reason.  Nobody want's to hide anything.  The reality is that MP3 is a licenced technology as well as not a free-libre one.  MP3 support has to be enabled by each individual user, and not the distribution.

[https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)

Maybe someone can package a sound-juicer profile to go along with the gstreamer plugins.  That has not been done simply because no one has thought of doing it, I would say, but not because anyone wants to make it more difficult to emable support for these restricted formats.

---

### Post by markfasano on 2006-05-25
I finally found gstreamer0.8-lame at Marillat's Debian repository: [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) My Sound Juicer is ripping CDs into MP3 quite nicely. Thank you, Jacob. 

I don't know if the powers that be in the freeware/Linux community intentionally put up roadblocks for noobs trying to truck in MP3 or not, but I do know that Jacob is the only person who has actually told me where this critical lame package can be found. 

Other responses, frankly, have tended toward the sanctimonius: "You should just rip audio files into OV, they sound better," or "If everyone avoided MP3 and used the free format, it would catch on, etc." 

Look, I realize the political implications of freeware. I do rip CDs into OV and MP3. But I can't say to interested parties, "Hey I've started using Linux and it's amazing but my OS doesn't support MP3 so all those audio files you have you can forget about listening to. You should just start over with this other format that sounds better."

I've moved away from Microsoft in large measure to escape lack of choice, not to substitute one form of totalitarianism for another.

Thanks again for your help.

---

### Post by az on 2006-05-25
[QUOTE=markfasano]I finally found gstreamer0.8-lame at Marillat's Debian repository: [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) My Sound Juicer is ripping CDs into MP3 quite nicely. Thank you, Jacob. [/QUOTE]


That package is in multiverse.  No need to go outside of the ubuntu repos.
[http://packages.ubuntu.com/breezy/libs/gstreamer0.8-lame](http://packages.ubuntu.com/breezy/libs/gstreamer0.8-lame)

[QUOTE=markfasano]
I don't know if the powers that be in the freeware/Linux community intentionally put up roadblocks for noobs trying to truck in MP3 or not, but I do know that Jacob is the only person who has actually told me where this critical lame package can be found. [/QUOTE]

First of all, it's not freeware.  Freeware is still someone else's property.  free-libre open source software is completely different.

Secondly, the instructions are on the wiki.  The most popular UserDocumentation page is the restricted formats one, and it's on it.  No roadblock.


[QUOTE=markfasano]
Other responses, frankly, have tended toward the sanctimonius: "You should just rip audio files into OV, they sound better," or "If everyone avoided MP3 and used the free format, it would catch on, etc." [/QUOTE]

You shouldn't rip everything to ogg.  You just can.


[QUOTE=markfasano]
Look, I realize the political implications of freeware. I do rip CDs into OV and MP3. But I can't say to interested parties, "Hey I've started using Linux and it's amazing but my OS doesn't support MP3 so all those audio files you have you can forget about listening to. You should just start over with this other format that sounds better."[/QUOTE]

It actually does support mp3, you just have to enable it by hand since it is not legal for the distributer to do otherwise.  


[QUOTE=markfasano]
I've moved away from Microsoft in large measure to escape lack of choice, not to substitute one form of totalitarianism for another.

Thanks again for your help.[/QUOTE]

So, are you *sure* you have multiverse enabled?

---

### Post by markfasano on 2006-05-25
uh huh. I'm sure. none of those i386 lame links from [http://packages.ubuntu.com/breezy/li...reamer0.8-lame](http://packages.ubuntu.com/breezy/li...reamer0.8-lame) worked when I tried to access them.

---

### Post by clint1010 on 2006-05-26
Try out Automatix. Its a simple GUI that will install the mentioned codecs for you, and alot more.

Automatix made it allot easier to get my ubuntu installation to a fluid state that i was used to with mircosoft. And then some

search the forums for Automatix, if i new how to put a link to that particular thread here i would.

---

### Post by Lord Illidan on 2006-05-26
Try here : Automatix links

[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=Automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=Automatix)

[http://www.ubuntuforums.org/showthread.php?t=177646&highlight=Automatix](http://www.ubuntuforums.org/showthread.php?t=177646&highlight=Automatix)

---

### Post by markfasano on 2006-05-27
got it installed. a solid tip. thanks.

---

