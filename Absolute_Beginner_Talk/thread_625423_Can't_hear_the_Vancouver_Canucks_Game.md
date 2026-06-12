---
title: "Can't hear the Vancouver Canucks Game"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Dannyblueyes on 2007-11-28
Just installed Ubuntu while on vacation. Absolutely love it. Apps are WAY easier to run. Most problems have been easy to solve.

This problem is really killing me though. I'm in Hawaii and I can't play the Canucks game at [http://www.team1040.ca/player/](http://www.team1040.ca/player/)

Before I could get it using windows media player. Now every time I load the site up the player immediately switches into stop mode. 

Can anyone tell me what program to use to download this feed? Better yet, can anyone tell me a way to get this data using Totem, Music box, or Kaffine?

I'm a complete linux newbie. I know very little about command lines, entering code, or whatever the hell it's called. Most of my programs have either come from the application menu, included automatic installers (i.e. Nero linux), or have run using WINE.

I know there's other patriotic Canadians like myself here that can help me out. Best believe I have your back. Thanks in advance

---

### Post by DutyDuty on 2007-11-28
Do you have MPlayer installed? It is supposed to play most things in Firefox, etc. 
(Flyers fan, btw)

---

### Post by Dannyblueyes on 2007-11-28
I just installed both the player and the firefox extention as well. I'm getting the same result as before. I even tried to manually input the url for the site. That failed. 

I'm having the same problem trying to log on to 106.1 kmel as well. Any advice

---

### Post by crf on 2007-11-29
> **Dannyblueyes said:**
> I just installed both the player and the firefox extention as well. I'm getting the same result as before. I even tried to manually input the url for the site. That failed. 

I'm having the same problem trying to log on to 106.1 kmel as well. Any advice

Go to nhl.com, and go to the media section, where you can click to open links to the games on radio. Maybe some of those will work. They are in some sort of windows media format. They changed the site around since last year though (of course it's worse :P ).

What works for me --> use synaptic package manager to install the Gstreamer "bad" plugins. 

In the web page, click or copy the link to the radio stream. For example, from [http://www.team1040.ca/player/](http://www.team1040.ca/player/), go to view source in firefox and see the link [http://www4.insinc.com/ibc/mp/md/play/u/356/1408/wa56en.asx](http://www4.insinc.com/ibc/mp/md/play/u/356/1408/wa56en.asx).

Paste that link into firefox and it should put up a dialog box for opening a file called wa56en.asx (this is a windows media playlist file). Tell firefox to open it with the Movie Player (or whatever). Then Totem Movie Player opens and you can listen to the canuckleheads.

---

### Post by Znort_Ubern00b on 2007-11-29
[Try this link]("https://addons.mozilla.org/en-US/firefox/browse/type:7") it adds plugins to firefox...for winmedia player and others...

---

### Post by Dannyblueyes on 2007-11-29
> **crf said:**
> Go to nhl.com, and go to the media section, where you can click to open links to the games on radio. Maybe some of those will work. They are in some sort of windows media format. They changed the site around since last year though (of course it's worse :P ).

What works for me --> use synaptic package manager to install the Gstreamer "bad" plugins. 

In the web page, click or copy the link to the radio stream. For example, from [http://www.team1040.ca/player/](http://www.team1040.ca/player/), go to view source in firefox and see the link [http://www4.insinc.com/ibc/mp/md/play/u/356/1408/wa56en.asx](http://www4.insinc.com/ibc/mp/md/play/u/356/1408/wa56en.asx).

Paste that link into firefox and it should put up a dialog box for opening a file called wa56en.asx (this is a windows media playlist file). Tell firefox to open it with the Movie Player (or whatever). Then Totem Movie Player opens and you can listen to the canuckleheads.

Canuckleheads? LOL you must be from Vancouver too. I just installed the "bad" gstreamer plugins that were on the application menu and now both stations work just fine. Same as they did using windows Vista. Thank you very much for your help.I'm looking forward to hearing Luongo break the team shutout record against the blue jackets

---

