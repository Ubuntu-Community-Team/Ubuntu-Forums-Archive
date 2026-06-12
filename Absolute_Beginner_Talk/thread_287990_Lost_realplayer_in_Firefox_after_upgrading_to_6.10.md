---
title: "Lost realplayer in Firefox after upgrading to 6.10"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2006-10-29
I've just upgraded from 6.06 to 6.10 and I'm no longer able to view video from the BBC News website in Firefox as I was able to in 6.06. In the latter it opened up a RealPlayer window and the video played in that. Now, a separate window opens up but with no video. 

Realplayer 10 is still listed in my applications list and I can run it separately. It seems that the upgrade has changed some settings; how can I change them back or get video to play in Firefox again?

Thanks.

---

### Post by ajgreeny on 2006-10-29
Is it still listed in your "about:plugins" in firefox?  Type that in the address bar and see if it's there.  If not, I presume you need to reinstall the realplayer plugin.

---

### Post by fsman on 2006-10-29
I have the same problem too.
I think that about:plugins is looking for the totem plugin for realaudio/video rather than realplayer - hence BBC site doesn't work as it is looking for realplayer.

I'm looking for a fix too.

---

### Post by tomcat1965 on 2006-10-29
Me too,it's listed in plugins and just tried a re-install and still get blank player window:-| 
However there is a workaround,change your preferences to windows media player and the BBC video will play via the totem xine plugin. Not quite the quality of RealPlayer but perfectly acceptable.:)

---

### Post by BackInTimeMan on 2006-10-30
Edgy here and just another me too I'm afraid, it's very frustrating. I have lots of plugins, Totem, Helix, mplayer, DivX, Realplayer 9, QT and so on. It appears that I should be able to play any format known to wo/man, but I can't. Trying at BBC, Firefox always trys to use the Totem plugins but they don't work and there is no way to select which one you want to use. Not all of them appear in the File Types config box and those that do, only appear occasionally. Maybe have to uninstall the lot and start from scratch.

---

### Post by fsman on 2006-10-30
I've found a fix.
the problem is that the totem-mozilla plugin is trying to play realmedia files - so the bbc site doesn't like it as its looking for realplayer.

If you goto firefox and then about:plugins you see that real files are associated with the totem complex plugin - even through the real plugins are in the firefox directory.

to make firefox use realplayer you need to get rid of libtotem-complex-plugin.so and libtotem-complex-plugin.spt from /usr/lib/firefox/plugins

e.g. cd /usr/lib/firefox/plugins
sudo mv libtotem-complex* ~/

now bbc site uses realplayer and all is well.

Caution - I don't know what these libtotem-complex plugins do (other than realmedia) so this is really a hack at the moment.

---

### Post by Perfect Storm on 2006-10-30
Just remove totem-mozilla plugin from synaptic will do the trick.

---

### Post by Charlie Chick on 2006-10-30
Thanks for all your replies. I've been tearing my hair out on this one. Nothing seems to work. I've tried everybody's suggestions, but without success. 

Given that I upgraded from a fully working 6.06, you would expect an upgrade to be at least no worse than the version it replaced, but frankly, 6.10 doesn't work as well as 6.06 and I'm going to go back to 6.06.

---

### Post by Perfect Storm on 2006-10-30
Aye, 6.10 is an experimental version and needs a bit of tweaking if it doesn't work.

Or you could try 6.10 fresh install. Bigge and better chance that it will work than dist-upgrade.

---

### Post by Mr*Wiggy on 2006-10-30
to make firefox use realplayer you need to get rid of libtotem-complex-plugin.so and libtotem-complex-plugin.spt from /usr/lib/firefox/plugins

e.g. cd /usr/lib/firefox/plugins
sudo mv libtotem-complex* ~/

I'm a newbie on Linux and Ubuntu. I've been trying for 2 days to get Firefox/RealPlayer working on the with BBC website. I thought it was all my fault ](*,)

So I tried your fix as above and guess what - it's working now! - but with Mplayer! How come? 

Eric

---

### Post by Perfect Storm on 2006-10-30
Somehow totem's plugin rules above all else, I guess.

---

### Post by BackInTimeMan on 2006-10-30
fsman:

I took out all the Totem plugins as the MPlayer ones cover everything. Now at the BBC, it does initialise the MPlayer plugins both for Real and WM. That's the good news :) ... the bad news is that all that happens is I see the plugin comtacting the URL for the stream, then it stops, zilch. Nothing will actually play. A step in the right direction though, cheers.

---

### Post by fsman on 2006-11-03
> **BackInTimeMan said:**
> fsman:

I took out all the Totem plugins as the MPlayer ones cover everything. Now at the BBC, it does initialise the MPlayer plugins both for Real and WM. That's the good news :) ... the bad news is that all that happens is I see the plugin comtacting the URL for the stream, then it stops, zilch. Nothing will actually play. A step in the right direction though, cheers.

Get realplayer installed as all will be well - right tool for the right job

add the ubuntu-commercial repo (note add dapper for now (edgy is incomplete)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

then
sudo aptitude install realplay

---

### Post by BackInTimeMan on 2006-11-03
I'm reluctant to install Realplayer TBO, never installed it in Windows because of it's bad reptutation. Do you have experience with it on Linux? Other people have got the Beeb working with MPlayer plugins but I can't seem to find a way of making it work. I wish they (BBC) would go with an OS format, I know they are developing their own but it isn't happening very fast. Can't see the need to do that anyway as Ogg is already available.

---

### Post by mnmallik on 2006-11-03
Hi Guys,
I am newbie to linux and just yday i installed ubuntu 6.10. I a problem with real audio.I am not able to play online media audio and video i dont know why? i removed helix player as it was having a conflict on some file with real player.
To sum it up i would like to open raaga.com and listen to music and open trailer sites and watch trailers.
PLs guide me through the process.

p.s: I already have real player 10 instaled but when i cjecked the preference s of mozilla content it does not show association of real media to real player.i removed totem plugin too

thks in advance
Mallik.

---

### Post by BackInTimeMan on 2006-11-03
Hi mnmallik,

Sorry I can't help you with this as I can't get online media to work myself. Maybe if you posted again, starting your own thread, then  someone may be able to help you. Good luck!

---

### Post by steevc on 2006-11-04
I had similar problems on upgrading to Kubuntu Edgy. I was getting Kaffeine opening on Realplayer streams. It would play the audio, but I could not fast forward from the BBC player.

I fixed this by removing

/usr/lib/firefox/plugins/kaffeineplugin.so

This must have been added by the upgrade. I'm sure that might be useful in some cases, but for now I just need my BBC radio playback, even if it doesn't play nicely with other audio, i.e. blocks sound from other apps.

---

### Post by Charlie Chick on 2006-11-05
Guys (and Girls), I eventually solved this problem by installing Realplayer and removing MPlayer, including all the plugins. I use Gxine for everything else. Now, when I open video in the BBC News site, it opens automatically in Realplayer and Gxine copes well with virtually all other formats (assuming that you installed the Windoze codecs etc). 

If you then re-install MPlayer and its Firefox plugin, BBC News video tries to use that to play video and, for me, that never worked. Un-installing it when you already have Realplayer installed appears to re-instate Realplayer for BBC News videos.

I hope that this might help someone.

---

