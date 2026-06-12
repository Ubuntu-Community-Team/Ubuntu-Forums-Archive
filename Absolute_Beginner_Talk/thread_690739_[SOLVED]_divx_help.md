---
title: "[SOLVED] divx help"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by myddewji13 on 2008-02-07
hi,

I am having no luck watsoever at playing divx files...ive downloaded the codecs and the files are recognized as video files. If i try to play in firefox the mplayer plugin starts to buffer then freezes and firefox stops working....if i download then try to open...totem opens and then closes just as quickly...someone help pls!!!

---

### Post by Crumpets and Jam on 2008-02-07
> **myddewji13 said:**
> hi,

I am having no luck watsoever at playing divx files...ive downloaded the codecs and the files are recognized as video files. If i try to play in firefox the mplayer plugin starts to buffer then freezes and firefox stops working....if i download then try to open...totem opens and then closes just as quickly...someone help pls!!!

Try VLC Media Player. It is a very popular media player that can play pretty much every file format. It is in the Applications --> Add/Remove. You can install it from there.

---

### Post by myddewji13 on 2008-02-07
tried it ...no luck...same open close phenomenon

---

### Post by myddewji13 on 2008-02-07
anyone?

---

### Post by jrusso2 on 2008-02-07
I can't play divx either

---

### Post by myddewji13 on 2008-02-07
can anyone atleast point me to somwhere where i can find help for this (besides the forums...ive lookes all over...none of it worked for me)

---

### Post by Presto123 on 2008-02-07
How are your .avi videos running?

I have several codecs and am running DivX files to the best of my knowledge. 

*Edit* Search for Codec in the Add/Remove applet and there's a codec that says it plays divx and that would be "GStreamer ffmpeg video plugin".

See if that helps. If not, I will search for more of what I have here.

---

### Post by myddewji13 on 2008-02-07
havent tried avi... but i do have the plugin your talkin abt...

---

### Post by Presto123 on 2008-02-07
Okay...lets try something else then. I can confirm that I can watch Divx since I am watching some crappy show/webthingy on Stage6.

---

### Post by Blutack on 2008-02-07
Is the file definately not corrupt?

---

### Post by Presto123 on 2008-02-07
I right clicked and Divx is running through Totem of all things...with the Gstreamer plugin. So, type in Gstreamer in that box and see if you have these following codecs:

"Ubuntu Restricted Extras", "Gstreamer Extra Plugins", "GStreamer plugins for aac, xvid, mpeg2, faad"; "GStreamer plugins for mms, wavpack, quicktime, musepack". 

Now, I gave you a "dirty" list of codecs and plugins there as I am unsure of what is actually making it work correctly.

---

### Post by Presto123 on 2008-02-07
> **Blutack said:**
> Is the file definately not corrupt?

Yeah...that's a good question. Goto Stage6 and see if you can watch anything there. That might help us to rule out that much.

---

### Post by myddewji13 on 2008-02-07
i cant watch anything on stage 6...can download files but cannot play within browser...and once downloaded..opening with any program causes the program to open then close....trying to load the file by using 'open file' within the program causes it to crash too... so im completely stuck...i installed all plugins u mentioned...and still no luck

---

### Post by linuxisfree on 2008-02-07
These are **.divx** file extension, right? Coz i can play AVI files but absolutely not the **.divx **files. So, yeah, i have the same problem...

---

### Post by Presto123 on 2008-02-07
Ah...thanks to Rocket2DMn here on the forums he pointed me to the most likely place for the codec you need.

It is called libdvdcss and it comes from the Mythbuntu repositories (Aka medibuntu). 

*Edit* Follow what is posted below.

---

### Post by Presto123 on 2008-02-07
Crud...that may not be enough. Just follow this, lol:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I'm finished now, I think.

---

### Post by bodhi.zazen on 2008-02-07
Did you try this link ?

[http://ubuntuforums.org/showthread.php?p=2591939](http://ubuntuforums.org/showthread.php?p=2591939)

---

### Post by myddewji13 on 2008-02-08
ok...my comp just crashed...had to reinstall ubuntu....everything works now though...but that aint such a good fix...

---

### Post by myddewji13 on 2008-02-08
UPDATE!!

ok...all video files cause totem and mplayer to crash at startup..got it working once but could only hear sound..mplayer plugin on firefox works with stage 6...but sound only NO VIDEO!!! HELP!!!

(PS youtube works fine :D)

---

### Post by justsomedude on 2008-02-08
mplayer plugin works like a charme on Stage6, I'm watching right now. :)

Your problem might actually be too many conflicting plugins, I only got mplayer plugin installed. You could try to navigate to /usr/lib/mozilla/plugins and delete everything exept Flash, Java and the various mplayer plugins. **BACKUP THIS FOLDER FIRST!!!** Uninstalling the plugins doesn't have the same effect btw, they remain inside that folder...

---

### Post by myddewji13 on 2008-02-08
all i have in that folder are flash,java and a bunch of mplayer plugins ... any other ideas ?

---

### Post by myddewji13 on 2008-02-08
ok... i got video working!!!! if i disable all desktop effects i can play video...can someone please explain to me why this is so and if theres anyway to fix this?

---

### Post by myddewji13 on 2008-02-08
ok to all that are having a problem... 

visit this and follow all instructions here:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

and if you have desktop effects enabled and cannot play video (but can if you turn em off) the fix is on this thread:
[http://ubuntuforums.org/showthread.php?t=615539](http://ubuntuforums.org/showthread.php?t=615539)

---

