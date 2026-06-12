---
title: "How do I get RealPlayer/Helix Player to work?"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-04-22
I built a custom toolbar for Firefox, for the most part the toolbar works fine except the radio player built into it (the radio player works fine on XP) on Ubuntu I get this message:

[http://img204.imageshack.us/img204/5247/toolbar4fh.jpg](http://img204.imageshack.us/img204/5247/toolbar4fh.jpg)

then when I try to load Real player through ADD Programs I get the following message and I don't know what to do next?

[http://img54.imageshack.us/img54/9105/screenshot1nb.png](http://img54.imageshack.us/img54/9105/screenshot1nb.png)

:-k

---

### Post by jazzmuzik on 2006-04-22
Do you have Realplayer installed or just downloaded?

---

### Post by RAV TUX on 2006-04-22
[QUOTE=jazzmuzik]Do you have Realplayer installed or just downloaded?[/QUOTE]

downloaded NOT installed.

How do I install after download?

:-k

---

### Post by htinn on 2006-04-22
That process is described here:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by jazzmuzik on 2006-04-22
> downloaded NOT installed.

I thought so from the images. You want to install Realplayer from Synaptic (or Automatix). Like the poster above says, look at the Restricted Formats info.

Don't install Realplayer from a file you got at real.com. You want to install packages in the .deb package format. It makes life a lot easier.

As for Helix, does Helix even do anything? It seems like one big bump on a log to me.

If you install mplayer and the extra codecs, it will play realmedia formats as well.

---

### Post by RAV TUX on 2006-04-23
[QUOTE=jazzmuzik]I thought so from the images. You want to install Realplayer from Synaptic. Like the poster above says, look at the Restricted Formats info.

Don't install Realplayer from a file you got at real.com. You want to install packages in the .deb package format. It makes life a lot easier.

As for Helix, does Helix even do anything? It seems like one big bump on a log to me.

If you install mplayer and the extra codecs, it will play realmedia formats as well.[/QUOTE]

Thanks I loaded Mplayer...I hope it plays the internet radio player with no problems...

:-({|=

---

### Post by jazzmuzik on 2006-04-24
Generally you can play stuff with mplayer from the net like this:

mplayer [http://somesite.com/song.mp3](http://somesite.com/song.mp3)

But if you are listening to sites that use playlist files like .pls or .m3u try this:

mplayer -playlist [http://somesite.com/songs.m3u](http://somesite.com/songs.m3u)

---

### Post by RAV TUX on 2006-04-24
[QUOTE=jazzmuzik]Generally you can play stuff with mplayer from the net like this:

mplayer [http://somesite.com/song.mp3](http://somesite.com/song.mp3)

But if you are listening to sites that use playlist files like .pls or .m3u try this:

mplayer -playlist [http://somesite.com/songs.m3u](http://somesite.com/songs.m3u)[/QUOTE]

I am simply trying to get a internet radio player on a toolbar to work on Ubuntu in Firefox:


[http://jozefandleahs.ourtoolbar.com/](http://jozefandleahs.ourtoolbar.com/)

:-k 

Mplayer doesn't appear to work?

---

### Post by adamkane on 2006-04-24
You probably won't get much help with the toolbar. 

There are currently two ways to get streaming media to work in Ubuntu/Firefox.

Install the mplayer plugin for firefox via the automatix script:
[http://easylinux.info/wiki/Ubuntu#How_to_get_Automatix]("http://easylinux.info/wiki/Ubuntu#How_to_get_Automatix")

The other method is the mediaplayerconnectivity firefox extension:
[https://addons.mozilla.org/addon.php?id=446]("https://addons.mozilla.org/addon.php?id=446")

You'll want the latest version of ffmpeg, if you want mplayer to have support for ape/flac/mpc/wma/aac:
[http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb]("http://issaris.be/breezy/ffmpeg_0.20060410T134157_i386.deb")

If you get the toolbar working, please share the info with the rest of us.

---

### Post by jazzmuzik on 2006-04-24
You can drag and drop icons from the menus onto the tool bar.

---

### Post by eeried on 2006-04-24
Helix player, as you say, jazzmuzik, (i like jazz too!), doesn't seem to achieve anything much.

It would be a good idea though to have a free softawre replacement for realPlayer in countries whrer only RealPlayer is legal to read certain files -- Helix player would be just as legal, wouldn't it?
 
I tried to use it as a plugin. No way. And it seems  unable to read rst (something) protocol.

---

### Post by jazzmuzik on 2006-04-24
As for plugins... I'm trying to remember if the Realplayer plugin even works. I don't think I ever had much luck with it. Anyway, this is what I do. I'm not totally thrilled with the results, mostly when it comes to the buffering time before playing, but it works.

Install mplayer and all the extra codecs. 

Install mplayerplug-in which lets Firefox play all types of embedded movies via mplayer.

Then I tweak mplayerplug-in.conf (there's one in /etc/ or you create one in /home/user/.mplayer/mplayerplug-in.conf

I might add the following to it:

noembed=1

noembed lets the video play in a separate window. That way you can resize it by dragging the corners. Or you can use mplayer commands like +/- to control audio/video sync if it plays out of sync. Press 'f' and you get full screen.

Once you get it all installed, visit this page to test it out:

[http://service.real.com/realone/test/](http://service.real.com/realone/test/)

There are other test pages on the net to test other formats: avi, mpg, etc.

I also have RealPlayer installed although I don't care for the company or the format.

As for jazz, check out Bill Charlap or the New York Trio.

---

### Post by adamkane on 2006-04-24
You can play realmedia streams without RealPlayer:
[http://www.ubuntuforums.org/showthread.php?t=158337](http://www.ubuntuforums.org/showthread.php?t=158337)

---

### Post by jazzmuzik on 2006-04-24
[QUOTE=adamkane]You can play realmedia streams without RealPlayer:
[http://www.ubuntuforums.org/showthread.php?t=158337](http://www.ubuntuforums.org/showthread.php?t=158337)[/QUOTE]


Cool. Works for me so far.

---

