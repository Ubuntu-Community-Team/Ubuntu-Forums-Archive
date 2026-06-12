---
title: "Sound juicer mp3 file sizes"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by fatphilthethird on 2007-03-16
Hi

Can anyone help please; why am I getting such large file sizes, 20+MB for one track, using Sound Juicer to rip to mp3?

I've got a profile set up with the following in GStreamer Pipline:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=medium

Ideally I'd like to have a minimum bitrate of 192 if possible. I can get the file size down using Grip or RipperX but they are so slow compared to Sound Juicer.

Cheers

fat

---

### Post by mcduck on 2007-03-16
I don't know about Soundjuicer, but Grip is pretty fast if you only disable Paranoia & Extra Paranoia (and enable running in 2 threads if you have dual core CPU) ;)

---

### Post by plainjane on 2007-03-16
I am very new to all this, but I can tell you out of The Official Ubuntu Book the GStreamer Pipeline is:
           audio/x-raw-int,rate=44100,channels=2 ! lame name=enc 

so basicly exactly what you have except for the preset=medium on the end.  I seem to recall reading somewhere that this was the setting for 192 bitrate, but I could be wrong.

---

### Post by fatphilthethird on 2007-03-17
Hi

> **mcduck said:**
> I don't know about Soundjuicer, but Grip is pretty fast if you only disable Paranoia & Extra Paranoia (and enable running in 2 threads if you have dual core CPU) ;)

I suspect this is a dumb question, but how do I disable Paranioa & Extra Paranoia in Grip? Do you mean select something else in the Ripper dropdown under Config > Rip > Ripper? Also, it's not the ripping side that's slow, it the encoding part that takes by far the most time.

[B]
plainjane[/B]

I just tried that and still got a file size of about 30mb for one track. The preset=standard part came from [this ubuntu doc]("https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58"). I've also tried a couple of the other entries on there and still end up with a similar file size.

Thank you both for replying

fat

---

### Post by mcduck on 2007-03-17
> **fatphilthethird said:**
> Hi

I suspect this is a dumb question, but how do I disable Paranioa & Extra Paranoia in Grip? Do you mean select something else in the Ripper dropdown under Config > Rip > Ripper? Also, it's not the ripping side that's slow, it the encoding part that takes by far the most time.


In Config/Rip/Ripper there are check boxes for 'Disable paranoia', 'Disable extra paranoia', 'Disable scratch detection' and 'disable scratch repair'. These have huge impact on your ripping speed.

If encoding is slow, try some other encoder. (I'm using LAME myself, and encoding is faster than ripping..) Also, like I mentioned, for dual-core CPU's change the 'Number of CPU's to use' to 2 in Config/Encode/Options.

---

### Post by fatphilthethird on 2007-03-17
> **mcduck said:**
> In Config/Rip/Ripper there are check boxes for 'Disable paranoia', 'Disable extra paranoia', 'Disable scratch detection' and 'disable scratch repair'. These have huge impact on your ripping speed.

Cool, have tried that and the ripping is a lot quicker, cheers

> **mcduck said:**
> If encoding is slow, try some other encoder. (I'm using LAME myself, and encoding is faster than ripping..) Also, like I mentioned, for dual-core CPU's change the 'Number of CPU's to use' to 2 in Config/Encode/Options.

I'm using LAME too, I'll have a play with some others, see if that makes a difference. 

Dual-core CPU's? I wish...

Thanks for replying, appreciated.

Fat

---

### Post by jimarko on 2007-03-20
> **fatphilthethird said:**
> Hi

Can anyone help please; why am I getting such large file sizes, 20+MB for one track, using Sound Juicer to rip to mp3?

I've got a profile set up with the following in GStreamer Pipline:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=medium

Ideally I'd like to have a minimum bitrate of 192 if possible. I can get the file size down using Grip or RipperX but they are so slow compared to Sound Juicer.

Cheers

fat

Howdy!

I've been flicking briefly thru the replies and havent seen an answer for the original question regarding the size of imported tunes :)

Does anyone know an encoding 'sweet spot' to reduce the size of a 'juiced' mp3?

Thanks :)

---

### Post by zvacet on 2007-03-21
>  audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux
change bitrate to 192

---

### Post by fatphilthethird on 2007-03-22
> **zvacet said:**
>  	
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux

change bitrate to 192



Yup, tried that, still getting file size of 20MB+ for one track. Can you tell me what file size you get when you use those settings?

Basically, I seem to have tried most variations on that pipeline but still end up with huge file size in Sound Juicer. What kind of sizes do other people get on average?

Thanks

Fat

---

### Post by AlistairH on 2007-03-25
I've just tried ripping mp3s with Sound Juicer for the first time so I'm not at all sure what settings I should have for the pipeline - I've just been copying those listed in the thread and elsewhere.

An 9 minute track is coming out at 85MB ! It won't play in Rythmbox - it crashes instead.

I'll carry on investigating and let you know if I discover what's wrong.

---

### Post by fatphilthethird on 2007-03-26
Cheers Alistair. I find it very odd that the default ripping software in Ubuntu is just so bad at the job (85MB for 9 mins?!?!!!? Crazy numbers). 

It must be a setting us noobs have wrong somewhere...

Fat

---

### Post by wj32 on 2007-03-26
OK, here is a checklist:

* You've got the bad and ugly plugins for gstreamer installed. Including LAME.
* You've added the pipeline
* You've selected the pipeline/format in Sound Juicer
* You've... tried 10 million times and it still gives you 20mb files. It kinda sounds like you're using FLAC, or it isn't encoding MP3s but WAVs. Still, that's my prediction.

---

### Post by fatphilthethird on 2007-03-26
Hi wj32

Nope, they are definitely mp3s. They've got a mp3 file extension and everything ; )

As stated in my original post, when I use ripperX or grip I get a reasonably sized mp3. This is what makes me think the problem lies with Sound Juicer, 

Why don't I just use ripperX or Grip? They take sooooooooooo long to rip a cd compared to Sound juicer

Cheers

Fat

---

### Post by wj32 on 2007-03-26
Just to make sure, have you got *everything* ticked in the checklist? Just to make sure :)

---

### Post by zvacet on 2007-03-26
Look at this page for preset.I think(memory doesn´t serve me well) I did it like this
```
lame --preset standard fast - mp3
```
To be sure look help page

---

### Post by ca03jon on 2007-04-25
I was struggling for ages to get sound juicer to rip mp3s at a reasonable size.  I have now got it working by installing gstreamer0.10-plugins-ugly-multiverse (install it via Synaptic).  In the Gstreamer pipeline box (under the mp3 profile) I put the following: 

audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192

and it worked.

The help section in sound juicer tells you to put the following in:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux

To adjust the size of the mp3 just change the bit rate.

Hope this helps

---

