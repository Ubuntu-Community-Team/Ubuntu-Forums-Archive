---
title: "MONO- sound in Debian Testing"
date: 2012-09-26
forum: Any Other OS
---

### Post by october1917 on 2012-09-26
I have an ASUS P5N73-CM with a VIA VT1708B 8 -Channel High-Definition Sound Card (as it says in the manual). Anyway my lspci gives

Audio device: NVIDIA Corporation MCP73 High Definition Audio (rev a1)

I've plugged everything right (main jack plugged to the Lime port / but no difference wherever else I plug it) [see image](http://www.insomnia.gr/index.php?app=core&module=attach&section=attach&attach_rel_module=post&attach_id=168996)  but there is no stereo sound. The sound comes out of both 2 speakers and the woofer (Logitech X210) but I only listen the one of the 2 recorded channels.

For example I cannot hear the violin/harmonica in the song [Hurricane](http://www.youtube.com/watch?v=7zdN-oYRP0A) at 0:11 neither in utube nor from the local flac file!!!

It's not a matter of equalization, I've tested (that's my job).
My speaker test gives the following:

```
-$ speaker-test -c 2

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 11.170204
 0 - Front Left
 1 - Front Right
Time per period = 11.182266
 0 - Front Left
 1 - Front Right

```
But when it runs the 0 - Front Left speaker test there is NO sound from NONE of the two speakers. When it runs the 1 - Front Right speaker test noise comes out from BOTH!!!

Is there something I can fix in the configuration? Please help!

---

### Post by lisati on 2012-09-26
*Thread moved to **Other OS/Distro Talk**.*

Although Ubuntu is based on Debian, there are diffeences, which have a habit of sneaking in to confound things when you're least likely to expect it.

---

### Post by UltimateCat on 2012-09-26
I have Debian Squeeze 6.0 and had a sound issue as well.

I solved it but not sure if it will solve yours but you can try adjusting the alsa mixer.

Open the terminal and type:
```
alsamixer

```
Hit <Enter>
When you do a large black/grey window will open and you'll see colums.
Raise up the controls on all of the columns each at a time to ensure the mic and etc. are all turned up.

Mute and um-mute each column at the bottom of each bar.
When the column is muted the symbols in brackets will look like this:
```
{mm}

``` 
When the column is un-muted it will look like:
```
{oo}

```

When done adjusting all of the columns, muting and UN-muting each close the alsa mixer and close the terminal.

It worked for me and now I have sound.
Hope this helps. Here's the video I learned from-
[http://www.youtube.com/watch?v=JuEEEHcHxEE](http://www.youtube.com/watch?v=JuEEEHcHxEE)

---

### Post by october1917 on 2012-09-26
Thanks friend, but that's not the issue for me. Thanks anyway!

---

