---
title: "Beep Media Player"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by Solomon on 2005-08-17
Ok, I have a rather dumb question. Earlier today I worked on making AVI and MP3 files playable on this system and it worked. They work. I can hear them & enjoy them. In a search to find a program to replace WinAmp, I installed BEEP Media Player. I call it the "Winamp Rip" in a good way. However, In this program... I am unable to play MP3 music files among others. Why can I not play such files in this program but I can in the others such as the pre-installed "Music Player"? I need advice on how to fix this problem as well as detailed steps if you have the time.

---

### Post by Solomon on 2005-08-17
Anyone out there?

---

### Post by aysiu on 2005-08-17
You've done this already?

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by Solomon on 2005-08-17
[QUOTE=aysiu]You've done this already?

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)[/QUOTE]
 Indeed I have Aysiu. I installed those via the Terminal before I installed B.M.P. Should I install them again?

---

### Post by aysiu on 2005-08-17
[QUOTE=Solomon]Indeed I have Aysiu. I installed those via the Terminal before I installed B.M.P. Should I install them again?[/QUOTE] I don't know. It's weird. When I went to the BMP website, its list of plugins

[http://www.sosdg.org/~larne/w/Plugin_list](http://www.sosdg.org/~larne/w/Plugin_list)

didn't have MP3 on it. It had MP4 and Flac, though. Is it possible BMP doesn't do MP3? I don't know. I use Amarok and Rhythmbox myself.

---

### Post by Solomon on 2005-08-17
[QUOTE=aysiu]I don't know. It's weird. When I went to the BMP website, its list of plugins

[http://www.sosdg.org/~larne/w/Plugin_list](http://www.sosdg.org/~larne/w/Plugin_list)

didn't have MP3 on it. It had MP4 and Flac, though. Is it possible BMP doesn't do MP3? I don't know. I use Amarok and Rhythmbox myself.[/QUOTE]
 I highly doubt it doesn't play MP3's. That's just... not right.

---

### Post by aysiu on 2005-08-17
This isn't the solution, of course, but you said you were looking for a WinAmp replacement. Have you tried XMMS?

---

### Post by Solomon on 2005-08-17
Yes, that was in fact what I was planning to install. B.M.P is XMMS, Ubuntu style as I understand it. B.M.P is based on XMMS.

---

### Post by aysiu on 2005-08-17
The best I could find was this:

[http://stentz.freshrpms.net/rpm.html?id=33](http://stentz.freshrpms.net/rpm.html?id=33)

Maybe you could use alien to install the rpm?

---

### Post by endy on 2005-08-17
Does the "MPEG Audio Plugin" show up if you right click BMP then go: Preferences > Plugins > Media tab ?

If so you may want to check all the settings are right, however this is indeed strange  :-?

---

### Post by Solomon on 2005-08-18
Everything is in order my friend. The plugin is in fact, installed. And I believe it to be configured correctly because I can hear audio on the other music player. It is just this paticular player.

---

### Post by rpgcyco on 2005-08-18
Have you tried different output plugins?

- Rpg Cyco

---

### Post by Solomon on 2005-08-18
[QUOTE=rpgcyco]Have you tried different output plugins?

- Rpg Cyco[/QUOTE]
 I am sorry. This is my second day using Linux. Could you explain your question in more detail please?

Also, on a side note: BMP seems to freeze up when I attempt to play the file. The time displays but it doesn't play and the program seems to freeze up. Does this have anything to do with it?

---

### Post by aysiu on 2005-08-18
[QUOTE=Solomon]I am sorry. This is my second day using Linux. Could you explain your question in more detail please?

Also, on a side note: BMP seems to freeze up when I attempt to play the file. The time displays but it doesn't play and the program seems to freeze up. Does this have anything to do with it?[/QUOTE] I had the same problem with BMP, actually.

---

### Post by Solomon on 2005-08-18
You gotta give me a little more than that. Did you get rid of it? If so, how do I uninstall it? What do you use? The actual XMMS player? If so, how do I install it? Where does the newborn go from here?

---

### Post by aysiu on 2005-08-18
[QUOTE=Solomon]You gotta give me a little more than that. Did you get rid of it? If so, how do I uninstall it? What do you use? The actual XMMS player? If so, how do I install it? Where does the newborn go from here?[/QUOTE] Truthfully, I never dug XMMS. You can try it out if you want. There's no harm in that. For a while I was using Rhythmbox, but I didn't like how it kept refreshing my library every time I started up. So I ditched Rhythmbox for Amarok. A few things I like about Amarok:

1. Smart playlists
2. Lyrics-fetching for just about any song
3. Customizable keyboard shortcuts
4. Refreshable library (manual refresh *or* automatic)

I've also heard good things about Juk, but it didn't do much for me. What's the harm in downloading these all through Synaptic and seeing what works for you?

Oh, and you uninstall the same way you install. Just go to Synaptic Package Manager. Find the program, mark it for removal, then hit Apply. "Complete" removal means the configuration files get removed as well (your settings and preferences).

---

### Post by rpgcyco on 2005-08-18
[QUOTE=Solomon]I am sorry. This is my second day using Linux. Could you explain your question in more detail please?

Also, on a side note: BMP seems to freeze up when I attempt to play the file. The time displays but it doesn't play and the program seems to freeze up. Does this have anything to do with it?[/QUOTE]

Sorry. :)

Open BMP -> Preferences -> Plugins -> Output.

There should be three plugins in the dropdown box that you can try.

- Rpg Cyco

---

### Post by Solomon on 2005-08-18
Ok that worked. I had to change my output. Thank you very much. :)

---

### Post by rpgcyco on 2005-08-19
No problem.

Hopefully, the in development version BMPx will be backported to Breezy when it's eventually done. I don't think there is a chance of it being done by Breezy's release in October.

- Rpg Cyco

---

