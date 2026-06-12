---
title: "change default music box"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by Snodgrass on 2006-05-15
I'm using dapper beta 64. I'd like to use something other than Rhythmbox. I've used beep in the past, but it's not available from the pure FOSS repositories, evidently. At any rate I can't get at it with synaptic or apt-get. Maybe I'm doing something wrong. Anyway, I've downloaded xmms and would like it as my default audio player, but I don't know how to replace rhythmbox as the default.

---

### Post by meng on 2006-05-15
The way I would do it is to use the GUI. Navigate via Nautilus to a folder containing an mp3 (or whatever other format) file, then right click and Properties > Open With. This should change the default prorram to open all mp3 files.

---

### Post by easyease on 2006-05-15
do you want to use xmms for shoutcast streams?  If so use firefox to browse shoutcast.com. you will need to click Edit > Preferences > Downloads > View & Edit Actions, then set the PLS extension to open with xmms if its not already the default.

---

### Post by easyease on 2006-05-15
oh and i can recommend "sudo apt-get install kstreamripper" so you can record those shoutcast streams.......

---

### Post by kttrina on 2006-05-15
hi meng
i tried a lot of times to set permanently xmms as a default application for mp3 through GUI right-clicking on the icon.
but it doesnt't work to set it permanently
wat else could i do?

fnx u all

 KT

---

### Post by mcduck on 2006-05-15
[QUOTE=easyease]oh and i can recommend "sudo apt-get install kstreamripper" so you can record those shoutcast streams.......[/QUOTE]
..or streamtuner and streamripper if you are running Gnome :)

Anyway, why not enable universe/multiverse repositories? Beep is in universe.

---

### Post by mcduck on 2006-05-15
[QUOTE=kttrina]hi meng
i tried a lot of times to set permanently xmms as a default application for mp3 through GUI right-clicking on the icon.
but it doesnt't work to set it permanently
wat else could i do?

fnx u all

 KT[/QUOTE]
You need to right-click the file, then select 'Properties' and in the 'Open With'-tab choose the program you want (or click 'Add' to add new one).

---

### Post by meng on 2006-05-15
^^^^
Yup, what he said. Don't just "Open With", you have to go to Properties and Open With, then it will stick.

If that doesn't work, someone else will have to help you.

---

### Post by Snodgrass on 2006-05-15
Thanks Meng, this was real darn helpful.

---

### Post by Snodgrass on 2006-05-15
[QUOTE=easyease]do you want to use xmms for shoutcast streams?  If so use firefox to browse shoutcast.com. you will need to click Edit > Preferences > Downloads > View & Edit Actions, then set the PLS extension to open with xmms if its not already the default.[/QUOTE]

Meng's post helps me when I download a shoutcast, but I'd like to follow up your suggestion so that the browser will open up xmms automatically. I got to the last part of your instructions, "then set the PLS extension to open with xmms." I'm not sure how to do this. I've tried putting PLS in the search box. I know I'm being clueless. :mrgreen:

---

### Post by kttrina on 2006-05-16
fhnx u all now dat stuff works all rite!! KTT

---

### Post by meng on 2006-05-16
Snod - I don't know much about shoutcast, but when I want firefox to change the default application associated with a file extension, I go to Preferences, Downloads and Edit the association. Sometimes this requires going to plug-ins and disabling that plug-in, but AFAIK rhythmbox doesn't come with such a plug-in.

---

