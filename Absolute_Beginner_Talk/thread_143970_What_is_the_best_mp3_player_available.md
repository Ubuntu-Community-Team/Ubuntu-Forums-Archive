---
title: "What is the best mp3 player available"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by madhu on 2006-03-13
What is the best mp3 player available,that best suites Ubuntu.If possible plz get me the URL of the page from where I can download it.


Thank You.

---

### Post by TrendyDark on 2006-03-13
Amarok, although it's supposed to be a KDE application, using the following code gets it working fine under Gnome:

```
sudo apt-get install amarok
```

:)

---

### Post by Kurt` on 2006-03-13
I prefer XMMS,

```
apt-get install xmms
```

Just try out a few and see which you like best. :)

---

### Post by TrendyDark on 2006-03-13
Yes, XMMS is a good choice as well. This is where you need to make a choice. 

XMMS: Good for light-weight listening. It's got a nice, small, "put away" look. It's just like Winamp (without the library feature).

Amarok: Has a whole bunch of features including a library, lyrics, wikipedia artist profile, and native last.fm support.

---

### Post by chimera on 2006-03-13
I prefer Rythmbox, it has a great library that I really miss in other players.

---

### Post by Perfect Storm on 2006-03-13
BMP is what I prefer.

Though it requires that you have universe enable.
then:

```
sudo apt-get install beep-media-player
```

[[img]http://www.imageviper.com/displayimage/27889/0/smallbmp.jpg[/img]]("http://www.imageviper.com/displayimage/27887/0/bmp.jpg")
*[size=1]Click the picture to enlarge*[/size]

---

### Post by ronmarley1 on 2006-03-13
I second the nomination of XMMS.  I also added the EQU equalizer for XMMS.  XMMS is available in the repos, and EQU can be had at sourceforge.  See the screen cap below of XMMS.

---

### Post by mcduck on 2006-03-13
I prefer MPD with GMPC and NCMPC. It has fastest library I have ever seen in any player, and music continues playing even if I log out. And if I leave it playing when I shutdown, when I boot again it starts playing even before the login screen is loaded. \\:D/ 

I think it's not about what player bests suits Ubuntu, it's about what player best suits you.

edit: Here is a nice HOWTO for MPD: [http://www.ubuntuforums.org/showthread.php?t=31763&highlight=mpd]("http://www.ubuntuforums.org/showthread.php?t=31763&highlight=mpd")

---

### Post by aysiu on 2006-03-13
I favor either JuK or AmaroK, as they both have global keyboard shortcuts for changing songs, adjusting volume, seeing what song is playing, etc.

---

### Post by purdy hate machine on 2006-03-14
[QUOTE=ronmarley1]I second the nomination of XMMS.  I also added the EQU equalizer for XMMS.  XMMS is available in the repos, and EQU can be had at sourceforge.  See the screen cap below of XMMS.[/QUOTE]

Now that I like, thanks for sharing.

The beauty of Ubuntu is that it’s so easy to install and cleanly remove applications using Synaptic that you can just try a whole bunch of players until you find one you like.
These seem to be the most popular.

XMMS
Amarok
Beep
Rhythmbox
Muine
Beep-media-player

---

### Post by predaeus on 2006-03-14
another one I did not see above is

Banshee 

Very much like amarok for gnome, I'd say. But still missing some features like the Q (for queueing) option in XMMS and lyrics etc.

That's the reason why I still use XMMS. Use gxmms to integrate XMMS into the gnome panel.

---

### Post by zi99y on 2006-03-14
I've taken to amarok lately, it does everything I want with global shortcuts - has a sweet interface, gives me nice suggestions and shows what I've listened to most. And there's tons of plugins, some good and some not, but you can even use a bluetooth device (such as a mobile) as a remote control. Then when you're playing radio streams, there's a plugin to record them to mp3.... 

It's fully featured, but if you want something lightweight, best stick with xmms.

---

### Post by mrgnash on 2006-03-14
I'm going to nominate Amarok as well. It's one of the apps which makes Windows users mad with jealousy :twisted:

---

### Post by Stinger on 2006-03-14
The greatest mp3 , ogg , flac player / tag editor / jukebox is in my opinion 

[Gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html")

Try it and you'll be convinced too !
:mrgreen: :mrgreen: :mrgreen:

---

### Post by jazzgossen on 2006-04-17
I'll take this opportunity to rant about my experiences with the music players I've tried.

Amarok is really nice. Only drawbacks are that it looks KDE, and, more seriously, that the version in the Dapper repositories doesn't work for me. I just get a bunch of dialog boxes complaining about unknown MIME types, and amarok crashes.

Banshee also crashes when I try to import my library.

Gmusicbrowser just refuses to play anything. Nothing happens when I click the play button.

Muine complains about a backend error, and wants me to install the appropriate plugins (but doesn't say which plugins). It also refuses to quit, so I have to kill it the "hard" way.

Listen has an issue with 8-bit characters. Song titles with åöä looks strange (a lot of characters are just missing) in the pop-ups and song list. Also, it creates a ~/Podcasts directory on startup, which I find very annoying.

XMMS is good, but I *really* miss a media library plugin.

Rhythmbox is OK, but the interface is not perfect. One annoyance is that you can't queue all songs by an artist by right-clicking in the "artist pane". You have to select the artist, then select all of the songs in the "song title pane", then add them to the queue. And also, you can't shuffle the queue. Once you put songs in the queue, they play in that order. 

Quodlibet is OK. I'm not totally happy with the UI, but it's the best for me so far.

---

### Post by mostwanted on 2006-04-17
My favourite is Muine. I really like how albums and no nonsense controls are in focus:

[IMG]http://monkeyblog.org/img/screens/Muine_dapper.jpg[/IMG]

---

### Post by tom56 on 2006-04-17
[QUOTE=jazzgossen]Once you put songs in the queue, they play in that order.[/QUOTE]

Not strictly true; you can change the order manually, though yes, there's no way to shuffle it.

Personally I'd say Rhythmbox is the best, and the development going on right now seems good, lots of innovation and new features. Definitely the most stable for me too, though as always YMMV. The version shipped by default is fairly old though, get the one on the mighmos site (google for the URL).

---

### Post by henriquemaia on 2006-04-17
I'm with the Amarok fans. 

It has everything.

---

### Post by steve.horsley on 2006-04-17
Nobody has mantioned Xine yet.

---

### Post by gigi1234 on 2006-04-17
Amarok is great if you want all those bells and whistles.

I really Beep for a stripped-down just-works MP3 player.

---

### Post by bom28 on 2006-04-18
[QUOTE=jazzgossen]
Gmusicbrowser just refuses to play anything. Nothing happens when I click the play button.
[/QUOTE]
You should install at least one of mpg321 (for mp3), vorbis-tools (for ogg) and flac123 (for flac)
I tried them all, and for me gmusicbrowser is the best, even if some things could be improved, and it doesn't support ipod or radio. And it doesn't yet support translations. Maybe not for everyone, but very powerful and customizable.

---

### Post by jazzgossen on 2006-04-19
[QUOTE=bom28]You should install at least one of mpg321 (for mp3), vorbis-tools (for ogg) and flac123 (for flac)
I tried them all, and for me gmusicbrowser is the best, even if some things could be improved, and it doesn't support ipod or radio. And it doesn't yet support translations. Maybe not for everyone, but very powerful and customizable.[/QUOTE]
The description of gmusicbrowser says that it uses either gstreamer or mpg321 etc. I have both gstreamer 0.8 and 0.10, so I thought that would be enough. Will try with mpg321, though.

Edit:
OK, after installing mpg321 it works. This is a great player!! Now I'm happy again!

---

### Post by Gustav on 2006-04-19
[QUOTE=jazzgossen]Rhythmbox is OK, but the interface is not perfect. One annoyance is that you can't queue all songs by an artist by right-clicking in the "artist pane". You have to select the artist, then select all of the songs in the "song title pane", then add them to the queue.[/QUOTE]
I miss that feature to, but you don't have to do all that, you can drag'n'drop the artist (or album) to the queue.

---

### Post by dr.drake on 2006-04-19
[QUOTE=zi99y]... Then when you're playing radio streams, there's a plugin to record them to mp3.... 
[/QUOTE]

**what? where? what's that plugin called, I neeeeeeed it!**

anyway, amarok is the player for me, no windows or mac player comes close for me, and I run all 3 systems.
and don't worry about the way it looks, you can dress it down to just the essentials, like you can see in this screenshot:
[IMG]http://www.geocities.com/mrktpltsnl/amarok.jpg[/IMG]

---

### Post by Stinger on 2006-05-18
If you want to add the tray icon features to gmusicbrowser , don't forget to install the "libgtk2-trayicon-perl" package !!

---

### Post by Klaidas on 2006-05-18
I use both XMMS and amaroK. XMMS more often I think. :)

---

### Post by Biltong (Dee) on 2006-05-18
Tried em all and still consider 'Listen' to be the best. 
It's easy to use, which for me is very important.

---

### Post by manicka on 2006-05-18
[QUOTE=Biltong (Dee)]Tried em all and still consider 'Listen' to be the best. 
It's easy to use, which for me is very important.[/QUOTE]

yeah, for me it's a toss of the coin between amaroK and Listen. If I could find an xchat plugin for Listen it would be perfect :)

---

### Post by Biltong (Dee) on 2006-05-18
If you do then my life will be complete. :-)

---

