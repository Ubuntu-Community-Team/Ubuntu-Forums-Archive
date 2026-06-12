---
title: "OSS device &quot;/dev/dsp&quot; is already in use by another program."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-06-05
OSS device "/dev/dsp" is already in use by another program. = how do i fix this problem guys?? please assist me , thanks!

---

### Post by rck_hitokiri on 2006-06-05
please help me! i cant play anything on my pc and im dying without sounds..... please help out....

---

### Post by hw-tph on 2006-06-06
There are a few different workarounds. First off, this problem shows up because the OSS audio interface /dev/dsp can only be used by one application at a time - first application that claims it owns it until it closes the "file" /dev/dsp.

The most common workaround is using a sound server, and in Ubuntu there is the esound (a.k.a. esd) sound server. This application will mix several audio streams into a single stream which is fed to the sound card.

You can also set up software mixing with Alsa and its Dmix plugin. This is described on several different places, like [in the Alsa wiki](http://alsa.opensrc.org/DmixPlugin). When you use Dmix software mixing you must disable sound server startup because esound will claim /dev/dsp.

I set up all applications that have sound options to use Alsa instead of esound or OSS (**mplayer -ao alsa** and so on) and I have this in my /etc/asound.conf to actually enable software mixing:```
pcm.card0 {
	type hw
	card 0
}

pcm.!default {
	type plug
	slave.pcm "dmixer"
}

pcm.dmixer {
	type dmix
	ipc_key 1025
	slave {
		pcm "hw:0,0"
		period_time 0
		period_size 2048
		buffer_size 32768
		rate 48000
	}
	bindings {
		0 0
		1 1
	}
}
```

Håkan

---

