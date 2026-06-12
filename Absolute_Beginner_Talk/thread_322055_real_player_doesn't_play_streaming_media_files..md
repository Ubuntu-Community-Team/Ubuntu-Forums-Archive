---
title: "real player doesn't play streaming media files."
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by tony2 on 2006-12-19
real player plays mp3 files. but it does not play streaming media files. how to solve this?

---

### Post by pay on 2006-12-20
Do you have the amd64 version of Ubuntu? Make sure that there is the appropriate link from the plugin to firefox. Open up firefox and type in about:plugins in the searchbar.

---

### Post by macogw on 2006-12-20
I tried it on my comp too.  The thing says port 554 is closed and needs to be open.  I don't know how to edit iptables.  I found something that looked promising but tony said it didn't work.

---

### Post by tony2 on 2006-12-20
> Open up firefox and type in about:plugins in the searchbar

in the searchbar or location bar?

---

### Post by pay on 2006-12-20
I meant the address bar, where you type the internet adress. ie http

---

### Post by tony2 on 2006-12-23
i have intel p4 processor. streaming real media files don't play in firefox. real player is installed. rp plays files. but streaming media doesn't play in firefox. that's the problem now.

> **pay said:**
> I meant the address bar, where you type the internet adress. ie http

---

### Post by obsidion on 2006-12-23
> **tony2 said:**
> i have intel p4 processor. streaming real media files don't play in firefox. real player is installed. rp plays files. but streaming media doesn't play in firefox. that's the problem now.
  
do you see something like this when you ask firefox about it's plugins ?

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes

By my reckoning this is the third thread you have startted asking the same basic question, yet nowhere in any of those threads have you answered the question about whether you have the real player plugin enabled. Do you really want help or are you just trolling ? Please ask firefox about its plugins and post the output if you really do want help.

---

### Post by tony2 on 2006-12-26
no offense. 

when i try to visit [this page]("http://www.raaga.com/channels/tamil/movie/T0000386.html") and listen to a song. i get to see this

[snapshot attached]("http://img162.imageshack.us/img162/3148/snap2xz1.png").

any solution for this?

---

### Post by obsidion on 2006-12-26
> **tony2 said:**
> no offense. 

when i try to visit [this page]("http://www.raaga.com/channels/tamil/movie/T0000386.html") and listen to a song. i get to see this

[snapshot attached]("http://img162.imageshack.us/img162/3148/snap2xz1.png").

any solution for this?

  What plugins have you installed in firefox ?
Without this basic information, helping you is virtually impossible.

---

### Post by imda2001 on 2007-05-12
Let's say I have a similar problem...I installed RealPlayer and did the wrapper solution to get Helix into my FireFox plugins page (see below), but I can't watch any video on CBS's Innertube setup.

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: npwrapper.nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes




Am I missing something?  It keeps kicking back with an error that reads:

The player does not have the capabilites to play back this content.
The following components are required:
text/html

URL:
[http://www.w3.org/2001/SMIL20/Language](http://www.w3.org/2001/SMIL20/Language)


Thanks for any help!

---

