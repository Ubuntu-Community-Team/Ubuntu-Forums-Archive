---
title: "Front Mic not working"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by futuroimperfetto on 2008-01-20
Hello,

I'm trying to make Ubuntu detect my front mic, so that I can use it with Skype. However, I seem to have success only when I use an external microphone (which works normally).

I've tried to type

```

alsamixer

```

and I learn that my card is a "HDA-intel" and my chip is a "Realtek ALC882". If I raise the bar of "front mic", but I cannot get it to work under Gutsy. Is it possible that it is not detected?

Alternatively, is there any package I could install to fix this or commands I might try?

Thank you

---

### Post by sirgogo on 2008-01-23
Hello Fetto,

Honestly, I do not know what is going on, as there can be many sound problems. But, I suggest you go to --->System--->Preferences--->Sound. From there you should probably make sure that all of your settings allow for microphone activity (It would be best if you take a screenshot of that window, Alt + PrintScreeen). Also, open up the sound preferences (from taskbar, its easy to just double click on the speaker symbol) and check to make sure your microphone/capture X is not muted.

Sorry if it doesn't work! Good luck!

---

### Post by futuroimperfetto on 2008-01-24
Hi Sirgogo,

 Thank you for you answer. I tried both of the things you suggested. If I open the volume control by clicking on the speaker on the taskbar, everything looks OK.

However, if I go to System -> Preferences -> Sound and I test the "sound capture" feature, I get an error! This is good, as I have something to start with!

I don't yet know what to do with this error message, but I'll look for info about it later today. Meanwhile, I'm posting the "sound preferences" and the "error message" I have.

My error message says

```

Failed to construct test pipeline for 'gconfaudiosrc ! 
audioconvert ! audioresample ! gconfaudiosink profile=chat'

```

Not sure it may be of help, but my laptop is an Asus Z96J with an Intel Core Due 2:16Mhz, ATI X1600 Mobilty graphic card.

Thanks for the suggestions!

---

### Post by BandD on 2008-01-25
I don't know if you've looked through these threds yet, but they may help:

[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]https://help.ubuntu.com/community/HdaIntelSoundHowto
[/URL]
[http://ohioloco.ubuntuforums.org/sho...d.php?t=530374]("http://ohioloco.ubuntuforums.org/sho...d.php?t=530374")

I don't have this particular chip set, I've got an Intel ICH6 family with a Realtek ALC260 codec and had some trouble with the mic. I finally got it working by editing /etc/modprobe.d/alsa-base with an option where model=acer (even though I'm on a Sony Vaio) at the bottom of the file.

---

### Post by sirgogo on 2008-01-26
> **futuroimperfetto said:**
> 

My error message says

```

Failed to construct test pipeline for 'gconfaudiosrc ! 
audioconvert ! audioresample ! gconfaudiosink profile=chat'

```


Hey Fetto,

Sorry, I was for a while. Hmm. I need to look into that a little more, but judging from that message it looks like there may be a problem with your test pipeline. You might want to try installing/removing-then-rebooting-then reinstalling (synaptic package manager this) "esound" "pulseaudio", or any modules related to this. I'll look into it a bit more when I get back.

Good luck!

---

### Post by cthulhu666 on 2008-02-01
Have a look here: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

