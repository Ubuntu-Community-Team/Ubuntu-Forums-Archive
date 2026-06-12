---
title: "What trick causes OGG files to autoplay on mouseover?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Rizlaw on 2007-04-08
There is a nice feature in Ubuntu 6.10 that causes OGG audio media files to automatically begin playing when you pause the mouse over the filename. Alas, most of my ripped CD's are kept as "flac" audio, so I'd like to know 3 things about this feature:

1. What program is responsible for the feature?
2. Can this easily be done for "FLAC" audio files?
3. If the answer to #2 is Yes, how would you go about doing it?

Thanks.

---

### Post by ComplexNumber on 2007-04-08
> **Rizlaw said:**
> There is a nice feature in Ubuntu 6.10 that causes OGG audio media files to automatically begin playing when you pause the mouse over the filename. Alas, most of my ripped CD's are kept as "flac" audio, so I'd like to know 3 things about this feature:

1. What program is responsible for the feature?
2. Can this easily be done for "FLAC" audio files?
3. If the answer to #2 is Yes, how would you go about doing it?

Thanks.
i believe its automatically enabled in nautilus. but just in case i' wrong, fire up naultilus and go to Edit -> Preferences -> Preview.

i don't know the answer to 2 and 3. it doest seem to work with flac. i supose you could install a program called soundconverter(you can install it via synaptic) ato convert the flacs to oggs.

---

### Post by Rizlaw on 2007-04-08
> **ComplexNumber said:**
> i believe its automatically enabled in nautilus. but just in case i' wrong, fire up naultilus and go to Edit -> Preferences -> Preview.

i don't know the answer to 2 and 3. it doest seem to work with flac. i supose you could install a program called soundconverter(you can install it via synaptic) ato convert the flacs to oggs.

Thanks for a reply. Nautilus Preferences only permits you to turn the feature on or off, which doesn't help. I'm looking for a setting to turn the feature on/off for "flac" files as well. It may not exist, but it should for all open source media files. As for converting from flac to ogg, that's not an option for me.

---

### Post by hoheszeh on 2007-04-09
> **Rizlaw said:**
> Thanks for a reply. Nautilus Preferences only permits you to turn the feature on or off, which doesn't help. I'm looking for a setting to turn the feature on/off for "flac" files as well. It may not exist, but it should for all open source media files. As for converting from flac to ogg, that's not an option for me.

afaik mp3 playback on mouseover can be enabled with installing mpg123. maybe there is a package for flacs as well which just needs to be installed?

---

### Post by Rizlaw on 2007-04-09
> **hoheszeh said:**
> afaik mp3 playback on mouseover can be enabled with installing mpg123. maybe there is a package for flacs as well which just needs to be installed?

Thanks for a reply. Ogg123, which plays newer flac files, was already installed and doesn't work for mouseovers. I did try flac123 and it didn't work either. I noticed that there was an mpg123 and mpg123-alsa. I tried mpg123-alsa and it worked for mouseovers of mp3 files.

My guess is I need a flac package like "flac123-alsa" since that is the linux sound support system I am using (not "oss").

---

