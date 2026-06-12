---
title: "A newbie to linus ... HELP!!!"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by mourad on 2006-06-15
Hi guys ... talking about new to linux, I admit I am a newbie to linux by all the senses of the word, I just finished downloading the ubuntu and I didn't even intall it yet .... However, I have very serious concers that I hope anybody can help ...
I see some of you helped by posting the programs of Windows and the counterpart of it in linux, but I still have in deep questions;

1) Is google talk can be used in linux ?? if yes, and whatever program will make it available , Am I going to find my contact list ready, or should I start collecting it back again ???

2) Some mentioned that windows media player in Windows is Totem in linux, however ... I am used to listen to many radio stations that air using WMP, does totem have radio stations, not to mention those like of the WMP ???? OR Am I going to miss my radio stations like "live 365":-( :-( 

3) I watch the news through the msnbc on my msn dot com, but when I try to watch the video using firefox, it tell me that I need to have IE, WMP and macromedia flash ... So when I am using linux , Will not I be able to watch msnbc news again ????:-( :-( 

4) FIFA ... talking about the world cup seems to be in time ;) ... playing the game FIFA , is it available in linux ????

---

### Post by nalmeth on 2006-06-15
[quote=mourad]Hi guys ... talking about new to linux, I admit I am a newbie to linux by all the senses of the word, I just finished downloading the ubuntu and I didn't even intall it yet .... However, I have very serious concers that I hope anybody can help ...
I see some of you helped by posting the programs of Windows and the counterpart of it in linux, but I still have in deep questions;

1) Is google talk can be used in linux ?? if yes, and whatever program will make it available , Am I going to find my contact list ready, or should I start collecting it back again ???

2) Some mentioned that windows media player in Windows is Totem in linux, however ... I am used to listen to many radio stations that air using WMP, does totem have radio stations, not to mention those like of the WMP ???? OR Am I going to miss my radio stations like "live 365":-( :-( 

3) I watch the news through the msnbc on my msn dot com, but when I try to watch the video using firefox, it tell me that I need to have IE, WMP and macromedia flash ... So when I am using linux , Will not I be able to watch msnbc news again ????:-( :-( 

4) FIFA ... talking about the world cup seems to be in time ;) ... playing the game FIFA , is it available in linux ????[/quote]

1) I think GAIM can use google talk, and import your contacts. 

2) Totem is just a front-end to your video 'engine' and as long as you have all the codecs for the video you're trying to watch, they will play, except:

3) MS and its affiliates are inherently linux-unfriendly, they don't want to know you unless you have MS installed. If you can find a different news site, it would be best. If not, then you can install an older IE and WMP through wine, wine_tools is a more automated way if you're not comfortable with wine at first (BTW Wine is a windows compatibility layer.)

4) Doubtful that whomever made the game made linux binaries for it (EA Sports probably?). Slim chance you may be able to use Wine or a linux installer to play it, otherwise you'll need Cedega to run it, which costs $15 ($5/month, minimum 3 month subscription).

OH, and lastly, you can probably listen to those radio feeds with a music player, or with the mozilla-mplayer plugin.

To install codecs, mplayer-plugin, and wine, click the Almighty Automatix link in my signature for a do-it-all script.

Cheers!

---

### Post by u.b.u.n.t.u on 2006-06-15
Q1 Yes
[http://www.google.com/talk/](http://www.google.com/talk/)
"Requires Windows XP/2000, minimum 56k (broadband recommended)
Mac and Linux users can connect to Google Talk using other IM clients"



Q2 Yes in principle, (not sure about "live 365").
[http://en.wikipedia.org/wiki/Totem_%28media_player%29](http://en.wikipedia.org/wiki/Totem_%28media_player%29)
"SHOUTcast, m3u, asx, SMIL and RealAudio playlists support"



Q3 Yes in principle, install the correct codecs. (Not sure about MSNBC).



Q4 Yes in theory.
[http://www.desktoplinux.com/news/NS9266567941.html](http://www.desktoplinux.com/news/NS9266567941.html)
"If you want to play Windows games on your Linux desktop, you'll be glad to learn that Transgaming Technologies has enhanced its enabling software. Cedega version 5.1 adds support for three popular Windows games -- Civilization IV, FIFA 06, and Need for Speed -- among other enhancements."

---

### Post by Nikusan on 2006-06-16
[QUOTE=mourad]
1) Is google talk can be used in linux ?? if yes, and whatever program will make it available , Am I going to find my contact list ready, or should I start collecting it back again ???
[/QUOTE]

google talk is basically just a jabber server, so gaim will connect to your google talk account. You contacts are all stored server side so that's not an issue.

---

### Post by WADemosthenes on 2006-06-16
1) Can't you use google talk straight from your gmail inbox in a browser (like firefox)?

3)I'm an extreme noob too, I'm just barely hanging on.  Yager suggested to me a program called Automatix.  It seems really good, and it looks like it make it easier for me. ([http://www.getautomatix.com/](http://www.getautomatix.com/))  It would require knowlege in editing the source list (which I found out how to do today), but it's not too hard.

---

### Post by mozetti on 2006-06-16
You can also install Tapioca -- do a search here for it to find the instructions/linksyou need -- it's specifically for GoogleTalk.

---

### Post by 3rdalbum on 2006-06-16
Live 365 definately works in Rhythmbox. Many 365 streams are in MP3Pro and Rhythmbox doesn't support it, but they still play at a lower quality.

---

### Post by akudewan on 2006-06-16
> **mourad]
1) Is google talk can be used in linux ?? if yes, and whatever program will make it available , Am I going to find my contact list ready, or should I start collecting it back again ???
[/QUOTE]

Google talk uses the Jabber Protocol, and can be used with GAIM.

[QUOTE=mourad]
2) Some mentioned that windows media player in Windows is Totem in linux, however ... I am used to listen to many radio stations that air using WMP, does totem have radio stations, not to mention those like of the WMP ???? OR Am I going to miss my radio stations like "live 365":-( :-( 
[/QUOTE]
There is something called "streamtuner". You can listen to radiostaions like "live 365" and many others.


[QUOTE=mourad]
3) I watch the news through the msnbc on my msn dot com, but when I try to watch the video using firefox, it tell me that I need to have IE, WMP and macromedia flash ... So when I am using linux , Will not I be able to watch msnbc news again ????:-( :-( 
[/QUOTE]
If it asks for IE, then you'll need IE. You could probably use WINE, but there are no gaurantees that it will work. (Wine is used for running windows apps in linux)


[QUOTE=mourad]
4) FIFA ... talking about the world cup seems to be in time  said:**
> 

"Cedega"  is a program similar to Wine. Again, I don't know if the game is supported by cedega. Cedega costs money btw, but you can get it for free if you compile it yourself.

---

### Post by mourad on 2006-06-17
thank you guys for all your help .... But still talking about programs, I did not notice anyone talking about antivirus and anti spyware programs ??? Is this because Linux so impentratable and secure ??? or is it because the hackers and virus people are busy hacking and impaling the windows :) ....!!!

---

### Post by Nikusan on 2006-06-17
[QUOTE=mourad]thank you guys for all your help .... But still talking about programs, I did not notice anyone talking about antivirus and anti spyware programs ??? Is this because Linux so impentratable and secure ??? or is it because the hackers and virus people are busy hacking and impaling the windows :) ....!!![/QUOTE]

Some people say it's because of your first reason, others say it due to the second. The truth is probably somewhere inbetween though. Whatever the reason is you don't need it. ;)

---

### Post by skale on 2006-06-17
There is a firefox plugin that allows you to render the page in an IE tab. As I installed ubuntu three days ago I haven't tried it yet on linux. It worked on Windows quite well, you might want to try it out. I'm about to try it now, actually.

edit:
> IE Tab is not available for Linux.

phhtt...

---

### Post by brentoboy on 2006-06-17
gmail chat works inside of firefox no issues at all.
you can also use gaim.  I use the browser version, my wife prefers to run gaim so it can notify her and play noises when she isnt sitting there to use it.

the ie tab doesnt work on linux.
it uses the acitivex object that only exists if you install ie, it is just for devs who want to switch back and forth to see if stuff looks nice for both.

as far as msnbc, it might take some elbow grease.  I had to do some work to get  stuff from cnn.com to play vidios, but in the end it worked.  I had to go to the mplayer official site, and download the codecs from there and follow thier instructions for installing them. after doing so, cnn's site said "you have an unrecognized version of windows media player...." "we reocmmend version 10" "you should upgrade" "do you want to continue anyway"  and all that, then, it just worked, I never had another question or problem.  dont give up, I promise it works, just post questions if you bump into them.  Start off by looking in the ubuntu wiki for help with restricted formats.


as far as virus stuff, if you are worried, there are antivirus things out there for linux, most of them are to find windows viruses that windows boxes put on your linux server, they arent made to do anything to you, but you can install it anyway, and if a linux virus does someday show up, you will get an update to your antivirus and it will protect you.  I personally give linux another 3 to 5 years before it starts to be a target worth writing viruses for.  these days, viruses are written to make someone money, so there is no reason to  attack small audiences.

---

### Post by mozetti on 2006-06-26
[QUOTE=Nikusan]Whatever the reason is you don't need it. ;)[/QUOTE]

AV software is still a good idea on Linux, only so you don't accidentally transmit an infected email/file from your Linux machine (where the virus has no effect) to a friend/relative using Windows.

---

### Post by malegria on 2006-06-26
For FIFA scores and results go to [http://www.mozilla.com/add-ons/jogacompanion/](http://www.mozilla.com/add-ons/jogacompanion/)

it's an add-on to Firefox that's great!!!

(see screenshots there)

---

