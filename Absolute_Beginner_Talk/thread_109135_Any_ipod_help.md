---
title: "Any ipod help?"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by myke on 2005-12-27
Using a new shufflle.   No luck at all getting songs on it from breezy.  Quite frustrating actually.   I've tried amarok (won't recognize the ipod), gtkpod (syncs tunes, shows smaller database left, but when I try to listen to the loaded songs ... nothing happens yet when I then remount the ipod, it still shows the songs there ... they just won't play), and banshee (recognizes the ipod, accepts chosen songs, then shuts down as soon as I hit sync -- just blinks off.  i even went outside the officially supported repositories to upgrade banshee to .10.2 and still no luck).  I've made sure all dependencies are loaded correctly.  I even installed the recommended files as well to try to help.  Nothing works.  I'll hate to have to use XP alot more again just for the ipod.  That would suck.  But right now it's the only way I can get songs on the ipod.  

Any help or suggestions??   :confused:

---

### Post by Zelut on 2005-12-27
I just helped my sister with her iPod shuffle using Breezy 5.10.  I think I've got it figured out... see if these work for you.

I realized it was important to mount the drive BEFORE loading gtkpod.  After it is mounted you can start gtkpod and, just the first time, you need to make sure you Import iTunesDB and Create Filelist (I think it is, near the bottom).

Also, to listen to songs from your iPod you'll need the xmms-mp4 package for .mp4 support. (this is for xmms, of course)

Another important note is that you MUST eject your iPod before you unplug it.  This gave me the most problems.  Best way I found to do this is 'sudo eject ipod' before you pull it out.

Take those into consideration and get back to me if you're still having troubles.  Personally I don't like iPods but I seemed to get it working..  it can be done.

---

### Post by myke on 2005-12-27
well ... I think you may have given me the key to gtkpod working.  I was doing the initial steps already but when I added in the 'sudo eject ipod' via the terminal before pulling out the shuffle, all songs are playable (of the ones I've skimmed thru to this point).   Seems to be going ok so I'm going to keep up with this.  I need that damned ipod to get me through a good chunk of my work day!

I do wish there was an easier way to do things but at least it works.  

Here's what I do wonder -- why does the eject method make all the difference???  :confused:

---

### Post by Zelut on 2005-12-27
Well as far as I can tell, even in Windows, iPods are very picky about being unplugged before they are ready.  I'm not sure why this is (again, I am NOT a fan of iPods) but realize, for the iPods sake, its pretty critical.  I noticed that removing it under windows before I got approval from iTunes caused problems as well.  I think you should be fine as long as you remember to 'sudo eject ipod' before you unplug it.  I guess someone could hack the gtkpod code and add a 'unplug' button... second thought, maybe someone should mention it to the developer.  Might lead to less problems with proper un-mounting.

---

### Post by myke on 2005-12-27
Agreed.  That would be a great thing ... surely a button could be added to simplify the eject procedure.  Good idea.  The shuffle is the only ipod I own so I'm not overly familiar with any of them as I just got it.  Are there other mp3 players that you're more comfortable with and would work well with linux?

---

### Post by qiemem on 2005-12-27
I've been having similar ipod troubles... The only one that I've really found to be at all usuable is [yamipod]("http://www.yamipod.com/"). Its pretty slow, and pretty unstable (on my system at least), but a lot of people really like it. Anyway, you could give that a shot...
Oh ya, you can't get it off the repositories, you gotta download off the site.
Good luck!
EDIT: Looks like theirsite my be down right now... odd... well whatever, when it comes back up, have a look.

---

### Post by Zelut on 2005-12-27
I honestly haven't shopped around for mp3 players. I work in an office and I've setup remote streaming access to my .mp3 collection so I don't have a need for a mobile .mp3 player :)

If I were to buy something though I would go with something that leaves files in an .mp3 format (not changing them to a proprietary mp4) and also one that doesn't use so much DRM. I can't stand that stuff.

Pending a button from the developer I created a toolbar button for my sister. Might work for you if you dont want to open a terminal each time. Here is a quick Howto:

at the terminal:
> gedit eject.sh 
enter:
> sudo eject ipod 
save the file & then:
> sudo chmod +x eject.sh 
right-click > add to panel > custom launcher > ...path-to-your-eject.sh-file

Now you can just click this launcher button to eject your ipod..

---

### Post by myke on 2005-12-29
i think this is an excellent work around.  a custom launcher will do the trick just as easy for me ... but i can't get it to work.   i followed the instructions you gave but when I hit my launcher .. nothing happens.   the sudo command works directly from the terminal so clearly i'm doing something wrong here!

---

### Post by Zelut on 2005-12-29
It sounds like maybe it needs to be restored using the iTunes software.  I ran into that issue with mine a few times before I got the steps right.  If it wont play &/or won't mount right on your box it may need to be restored.

You should be able to copy all of the .mp4 from your player to your hard disk (they'll be erased at restore).

Get access to a windows machine & download iTunes & the iTunes updater.  The updater will have an option for 'update' & 'restore'.  It sounds like you may need to restore it and then you're starting at 0 again.

At that point try our steps for using it under linux, use gtkpod to add the songs you saved.  As long as you eject it correctly from then on you should be ok.

---

### Post by Suger on 2005-12-30
I don't want to criticize, but

```

gedit ipodeject

#!/bin/sh
gksudo eject ipod

```
save as ipodeject and close, then

```

sudo chmod +x ipodeject
sudo mv ipodeject /usr/local/bin


```
would be cleaner ;) (I changed from eject to ipodeject due to observations later in this thread)

But thanks, the "eject ipod" was the thing I missed for using my ipod under ubuntu.

---

### Post by crane on 2005-12-30
I would also note the end of the script. People new to this would really be confused.

Open a text editor and enter the following,

> #!/bin/sh
gksudo eject ipod

[color=blue]save as eject and close[/color]

sudo chmod +x eject
sudo mv eject /usr/local/bin

---

### Post by kaamos on 2005-12-30
[QUOTE=Suger]I don't want to criticize, but

```

gedit eject

#!/bin/sh
gksudo eject ipod

sudo chmod +x eject
sudo mv eject /usr/local/bin


```
would be cleaner ;)

But thanks, the "eject ipod" was the thing I missed for using my ipod under ubuntu.[/QUOTE]
But this shoud be renamed for example "ipodeject" since the command eject already exists. Otherwise if you try to eject the cdrom, your ipod disconnects instead.. :P

---

### Post by Suger on 2005-12-30
:oops: You're both right. First post edited.

---

