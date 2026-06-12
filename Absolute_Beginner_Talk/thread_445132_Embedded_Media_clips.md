---
title: "Embedded Media clips"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-05-15
Is it possible to play embedded media, the sort of clips that appear on the BBC News website. Thanks.

---

### Post by Hobo Joe on 2007-05-15
Yes. In what format?

---

### Post by crimesaucer on 2007-05-15
What browser do you use? And what formats?

In Firefox, Opera, and Epiphany, the mplayer with the mozilla-mplayer "plug-in" or the mozplugger "plug-in" works.

But in Firefox, you can also use the Media Player extension and play embedded media in whatever media player you use, it just doesn't play "embedded" in the page.

mozilla-mplayer:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-123.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-123-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-123-1.png)

mozplugger:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-122.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-122-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-122-1.png)

---

### Post by crimesaucer on 2007-05-15
Also, here is the wiki links: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28MPlayer.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28MPlayer.29)

or the Firefox add-on: [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

...and I think the mozplugger is only needed for Opera, I could be wrong.

---

### Post by ugm6hr on 2007-05-15
I found that the combination of VLC (search for VLC on Synaptic Package Manager, and install Firefox Plugin) for most formats and Realplayer (search for realplayer_10.0.7-0.0.i386.deb in google, and just open file with GDeb I think) for realmedia works for most formats.  I've also got the Firefox MediaPlayer Connectivity plugin (which I think I installed from the Firefox website, although I'm not certain), and this allows you to select which Player to use for each media format.  Can't get and Digital Rights Management embedded files to work though (as in channel4.com), since they require Windows Media Player.  But I'm happy to live without that (unless someone has a solution!).

---

### Post by linuxforrealpeople on 2007-05-21
Folks

I have tried all of the above with no success. When I try to play a windows media clip in Firefox I get:

[IMG]http://farm1.static.flickr.com/225/508489507_a7f27ec49c.jpg?v=0[/IMG]


Any help would be appreciated. Thanks.

---

### Post by chang47 on 2007-05-22
If you are on Feisty Fawn, for Real Player, you should get the latest version from [www.real.com](www.real.com).  
Follow the link to download RealPlayer10GOLD.bin


See [http://ubuntuforums.org/showthread.php?t=433103&highlight=Real+Player](http://ubuntuforums.org/showthread.php?t=433103&highlight=Real+Player) 

thread for installation instruction.  I hope you are not afraid of doing command lines as there is no graphical tool to do this install.  This is the only version I find working.  

I am still trying to find a good solution to play embedded Windows stuff as MPlayer is not working with CNN that requires Windows Media Player.

I ran Xubuntu 7.04 on a Celeron 128MB RAM and it is still peppy.  It is a giant step compared to the old Windows ME running on it.

Good luck.

---

### Post by linuxforrealpeople on 2007-05-22
I have managed to install Real Player (&could not have done without a bit of Unix knowledge).

I then had to configure Firefox to use the correct executable and Bingo - I can now play BBC clips.

Thanks

---

### Post by linuxforrealpeople on 2007-06-30
All of a sudden I now find that there is no sound (there was initially). This is usng real player. For all other apps sound is fine. Any ideas folks? Thanks.

---

