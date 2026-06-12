---
title: "Need help getting my Emu 1212m working in ubuntu."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Anarchy965 on 2007-07-01
I'm still trying to get my soundcard (an Emu 1212m) working with alsa. I just reinstalled ubuntu because I had screwed something up and it wouldn't boot. So, I have a fresh feisty install now. There is an install guide ([here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=E-MU+1212m.&chip=CA0102%2C+FPGA&module=emu10k1-fpga")) on the alsa website but It's kind of confusing.

---

### Post by cleverselfreferentialname on 2007-07-05
I'll condense it for you.

You might need awesfx and ld10k1 and liblo10k1-0 installed.

sudo apt-get install awesfx ld10k1 liblo10k1-0.

Then, run the following:
modprobe snd-emu10k1-fpga
modprobe snd-pcm-oss
modprobe snd-mixer-oss
modprobe snd-seq-oss

Those load various linux kernel modules

if that doesn't work, you need to download all that alsa stuff and compile it.

Make the file /etc/modutils/alsa, maybe with:

sudo gedit /etc/modutils/alsa

and put the following in it:
        # ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-emu10k1-fpga
	# module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0
	
	# card #1
	alias sound-service-0-0 snd-mixer-oss
	alias sound-service-0-1 snd-seq-oss
	alias sound-service-0-3 snd-pcm-oss
	alias sound-service-0-8 snd-seq-oss
	alias sound-service-0-12 snd-pcm-oss

then run 'update-modules'

Put those linux kernel module names in /etc/modules, one a line.

snd-emu10k1-fpga
snd-pcm-oss

and so on.

You can do it, anarchy965. I know this because somebody who's going to help me take down the man isn't going to let his sound card beat him.

---

