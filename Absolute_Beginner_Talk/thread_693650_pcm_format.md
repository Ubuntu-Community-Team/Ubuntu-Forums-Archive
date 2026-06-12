---
title: "pcm format"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by kurian on 2008-02-11
hi,

i have converted a mp3 file into the format defined in the manner shown below using maplay,

hex : ASCII  hexadecimal  [24-bit] linear PCM, stereo interleaved, one
         sample per output line

1.in the o/p file i could see 6 positions with each having 0-f positons....does that mean 6*16 bits....then how its called a 24 bit pcm.....

2.one more doubt, is the first line goes to left channel and second line in the file goes to the right channel and so on...?

3. is the  entire  samples are  positive in this o/p???

is it possible to use this information to play the music  if  iam redirecting this to a dac ic ? if  so  please tell me how to.... iam intrested in mono and not sterio playback


the first few lines of this hex file is also given below :

 # 2 channels, 44100 Hz, 24-bit samples
000001
000001
FFFFFF
FFFFFF
000000
000000
000000
000000
FFFFFF
FFFFFF
000001
000001
000000
000000
000000
000000
000000
000000
000001
000001
FFFFFF

---

### Post by lloyd_b on 2008-02-11
> **kurian said:**
> hi,

i have converted a mp3 file into the format defined in the manner shown below using maplay,

hex : ASCII  hexadecimal  [24-bit] linear PCM, stereo interleaved, one
         sample per output line

1.in the o/p file i could see 6 positions with each having 0-f positons....does that mean 6*16 bits....then how its called a 24 bit pcm.....

There's a big problem with your math.  Hex 0-F represents 16 possible values, which requires 4 bits to encode.  4 bits per digit * 6 digits = 24 bits.

> 2.one more doubt, is the first line goes to left channel and second line in the file goes to the right channel and so on...?

Correct.  "stereo interleaved" means precisely that - one sample for the first channel, then a sample for the second channel, so on and so forth.  Sorry, I don't remember if it's "left then right" or "right then left".  

> 3. is the  entire  samples are  positive in this o/p???

Audio can be encoded with either signed (positive and negative) or unsigned (positive only) values.  From your data, I *suspect* you're looking at 24 bit *signed* (those FFFFFF's would be -1, rather than the 16M if they were 24 bit unsigned).  A swing from 0 or 1 to -1 is quite believable, while swings from 0 or 1 to 16M would be a bit odd (not impossible, mind you, just unusual).

> is it possible to use this information to play the music  if  iam redirecting this to a dac ic ? if  so  please tell me how to.... iam intrested in mono and not sterio playback

Sorry, that question is way out of my depth.  

Lloyd B.

P.S. - this question really doesn't belong in the "Absolute Beginner" Forum.  Probably the "Programming" Forum would be a better choice.

---

