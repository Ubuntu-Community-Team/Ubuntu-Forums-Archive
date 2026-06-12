---
title: "Banshee not seeing iPod"
date: 2010-05-26
forum: Apple Hardware Users
---

### Post by Tim [DRX] on 2010-05-26
Hey guys, I'm the newest newbie you're gonna find. :3

Windows failed on me, so I've swapped to Ubuntu 10.04, and I'm having issues with the media players.

Rhythmbox was reading old ID3 tags, meaning all my music collection appeared messed up since I had apparently only been editing the newer tags in iTunes when I was on Windows. I tried using EasyTAG but then as soon as I loaded the music in Rhythmbox, it would just revert back to the old useless tags again.

I read around, and Banshee came highly recommended (so did Amarok, but that runs awful for me. :/) and I really like the layout and general appearance of Banshee, and it doesn't seem to screw with the file names or anything like Rhythmbox was doing, but my iPod does not appear at all. 

I've googled around, but all the fixes are from years ago and are not working for me.

It's a fairly new 160GB Classic iPod. Rhythmbox detects and edits files in it fine. Hipo iPod Management Tool does not detect it either.

So...any advice? Like I say, totally new to Linux, so a bit of hand holding might be in order. :3

---

### Post by Joe of loath on 2010-05-26
See if the iPod plugin is loaded, by clicking edit->preferences->extensions and scrolling down to 'iPod support'. If it's unchecked, check it and restart banshee and your iPod should work.

---

### Post by Tim [DRX] on 2010-05-26
It's definitely checked, and I have tried switching it on and off again.

---

### Post by Joe of loath on 2010-05-26
Have you tried plugging it in while banshee is closed, and seeing if you can navigate it as a storage device? Or, if you do that then open banshee, tried plugging it in with banshee running?

---

### Post by Tim [DRX] on 2010-05-26
^All of the above. Even plugged it in, and when prompted, "Open with Banshee Media Player"

No result - iPod does not appear. Am I missing some installed component? My brief exposure to Ubuntu tells me I need to go grab a hundred plugins off Software Manager to make anything work. :p

---

### Post by Joe of loath on 2010-05-26
Try 'sudo apt-get remove libgpod' then 'apt-get install libgpod'. Otherwise I'm stuck :( I'm not the most advanced user, and my mp3 player (creative zen) has worked with hacks since 8.10, and out of the box since 9.04, so I've not had to fiddle.

---

### Post by alexmurray on 2010-05-26
Banshee is built using Mono which doesn't yet have support for the latest libimobiledevice library which is used by Rhythmbox (and GtkPod) to access the newer iPods / iPhones. So unfortunately you may be stuck having to use either Rhythmbox or GtkPod...

---

