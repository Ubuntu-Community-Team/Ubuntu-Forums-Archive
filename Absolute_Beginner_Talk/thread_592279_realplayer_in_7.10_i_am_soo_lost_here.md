---
title: "realplayer in 7.10 i am soo lost here ? ? ?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by james.dismuke on 2007-10-26
**ok i am running 7.10 and need real player or windows media player to play bbc radio and i have tried every" how to guide" so far but none have worked can  someone please tell me how to do this**

**help ! ! ! i am in sudo heck here??**](*,)](*,)](*,)

p.s. thank everyone for all the help

---

### Post by Anicka on 2007-10-26
Including this? [http://ubuntuforums.org/showthread.php?t=587953&goto=newpost](http://ubuntuforums.org/showthread.php?t=587953&goto=newpost) ```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb
sudo dpkg -i realplayer_10.0.9-0.1_i386.deb
```

It would be slightly more helpful if you had wrote in your post which methods you have tried.

---

### Post by Billisnice on 2007-10-26
how to you get it to work in firefox?

---

### Post by philinux on 2007-10-26
Have you installed realplay10 from synaptic

Just search for realplayer in synaptic it should install the plugin for the bbc streaming audio it works fine for me.

---

### Post by genbuntu on 2007-10-26
```
 When you install RealPlayer in Ubuntu Edgy Eft, it will install not only the player but also the firefox plugins. There&#8217;s a problem, though. Firefox is preconfigured to play real audio streams with totem. To use the real player plugin you must remove the totem plugin responsible to play these real audio streams. Just go to the firefox plugins directory located on:

/usr/lib/mozilla-firefox/plugins

and remove

libtotem-complex-plugin.so

libtotem-complex-plugin.xpt

type:

sudo rm libtotem-complex-plugin.*

and happy listening with realplayer plugin for Firefox 2
```

-Above copied from: [http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/](http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/)

EDIT: Also see [https://help.ubuntu.com/community/FirefoxPlugins](https://help.ubuntu.com/community/FirefoxPlugins)

---

### Post by Dirty Ole on 2007-10-26
> **james.dismuke said:**
> **ok i am running 7.10 and need real player or windows media player to play bbc radio and i have tried every" how to guide" so far but none have worked can  someone please tell me how to do this**

**help ! ! ! i am in sudo heck here??**](*,)](*,)](*,)

Do this:

```
sudo apt-get install helix-player mozilla-helix-player
```

---

### Post by philinux on 2007-10-26
+1 dirty ole.

Could not remember how helix got in my plugins thought it came with RP 10

---

### Post by philinux on 2007-10-26
Thats weird just checked and I've got the helix plugin but mozilla-helix plugin is not installed when I checked in synaptic. :confused:

---

### Post by Anicka on 2007-10-26
Seems to be a problem with that package. Uninstall the one I suggested (sudo apt-get uninstall realplayer) and use this instead:
wget -c [http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.0_i386.deb)
sudo dpkg -i realplayer_10.0.9-0.0_i386.deb

It worked for me right now on a computer were it hasn't been installed earlier. However the package I suggested first worked at home, but maybe some old configuration-files were still around.

---

### Post by philinux on 2007-10-26
As you can see in synaptic from the installed files pane  realplay does install the helix plugins.

---

### Post by Anicka on 2007-10-26
Philinux,
As you also can see in synaptic is that you have the feisty-version installed. Realplayer is no longer available from the semi-official repos (medibuntu, canonical), neither for feisty nor for gutsy. This is a problem for many users of Ubuntu. I was (in a thread that I already have quoted) given the advise to do it like this and it worked for me. However the newest version from that webpage of some reason does not seem to have the plugin correctly, but the second newest does.

Helix might work for some users, but the webradio I usually listen to, doesn't recognize it.

---

### Post by philinux on 2007-10-26
Right well thats explains it for me then as I upgraded. Then enabled medibuntu repo again. but I didnt have to reinstall realplayer.

---

### Post by james.dismuke on 2007-10-27
thanks for all the help guys ! ! ! i have to switch the stream to the real player not in firefox but it works:P:)

---

### Post by por100pre1 on 2007-10-27
Try RealPlayer for Feisty:

[http://archive.canonical.com/pool/main/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/pool/main/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

---

### Post by Orbital75 on 2007-10-27
Make sure you have all the repositories enabled and then search
for real player as suggested above.....  It may be you don't have
the correct repository enabled.  If this doesn't work here is a link
to the Firefox Real Player plug in.

[https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)

---

