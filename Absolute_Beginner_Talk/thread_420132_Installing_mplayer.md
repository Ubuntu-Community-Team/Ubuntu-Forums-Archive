---
title: "Installing mplayer"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-04-23
I'm trying to install mplayer, mainly to display quicktime movies on web pages. I've been following various threads here, and  on [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) but I'm still having problems.

I downloaded the source, binary and a skin, and extracted them, and ran configure,  make, and make install. I downloaded the codecs and installed them.

I've already added the mplayer plugin to Firefox.

When I extracted mplayer, I extracted it to my /home - but when I installed it, of course it isn't in the ./mplayer directory, but the ./home. Can I just move it to where I want it to be (./mplayer)? Or should I remove it (how?) and reinstall to the correct place?

TIA - I'm having an extra stupid day today!

---

### Post by annda on 2007-04-23
i think it would be best to manually get rid of mplayer (since you installed it manually).

```
sudo updatedb
locate mplayer
```

to find all related files. then remove them by hand and install mplayer again from the repositories:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

---

### Post by lluisanunez on 2007-04-23
Alternatively, use VLC to see quicktime movies (and any other format)

---

### Post by freesitebuilder on 2007-04-25
The reason I downloaded and installed manually, was I got an error using the repositories:
"The following packages have unmet dependencies.
  mozilla-mplayer: Depends: mplayer (>= 1.0-pre5) but it is not installable"

And each step I went back gave me another dependency, so I thought it would be better to install from the mplayer site. 

I've got VLC installed, and it works for files I select, but when I try to view QT files on webpages, it speeds through them in a sort of "fast-play" mode. I'll play with it some more.

Thanks to you both for your advice!

---

### Post by oilchangeguy on 2007-04-25
use automatix to install mplayer and all of the needed codecs. [www.getautomatix.com](www.getautomatix.com)

---

### Post by maa on 2007-04-25
how can i install window apps like games, winrar, Turboc,jetaudio,and many more software in ubuntu 6.06
I m a beginner i know nothing about installtion.plzzzzzzz help me!!!!!!!!!!!!
:confused:

---

### Post by oilchangeguy on 2007-04-25
you can't, unless the disc includes linux as one of the operating systems it'll work with. if you're wanting to play games, your best bet is to dual boot with windows and ubuntu.

---

### Post by lluisanunez on 2007-04-25
I've been installing all the media players these days, and as every player has it's own mozilla plugin I can't remember exactly when, but I had the same problem with web QT videos. But I've found  Firefox extension Media Player Connectivity, it works as a Preferences menu where you can set a player for any media format (screenshot below)

---

### Post by freesitebuilder on 2007-04-26
And I really wasn't going to install more extensions! But that's a good one, thanks. 

The .mov file I'm having the problem with is one of those "tour" panorama embedded files - it works OK in windows, so I've viewed it. But I'd like to resolve the problem so I can make a complete switch eventually.

That's why I'm dual-booting now - I can get used to the Ubuntu way without panicking because I need to get something done and can't.

---

### Post by freesitebuilder on 2007-04-26
> **maa said:**
> how can i install window apps like games, winrar, Turboc,jetaudio,and many more software in ubuntu 6.06
I m a beginner i know nothing about installtion.plzzzzzzz help me!!!!!!!!!!!!
:confused:

This is a good page, "How to install anything in Ubuntu":
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I still find it useful - the different methods of installing, and questions that I had after switching from windows (I'm still dual-booting).

---

