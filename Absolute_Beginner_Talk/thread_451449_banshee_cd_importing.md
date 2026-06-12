---
title: "banshee cd importing"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-05-22
Hello,

I recently found the banshee music player.  I like it's similar interface to iTunes, plus it's iPod syncing abilities and a few other nice extras.  I just had a quick question I can't figure out.  Is it possible to import music in an mp3 format?  In the preferences it lists FLAC, Ogg, Waveform PCM, and Wavpack.

Thanks,

Helixed

---

### Post by helixed on 2007-05-22
bump

Helixed

---

### Post by helixed on 2007-05-22
Can anybody help me?

Helixed

---

### Post by dogskull on 2007-05-30
Same question.  Cannot find an option to import CDs to mp3 in Banshee, but I know that it supports it.  I'm sure it's a question of a config file somewhere.  Please tell us!!

---

### Post by jlc on 2007-05-31
Make sure you have some lame

```

sudo aptitude install gstreamer0.10-lame lame lame-extras

```

Check your gnome audio settings

```

$ gnome-audio-profiles-properties

```

You should see CD Quality, MP3

Highlight it,
Edit

Make sure it has **Active** checked.

Start Banshee backup and check the import properties again.

---

### Post by ncappel1 on 2007-05-31
Does your music absolutely **have** to be in mp3 format? Use open source! :)

---

### Post by dogskull on 2007-05-31
> **jlc said:**
> 
Check your gnome audio settings

```

$ gnome-audio-profiles-properties

```

You should see CD Quality, MP3

Highlight it,
Edit

Make sure it has **Active** checked.

Start Banshee backup and check the import properties again.

That might be my problem, thanks.  I didn't know about the audio settings.  I'll check it when I get home.

---

### Post by dogskull on 2007-05-31
> **ncappel1 said:**
> Does your music absolutely **have** to be in mp3 format? Use open source! :)

This is not a helpful response!  Open source is great, and my iaudio X5 supports ogg, but my wife's Zen is tied to mp3.

---

### Post by lyceum on 2007-05-31
A little of topic, but... which do you think is better, iPod or Zen? or are they about the same?

---

### Post by ncappel1 on 2007-05-31
Ah, I understand, Didn't intend to be condescending. Apologies

---

### Post by dogskull on 2007-05-31
ncappel1: No problem

lyceum: I've not had an ipod, but I think they're probably better than the zen.  I've had a Zen Microphoto (which I dropped!) and my wife has a Zen Sleek.  I really don't like the interface at all.  Another plus on the ipod side is that you can convert it to Rockbox, which is open source and plays many more formats.  The Zen has yet to be opened up to that process.  I prefer the iaudio players in general, but my needs are very particular.

---

### Post by lyceum on 2007-05-31
> **dogskull said:**
> ncappel1: No problem

lyceum: I've not had an ipod, but I think they're probably better than the zen.  I've had a Zen Microphoto (which I dropped!) and my wife has a Zen Sleek.  I really don't like the interface at all.  Another plus on the ipod side is that you can convert it to Rockbox, which is open source and plays many more formats.  The Zen has yet to be opened up to that process.  I prefer the iaudio players in general, but my needs are very particular.

Cool, thanks for the info!

---

### Post by dogskull on 2007-05-31
> **jlc said:**
> Make sure you have some lame

```

sudo aptitude install gstreamer0.10-lame lame lame-extras

```

Check your gnome audio settings

```

$ gnome-audio-profiles-properties

```

You should see CD Quality, MP3

Highlight it,
Edit

Make sure it has **Active** checked.

Start Banshee backup and check the import properties again.

Hey jlc, this didn't work for banshee.  I still can't see the option for mp3.  I have all the xml files in /usr/share/banshee/audio-profiles, which seems to be where they're organized, but it doesn't show up in the UI.  

But now that I know about the audio settings, I can just use Sound Juicer.  I would like to be able to edit the lame preferences with menus, instead of gstreamer code, but overall I think that Juicer is a nicely designed application.  I'm sure I'll get banshee straightened out eventually...

---

### Post by neorou on 2007-06-12
Hi, try installing these 2 gstreamer packages:

gstreamer0.10-plugins-bad-multiverse

gstreamer0.10-plugins-ugly-multiverse

If it isn't working and there is no obvious solutions, throw libraries at it. Who knows...

---

