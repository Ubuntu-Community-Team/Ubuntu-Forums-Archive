---
title: "Can't play DVDs"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by Tosa on 2005-11-27
Hi,

I've got codecs installed (libdvdcss2 included) but when I try to play dvd Totem returns:
"*Totem could not play 'dvd:/'. The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?*".

When I sweetch to Mplayer I get:
"*Failed to open dvd://1*".

Now, VLC player simply doesn't do enything. But when I manualy start the first VOB it continues with the rest (menus disabled).

I've gone through the posts but couldn't find help on this (or didn't recognize it).

Any ideas what should I do?

Tosa

---

### Post by teaker1s on 2005-11-27
css
and look [here]("https://wiki.ubuntu.com/RestrictedFormats")
totem doesn't work well for me I use okle

---

### Post by asombill on 2005-11-27
I am having problems also, I am getting this:

Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-a md64_Packages) - stat (2 No such file or directory)
...

I am stuck here and still can't play DVDs, help anyone?

---

### Post by Tosa on 2005-11-27
Thanks, but as I've said it in my post I've allready installed codecs and libdvdcss2. By the way the libdvdcss2 that is installed on the page is lower version than the one in the repositories.
Anyway the players are acting the same way...

---

### Post by Tosa on 2005-11-27
Hi asombill,

I've just (re)installed libdvdcss2 through synaptic. There were no problems, at least not according to synaptic.

---

### Post by asombill on 2005-11-27
[QUOTE=Tosa]Hi asombill,

I've just (re)installed libdvdcss2 through synaptic. There were no problems, at least not according to synaptic.[/QUOTE]


I did a search, probably not thorough enough, but how do I install synaptic?

---

### Post by Tosa on 2005-11-27
You don't have to, it's allready there!
System > Administration > Synaptic package Manager
Just type the libdvdcss2 (or whatever else you are trying to find) in search dialog and after a couple of clicks you are done...

---

### Post by asombill on 2005-11-27
Thanks, but it is not in the list.

---

### Post by raublekick on 2005-11-27
[QUOTE=asombill]Thanks, but it is not in the list.[/QUOTE]


you have to enable the other repositories, do a quick search on here and you should be able to find what you need.

i too am having similar problems. installed all the stuff needed and still can't play DVD discs.

---

### Post by Tosa on 2005-11-27
Oops, sorry, you should check universe and multiverse repositories, and add these:

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) binary free non-free
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) source free non-free
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) binary free non-free
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) source free non-free

Settings > Repositories > Add > Custom

---

### Post by raublekick on 2005-11-27
[QUOTE=teaker1s]css
and look [here]("https://wiki.ubuntu.com/RestrictedFormats")
totem doesn't work well for me I use okle[/QUOTE]


i just did this ```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

from the wiki page, and it worked. it's weird that it downgrades libdvdcss2, but it made it work. i even updated back to the original when the little update butom showed up in the tray. 

totem is a little skippy with the video, maybe i'll give okle a try.

---

### Post by Tosa on 2005-11-27
[QUOTE=Tosa]
I've got codecs installed (libdvdcss2 included) but when I try to play dvd Totem returns:
"*Totem could not play 'dvd:/'. The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?*".

When I sweetch to Mplayer I get:
"*Failed to open dvd://1*".

Now, VLC player simply doesn't do enything. But when I manualy start the first VOB it continues with the rest (menus disabled).[/QUOTE]

I've tried again, but no luck. Still the same thing with either version of libdvdcss2...

---

### Post by kingsidy on 2005-11-27
are u using totem-xine. if not install it from apt or from synaptic and see what happens

---

### Post by Tosa on 2005-11-27
It says it's totem 1.2.0 using xine lib 1.0.1.
Is that what you mean by totem-xine?

---

### Post by starNIX on 2005-11-28
I am having the exact same issue.  Anyone figure this out?  It only started happening since I upgraded to breezy.  It worked fine in Hoary.

---

### Post by PrincessPeach on 2005-12-03
I'm having the same problem.  I have libdvdcss2 already. I tried playing my DVD through Totem, Xine, Totem-Xine, Mplayer, VLC, and none of them are working.  I'm also on Breezy.

---

### Post by starNIX on 2005-12-03
I dont know if this will help anyone else but "Automatix" fixed this for me.

---

### Post by ned.b on 2005-12-03
What is "Automatix"?

---

### Post by raublekick on 2005-12-03
It's a script that helps you install lots of useful stuff (Audio/video codecs, etc...)

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by ned.b on 2005-12-03
thanks for the link :-)

---

### Post by chiisu on 2005-12-03
[QUOTE=raublekick]totem is a little skippy with the video, maybe i'll give okle a try.[/QUOTE]

all programs will be skippy when playing dvd's until DMA is enabled

---

### Post by chiisu on 2005-12-03
[QUOTE=Tosa]It says it's totem 1.2.0 using xine lib 1.0.1.
Is that what you mean by totem-xine?[/QUOTE]

that's correct, instead of totem-gstreamer which is the usual installation on most linux distros

---

