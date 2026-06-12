---
title: "Lossless oggflac audio"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by reldruH on 2006-08-14
My apologies if this isn't the right place to put this but I didn't see an audio forum. My question is this: I have a lot of CD's that I'd like to rip, both for preservation and enjoyment onto my computer. I started looking into different audio codecs and container formats and found oggflac (sort of). What I've managed to learn so far is that it's possible to embed flac within an ogg file. What I haven't managed to learn is *how* to do this, what effects it may have on the ability to play back this file and whether or not there's some reason that this isn't widely done. I found very little information about this type of setup at all and what I did find was difficult to follow. Suggestions?

---

### Post by em3raldxiii on 2006-08-14
Hmm, since no one else has replied yet, I'll weigh in.  First off ... is it necessary to embed FLAC into your audio files?  Why not just use plain 'ole ogg Vorbis which is easily playable in Windows and in Linux?  Generally I prefer Ogg Vorbis (smaller file better quality), but MP3 VBR is alright too.

---

### Post by reldruH on 2006-08-15
> **em3raldxiii said:**
> is it necessary to embed FLAC into your audio files?  Why not just use plain 'ole ogg Vorbis which is easily playable in Windows and in Linux?
That's the same issue I ran into when trying to figure out a format and I'm still not sure that I made the right decision. What my line of thought basically boiled down to was that Vorbis is a lossy codec and hard drive space is cheap. The plan is for this music to go on a file server, so how much space it takes up is a relatively minor issue. Future-proofing it is more important to me. If one day somebody invents a set of speakers for $10 that have better quality than anything else, I want to make sure that I can make the best use of them. Basically, it's a safety measure, one with no real risk.
The reason I want to embed the flac in an ogg file is because I read that ogg streams much better than flacs do and I want to stream my music from my server to other computers in my house. None of them run Windows, but even if I do get a windows comp one day, the only oggflac player I found was a plugin for a windows player. Will Amarok or Rhythmbox play oggflac? Will Sound Juicer encode it? Thanks for the response, and if any of my reasoning is wrong I'd appreciate hearing about it.

---

### Post by MetalMusicAddict on 2006-08-15
Maybe give the Grip guide in my sig a look. Its setup for people who wanna go to mp3 but its easily changed to FLAC or whatever you want to go to. Ive found Grip the best ripper/encoder for linux. Closest thing to EAC/Audiograbber.

As far as players go. Its just a matter of having the right plug-in installed like in windows. I use Listen and Totem. They use the gstreamer framework. I havnt had any problem playing any audio files.

I also have my own home-server with all my media on it. The only format Ive seen issues with is WMVs. They just track a little slower than some audio/video.

Ill try to keep an eye here or PM me with questions.

---

### Post by em3raldxiii on 2006-08-15
Well, I read up on FLAC and I completely understand now why you'd want to use it.  It looks fantastic.  On the other hand, there was another one that looks maybe a little better - called WavPack ([http://www.wavpack.com/](http://www.wavpack.com/)).
 
Here is a neat wiki site that has comparisons, among other nice pages, between FLAC, WavPack and a bunch of others.  I think you might prefer to use WavPack in the end ... good compression, fast, stremable, free, and linux/windows friendly.  Just a thought.  I'll see what else I can find about FLAC and Ogg. :D  From what I can tell so far, if a player plays OGG, then it should play any embedded form of OGG - what would be the point of going OGG if it didn't behave like an OGG?  Just a thought.
 
Now, on a completely related but totally different point ... setting up this music server in your house.  You have my interest piqued.  I have 5 computers, but they're all in the office ATM.  So what is it that you are doing, and why might I want to do this too?

---

