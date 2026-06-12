---
title: "which digital format should I convert my audio CD for use on comp &amp; iPod: mp3 or m4a?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-07-07
Hello, 
When I put in an audio CD into my drive, Sound Juicer CD extractor pops up. Under Preferences, I can choose my output format. Some that I can readily choose are:[LIST]
[*]CD Quality, AAC (MPEG-4 audio)
[*]CD Quality, Lossless (FLAC Audio)
[*]CD Quality, Lossy (Ogg Multimedia)
[*]CD Quality, MP3 (MP3 Audio)[/LIST]Is MPEG-4 audio better than MP3 audio? At first glance, I would suppose it is, because the number 4 is greater than the number 3. 
I extracted the audio CD into m4a and mp3. The mp3 files play fine, but with the m4a files, they "stutter".   Why is that?

Here's what I would like to do with the audio files: I want to be able to listen to it on my computer and on my video iPod. According to [http://www.apple.com/ipod/specs.html](http://www.apple.com/ipod/specs.html), the iPod supports these audio formats:  AAC (16 to 320 Kbps), Protected AAC (from iTunes Store), MP3 (16 to 320 Kbps), MP3 VBR, Audible (formats 2, 3 and 4), Apple Lossless, AIFF and WAV.


I understand that OGG is opensource and there's no legal restrictions with this format. But my iPod (at least the way it is now) won't be able to play OGG files.

---

### Post by p_quarles on 2007-07-07
No, the iPod (and most music players) can't play OGG. As for MP3 vs. MP4 (=M4a), it doesn't really matter. MP4 is more advanced, but I've read that sound quality depends more on the bit rate than on the encoding method. So, an MP3 at 128 won't be noticeably different from an MP4. 

That's just my opinion, though. I could have a terrible ear, for all I know.

---

### Post by Ted_Smith on 2007-12-26
> The mp3 files play fine, but with the m4a files, they "stutter". Why is that?

Same here - would be interested to know why?

---

### Post by wh0rd on 2007-12-26
You should consider Lossless FLAC format. That way you won't lose the quality of your music but at the same time if you need to convert them to a lower format like mp3 then you still have a higher quality to convert from.

---

### Post by funrider on 2007-12-26
mp3 - virtually supported by everything!

---

### Post by Ted_Smith on 2007-12-26
I'm aware of the various trade offs and have chosen MP3\4 @ 320 bit rate for my player, thanks anyway. 

I was wanting to know what causes the stuttering of the MP4 using Sound Juicer, specifically. But then I realised it's not the music files themsevles, or my disk. It's the player. By default they're opened by Totem which stutters. But when I play them with mplayer or anything else they play fine. Problem solved. 

Cheers

Ted

---

### Post by disturbedite on 2007-12-26
if you're stuck with using mp3 vs mp4/m4a, definitely use m4a.  i know for a fact it support better sounding compression techniques & has far better options so it is more flexible.  (i.e.  surround sound support).  it also has higher compression, so you can get smaller file sizes, comparatively.

---

### Post by ericesque on 2008-01-02
I too am searching for my new standard for encoding.  I had been quite happy with MP3 @ 190kbps, but recently procured a set of Infinity Beta 50s and can now easily distinguish the lack of quality in those MP3s.  I find that I can even tell the difference between those MP3s and AAC @ 256kbps on my earbuds!

I can relate to the AAC stutter.  It plagues Rhythmbox as well.  I turned to Banshee and haven't looked back.  I believe gstreamer has a hard time dealing with AAC in general.  When used (via sound juicer) to encode AAC files, they don't play correctly in Windows either.

FLAC was recommended earlier in the thread.  Unfortunately, FLAC isn't supported by the iPod (sans rockbox).  I'm curious if Apple lossless is supported by Ubuntu.  If not, I may find myself going with AAC @ 320kbps.

---

### Post by ericesque on 2008-01-03
just an update:  Apple lossless uses a .m4a file extension-- the same as AAC.  They both play fine in Banshee.

---

### Post by mihai.ile on 2008-01-04
What you should do is rip the CD's in FLAC format because you don't loose quality.
When you are transfering the files to iPod Rhythmbox or Banshee can transcode the files on-the-fly into 128kb mp3 so that will work.

This is the best thing you could do, and is what I am doing right now. Of course there is the space problem for FLAC files but the sound quality and the fact that the music looses 0% quality is very good.
If some years from now decide to re-encode the entire library in other format just convert the FLAC files and you're done, but if you have them in mp3 or any format that looses quality you can't re-convert them without loosing even more sound quality

---

