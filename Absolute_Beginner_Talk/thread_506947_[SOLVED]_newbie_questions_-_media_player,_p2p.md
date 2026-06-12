---
title: "[SOLVED] newbie questions - media player, p2p"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-22
Just gave up Windows XP for Ubuntu Feisty. 

Media player questions:
Which media player works best ? (other that movie player, and rhythmbox, of course)
Do Kaffeine or Amarok work ok in Ubuntu?
The particular feature I'm looking for is the ability to put songs in a queue from the folder itself (I know some people will think of it as a Windows Media Player hangover, but this sort of a feature is more suited to the way I choose what music I want to listen to.)

P2P questions:
I used Ares to download music and stuff on Windows - which one works best on Ubuntu?

---

### Post by tomcheng76 on 2007-07-22
i am running Amarok in Fluxbox and Gnome, so it works in Ubuntu
i would suggest Audacious - Winamp like player, support unicode
what does "put songs in a queue from the folder itself " means ?
i am not good at english , sorry
Amarok is good at manage songs, it has music library function to help u keep track of your Music folder and add them to playlists
while Audacious is fast and as gd as winamp 2.x

I would suggest Ktorrent
or wine + utorrent , both are very good

---

### Post by testube_babies on 2007-07-22
Similar to Ares is [Frostwire]("http://www.frostwire.com/").  If you're looking for other bittorrent clients, then there are plenty of options for that:  ktorrent, utorrent + wine, azureus, deluge, etc.

For a movie player, I'd go with VLC (available from repos).

Amarok is one of the greatest audio players out there, but if you're looking to queue directly from a folder, perhaps xmms or audacious is what you are looking for (both are similar to Winamp).

---

### Post by kleo skywalker on 2007-07-22
Thanks.
I downloaded audacious, and it works ok, but I still don't know how to enqueue files from the folder itself. 
P.S.: Just checking, is that not possible using another player?

---

### Post by testube_babies on 2007-07-22
I would try the player XMMS.  I'm not sure it has that feature, either, though.  That's not a very popular feature in the age of iTunes :)

---

### Post by kleo skywalker on 2007-07-22
Never used iTunes or anything like it. Point is, I like to selct my music manually -  go to my music folder, browse and enqueue all the songs I want to listen to - then later I can change the order and stuff if I want - but that's that. So I seriously need a music player that can do that. Preferably a media player, so the same can be done for videos. That's why I asked earlier about Amarok and Kaffeine...
So, help still wanted!

---

### Post by testube_babies on 2007-07-22
I think you may be out of luck...most music players have an built-in search function to find songs.  And I don't think ANY have nautilus integration of the type you're looking for.


...And yes, Amarok and Kaffeine will both work in Gnome, but again neither have nautilus integration.

---

### Post by benerivo on 2007-07-22
Amarok works fine in Ubuntu, and it does exactly what you want - and many other things.

update - sorry i misunderstood what you meant by 'folder'. I thought you meant the folder in the 'tree' view inside the music player. However you can the Amarok library view in a 'file manager' mode and drop contents of your download folder on to the playlist.

[http://wiki.ubuntu.org.tw/images/thumb/0/0b/500px-9-34amarok-file.png](http://wiki.ubuntu.org.tw/images/thumb/0/0b/500px-9-34amarok-file.png)

---

### Post by testube_babies on 2007-07-22
[COLOR="Red"][B]I hereby stand corrected; it's possible with this nautilus script and BMP, XMMS, or Amarok:

[http://dontoddrc.wordpress.com/2006/01/07/add2q-nautilus-script-to-add-files-to-queue/](http://dontoddrc.wordpress.com/2006/01/07/add2q-nautilus-script-to-add-files-to-queue/)[/B][/COLOR]

---

### Post by benx009 on 2007-07-22
for media player, mplayer all the way...

---

### Post by kleo skywalker on 2007-07-22
> **benerivo said:**
> Amarok works fine in Ubuntu, and it does exactly what you want - and many other things.

update - sorry i misunderstood what you meant by 'folder'. I thought you meant the folder in the 'tree' view inside the music player. However you can the Amarok library view in a 'file manager' mode and drop contents of your download folder on to the playlist.

[http://wiki.ubuntu.org.tw/images/thumb/0/0b/500px-9-34amarok-file.png](http://wiki.ubuntu.org.tw/images/thumb/0/0b/500px-9-34amarok-file.png)

No I don't mean the library thing. I mean folder as in the place where I store my music files. Isn't there a music player which I can use to enqueue one or more songs from the folder itself? Manually, not generated playlists...

---

### Post by benerivo on 2007-07-22
Well in kde (i don't know about the Gnome desktop) you can right click a file and select 'Append to playlist', and it adds the song(s) to the current Amarok playlist.

Also, the pic i attached shows Amarok with a file manager view on the left. It is the same as any normal window view such as nautilus (note the up, back, forward, home buttons on the top), except that it has a filter to only include audio files. Try it.

---

### Post by testube_babies on 2007-07-22
Alright, this will set up everything you need to queue a file in Beep Media Player from a folder:
```
sudo apt-get install beep-media-player
cd ~/.gnome2/nautilus-scripts
wget --no-check-certificate http://mywebspace.wisc.edu/kpolicano/web/add2queue
chmod +x add2queue
killall nautilus
```

After nautilus restarts, you can right-click on a file and choose Scripts -> add2queue

If you don't like this, you can remove it with:```
rm ~/.gnome2/nautilus-scripts/add2queue
```



...If this is really a big deal for you, maybe trying out KDE is in order.

---

### Post by kleo skywalker on 2007-07-25
The script thing sounds promising, just a question: how do I change the script to get the thing working for XMMS only? Also, will it work with Rhythmbox and if yes, how do I change the script for XMMs as default and Rhyhmbox as the next option?
And a last one: how do I find out if a player supports this or not?
Thanks again.

---

### Post by kleo skywalker on 2007-07-26
Thanks for the suggestions and help everyone.
Tried out several music players, as of now Exaile works for me. Also got XMMS, just in case. Would still like to give the script thing a shot though.
As for the P2P, I'm trying out GTK-Gnutella. It works fine, but the interface is complex and I can't figure out how to filter search results for content.

---

### Post by kleo skywalker on 2007-08-07
Music players: Exaile, XMMS
P2P: GTK-Gnutella, Frostwire
Thanks.

---

### Post by switchcode on 2007-08-11
Heres a solution I found on another ubuntu forum;

> 
_richardward101   November 30th, 2006, 11:56 PM_

OK then, bring up a terminal and type:

sudo nano /bin/xmmsqueue

then type:

#!/bin/bash
xmms -e "$@"


Now press CTRL+O (not zreo) to save, and CTRL+X to exit

now:

sudo chmod +x /bin/xmmsqueue

now right click an mp3 in the file browser and click properties, go to the 'open with' tab and click add, use a cuton command, and type in:

xmmsenqueue

make sure its selected as the default in the 'opens with' tab, and now when you double click files they should enqueue in xmms.

Hope that works.

I just set this up; Works perfectly =)

Edit: Just educated myself on bash scripts and discovered that arguments containing spaces are seen as separate particles by the command interpreter thingy, so if you were to try to enqueue a tune with spaces in it's filename, xmms would only be "sent" the final word after the last space; "Dead Reckoning.mp3" would become "Reckoning.mp3".. So I Changed $@ to "$@" ..Im learning =)

---

### Post by zakalwe_ukuk on 2007-08-11
You can add songs to the queue from folders in amarok. When you right click and select  "open with amarok" , rather than start playing the song it adds it to the queue, although it will play the very first track you choose.  Amoaroks library viewer would be a much easier way to do do this though as you can view and select from you whole collection.

---

### Post by Stefff on 2007-08-11
Hi guys, 
It's just amazing how quality of sound is 30-40 % better on Ubuntu, than on Windows!

Simple question:
Is there a library agent on Audacity, and how can I install it?

I switched on Ubuntu 2 days ago, from Vista:lolflag:

---

### Post by switchcode on 2007-08-11
System menu>Administration>Synaptic package manager
Click "Search" at the top, enter "audacity", hit Enter, Mark the beast for installation (click the square), then click apply (the green tick in the main button bar)..
All library dependancies will be installed automatically =D

---

