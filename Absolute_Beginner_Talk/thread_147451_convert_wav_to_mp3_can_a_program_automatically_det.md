---
title: "convert wav to mp3: can a program automatically determine optimal mode (bitrate/khz}?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-03-20
RE: converting the WAV file (that vsound outputs) to mp3
I have just used vsound to record a realaudio stream. It saved the file as a wav file.

Is there a way to let the mp3 converter (e.g. lame) automatically
decide the encoding/conversion settings?

Let's  say a streaming realaudio file which we record in vsound is 32
kbps. I know that the realaudio file is 32 kbps because that's what the realplayer program tells me in the statusbar. Is there a way to get the wav-to-mp3 converter to decide by itself to convert into the optimum? In other words, to convert the wav file into a 32kbps mp3 file? Because a higher bitrate is won't produce higher sound quality, would it? And anything lower would degrade the sound quality, right? Of course, bitrate is not the only thing I'd like the converter to determine. I'd like it to determine the optimum frequency (kHz) too, and other audio settings that I may not know about.

Or, maybe there's a program that has such intelligence. If so, please advise.

---

### Post by derelict on 2006-03-20
[QUOTE=hanzj]
Is there a way to let the mp3 converter (e.g. lame) automatically
decide the encoding/conversion settings?[/quote]
I think what you may want to use in LAME is the Variable Bit Rate mode, though it may not be exactly what you asked for :-k 

>  I know that the realaudio file is 32 kbps (...) a higher bitrate is won't produce higher sound quality, would it? 
Keep in mind that 32Kbps on RealAudio is different from 32Kbps on MP3, just as 64Kbps of WMA is different from 64Kbps on MP3 and son on when comparing with other codecs like AAC. It's the same amount of information per second but the encoding is different, therefore the quality isn't comparable that way.

---

### Post by hanzj on 2006-03-20
[QUOTE=derelict]I think what you may want to use in LAME is the Variable Bit Rate mode, though it may not be exactly what you asked for.
[/QUOTE]
Variable Bit Rate may help. But is that all I need to do? If I run a lame command to encode  in VBR, will this automatically mean that lame will figure out, all by itself, the optimum (no more, no less) settings?

> 
Keep in mind that 32Kbps on RealAudio is different from 32Kbps on MP3, just as 64Kbps of WMA is different from 64Kbps on MP3 and son on when comparing with other codecs like AAC. It's the same amount of information per second but the encoding is different, therefore the quality isn't comparable that way.

Okay. If I can find a command/program that can discern all this, I won't even have to know the audio quality/settings of the incoming audio.

---

### Post by derelict on 2006-03-20
As far as my knowledge goes LAME doesn't automatically detect the "quality" that the source file is at. 
Roughly, running LAME in VBR mode will compress the file less on segments with more data and more on the segments with less data, achieving a better quality /file size balance. You can specify thresholds for minimum and maximum admissible bitrates; "lame -v -b 128 -B 256 source.wav target.mp3" will encode the file in VBR with minimum and maximum bitrates of 128 and 256 respectively.
If VBR is somewhat helpful, you should actually look into using the ABR mode (as recommended by LAME): "lame --abr 192 source.wav target.mp3" will encode the file at around 192kbps, lowering when possible and increasing when needed.

---

### Post by mackinax on 2006-03-20
**VBR** encoding targets a certain (perceived) level of quality, and adjusts the bitrate as needed to maintain that targeted quality. The bitrate range (and file size) can vary greatly, depending upon the dynamics of the source material.

**CBR** encoding targets bitrate, and bitrate only, and the quality will vary to accommodate it. Constant bitrate encoding ensures that all files of the same bitrate will have the same file size per given unit of time. (and sometimes it is necessary to use CBR when dealing with buggy playback hardware or software. But any player that is fully compliant with mp3 specifications will not have trouble with VBR or ABR files.)

**ABR** is like a compromise between VBR and CBR, to be used when both quality and bitrate/filesize are matters of concern. Though the file size difference, between ABR and VBR encodings of a similar perceived quality, is usually not that big. LAME's ABR presets might also, in many cases, deal better with lower bitrate encoding than VBR presets, because of the different encoding algorithms just having different strengths and weaknesses in different areas.

Whichever method is used, the user must decide upon the appropriate quality or bitrate setting to target.

As for a recommended setting, I can't help much in that regard because transcoding files from such a situation is not something I ever do, and in general I rarely delve into low bitrate encoding. A site that is devoted to digital audio technology, like [http://www.hydrogenaudio.org/](http://www.hydrogenaudio.org/), would be a good place to seek advice. If I had to try it myself (guess), I'd try some encodings at around "--abr 64", "--abr 80", or "--abr 96" ... and see how they sound.

---

