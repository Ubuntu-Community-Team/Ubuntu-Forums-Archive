---
title: "just a few questions on totem..."
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Jareth on 2006-09-17
I've reinstaled dapper so there's no more windows (Did you cheer too?), I'm just trying to sort out the media player bit.

I don't mind using the totem so long as I can get as much media to work through it as poss.
At the moment it seems to be 'just out of the box' mode, everything I try just says no right now.
What 'stuff' should I install to get it working 'good and proper?'
I assume its all available in synaptic package manager.

Sorry if this just leads to further questions, but if anyone can give a list of the major stuff I'll probably get the gist from there.

Ta, la!

---

### Post by catlett on 2006-09-17
Go through the Dapper Guide, it will list the proper codecs etc. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
Make sure you use their repository list [http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories](http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories)
Then just follow the guide. It will list the multimedia codecs etc [http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Codecs](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Codecs)
The only thing the guide is missing is win32 codecs but you can get the instructions for them here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
You may have to experiment a bit before you get the player you like. Totem gstreamer is installed by default but there is also totem-xine, xine, vlc and others.

---

### Post by Ultra-Loser on 2006-09-17
*cheer*

Ok, so the first thing you'll want to do is enable the extra repositories. [This page]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") should help you out. 

After that, install totem-xine. That should allow you to play more media types, but to play non-basic formats you'll need to install extra codecs. [This page]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs") should help you with that. I've heard that automatix does this for you, but I've always been a do-it-yourself user so I wouldn't know about that.

Enjoy Ubuntu! :D

---

