---
title: "a question for anyone that has rockbox"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-06
how do i add videos?
i have a ipod video 5.5 generation
and i downloaded rockbox and have it installed
but how do i add videos so i can play them?
also i'd like some more applications and games if you can add theme...

---

### Post by RadiationHazard on 2008-03-06
anyonee....:(

---

### Post by vikrant82 on 2008-03-06
Rockbox has an MPEG plugin.

For complete HOWTO : [http://www.rockbox.org/twiki/bin/view/Main/PluginMpegplayer]("http://www.rockbox.org/twiki/bin/view/Main/PluginMpegplayer")

But I wont advice for it because, Rockbox still can't use the dedicated video decoder chip in the ipod and relies on iPod CPU to render the video. The frame rates are comparatively low (though watchable) and the plugin is a battery drainer.

By the way, Rockbox has brightness control finally added and I am finding increased battery backups on my 30g.

---

### Post by RadiationHazard on 2008-03-06
well i have mp4 files which is what ipod uses. can i not just add them or something? i mean if not i can just convert them but if mp4's play better i already have them...

---

### Post by vikrant82 on 2008-03-06
I am afraid you cannot play your MP4 files in rockbox. Sorry.

And I would advise against converting them as well. I'd say use Apple firmware, if you are into videos. Rockbox is great for music.

---

### Post by RadiationHazard on 2008-03-06
yeah i have my hard drive split for apple linux and rockbox and that's what i use rockbox for right now is music and games but why don't you think i should watch videos? and were can i go to download games and apps for rockbox if anywhere? or for ipod linux if you know...

---

### Post by mgm2rr on 2008-03-06
Hey, I hope you are enjoying Rockbox, I have been using it for about 6 months now and I think its really  great!  Check out [this page]("http://www.rockbox.org/twiki/bin/view/Main/PluginMpegplayer")
for help with video encoding issues.  It gives you options for a few command line approaches, but if you just want a quick and easy GUI solution, I would recommend WinFF.   Once you have a video encoded in the proper format, just add the file to the directory of choice on your player, and then once your player is on, use the "Files" menu to navigate to it.  Select the file, and the mpeg  plugin (which is installed by default) will automatically start playing it.  Good Luck!

---

### Post by RadiationHazard on 2008-03-06
for converting i always just use [www.media-convert.com](www.media-convert.com) it works really good
and i converted it to an .mpg
and put it into a file called Videos in rockbox's root directory.
but when i select files all it shows is like calender, contacts and notes? :confused:

---

### Post by RadiationHazard on 2008-03-06
any help?

---

### Post by vikrant82 on 2008-03-06
First of all I hope, you converted the video in proper size, [	 320x240, 320x240, 320x180 etc ].

Try placing the mpg file in some folder along with other folders (Calendar, Notes). Lets name this folder, Videos.

Now browse to that folder from Rockbox, You will see that mpg file. Keep "select" pressed untill you get the context menu, Choose -> Open with -> mpegplayer.

---

