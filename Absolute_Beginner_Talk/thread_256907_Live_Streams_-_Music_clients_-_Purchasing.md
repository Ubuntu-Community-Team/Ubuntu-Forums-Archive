---
title: "Live Streams - Music clients - Purchasing"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by MrLeN on 2006-09-13
Are there any clients for live streaming music? On Windows, I have iTunes and I am looking for some sort of replacement. I know that I can't have iTunes, but are there any alternatives at all?

Is there anyone that purchases music online, or listens to live streams through Ubuntu? If so, how do you go about it? 

I want to test out the different Audio players that i can see in the Add/Remove area -- but I need to purchase a sing first. So, what I am really trying to do is ascertain the best process for listening to, downloading and purchasing music.

Any help appreciated.

MrLeN

---

### Post by xyz on 2006-09-13
Streaming music:
```
sudo aptitude install streamtuner
```
Info/Plugins:
[http://www.nongnu.org/streamtuner/](http://www.nongnu.org/streamtuner/) is just one way to go!
Unfortunately I can't help you with music purchase; I like Creative Common Licences.

---

### Post by MrLeN on 2006-09-13
I put that code in Konsole and I got:

> Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "streamtuner"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


MrLeN

---

### Post by xyz on 2006-09-13
I think you can also download it trhu Synaptic and that should take care of needed dependnecies.
Have you universe/multiverse repositories enabled?
System > Administration < Synaptic Package Manager..and Search for Streamtuner
About repositories:
click on Settings in Synaptic and down to Repositories and finally on Add

A little window will open check universe/multiverse boxes.
Run the command line again.

---

### Post by stmiller on 2006-09-13
Xmms can play live mp3 streams.

---

### Post by MrLeN on 2006-09-13
Ok, I seem to have the above sorted now and I have Streamtuner installed. Look good too.

Now, when I try to tune into a station, it says: 

> 
Failed to execute child process
"xmms" (no such file or directory).


MrLeN

---

### Post by MrLeN on 2006-09-13
ok, I got it sorted -- I downloaded xmms too.

This looks great. Thanks heaps :)

MrLeN

---

### Post by MrLeN on 2006-09-13
Ok, I have been playing around with this now. Just a couple more questions:

1). If I click record, Terminal pops up and then it starts to buffer and then it records. I see that it creates a file in "Home Folder" for the recording, and inside that it has a folder called incomplete. How do I stop the recording so that I can complete the file?

2). Some file's can't be played in Movie Player, because it says I don't have the decoder to handle the file. Whare can I get them?

3). Can I set another player as my default player, besides Movie Player?

MrLeN

---

### Post by MrLeN on 2006-09-13
oh -- wow, it saves the file into my home folder after it is complete. That's cool! Bye Bye iTunes! Haha!

MrLeN

---

### Post by Wolki on 2006-09-13
> **MrLeN said:**
> 
2). Some file's can't be played in Movie Player, because it says I don't have the decoder to handle the file. Whare can I get them?


Open Add/remove programs, search for codecs. You should see something called gstreamer extra plugins and gstreamer ffmpeg plugin. Install both. For good measure, you can also install Xine extra plugins.

(gstreamer and xine are two different media frameworks, if you get both you'll also have the extra codecs already installed if you try to play something in a player based on that)

> 3). Can I set another player as my default player, besides Movie Player?


Right-click a media file, Properties, "Open with" tab.

---

