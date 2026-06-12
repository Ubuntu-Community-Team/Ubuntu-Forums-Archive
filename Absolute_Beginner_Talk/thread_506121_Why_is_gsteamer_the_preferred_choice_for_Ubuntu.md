---
title: "Why is gsteamer the preferred choice for Ubuntu?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-07-21
Hello

I've had no end of difficulty getting BBC News streaming video to work. I have finally got to work by using Firefox, Mplayer and setting the BBC News viewer to send streams in RealPlayer mode.

I have tried lots of other things including gstreamer and lost months.

Why do we offer defaults that do not work? Diversity is a good thing generally but when you get to the point of offering a production environment we really should concentrate on what works out of the box.

I am sure that the anarchic fraternity of Linux developers all offering a mirriad of solution for basically the same functionality is a good and healthy pre production mindset. But please, lets not carry this through to a naive new user who just wants things to work. 

Can we have some reality filter that says something like, "If it does not work out of the box in the default configuration for Ubuntu then it shall be rejected until it does." 

Kind Regards
Bob

I am using Mplayer and gstreamer in Gutsy and it runs BBC News streams 'out of the box'. Thank you!!

---

### Post by RomeReactor on 2007-07-21
Hi. The Gstreamer codecs are the default choice in Ubuntu due to certain factors:

* [Patent and copyright restrictions]("https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html") on Xine and the codec set that comes with Mplayer; 

* Gstreamer is more modular than Xine, and can more easily provide new implementations of media format decoders. While Xine is not monolithic (and is arguably more mature), it lacks the diversity of Gstreamer.

* Gstreamer is under heavy development, and is generally agreed upon that it represents the future of multimedia handling for Ubuntu.

> "If it does not work out of the box in the default configuration for Ubuntu then it shall be rejected until it does."

The problem with this approach is that the Ubuntu developers **can't** include every codec by default due to the licensing and patent issues. They make that very clear when Totem encounters a media format it can't play with the codecs that **are** included, and notifies you of possible legal risks **you** assume by installing the necessary codecs (there are Gstreamer codecs for pretty much everything; I have them all installed and don't have any problems playing practically **any** media format). I'm pretty sure the developers want to provide as much functionality as **legally possible** by default, but they just can't include everything and the kitchen sink.

---

### Post by armandh on 2007-07-21
had to down load a [not supported] codex just to play an MP3 but it works just fine after.

---

### Post by Daveth on 2007-07-21
perhaps we should ask why Auntie Beeb does not use an open media standard format to be inclusive of all of its licence payers- you and me!

---

### Post by ddrichardson on 2007-07-21
> **Daveth said:**
> perhaps we should ask why Auntie Beeb does not use an open media standard format to be inclusive of all of its licence payers- you and me!

A question that is already being asked:
[http://news.bbc.co.uk/1/hi/technology/6236612.stm]("http://news.bbc.co.uk/1/hi/technology/6236612.stm")
[http://digital-lifestyles.info/2007/07/13/bbc-trust-to-listen-on-iplayer-going-open-source/]("http://digital-lifestyles.info/2007/07/13/bbc-trust-to-listen-on-iplayer-going-open-source/")

And rightly so. There is absolutely no need for DRM on the BBC's content - we are the license payers.

---

### Post by bwallum on 2007-07-21
> **RomeReactor said:**
> Hi. The Gstreamer codecs are the default choice in Ubuntu due to certain factors:

* [Patent and copyright restrictions]("https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html") on Xine and the codec set that comes with Mplayer; 

* Gstreamer is more modular than Xine, and can more easily provide new implementations of media format decoders. While Xine is not monolithic (and is arguably more mature), it lacks the diversity of Gstreamer.

* Gstreamer is under heavy development, and is generally agreed upon that it represents the future of multimedia handling for Ubuntu.



The problem with this approach is that the Ubuntu developers **can't** include every codec by default due to the licensing and patent issues. They make that very clear when Totem encounters a media format it can't play with the codecs that **are** included, and notifies you of possible legal risks **you** assume by installing the necessary codecs (there are Gstreamer codecs for pretty much everything; I have them all installed and don't have any problems playing practically **any** media format). I'm pretty sure the developers want to provide as much functionality as **legally possible** by default, but they just can't include everything and the kitchen sink.

Hear what you say and acknowledge that it will be an uphill struggle to detach the viewer from some kind of copyright protector, which is where the BBC are.

If Gstreamer is indeed to be the flagship video app for Ubuntu then I am prepared to give it another try. I will also write to the BBC but would prefer to know what it is I'm supporting by getting it to work.

Can you tell me how I get Gstreamer to play embedded BBC News streams?

Currently I am using Firefox/Mplayer and viewing rm or ram files. I have tried to install RealPlayer10GOLD.bin and got it as far as viewing standalone, so I suspect I have a lot of RealPlayer litter about in my system. I have just about learnt where to find files and not much else. I know that system files are in usr/sbin.

Your advice will be welcome. The goal is to watch BBC News steams using gstreamer without having to evoke the standalone player mode.

Kind Regards
Bob

---

### Post by RomeReactor on 2007-07-21
Unfortunately we seem to be tied to Real Player (or at least the **mozilla-mplayer** plugin) when it comes to BBC media streams. Gstreamer doesn't have that functionality, and who knows if future versions will.

---

### Post by zerobinary on 2007-07-21
will it is because of the fact that gstreamer is legal
like w32 codec in some area d ex usa is illegal 
and we are good citizen don't do illegal things *COUGH COUGH
that's y and big company can't do illegal things *cough cough NOT

---

### Post by bwallum on 2007-07-22
I can't hear you because of all the bloo*y coughing on this forum! Perhaps if you email the solution to me at [email]rbw@btconnect.com[/email] I could hear you better.

Thank you for steering me in the right direction.

Kind Regards
Bob

---

### Post by bwallum on 2007-07-28
Well, well

I set up a new machine with AMD64 processor, installed appropriate Fiesty 7.04. Followed instructions on sticky by Adamant1988, (not too sure the instructions are perfect, but they do work with only a handful of surprises)

Eventually got to see Streaming BBC News. Not entirely sure how it happened, I'm convinced there was some prompting on the way but I can't repeat it. And...all with gstreamer and Movie Player. Never saw 'Totem' anywhere. It just works. However it also hangs the system from time to time with no real pattern of behaviour.

So, it would appear that gstreamer is almost there. Well done all concerned, now please stop it hanging my machine. It appears to happen when clicking on a new piece of streaming video with a piece still running.

Regards
Bob

---

### Post by thered on 2007-10-22
Still a little iffy about installing etc on Ubuntu.

I want to stream BBC News 24 - firefox invokes the mplayer plug in and I get the audio ok but no video.

I don't want to break what I have.  Would installing gstreamer fix this? Can I fix the mplayer plugin?

I'm running ver 7.10 on a Dell Inspiron laptop.

R.

---

### Post by bwallum on 2007-10-22
I'm now running gstreamer and Mplayer in Gutsy. It runs BBC News treams although I'm not too sure how! It also seems to not do video if the stream is a bit slow. You notice it when watching the rugby final for example. MS does the same thing though. 

Synaptic tells me the bits I have installed. If you want to try it I would be pleased to work with you. Note my specs below, I'm running the 64 bit version. I think i386 will use the same/similar bits but be prepared to fiddle for a while if you decide to try it. I 'm no expert but we can find them on the forum if we need them.

Regards
Bob

---

### Post by thered on 2007-10-22
OK Bob.

I've checked in synaptics and it seems I already have a lot of gstreamer bits installed already. - So how do I get it to run in firefox instead of mplayer. - or doesn't it work like that?8-[

---

### Post by bwallum on 2007-10-23
Hiya

I hope your Russ 'cos I received an email last night from Russ. let me know if you are one and the same.

Ok, if you have gstreamer and you have removed xine and gxine then open Mplayer Movie Player to see if that works ok as a standalone app.

Then check that you have mozilla-mplayer plugin. Again search for it in Synaptic and install. If you can't find exactly that plugin then park the load until you have done the next step.

Using System>Administration>Software Sources check that all Ubuntu Software sources are checked. Source code is optional and I suggest you leave it out (dashed) for now.

Then run System>Administration>Update Manager and check you have all the latest updates.

Then look for the mozilla-mplayer plugin again if needed.

If not then try to stream BBC News. if it still dosn't work:-

Run this command in a terminal (Applications>Accessories>Terminal - It's a good idea to add a shortcut to the terminal to your desktop menu - right click on 'Terminal' and add launcher to panel)

```
ps -u <username>
``` 

This will give you a list of processes. What we are looking for is a process called totem-plugin-vi. Let me know if you have it.

Bob

---

### Post by bwallum on 2007-10-24
Hi Russ

I tried realplayer in Fiesty and got strange graphics too...never did get to the bottom of it.

I have had a closer look at what is being used when I stream BBC news. I said MPlayer but have now discovered, following an upgrade, that Totem Movie Player version 2.20.0 is being used. It is called Movie Player in the Applications menu (icon is disc and clip of film material - not to be confused with MPlayer Movie Player). When I open Movie Player it shows a picture with the word Totem on a clapper board. Under help>about it says it is using gstreamer 0.10.14 on Gnome.

I know that you also need the right codecs, that is a piece of software that understands the format of the streamed file. To use the windows media player setting for BBC News streams you need the 'w32codecs' file for 32 bit machines, or 'w64codecs' for 64bit machines. 

So to recap, to use the windows media player BBC News stream option you need:-

"Movie Player" (Totem)
"gstreamer 0.10.14"
"w32 codecs" (or w64codecs)
"totem-mozilla" plugin

I think with those (install with synaptic: making sure main, universe, restricted and multiverse repositories are enabled in System>Administration>Software Sources) you should get streaming using the windows media player setting.

Bob

---

