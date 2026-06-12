---
title: "Sound over network"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Kit.wm on 2008-01-28
Hey, I'm a huge fan of Ubuntu and Linux (especially Amarok) and as a gamer I'm generally running Windows on my Desktop and Ubuntu on my laptop.

I've been using two cables and an adapter to get sound from my headphones plug on my laptop to the line-in on my desktop. This decreased the audio quality somewhat, but I was fine with it.

It wasn't until I recently made a separate computer as a MythTV backend (also Ubuntu) and I've been using my laptop to watch TV.

The low quality of the audio is starting to get to me now and I am seeking a solution to the problem of playing the audio from my Windows machine from my Linux laptop.

In conclusion, Sound from Ubuntu sends over network to Windows machine. Or the opposite, but this is less preferable.

I can't just use the speaker on my laptop because, 1. The speakers suck, and 2. I use headphones and I would have to have the speakers loud to hear over my headphones and would annoy others.

---

### Post by emarkd on 2008-01-28
I've never heard of anything like this, but that doesn't mean it doesn't exist.  What is your complaint with the cable setup you've got?  I would think that running the line-out of the laptop to the line-in of the desktop would work well.

---

### Post by HermanAB on 2008-01-28
You can easily pipe sound around the LAN using Netcat and Sox.

Just google for this: "pipe sound with netcat and sox"

Cheers,

Herman

---

### Post by Kit.wm on 2008-01-28
The cables I'm using are of very poor quality and the sounds don't turn out well, I think the cards/chipsets are not that great either.

I look thorough the first few pages of the google search of pipe sound with netcat and sox, I could not find what I was looking for.

---

### Post by shadow_slicer on 2008-01-28
This can probably be done more easily with Esound (at least streaming from linux to windows...).

I checked google and the following links appear to be relevant:

[http://www.liquid-reality.de/main/projects/esound](http://www.liquid-reality.de/main/projects/esound)
[http://linuxreviews.org/howtos/sound/](http://linuxreviews.org/howtos/sound/)

In short download the cygwin version of esound for windows.
Run 'esd.exe -tcp -public' to start the sound server on windows (from the command line).
Then on the linux laptop use 'esddsp --server=<windowsIpAddress> <name of audio program>' (from the command line).

---

### Post by Kit.wm on 2008-01-28
That doesn't work, I get errors,

> ERROR: ld.so: object '/usr/lib/libesddsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.

I'm not sure if thats fatal though.

That error is on the laptop (ubuntu) btw.

---

### Post by shadow_slicer on 2008-01-29
That's strange. Perhaps your copy of esd is broken.

Let's check the dynamic linking:

ldd /usr/lib/libesddsp.so.0 /usr/lib/libesd.so.0

If there is no problem it will look something like this:

```
/usr/lib/libesddsp.so.0:
        linux-gate.so.1 =>  (0xb7fac000)
        libesd.so.0 => /usr/lib/libesd.so.0 (0xb7f7b000)
        libdl.so.2 => /lib/libdl.so.2 (0xb7f77000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7ec0000)
        libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb7e97000)
        libm.so.6 => /lib/libm.so.6 (0xb7e71000)
        libc.so.6 => /lib/libc.so.6 (0xb7d41000)
        /lib/ld-linux.so.2 (0x80000000)
        libpthread.so.0 => /lib/libpthread.so.0 (0xb7d29000)
/usr/lib/libesd.so.0:
        linux-gate.so.1 =>  (0xb7f61000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7e7e000)
        libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb7e55000)
        libm.so.6 => /lib/libm.so.6 (0xb7e2f000)
        libc.so.6 => /lib/libc.so.6 (0xb7cff000)
        libdl.so.2 => /lib/libdl.so.2 (0xb7cfb000)
        libpthread.so.0 => /lib/libpthread.so.0 (0xb7ce4000)
        /lib/ld-linux.so.2 (0x80000000)
```

If any of the arrows point to 'not found', then your esd is broken. You could try installing the package containing the dependency you're missing, or maybe apt would find it if you reinstalled esound.

---

### Post by MonkeeSage on 2008-04-09
Since version 0.2.36-1, libesd-alsa0 puts libesddsp.so.0 in /usr/lib/esound rather than /usr/lib (fixes debian bug: [#220058]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=220058")). But the LD_PRELOAD variable in the esddsp script was not updated.

You can fix the script manually with the following command:

```
sudo sed -i -e 's:lib/libesddsp.so.0:lib/esound/libesddsp.so.0:' /usr/bin/esddsp
```


**Update:** Submitted Ubuntu bug: [#214465]("https://bugs.launchpad.net/ubuntu/+source/esound/+bug/214465") and a patch.

---

### Post by Tatty on 2008-04-09
I believe PulseAudio offers the functionality you are looking for.  If set up correctly it will list all computers in your network with pulseaudio installed, and you can select any of them to pipe your sound to.

I tried to install it early last year but failed to get it working myself.

 I read it was being included by default in Hardy Heron, but i dont know if that has happened or not.

---

