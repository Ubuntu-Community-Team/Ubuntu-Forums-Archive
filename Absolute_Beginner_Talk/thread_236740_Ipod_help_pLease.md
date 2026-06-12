---
title: "Ipod help pLease"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by i_pod25 on 2006-08-15
computer knowledge...0
understanding of programing......0

so keeping that in mind would someone please be able to help me find a way/program that would enable me to load songs on to my ipod (nano)?
i have that amaroK music player thing, does that help me?
i'm so clueless:confused: :confused: 

thanx in advance
...

---

### Post by orb9220 on 2006-08-15
Which version of amaroK? you need 1.4.1

Then go to prefences and there is an add media device tab.

---

### Post by hellfried on 2006-08-15
> **i_pod25 said:**
> computer knowledge...0
understanding of programing......0

so keeping that in mind would someone please be able to help me find a way/program that would enable me to load songs on to my ipod (nano)?
i have that amaroK music player thing, does that help me?
i'm so clueless:confused: :confused: 

thanx in advance
...

might want to try using banshee or gtkpod

---

### Post by i_pod25 on 2006-08-16
..but umm problem how do i download the programs and actually get them to work? cause at the moment they dont install properly...

thanx

---

### Post by angkor on 2006-08-16
What happens when you try to install one of those programs?

Maybe you need to enable the extra repositories?

Read this if interested:

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

---

### Post by i_pod25 on 2006-08-16
ok i found and somehow managed to install banshee...it says i need a plug in to play music from my ipod? and how do i (by using this program) add music onto my ipod?

thanx

---

### Post by petersjm on 2006-08-16
Not sure about the Banshee plug-in issue, but as for adding music to your iPod, assuming the music is on your computer already, and is showing in your playlist window, you can simply drag and drop the files from "Library" (your system's music files) to "iPod". Then you need to press "Sync" or "Sync iPod" or whatever it's called, top right of screen.

---

### Post by i_pod25 on 2006-08-16
ok thanx!

n i see alot of codes all over da place where do they actually go?

---

### Post by i_pod25 on 2006-08-16
it didnt work...i dragged music into the ipod icon thingy and then press the sync ipod button and the screen came up with "snynin ipod please wait" but nothing happened...

---

### Post by i_pod25 on 2006-08-26
hello?:confused:

---

### Post by Skia_42 on 2006-08-26
Check out [this]("http://ubuntuforums.org/showthread.php?t=103071") thread by KingOfNowhere, it has all the info you need.

---

### Post by i_pod25 on 2006-08-26
but i can only delete songs from my ipod not add them using banshee...

---

### Post by Skia_42 on 2006-08-26
I couldn't get my ipod to work with Banshee or amaroK, my advice is to simply install GTKpod and use that, it works well and it is easy to use. If you simply follow the instructions in the thread I mentioned you will have your ipod up and running in no time.

---

### Post by thoffland on 2006-08-26
I use Amarok for playing music, and gtkpod for transferring songs. I didn't know amarok could do that... I'll have to check it out. 

Anyhow, I had some trouble with my Ipod in the beginning so I downloaded the iPod updater and restored it to factory defaults, then connected it to gtkpod and everything is great now. Just drag and drop songs, groups of songs, or playlists onto the ipod and hit sync. 

good luck!

---

### Post by i_pod25 on 2006-08-26
ok when i press download for gtkpod or when i download anything it opens up a file and i dont know what to da with the file it doesnt open into a program or anything....

and i see alot of codes for different things being mentioned...where do they acually go???

---

### Post by Jerome36 on 2006-08-26
> **i_pod25 said:**
> ok when i press download for gtkpod or when i download anything it opens up a file and i dont know what to da with the file it doesnt open into a program or anything....

and i see alot of codes for different things being mentioned...where do they acually go???

How are you trying to download gktpod?  Off of a website?  You can have it downloaded and installed automatically from the "Add/Remove" programs application.

---

### Post by i_pod25 on 2006-08-26
> **Jerome36 said:**
> How are you trying to download gktpod?  Off of a website?  You can have it downloaded and installed automatically from the "Add/Remove" programs application.

ohhh ok thanks!!!!:wink: :D

---

### Post by i_pod25 on 2006-08-26
ok problem again i downloaded gtkpod but when i try and add a song onto my ipod this comes up:

The following track could not be processed (filetype unknown): '/home/bh/Music/The All American Rejects/Dirty Little Secret/01. Dirty Little Secret.ogg'

help please....

---

### Post by Jerome36 on 2006-08-26
I don't have an iPod (I have a Creative Zen Nano), but do iPods (or at least the Nano specifically) support ogg music files?

---

### Post by i_pod25 on 2006-08-26
i really dont know...im not much of a computer person....

---

### Post by Jerome36 on 2006-08-26
You might want to try adding an mp3 file to your MP3 player, and see if that works.  I don't think iPods support ogg audio files, which is what you were trying to add to your player, according to your error message.

Ubuntu doesn't support MP3 playback, out of the box, and you have to add a couple multimedia plugins.  It's not hard to do.  First [open up the Synaptic Package Manager](https://help.ubuntu.com/ubuntu/desktopguide/C/synaptic.html).  Then download the "gstreamer0.10-plugins-ugly" and/or "gstreamer0.10-plugins-bad" plugins.  It might only be that you need only one of those two, for MP3 support, but I can't remember which.  You also might have to [add a new Repositories](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html#id2542172) to see them.  This shouldn't be needed to send an MP3 to your MP3 player, but it'll let you listen to them, ON your computer, if you haven't already done so.

---

### Post by i_pod25 on 2006-08-26
what do i need to add in the repositories???

---

### Post by Jerome36 on 2006-08-26
I believe the "Universe and Multiverse repositories."  Here's [a more detailed link](https://help.ubuntu.com/community/RestrictedFormats) regarding installing "Restricted Formats."

---

### Post by i_pod25 on 2006-08-26
its all selected and done but it's still not adding music onto my ipod....

---

### Post by Jerome36 on 2006-08-26
Did you get the same message, when trying to add an mp3 file, like you did with an ogg file?

---

### Post by i_pod25 on 2006-08-26
it wont let my extract music form my cds it says "reason- not linked to pipline" or somthing along those lines

how do i change or get my original music to become ogg files to mp3?

---

### Post by Jerome36 on 2006-08-26
> **i_pod25 said:**
> it wont let my extract music form my cds it says "reason- not linked to pipline" or somthing along those lines

how do i change or get my original music to become ogg files to mp3?

Sorry for the long delay.  I had to run, to grab something to eat.  Are you using "Sound Juicer" for tying to rip a CD to MP3?  [Here's some documentation](https://help.ubuntu.com/community/CDRipping) on the process.  Towards the bottom they dive into the MP3 format.  It looks like all you'll need is the "gstreamer0.10-plugins-ugly-multiverse" package.

I think there are ways to convert ogg files to mp3, but they might yield poor results, as you're taking one lossy file format, and converting it to another.  The quality will degrade.

I just want to ask one more question, and it's going to sound like a stupid question, so I appologize.  After downloading gtkPod, are you actually opening it up after you plug your iPod in?  The reason I ask is because when I was trying to get my Sister's computer to work with her iPod, when I plugged it in Ubuntu would automatically launch "Rhythmbox Media Player."  It'd show her iPod listed in the program, but you couldn't access it.

I then found out about gtkPod, and installed it.  However, after I plugged her iPod back in, and a program launched, I thought that was it and I told her everything was set, and left it at that.  A few minutes later, after leaving, it dawned on me that Rhythmbox Media Player was still launching when the iPod was connected, and she'd have to close that, and then open gtkPod.  I was in a rush when I did it, but I just thought I'd make sure you're using gtkPod.

If you're still unable to rip an album to MP3, and that won't transfer to your iPod, via gtkPod, then I'm at a loss, and hopefully somebody else can step in and offer some suggestions.  Good luck.

---

### Post by i_pod25 on 2006-08-27
i followed the intrustions but sound juicer still comes up with the same thing when i try to extract a cd

"Sound Juicer could not extract this CD.
Reason: Could not link pipeline"

thanx heaps anyway

---

### Post by i_pod25 on 2006-08-27
wait i think its working now....

---

### Post by Skia_42 on 2006-08-27
Just to clear things up, you can't import or play .ogg files on an ipod, only mp3...

---

### Post by Jerome36 on 2006-08-27
> **i_pod25 said:**
> wait i think its working now....

Cool.  I hope it worked...  and hopefully those new MP3 files will transfer to your iPod.

---

### Post by i_pod25 on 2006-08-27
Thanx sooo much!!!!

its working now!!!!O:)

---

### Post by Jerome36 on 2006-08-27
Awesome!  I'm glad I could help you out.  Enjoy the tunes! :)

---

