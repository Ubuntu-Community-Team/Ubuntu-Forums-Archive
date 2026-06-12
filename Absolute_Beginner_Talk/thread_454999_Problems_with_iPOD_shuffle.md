---
title: "Problems with iPOD shuffle??"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-05-26
Hello Everyone

I've a problem with saving music on my iPod shuffle (512mb). If I use Gtkpod following problem appears : when I save music on iPod and click eject device everything seems to be Ok, but if I listen the music on iPod later some songs (even if program shows me that all songs are saved on iPod)  iPod couldn't find or play (all song are in same format wich iPod support). 
But If I use rhythmbox music player problem start when I click on eject device button. System gives me an following error: "Cannot ejec volume" (with no details or desicrition of an error). Then my iPod stop playing songs becouse songs are incomplete written on iPod.
I would me very glad if someone could help me solve this problem???????????????

Thnx to everyone!!!!!

---

### Post by someusernoob on 2007-05-26
The iPod Shuffle works different then the normal iPod models (and the Nano), I couldn't get mine to work with any iPod 'application' on Linux. Therefor I use this little script: [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

Just plug your iPod in its dock and mount it as a normal USB Mass Storage Device (the default behavior here). Fill it with music (with Nautilus/Konqueror like any other normal mp3-player), place the script from the link above in the root dir of your iPod (/media/iPod for example, depends on where you mount it/it has been mounted) and run it by double-clicking the file (it needs to be opened/executed by python). The database on the iPod will be regenerated and it will see the music you've copied to it.

Good thing is that you only need this script, no other application is needed anymore, bad thing is that you need to execute the script every time you change the music on the iPod.

Oh, and make sure when you unplug the iPod, you unmount it first by right-clicking on the icon on your desktop (I assume it is there). Copying files might be slow sometimes (when its memory is getting full), so the copy-process needs to finish first before you unplug it (sometimes it is still running while the copy-progress-bar is already done- when you unplug it at that moment you'll find your music to be incomplete).

---

### Post by thesonisshining on 2007-05-28
:biggrin: IT'S ALIVE; IT'S ALIVE HAHAHAHAHAHAHAHAHAHAHHAA BWAHAHAHAHAHAHA IT'S ALIIIIIIIVE! :D
It actually worked. Thank you for that post. 

iPod shuffle Gen2: fully functional....

---

### Post by ugashia on 2007-09-12
Wow thats great, Now i have cut off every tie with windows and i have absolutely no need to use it ever again now i can listen to music on my Ipod :guitar:

---

### Post by blackaardvark on 2007-10-19
Yes! Thank you! Sweet sweet music to my ears!

---

### Post by nzruss on 2008-02-25
> **someusernoob said:**
> .... I use this little script: [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

Just plug your iPod in its dock and mount it as a normal USB Mass Storage Device (the default behavior here). Fill it with music (with Nautilus/Konqueror like any other normal mp3-player), place the script from the link above in the root dir of your iPod (/media/iPod for example, depends on where you mount it/it has been mounted) and run it by double-clicking the file (it needs to be opened/executed by python). The database on the iPod will be regenerated and it will see the music you've copied to it..


Anyone here clever enough to write a script to automatically do all the above with a shuffle selection of xxx MB from the music folder?

1. detects ipod shuffle and mounts it (normal behavior)
2. Deletes the existing music
3. fills shuffle with random selection of music from /home/user/Music until full
3. runs the renew db script to rebuild the database
4. unmounts and informs the user the process is complete

I don't have the skills to write such a script. So it may be really easy for someone out there. I'll look around and see if I can do it though. Step 3 looks tricky.

-----------------------------------------------

Update:   Found something!!!!! Check this out  [http://ubuntuforums.org/showthread.php?p=1002321]("http://ubuntuforums.org/showthread.php?p=1002321")

---

### Post by ShadowVlican on 2008-02-29
relating to the ipod shuffle (and other ipods), is there any solution for linux that's as smart as this?

[http://yuo.be/wiki/dop:dop](http://yuo.be/wiki/dop:dop)


the key feature i'm looking for is **Automatically convert files which are in a format not supported by the iPod**

i've got a ton of formats not supported by the ipod (FLAC, APE, OGG, MPC, etc.) and foo_dop (plugin for foobar in windows) does a fantastic job with one click!

---

### Post by vwbunnylove on 2008-06-28
> **someusernoob said:**
> The iPod Shuffle works different then the normal iPod models (and the Nano), I couldn't get mine to work with any iPod 'application' on Linux. Therefor I use this little script: [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

Just plug your iPod in its dock and mount it as a normal USB Mass Storage Device (the default behavior here). Fill it with music (with Nautilus/Konqueror like any other normal mp3-player), place the script from the link above in the root dir of your iPod (/media/iPod for example, depends on where you mount it/it has been mounted) and run it by double-clicking the file (it needs to be opened/executed by python). The database on the iPod will be regenerated and it will see the music you've copied to it.

Good thing is that you only need this script, no other application is needed anymore, bad thing is that you need to execute the script every time you change the music on the iPod.

Oh, and make sure when you unplug the iPod, you unmount it first by right-clicking on the icon on your desktop (I assume it is there). Copying files might be slow sometimes (when its memory is getting full), so the copy-process needs to finish first before you unplug it (sometimes it is still running while the copy-progress-bar is already done- when you unplug it at that moment you'll find your music to be incomplete).
Thanks, this scrypt was a life saver! :)

---

