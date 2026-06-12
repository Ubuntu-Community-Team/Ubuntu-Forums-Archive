---
title: "How to play movies"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-10-11
I have Dapper 6.06.1 LTS from a DVD and think I have all the updates available but cannot open a .WMV file.

I Googled for Ubuntu and WMV and found this:-

[http://www.zerohex.org/2006/04/06/ubuntu-and-wmv-support-how-to/](http://www.zerohex.org/2006/04/06/ubuntu-and-wmv-support-how-to/)

but since this info is about 6 months old, I wondered if there was something newer and more appropriate for my version of Ubuntu?

Thanks.

Lewis.

*****

---

### Post by skymt on 2006-10-11
For this kind of thing, you should go to the [wiki](https://help.ubuntu.com/community/RestrictedFormats) before Google. It (the wiki) is always up-to-date.

---

### Post by gn2 on 2006-10-11
> **L Campbell said:**
> I have Dapper 6.06.1 LTS from a DVD and think I have all the updates available but cannot open a .WMV file.

I Googled for Ubuntu and WMV and found this:-

[http://www.zerohex.org/2006/04/06/ubuntu-and-wmv-support-how-to/](http://www.zerohex.org/2006/04/06/ubuntu-and-wmv-support-how-to/)

but since this info is about 6 months old, I wondered if there was something newer and more appropriate for my version of Ubuntu?

Thanks.

Lewis.

*****


[www.getautomatix.com](www.getautomatix.com)

This should get you sorted.

You need to add codecs and other bits and pieces for Ubuntu to be really useful.

This is easily done with Automatix.

---

### Post by whiterabbit on 2006-10-11
Try VLC.  

```
sudo apt-get install VLC
```

...and follow this guide if you need much else.  It'll tell you how to install multimedia support and other misc. goodies with no trouble.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by L Campbell on 2006-10-12
> **whiterabbit said:**
> Try VLC.  

```
sudo apt-get install VLC
```

...and follow this guide if you need much else.  It'll tell you how to install multimedia support and other misc. goodies with no trouble.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Thanks.

I tried this but couldn't get it to work.

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package VLC

Did I do something wrong?

Kind regards.

---

### Post by PriceChild on 2006-10-12
its actually "vlc" not "VLC"

I suggest you follow [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) instead of automatix or vlc.

This will help you learn how to do things yourself, and let you learn about how your system works, and how to fix it. Automatix also doesn't crash easily.

VLC player uses its own codecs, whereas that wiki page will install codecs for all the multimedia players on your pc.

---

### Post by thornomad on 2006-10-12
> **L Campbell said:**
> I tried this but couldn't get it to work.

Maybe (and I am not sure) VLC is part of the Universal Packages ?  Or, try it without capital letters "vlc" ... if it is a Universal app, you need to enable those in your /etc/apt/sources.list by uncommenting the two "unviverse" lines:

```
sudo gedit /etc/apt/sources.list 
```

Then scroll down, you will see them ... remove # marks.  Then run a apt-get update and then try to install it again.

D

---

### Post by Delkster on 2006-10-12
> **L Campbell said:**
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package VLC

Did I do something wrong?

Package names shouldn't have capital letters. Try with "vlc". You'll also need the "universe" software repository enabled if you don't already.

---

### Post by whiterabbit on 2006-10-12
Ah, you're correct.  My bad.  It should be in lower case.

---

### Post by carloslosgrande on 2006-10-12
Hi Lewis, I'm a beginner myself and I'm often confused with the command line stuff. *Just to start things off* you might want to look around the very top left of your screen for 'System' click this then click 'Administration' then click 'Synaptic Package Manager'
this lists many applications and the parts that go with them. I also highly recommend doing what I am in the process of right now - reading detailed instructions on how to use linux commands etc, etc as well as the Wiki's available. If you look at some of my recent threads you'll find many helpful links posted by members here.
hope this helps.

---

### Post by L Campbell on 2006-10-12
> **PriceChild said:**
> its actually "vlc" not "VLC"

I suggest you follow [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) instead of automatix or vlc.

This will help you learn how to do things yourself, and let you learn about how your system works, and how to fix it. Automatix also doesn't crash easily.

VLC player uses its own codecs, whereas that wiki page will install codecs for all the multimedia players on your pc.

............

Thanks, this is an interesting link you sent and I followed the instructions it gave but, after doing it all, I did 'search' and still was unable to find ' wmv '.

In the left column of Synaptic I have ALL and wmv.

In the 'package' section I have 14 itmes from

' helpdeco ' to   ' wxvic '.

Does this give a clue as to what is going on?

Kind regards.

---

### Post by devnulljp on 2006-10-12
Use automatix to install the w32 codecs
then use 
Mplayer or Kaffeine

---

