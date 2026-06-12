---
title: "&quot;my iPod, synching, and a lot of questions&quot;."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-08-03
Some autobiography::KS 
I have a 5th gen (video) iPod. I use Xubuntu. I still haven't settled on what app to use, but I have heard many people suggest using gtkpod.

If you are a Xubuntu user with an iPod, let me know what you use.  But  _all_ are welcome to chime in. I appreciate any and all feedback.

**------------------------------------**
[COLOR="Red"]Section A: These are questions that have been answered. Please feel free to add your post to confirm the posted answer, or to "unconfirm" the answer.[/COLOR]

[*this has been answered below by arisna and nalmeth. thanks.*]
How come the "Do not disconnect" sign on my iPod doesn't go off even after I right-click on the iPod icon on the desktop, and then select unmount? If I unmount it's still there. Only when i type "eject ipod" in terminal does the "do not disconnect" sign go off. 
If I do eject ipod, how can i undo it, without having to unplug and then re-plug ipod? In other words, I know that after i "eject iPod", I can get the syncing ability again by physically manipulating the ipod, but how can i get the iPod to be synch-able again without touching the iPod?

[*this has been answered below by ThirdThoughts.thanks.*]
If I have synched a music file from my computer to my iPod, and then I later delete the file from my hard drive, is there a way to recover that file, and put a copy back onto the hard drive? If you asked me, "How did you delete that file from your hard drive?", let's say I did either:
a) delete via the syncing program (e.g. gtkpod)
b) delete via outside the syncing program (file manager/thunar/terminal)

Would the way I delete the file make a difference? If so, kindly let me know.



[*this has been answered below by ThirdThoughts.thanks.*]
My iPod is 30 gigs and my hard drive is only 20 gigs, so i can't store my entire audio collection on my hard drive. What i have on my Ipod, i probably will not be having on my hard drive, due to space limitations. Is this manageable? Or will the iPod (or syncing software) require that a copy of the music file be found in both iPod and computer?


**----------------------------------------**


[COLOR="Red"][SIZE="3"]Section B: These questions still need answers.[/SIZE][/COLOR]

[COLOR="#ff0000"][still partially unanswered.] [/COLOR]
If I use gtkpod to sync, will i be able to use other ubuntu apps later on without having to start my cataloguing from scratch? In other words, if I add some music into my iPod via gtkpod, in the future, when I use, say, amarok, or banshee, or even Windows/Mac iTunes, what will happen to the music that's on my iPod? Will they have to be deleted? Will they be easily sync-able to the new desktop syncing program?
 Will the reverse (using gtkpod later on, after first using a different program) be true, too?


How do i add photos to my iPod? Can gtkpod do it? or should i use something else? If gtkpod can't do it, what do you guys suggest?

Is there a help file for gtkpod? In particular, i want to know what all those stuff in the Gtkpod's File Menu are all about. From [Read Itunes Db] to [Check iPod files]

I think gtkpod is good for people who plan on doing most of their
listening on their ipod, isn't it? Coz that's what i think i'll end up
doing. I don't think i'll be diong a lot of listening on the computer.
or if i do, i don't think i'll be using gtkpod, because gtkpod wasn't
realy meant for that, is it?

How can i input lyrics into my songs? I heard that iTunes has this capability. I know that Amarok can do this too. but what about gtkpod.

[COLOR="Magenta"]**UPDATE: New Question: **[/COLOR]After I sync music from gtkpod (for example) to iPod, would i be able to edit, say, the Title in gtkpod and have this new Title for an mp3 reflected in the iPod?
Thank you so much for your help.

---

### Post by Arisna on 2006-08-03
> **hanzj said:**
> How come the "Do not disconnect" sign on my iPod doesn't go off even after I right-click on the iPod icon on the desktop, and then select unmount? If I unmount it's still there. Only when i type "eject ipod" in terminal does the "do not disconnect" sign go off.

If I do eject ipod, how can i undo it, without having to unplug and then re-plug ipod? In other words, I know that after i "eject iPod", I can get the syncing ability again by physically manipulating the ipod, but how can i get the iPod to be synch-able again without touching the iPod?

That happens to me with my non-iPod music player, as well.  I suspect it is because HAL (Hardware Abstraction Layer) is querying the device for general information about it even when it is unmounted.  Using the eject command probably releases the device from the system's control, which makes HAL leave it alone.  I always just unmount it and remove it without paying attention to that warning, personally, and it has never caused any problems for me.

Getting HAL off of it with eject would also explain why you have to disconnect and reconnect it before you can mount it again--your system stops acknowledging the device and assumes you are going to remove it.  Of course, it still takes notice when a "new" device is connected.

Since I don't have an iPod, I'm afraid I can't help you with the rest of your post.

---

### Post by hanzj on 2006-08-03
thanks arisna for your answer regarding "Do Not Disconnect".

---

### Post by nalmeth on 2006-08-03
Wow, a lot of questions, I'll try to answer what I can.

The do not disconnect thing is an Ipod usability problem, IMO. It tells you always to keep in connected, and naturally, you won't, so you won't take the warning seriously.

The absolute key is to not disconnect while syncing, as this will lead to bad things happening. :p Otherwise, although it is safe to simply remove, you should take the precaution of the "software removal", the way you do now.

GTKpod is good, especially if you're using xubuntu, it won't have much of a footprint. You should use it to create the directories for the ipod, if you haven't done this already. Does the ipod work with GTKpod already? For my buddies ipod nano, I had to compile a newer version of GTKpod to get it to work. If you find the repo version isn't working, you can PM me and I'll link you up with instructions for a beta version.

That said, when you've created the directories, you should be able to use whatever other app you want, and all should go smoothly. I use amarok for syncing now. 

As for copying the music onto the HDD, I know it can be done, but have never tried, or needed to try.

With amarok, and likely banshee, you can play the music from your ipod with the app.

---

### Post by hanzj on 2006-08-03
> The absolute key is to not disconnect while syncing, as this will lead to bad things happening.
Yes. I think that the status bar in gtkpod will tell me when the synching is finished.

---

### Post by Third Thoughts on 2006-08-04
> **hanzj said:**
> 

If I use gtkpod to sync, will i be able to use other ubuntu apps later on without having to start my cataloguing from scratch? In other words, if I add some music into my iPod via gtkpod, in the future, when I use, say, amarok, or banshee, or even Windows/Mac iTunes, what will happen to the music that's on my iPod? Will they have to be deleted? Will they be easily sync-able to the new desktop syncing program?

 Will the reverse (using gtkpod later on, after first using a different program) be true, too?

To the best of my knowledge this shouldn't be a problem, I've jumped from program to program on my old 4G ipod and things have been fine.


> **hanzj said:**
> 
If I have synched a music file from my computer to my iPod, and then I later delete the file from my hard drive, is there a way to recover that file, and put a copy back onto the hard drive? If you asked me, "How did you delete that file from your hard drive?", let's say I did either:
a) delete via the syncing program (e.g. gtkpod)
b) delete via outside the syncing program (file manager/thunar/terminal)

Would the way I delete the file make a difference? If so, kindly let me know.

You can recover stuff from your ipod, fairly easily. Just open up amarok (or listen, or rhythmbox, and maybe even gtkpod I'm not sure) select the file you want off of you ipod and drag and drop into thunrar. It'll copy it over.

> **hanzj said:**
> 
My iPod is 30 gigs and my hard drive is only 20 gigs, so i can't store my entire audio collection on my hard drive. What i have on my Ipod, i probably will not be having on my hard drive, due to space limitations. Is this manageable? Or will the iPod (or syncing software) require that a copy of the music file be found in both iPod and computer?

No definitely not. If this was the case I would have been fsked when I accidentally reformatted my hard drive. Thank god all of my music was backed up on my iPod


~Andrew S.

---

### Post by hanzj on 2006-08-04
> **Third Thoughts said:**
> To the best of my knowledge this shouldn't be a problem, I've jumped from program to program on my old 4G ipod and things have been fine.


so switcihng among linux apps is safe. What if, besides synching on Ubuntu, a person also uses iTunes on a Mac or Windows? Will there be no missing files? Will synching still work?

---

### Post by mdelorme on 2006-08-04
I'm not sure about the video iPods, but the 4G ipods could be set up to run under windows OR mac... implying that if you initially set up your iPod under windows, it will not connect to a mac and/or vice versa.  Under the settings -> about in my iPod it says the operating system that it was initially set up under.  Note that there may be third party apps that worked around this, I just have never had the need to investigate the issue.  In regards to linux, my iPod was set up under windows, and I am able to use it in ubuntu without any problems.  I don't know if the same would hold for one that was set up on a mac (i know the windows installer will create a fat32 filesystem on the iPod... don't know about mac)

---

### Post by hanzj on 2006-08-04
[COLOR="Magenta"]New Question:[/COLOR]

After I sync music from gtkpod (for example) to iPod, would i be able to edit, say, an mp3's Title in gtkpod and have this new Title for an mp3 reflected in the iPod?

---

### Post by hanzj on 2006-08-04
I have found one more indication of when it is safe to phsycially disconnect the iPod. On my 5th gen iPod's upper left hand corner of the screen, a little twirly pinwheel rotates when synching is going on. When the  snyc is over, the twrily pinwheel disappears.

---

### Post by hanzj on 2006-08-04
Now about Podcasts.

So I have the URL for a podcast that i want to listen to on my iPod.
The URL begins with http:// and ends in .xml. So how do i go about
entering this URL into gtkpod? I see the word "podcast" twice in the
Playlist Pane. 

if the current version of gtkpod (0.99.2) won't work,
a. will the latest one?
b. what do you suggest for a simple podcast app? hopefully it's a tiny app, so that it won't slow down my old computer too much.


thanks.

---

### Post by nalmeth on 2006-08-04
$ apt-cache search podcast
ipodder - a podcast receiver
penguintv - podcasts and video blogs for Linux
podracer - podcast aggregator/downloader
democracyplayer - GTK+ based RSS video aggregator
democracyplayer-data - GTK+ based RSS video aggregator data files

---

### Post by hanzj on 2006-08-04
nalmeth, do you use a podcast app? if so, which?
i'm trying to find gPodder, coz i read that it seems to be quick and simple and compatible with gtkpod. I wonder where gPodder is.

---

### Post by hanzj on 2006-08-04
gPodder looks like it's not available from the repo. I wish it were, because it looks very easy to use and lightweight. Because it isn't, I think I'll avoid it. I read on another post of a person's difficulty trying to get all the depencies and compiling and stuff.

---

