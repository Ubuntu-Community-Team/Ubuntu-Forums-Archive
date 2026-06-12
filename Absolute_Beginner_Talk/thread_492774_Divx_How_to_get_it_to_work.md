---
title: "Divx: How to get it to work?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-07-05
Hello once again!

I have read a few Divx problem threads, and I tried the different ways on how to get Divx embeded movies to play, but none of them work for me!:(

I even tried installing a Firefox add-on, but that lead me to think that5 none of my media players can play Divx, not even mplayer.

Any thoguhts?

---

### Post by moredhel on 2007-07-05
first, install vlc.

Then use the media connectivity plugin (aka addon) for firefox.

Then after running the wizard (i normally set everything to vlc, except realmedia which i set realplayer for linux as), go into the settings and set divx (which isn't included in the wizard) to vlc.

That worked for me ;)

---

### Post by Akuma Shiro on 2007-07-05
I tried all of that. VLC just sat there, it would try to play then just stop. Even a direct stream didn't work.
My friend said to get the mplayer codecs, but I can't figure out how to get them to install...:(

---

### Post by moredhel on 2007-07-05
try downloading a random divx file off the internet, then try to open it with totem. It should ask you whether you want to search for the codecs neccesary to play the file. Then try viewing embedded ones again.

---

### Post by overdrank on 2007-07-05
> **Akuma Shiro said:**
> I tried all of that. VLC just sat there, it would try to play then just stop. Even a direct stream didn't work.
My friend said to get the mplayer codecs, but I can't figure out how to get them to install...:(

HI maybe these links will help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Good luck!

---

### Post by mcduck on 2007-07-05
Mplaye-plugin plays mpeg4 movies (like those created with divx) just fine. But you need to remove totem-plugin first, as firefox seems to prefer using it but Totem doesn't work too well with all mpeg4-movies created with divx.

If it doesn't work, you may need to create symlink for one of the plugin files, as it seems it's not always linked to correct place unlike other plugin files. I'm not at my own computer right now but I'll check the file and where it should be linked when I get back home.

---

### Post by moredhel on 2007-07-05
That could come in handy for me as well, instead of having to view them externally in vlc!

---

### Post by mcduck on 2007-07-05
First uninstall the totem plugin for Firefox, and make sure mplayer-plugin is installed.

Run this command in a terminal and check if you can see "mplayerplug-in-dvx.so" and "mplayerplug-in-dvx.xpt" listed:
```
ls /usr/lib/firefox/plugins/
```

If you did see them, mplayer-plugin should be able to handle embedded divx videos. If you they weren't listed, run following commands to create symlinks for those files:
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```

Restart Firefox and try if embedded divx movies now work. :)

---

### Post by Akuma Shiro on 2007-07-05
> **mcduck said:**
> First uninstall the totem plugin for Firefox, and make sure mplayer-plugin is installed.

Run this command in a terminal and check if you can see "mplayerplug-in-dvx.so" and "mplayerplug-in-dvx.xpt" listed:
```
ls /usr/lib/mozilla/plugins/
```

If you did see them, mplayer-plugin should be able to handle embedded divx videos. If you they weren't listed, run following commands to create symlinks for those files:
```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```

Restart Firefox and try if embedded divx movies now work. :)

Here is everything I have. The .so part didn't appear to be in the blue'ish color...

troy@nave1L:~$ ls /usr/lib/mozilla/plugins/
libtotem-basic-plugin.so         mplayerplug-in-dvx.xpt
libtotem-basic-plugin.xpt        mplayerplug-in-qt.so
libtotem-gmp-plugin.so           mplayerplug-in-qt.xpt
libtotem-gmp-plugin.xpt          mplayerplug-in-rm.so
libtotem-mully-plugin.so         mplayerplug-in-rm.xpt
libtotem-mully-plugin.xpt        mplayerplug-in.so
libtotem-narrowspace-plugin.so   mplayerplug-in-wmp.so
libtotem-narrowspace-plugin.xpt  mplayerplug-in-wmp.xpt
mplayerplug-in-dvx.so            mplayerplug-in.xpt
troy@nave1L:~$ 

So, yeah...

---

### Post by Akuma Shiro on 2007-07-05
For reference, here is all I get on Divx movies...

[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/divx.png[/IMG]

On every single Divx link...

---

### Post by Akuma Shiro on 2007-07-05
> **mcduck said:**
> Mplaye-plugin plays mpeg4 movies (like those created with divx) just fine. But you need to remove totem-plugin first, as firefox seems to prefer using it but Totem doesn't work too well with all mpeg4-movies created with divx.

If it doesn't work, you may need to create symlink for one of the plugin files, as it seems it's not always linked to correct place unlike other plugin files. I'm not at my own computer right now but I'll check the file and where it should be linked when I get back home.

Also, I looked at the add on's / plug-ins on firefox, and i didn't see any totem items, unless it's in the file directory somewhere. If that's the case, I am still unfamiliar with navigating around linux.

---

### Post by Akuma Shiro on 2007-07-06
> **overdrank said:**
> HI maybe these links will help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Good luck!

I just tried the restricted formats link, the terminal said that the win32codec saved, but the page says nothing about any further action. and I still cant play divx videos on [tv-links.co.uk]("http://tv-links.co.uk")

here is everything the terminal said...



troy@nave1L:~$ wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
--07:45:11--  [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
           => `w32codecs_20061022-0.0_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 213.186.33.17
Connecting to www.debian-multimedia.org|213.186.33.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb) [following]
--07:45:12--  [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
           => `w32codecs_20061022-0.0_i386.deb'
Resolving ftp.sunet.se... 194.71.11.69
Connecting to ftp.sunet.se|194.71.11.69|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,243,872 (14M) [application/x-debian-package]

100%[====================================>] 14,243,872   129.82K/s    ETA 00:00 

07:47:31 (100.24 KB/s) - `w32codecs_20061022-0.0_i386.deb' saved [14243872/14243872]

troy@nave1L:~$ sudo dpkg -i w32codecs_20061022-0.0_i386.deb


Nothing... Then I hit enter thinking that would do something...

troy@nave1L:~$ sudo dpkg -i w32codecs_20061022-0.0_i386.deb
Password:
(Reading database ... 118543 files and directories currently installed.)
Preparing to replace w32codecs 20061022-0medibuntu1+build1 (using w32codecs_20061022-0.0_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20061022-0.0) ...



Still won't play.:(

---

### Post by mcduck on 2007-07-06
> **Akuma Shiro said:**
> Also, I looked at the add on's / plug-ins on firefox, and i didn't see any totem items, unless it's in the file directory somewhere. If that's the case, I am still unfamiliar with navigating around linux.

Use Synaptic to remove the totem plugin. Don't even try to remove it manually. (In your screenshot it's clearly the totem-plugin, not mozilla-plugin.

You can also see available plugins if you type "about:plugins" in the address bar.

---

### Post by Akuma Shiro on 2007-07-06
> **mcduck said:**
> Use Synaptic to remove the totem plugin. Don't even try to remove it manually. (In your screenshot it's clearly the totem-plugin, not mozilla-plugin.

You can also see available plugins if you type "about:plugins" in the address bar.

Ok, I removed the plug-in. Now I get a notification that I need the plug-in to play the vid.

Nothing out of the ordinary...

Untill I clicked to get the plug in...

[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/noplugin.png[/IMG]

No plug-in available.

So I remembered this... [MediaPlayerConnectivity]("https://addons.mozilla.org/en-US/firefox/addon/446")

Not working either. No matter how I configure it.

---

### Post by mcduck on 2007-07-07
Did you create those links? Try to find some video that m player-plugin can open, then right-click on the playing video and select "Configure" to open the settings window. Then make sure "Enable DivX Support" is enabled.

---

### Post by Akuma Shiro on 2007-07-07
> **mcduck said:**
> Did you create those links? Try to find some video that m player-plugin can open, then right-click on the playing video and select "Configure" to open the settings window. Then make sure "Enable DivX Support" is enabled.

Divx support is enabled, i'm guessing it was already marked by default.

I went to the Divx stage 6 site, and it said on a movie screen that I need mplayer (which I have).
So, I clicked on a movie to watch, and it said I needed the firefox plugin, so I clicked on manual install plug0in, and it took me to the Divx web player download site, but the player is only for windows, and I doubt if it will work right with Wine.

I went into the synaptic package manager, and installed the mplayer-doc iten, and that took care of another problem I was having, but I still can't play Divx. And I am trying different links as well.

I am sure it is just a simple problem to fix, and I am trying my best to follow instructions, and I am learning alot as well.

---

### Post by mcduck on 2007-07-07
Did you run these commands I gave you? If not, try them now and restart Firefox.

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```

---

### Post by Hallvor on 2007-07-07
Just out of curiousity, have you only tested the previously mentioned page or others as well?

I visited tv-links.co.uk with a laptop running Windows XP, and the page would not even run on Windows Media Player. Insted I was prompted do download some "DivX web player", which should have been totally unneccesary considering WMP should be able to play it without a problem.

My guess is that the page uses DRM.

So what other pages have you tested?

The FF MediaPLayerConnectivity plugin and VLC should play almost anything out there.

---

### Post by Akuma Shiro on 2007-07-07
> **mcduck said:**
> Did you run these commands I gave you? If not, try them now and restart Firefox.

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```

It said the files already existed. I think I did the code a day or two ago. I restarted firefox, and presto! everything is working perfectly through mplayer. I think what I installed from the synaptic package manager helped as well, but when I did that, I didn't restart firefox.

Lesson learned: restart/reboot.

I am in your debt mcduck.

=i tested every page I could think of with Divx videos=
But now, all is well. I thank you all.

---

