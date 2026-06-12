---
title: "Sound issue with a twist"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by gymsmoke on 2006-03-26
I have two sound cards according to alsa.  1 is that Intel on-board, and the other is a usb device (I have a webcampro 3000 that does audio/video).

After the Ubuntu installation, everything worked great.  I wanted to give skype a try, so i installed that, but the webcam audio didn't work.  I asked in the forums, and was directed to a "HOW TO" where I followed the "How I got skype working" thread.

Now, I have no sound at all.

I removed the dsp hijacker package, and skype, reset alsamixer, but still - nothing.

Is there someone here who can point me in a direction to try and hunt this down?

Thanks for your help.

---

### Post by gymsmoke on 2006-03-26
update - i ran lsmod and lspci | grep -i audio.  Here are the results:

lsmod (showing sound portion)

snd_usb_audio          68160  0
snd_usb_lib            13824  1 snd_usb_audio
snd_rawmidi            22816  1 snd_usb_lib
snd_seq_device          8204  1 snd_rawmidi
snd_hwdep               8608  1 snd_usb_audio
pwc                    82036  0
videodev                9344  1 pwc
v4l2_common             5888  1 pwc
usblp                  11776  0
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

lspci | grep -i audio:
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

---

### Post by therunnyman on 2006-03-26
Hi gymsmoke,

I'm the sort of person who forgets little things, like load a piece of media when burning something, or plugging the speakers into my soundcard.

Just so I know, didja check:

Your master/PCM volume in alsamixer (or in the GUI, double clicking the little speaker icon)?

Is the proper device selected?

Are the speakers plugged in?  Turned on?  Tuned in?  Dropped out?

Did you poke around "Sound" in the System-->Preferences-->sound menu?  (Once, I found my sound problems corrected by checking the "Enable Sound Server Startup" and selecting a default device from the dropdown).

You're obviously competent, so I feel a little silly asking those questions.  Might be worth a look though.

therunnyman

---

### Post by gymsmoke on 2006-03-26
Runny~
Sound worked fine after the initial install (see op).

I was able to go back, reconfigure alsa, and get the sound basically running again.  However, the "master" no longer controls sound at all.  Only PCM.

I'm wondering if it has something to do with the order of sound cards that alsa sees.
According to lsmod, it sees the usb device as 0, and the on-board as 1.

Don't know if that makes a difference or not.  If you or anyone here knows that it does, and how to reverse it, I'd really appreciate knowing...

---

### Post by therunnyman on 2006-03-26
Uh, lessee...

What about yanking the USB device, just for the moment, then restarting.  I know that'll put your onboard sound at ALSA 0 for sure.  Fiddle that way for awhile, maybe, see what happens?

therunnyman

---

