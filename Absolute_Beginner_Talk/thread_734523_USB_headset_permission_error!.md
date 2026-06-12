---
title: "USB headset permission error!"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by bschleusner on 2008-03-24
Ok, I have been using a SB Live card and a Logitech USB headset succesfully for a long time now, but for some reason the headset quit working today. Rhythmbox gave me the error "Could not open resource for writing".

I checked so see if for some reason that I didn't have permission for the device by running VLC as root, and it worked perfect, but when I run it under my normal user account it won't let me. 

Any ideas for getting my permissions back?:confused:

---

### Post by slimdog360 on 2008-03-24
wait which device are we talking about, the headset or the sound card?

```
sudo chmod -R 777 /place/of/device/mount
```

will change the privliges, but I don't completely understand your question, that is, how can you have write permissions to a headset or a sound card?

edit: here is a link if you wanted to learn about that command
[http://catcode.com/teachmod/index.html]("http://catcode.com/teachmod/index.html")

---

### Post by bschleusner on 2008-03-24
I was talking about my USB headset. I don't know how it could have write permissions, but all the media players I am using all say the same thing. :(

How would I figure out where my headset is mounted?

---

### Post by slimdog360 on 2008-03-24
check the /mnt or maybe even /media folders.

---

### Post by bschleusner on 2008-03-24
It doesn't appear in any of those.

I don't know if it helps any, but here is the output of lsusb for it.
```
Bus 006 Device 004: ID 046d:0a01 Logitech, Inc. 
```

---

### Post by bschleusner on 2008-03-25
I have the debug output for vlc:

```

ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM dmix:Headset
```

---

