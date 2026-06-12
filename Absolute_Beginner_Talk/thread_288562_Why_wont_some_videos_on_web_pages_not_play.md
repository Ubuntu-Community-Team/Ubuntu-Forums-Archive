---
title: "Why wont some videos on web pages not play?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-10-30
I was wondering why videos on some web pages will not play.  For example, on this news web site the videos in the right hand side of the page wont play unless I go to Windows and use IE
[http://www.news.com.au/adelaidenow]("http://www.news.com.au/adelaidenow")

Anyone know?

---

### Post by Mimsy on 2006-10-30
Well, when I tried a moment ago the site told me I need to install Windows Media Player before I can watch the movies, so I would guess that's your problem. Sorry. :)

/Mimsy

---

### Post by Russty of Oz on 2006-10-30
OH!  So it is the fact that the web site isn't Firefox friendlly!  I will have to change to another news provider or just read the text.

Thanks :)

---

### Post by land0 on 2006-10-30
Give this a shot [http://www.getautomatix.com/](http://www.getautomatix.com/) install the Multimedia codecs 
and whatever else you may want. When it is done install mozilla-totem-xine plugin using Synaptic. If the mozilla plug-in does not appear upon your first search go to Settings--> Repositories--> make sure all of the available repositories are selected. You do this by clicking on the add button to the left of the repository list. Then check the box beside Community Maintained (Universe) and None-Free(multiverse). Then click the add button and close the repository list. After that you should click on the reload button and it should appear. Install the plug-in and it should work. 


I hope this helps.

---

### Post by r4ik on 2006-10-30
Plays fine with Mplayer and plugin on Dapper don't know about Edgy. 

Good luck.

---

### Post by Mimsy on 2006-10-30
Or if you get Automatix2 instead, you can just check the box next to "Mplayer" and then click the start button. ;)

Good luck!

/Mimsy

---

### Post by cenoxo on 2006-10-30
The instructions at the following site will install the applications and codecs to view embedded Flash, Quicktime, RealPlayer, and Windows Media Videos. These include the latest Flash plugin, Totem-xine, Totem-xine Firefox plugin, W32 video codecs, and Sun Java5 plugin:

[INDENT]**How-To: Get Full Multimedia Support and Playback Capabilities in Ubuntu Desktop Linux**
[http://www.ehomeupgrade.com/entry/2663/how-to_get_full]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full")[/INDENT]

Afterwards, you can use Ubuntu's Applications > Add/Remove menu to uninstall the Banshee, Skype, Streamtuner, XMMS, and F-Spot applications. You can also avoid these uninstalls by editing the Terminal command (in the fourth How-To step) from this:

[INDENT]sudo apt-get install totem-xine totem-xine-firefox-plugin libxine-extracodecs flashplugin-nonfree msttcorefonts sun-java5-plugin skype banshee streamtuner xmms realplay f-spot[/INDENT]

to this:

[INDENT]sudo apt-get install totem-xine totem-xine-firefox-plugin libxine-extracodecs flashplugin-nonfree msttcorefonts sun-java5-plugin realplay[/INDENT]

Your results may vary, but this worked for me with Ubuntu 6.06 LTS *Dapper Drake* and FireFox 1.5.0.7.

---

### Post by Russty of Oz on 2006-10-30
I already have Automatix2 and it says I already have mplayer installed.:-?

---

### Post by Circus-Killer on 2006-10-30
and thats the reason i dont use progs like automatix and easyubuntu :neutral:

---

### Post by Sef on 2006-10-30
Read [Restriced Formats]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5").


Then Applications > Accessories > Terminal

Next install the w32 codecs as per the instructions [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5").

Update: Tried the site and had no luck.  Looks like another website would be best.

---

### Post by Perfect Storm on 2006-10-30
hehehe...it uses the evil .asf format. ](*,)

But it works on mine.

---

### Post by Russty of Oz on 2006-10-30
Yes, I will have to just read it, if there is a video there that I just HAVE to view, I will just use Windows for it.  I just thought there may have been something I was missing, but now I see that it is that the web site is designed for use with windows.  Hopefully one day in the not too distant future all web sites will realize that a lot of people are turning away from Windows and will make there sites more useable to everyone.  Why should we be dictated to by a conglomerate!  

Since I began using Edgy a couple of months back, I have been using Windows less and less every day.  This sort of thing happening only makes me more determined to use Linux and open source software.  In fact, I think I will remove that web site from my bookmarks, and use the ABC News instead! After all, Murdocks News Ltd and Microsoft are both in the same boat, trying to force everyone to use thier service.  

It's time for a revolt!!!

**LONG LIVE UBUNTU!  **:D

---

### Post by Russty of Oz on 2006-10-30
> **Artificial Intelligence said:**
> hehehe...it uses the evil .asf format. ](*,)

But it works on mine.

OH!  You must have something the rest of us don't!   Still don't bother telling me how as I have already deleted that bookmark.

---

### Post by xyz on 2006-10-30
Russty of Oz
Having all the correct codecs installed, I was able to watch the videos you pointed us to by clicking on it (didn't work with mplayer plugin) so then I right-clicked on it to copy the url and then pasted it in VLC.
Good day.

---

### Post by Russty of Oz on 2006-10-30
Well, I will have to try that myself, just in case I come across something else like that.

Thanks for the tip! :)

---

### Post by xyz on 2006-10-30
> **Russty of Oz said:**
> Well, I will have to try that myself, just in case I come across something else like that.

Thanks for the tip! :)
I really hope it'll work for you, too. Let us know...
Nice videos..by the way!

---

### Post by Perfect Storm on 2006-10-30
> **xyz said:**
> Russty of Oz
Having all the correct codecs installed, I was able to watch the videos you pointed us to by clicking on it (didn't work with mplayer plugin) so then I right-clicked on it to copy the url and then pasted it in VLC.
Good day.

Strange, mine works with mplayerplug-in. Though it take max. 25 secs before it starts up on a 1Mbit connection. Can it be because I'm using Epiphany browser, perhaps it's a firefox issue.

---

### Post by xyz on 2006-10-30
> Can it be because I'm using Epiphany browser, perhaps it's a firefox issue.
I downloaded Epiphany just to give it a try but no go either!

---

### Post by Mimsy on 2006-10-30
> **Artificial Intelligence said:**
> Strange, mine works with mplayerplug-in. Though it take max. 25 secs before it starts up on a 1Mbit connection. Can it be because I'm using Epiphany browser, perhaps it's a firefox issue.

I watched the video in Firefox, with the mplayer plugin. (At least I think I did, there was sound, and pictures that moved...)

/Mimsy

---

### Post by SunnyRabbiera on 2006-10-30
Just remember if stuff doesnt play on Ubuntu it normally means its M$ only, this is because of M$'s monopoly and general lack of interest for anything not M$ based.

---

### Post by Circus-Killer on 2006-10-30
well, if you just install everything from this guide: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
you will be able to play almost everything.

the only thing you cant play is video protected by DRM (Digital Rights Manager). so if you tryna view a clip on a subscription based news (or porn) site, then no luck, you wont be able to play those in linux.

but following the above mentioned guide will get you playing every other format needed. DO NOT BOW DOWN TO DRM! :twisted:

---

### Post by Russty of Oz on 2006-10-30
> **xyz said:**
> Russty of Oz
Having all the correct codecs installed, I was able to watch the videos you pointed us to by clicking on it (didn't work with mplayer plugin) so then I right-clicked on it to copy the url and then pasted it in VLC.
Good day.

I tried that but it didn't work for me??

---

### Post by SunnyRabbiera on 2006-10-30
You cant win everything, like i said some video's know what os you are on and what version of windows media you use.
This is the only reason to either have a dual boot or have XP in a virtual session.

---

### Post by Russty of Oz on 2006-10-30
XP in a virtual session??

---

### Post by Russty of Oz on 2006-10-31
Now this is weird!

I have been using FF2 which I downloaded from Mozilla, but when I switch to FF2 that is already in Ubuntu, I get a little black screen where the video should be!!  Nothing actually plays but it looks like there is actually a player there.  However, I also get a little message that says "Can't parse that"   "no files":-? 

I also tried Opera but it couldn't play it either.

Oh well!

---

### Post by d3v1ant_0n3 on 2006-10-31
It started playing for me. Then Firefox died. But it's been doing that all day for me. So it probably wasn't the video. I use Mplayer plugin and restricted codecs.

---

### Post by Russty of Oz on 2006-10-31
I've got Mplayer and all the codecs as well, but it still won't play for me.

---

### Post by Circus-Killer on 2006-10-31
err nevermind

---

### Post by Russty of Oz on 2006-10-31
](*,) I agree!

Subject closed.

---

### Post by xyz on 2006-10-31
Typing "about:plugins"...you are certain you've got all you need there?

Also just to make sure, I went back to the AdelaideNow site a few minutes ago and tried playing " Ch 9 - Good news for Hardie asbestos victims" . Clicking on the url below had my box trying to play it with the mplayer plugin...No go!:

[http://media01.news.com.au/adelaidenow/Willyama-BB.wmv?clipId=1383_58375&channel=Local+Videos&category=&site=adelaidenow%2fvideoplayer](http://media01.news.com.au/adelaidenow/Willyama-BB.wmv?clipId=1383_58375&channel=Local+Videos&category=&site=adelaidenow%2fvideoplayer)

So while the mplayer plugin was trying to read it, I then copied the url and pasted it into VLC. Just wanted to make sure!

I've read/seen/had many sound or video related problems and I've never been able to figure why "Method X" works for some and doesn't for others! Compatibility? Hardware? Whatever?

---

### Post by STREETURCHINE on 2006-10-31
yes i have firefox so i cheked the site it loaded and played all the vidios,
 so a little more reserch might solve your problem ,mind you i cant help everything has woked since i downloaded automatix.well all except my printer...:D

---

### Post by xyz on 2006-10-31
> **STREETURCHINE said:**
> yes i have firefox so i cheked the site it loaded and played all the vidios,
 so a little more reserch might solve your problem ,mind you i cant help everything has woked since i downloaded automatix.well all except my printer...:D

Yes I think you're quite right there...everybody has to try and find "his/her own way to make it work"...so to speak!

---

### Post by Russty of Oz on 2006-11-02
> **xyz said:**
> Typing "about:plugins"...you are certain you've got all you need there?

Also just to make sure, I went back to the AdelaideNow site a few minutes ago and tried playing " Ch 9 - Good news for Hardie asbestos victims" . Clicking on the url below had my box trying to play it with the mplayer plugin...No go!:

[http://media01.news.com.au/adelaidenow/Willyama-BB.wmv?clipId=1383_58375&channel=Local+Videos&category=&site=adelaidenow%2fvideoplayer](http://media01.news.com.au/adelaidenow/Willyama-BB.wmv?clipId=1383_58375&channel=Local+Videos&category=&site=adelaidenow%2fvideoplayer)

So while the mplayer plugin was trying to read it, I then copied the url and pasted it into VLC. Just wanted to make sure!

I've read/seen/had many sound or video related problems and I've never been able to figure why "Method X" works for some and doesn't for others! Compatibility? Hardware? Whatever?


I just clicked that link and it opened in Totem player!  

But where did you get the link from?  When I try to copy link location or save link as I dont get a link that will play.  I am definitly missing something here!:-k

---

### Post by maaronB on 2006-11-02
It worked in mine.  I got everything from Automatix2.

I noticed you said that you have multiple versions of firefox installed.  I wonder if that is causing you problems.  For instance installing one version might have over written some settings.

---

