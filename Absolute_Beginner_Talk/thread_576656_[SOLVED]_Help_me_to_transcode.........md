---
title: "[SOLVED] Help me to transcode........"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by applegrew on 2007-10-15
I am trying to capture video from my TV Tuner card, but unfortunately it doesn't have the audio out, i.e. I can't use /dev/dsp to capture sound. I have re-routed the **audio out of the tv-tuner to the line-in of my sound** card using a cable (provided vy the tv-tuner itself).

Now the problem is how do I capture the sound. The video is getting recored with no problem. Below is the code I am using currently.

```
transcode \
        -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
	-g 640x480 \
	-p /dev/audio \
        -i /dev/video0 \
	-e 32000,16,2 \
	-Q 3 \
        -N 0x55 \
        -J pp=hb/vb/al/tn/ci,resample,smartyuv,pv \
        -w 4000 \
        -y ffmpeg \
        -F mpeg4 \
        -o TheRecordedFile.avi \
        --avi_limit 1536 \
	--lame_preset standard \
	--encode_fields t

```

I can't indeed hear the audio in the preview window, but it doesn't get recorded.

---

### Post by applegrew on 2007-10-15
help pls. This is driving me crazy. :(

---

### Post by applegrew on 2007-10-15
This time I was toying with mencoder using the command shown below but still there is no no sound. :(
```

mencoder -o out.avi \
 -ovc lavc -lavcopts vcodec=msmpeg4:vbitrate=5000:vhq \
 -oac mp3lame \
 -vf crop=688:560:14:0,expand=704:576,dsize=4/3 \
 -ofps 25 -srate 48000 \
 -lameopts preset=standard \
 -tv driver=v4l2:norm=PAL:outfmt=yv12:input=0:width=640:height=480:amode=1:adevice=/dev/dsp \
 tv://

```

---

### Post by applegrew on 2007-10-15
oops the above command had problem it should be "width=704:height=576" and not "width=640:height=480". Anyway it will still **not work**.
OK I was now trying
```

mencoder -o out.avi  -ovc lavc -lavcopts vcodec=msmpeg4:vbitrate=5000:vhq  -oac mp3lame  -vf crop=688:560:14:0,expand=704:576,dsize=4/3  -ofps 25 -srate 48000  -lameopts preset=standard  -tv driver=v4l2:norm=PAL:outfmt=yv12:input=0:width=704:height=576:amode=1:alsa:adevice=hw.1  tv://

```
beacuse my alsa device 1 is probably the line-in device. Anyway running the above code makes mencoder throw "Error reading audio: Input/output error" error message continuously and it stops responding. I don't know what's going on.

---

### Post by applegrew on 2007-10-15
just came back to post that it has been fixed! I was dumb enough to not see that Line-In audio capture was not selected but instead Microphone was selected (which has no input). Anyway now I can record the sound too. :D

But, the sound is getting very distorted. I will be posting this in a new thread with the sample sound.

---

