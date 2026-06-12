---
title: "iPod troubles"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by VerdantLightning on 2007-08-14
I'm having trouble with my iPod. All of my music exists only on my iPod. I've tried Amarok and Banshee but in both cases they miss about 1000 songs off of my iPod and sometimes only get 2 or 3 songs off of an album. I tried GTKpod which seems to find all of my music but I get this error when I attempt to copy to my hard disk.

Template ('%o;%a - %t.mp3;%t.wav') does not match file type '/media/RILEY/iPod_Control/Music/F00/CXKE.m4a'
Failed to write 'Sonic Youth-Panty Lies'
Failed to write 'The Magnetic Fields-Lonely Highway'
Failed to write 'Barrett, Syd-Let's Split (Take 1) '

and so on. It's very important to me that I get all of my music back on my computer. Some of it I bought off iTunes and some of it I don't own the CD anymore.

---

### Post by mpospisil on 2007-08-14
I didn't like gtkpod and searching these forums I found a program called floola that I like very well. [http://www.floola.com/modules/wiwimod/](http://www.floola.com/modules/wiwimod/). I have a 30gb ipod video.

---

### Post by Alterax on 2007-08-14
What you are most likely getting are the songs that you introduced to your iPod as mp3s or some other format that lacks Digital Rights Management (DRM).  The ones that you won't be able to extract so easily are the ones that you purchased from Apple's Music Store.

Apple, like many other pay-for-music services, uses DRM as a means of preventing purchased files from being shared out.  To crack the DRM, you (usually) need to use their registered product to use it.  So you can't really pull it from your iPod directly into a Linux environment, as Apple does not make a Linux client.

This is going to suck, but the best way that I know of to get these files would be to get them from the music store again using your apple login on a Windows or Mac system (I recommend not using a Mac system for this since it will render your iPod unusable for Linux due to filesystem incompatibilities), and burn these to compact disc.  (You are allowed what, ten burns per track?).  Then take these compact discs and rip those into Ogg Vorbis or MP3 and then you can put those onto your Linux box.  

It's going to be a pain, but it is the only workaround that I know of.  It will be a lot easier if Apple comes out with a Linux client for iTunes, but I don't see that happening.

--Alterax

---

### Post by operator207 on 2007-08-15
> **Alterax said:**
> the best way that I know of to get these files would be to get them from the music store again using your apple login on a Windows or Mac system (I recommend not using a Mac system for this since it will render your iPod unusable for Linux due to filesystem incompatibilities), and burn these to compact disc.  (You are allowed what, ten burns per track?).  Then take these compact discs and rip those into Ogg Vorbis or MP3 and then you can put those onto your Linux box.  

It's going to be a pain, but it is the only workaround that I know of.  It will be a lot easier if Apple comes out with a Linux client for iTunes, but I don't see that happening.

--Alterax

Why do you state this: "I recommend not using a Mac system for this since it will render your iPod unusable for Linux due to filesystem incompatibilities"

He isn't going to reformat his iPod, therefore he is not going to have a problem with "filesystem incompatibilities". Unless your telling him (without using the correct words) to reformat his iPod in a Mac format. Which should not be needed. A Mac will read a PC formatted iPod, at least my powerbook does. A PC will NOT read a Mac formatted iPod. I think your confused. 

However I do agree, he needs iTunes, and the login he used to purchase the tracks from ITMS. Then he can burn them to CD, and then re-rip them. I am not sure if its legal to do that, but it would work.

---

### Post by SanjoEel on 2007-08-15
Sorry man but anything in Apple proprietary format is not going to work outside of your ipod or itunes. You could try playing the songs with itunes and recording them with Audacity in Windows to get them into MP3 format if the burn/rip trick stated before doesn't work. I ran into the same problem and swore off Apple forever because I feel like I totally wasted the money spent on itunes. Especially since my ipod stopped working after only 3 months. I say sell that ipod asap and buy a proper MP3 player. Good luck either way!

---

### Post by Hobo Joe on 2007-08-15
You can convert all your DRM songs to MP3 with Hymn.
[http://www.hymn-project.org/](http://www.hymn-project.org/)

But I'd check up the legality before I use it, becuase I don't know if it's legal or not.
(If it is ineed illegal, could the mods delete this post?)

---

### Post by operator207 on 2007-08-15
> **SanjoEel said:**
> Sorry man but anything in Apple proprietary format is not going to work outside of your ipod or itunes. You could try playing the songs with itunes and recording them with Audacity in Windows to get them into MP3 format if the burn/rip trick stated before doesn't work. I ran into the same problem and swore off Apple forever because I feel like I totally wasted the money spent on itunes. Especially since my ipod stopped working after only 3 months. I say sell that ipod asap and buy a proper MP3 player. Good luck either way!

Your iPod died in 3 months? Did you replace it? It had applecare at that point, unless your iPod was broken because you did something to it that was not covered (dropped it, ran it over, threw it across the room) Even if you didn't want it, you could have replaced it, and sold it on ebay or something.

Most of my MP3 collection is from my old LP and CD collection. I get some new stuff, but I don't buy from iTunes. I am not a fan of iTunes for anything but playing mp3s. I also do not like the fact that unless you tell iTunes to import the music in mp3 format, it will do aac format. Its in the prefs to change to import in mp3 format.

Oh ya, this app is pretty cool, and cross-platform: [http://www.floola.com](http://www.floola.com)

---

### Post by SanjoEel on 2007-08-15
Well, it's not really dead, just unusable. It wasn't mistreated at all, just exposed to a little sweat from working and wearing it, but no more than stress than any runner or athlete would put on it. Now after 3 months it has a bunch of different problems, hold button does not work, shuts off at random, etc. 
Now, I have a 1GB SanDisk(over a year old) and a chincy 512 Mb Napster MP3 player that have both been through HELL and work just fine, and at 1/3 the price! (of the Sansa, the napster one was free)
Forgive me if I am a little disenchanted with my ipod, hahaha. It has a warranty, but I have a funny feeling that they would refuse to fix it saying it has been abused. I guess it's worth a try though. I just didn't see the point in fixing it and then pushing it off on some other poor sap to deal with the poor quality and proprietary format.

---

### Post by vexorian on 2007-08-15
floola is very good, I even used it instead of itunes in Windows.

Notice that apple actively boycotts Linux and does indeed list windows or Mac OS/X in the requirements in the box.

---

### Post by VerdantLightning on 2007-08-15
I may have said this wrong. Only an album or two I actually bought off iTunes. The rest I ripped from CDs. Some of which I own but don't curretnly have with me and some of which I borrowed from friends. All of the programs I've tried have been missing a lot of the non-itunes purchased ones. There are 4253 songs on my iPod and all of the programs I've used only got about 3200 of them.

---

### Post by operator207 on 2007-08-16
> **SanjoEel said:**
> Well, it's not really dead, just unusable. It wasn't mistreated at all, just exposed to a little sweat from working and wearing it, but no more than stress than any runner or athlete would put on it. Now after 3 months it has a bunch of different problems, hold button does not work, shuts off at random, etc. 
Now, I have a 1GB SanDisk(over a year old) and a chincy 512 Mb Napster MP3 player that have both been through HELL and work just fine, and at 1/3 the price! (of the Sansa, the napster one was free)
Forgive me if I am a little disenchanted with my ipod, hahaha. It has a warranty, but I have a funny feeling that they would refuse to fix it saying it has been abused. I guess it's worth a try though. I just didn't see the point in fixing it and then pushing it off on some other poor sap to deal with the poor quality and proprietary format.

But pushing shoddy hardware off on unsuspecting people is the EBay motto... At least I thought it was... ;)

Seriously though, I would get it fixed via apple care. They have made commercials for the iPod endorsing running (nike commercial about it telling you your distance) Unless you bring it to them with gouges and holes in it, I would imagine they would replace it. As for the random problems, have you tried to update the firmware on it? My 60g video had some problems, and were fixed in a update. 

My biggest problem is when it will not "sleep" I will hold the play button, and nothing happens.
I found that you turn the volume up and down on it, THEN hold the play button it will work. Same with rating the song, if you cannot get to the rating for the song, adjust the volume. Something screwy with the interface. its not a deal breaker though, now that I know I can do this to fix it.

---

### Post by SanjoEel on 2007-08-17
Thanks operator, maybe I should take it in just to see, you never know right? 
VerdantLightning, even if you ripped your cds right into iTunes, by default i am pretty sure it imports everything as AAC unless you tell it otherwise. It may be possible to export these songs as MP3s, although I can't give you specific instructions because I stopped using iTunes a long time ago haha. But I think it's possible. I did find this program for you, but I have never used it so you'll have to see for yourself. It IS open source though. Good luck, let us know what happens.[ iTunesExport]("http://www.ericdaugherty.com/dev/itunesexport/")

---

