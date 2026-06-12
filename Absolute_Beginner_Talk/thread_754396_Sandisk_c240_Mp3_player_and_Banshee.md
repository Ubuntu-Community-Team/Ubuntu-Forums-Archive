---
title: "Sandisk c240 Mp3 player and Banshee"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Helpme! on 2008-04-13
Okay, so I'm only 14 and VERY new to Ubuntu which my mom got me into. As you could probably assume, I'm still stuck in Windows state of mind, so the problems in Ubuntu are harder to solve for me. I've made it through a few problems (or the only ones I've come up with so far) except this one:

I have a Sandisk (c240) mp3 player, and I use banshee.
I had files from my old computer put onto my mp3 player and my computer before I switched to Ubuntu, and so I didn't come across this problem until I got a new CD a few days ago. So I try to put the CD in, and sound juicer comes up and I extract the files and everything, and that does nothing to get them on my Music player, so I open up Rhythmbox and try to copy the CD into the music library and drag and drop into my MP3 player, but that doesn't work. Then I open up banshee (my last resort) and tried the same thing I did in rhythmbox. I had 49 mb left before hitting Sync, and after I hit sync it said I had 13 mb. So I look on my MP3 player and come to find the songs I put on there AREN'T THERE!

I searched forums I searched google I searched banshee bugs and everything.
I couldn't find anything.

And another thing, I tried to update banshee in the terminal, and it kept saying the code didn't work. Does someone have the code?
The code I used was sudo conary update banshee-1
because that's what someone gave me..

PLEASE HELP!

---

### Post by ahm911 on 2008-04-13
thats wierd first of all my favourite no problems till now player is AMAROK! very reliable as for ur mp3 player.. it didnt show up as a mass storage device? like when u plug in a usb thumb drive? because that makes it alot easier to manage just copy paste songs on and off..

go to places my computer and you should find ur cdrom, files system AND (if ur mp3 is conencted ) ull find a disk that u can explore. try doing that and see if the files are on it.

sync on rythm box if i am right is for the ipod and its smart playlists soo you might have added extra info to all ur tracks and did some wierd tags causing ur mp3 player to have problems reading.

so i would advice and try to find ur mp3 player on ur system as a storage device.. update on how taht goes!

---

### Post by Gen2ly on 2008-04-13
Well helpme, I have a Sansdisk and the process is pretty easy but unfortunately (maybe someone else here can think of a betterway) there isn't an automaticway to dothis.  Basically the procedure requires treating the Sandisk like any other folder.  On my sansdisk m240 I first use soundjuicer to create mp3's and then I put the files on the sansdisk in the "record/bandname" folder.  And the player works just fine.

---

### Post by Helpme! on 2008-04-13
how would I get the 36 mb it took up off my mp3 player, though? That's another problem.

---

### Post by ahm911 on 2008-04-20
no clue.. hopefully someone with more knowledge on recovery of missing data can help

---

### Post by stevek123 on 2008-04-25
I'm struggling with this sandisk nonsense too. Its a firmware issue and it looks like it involves what mp3 tags the unit will read. (I've no real clue what this is YET ;) ). I found info tho that points in the right direction here
[http://ubuntuforums.org/showthread.php?t=749795&highlight=sandisk](http://ubuntuforums.org/showthread.php?t=749795&highlight=sandisk)
Maybe info on that thread can help you. It looks like, from the thread, you should be able to use your ubuntu file system to see the files you added that wont show up in the player, and delete them from there...

---

