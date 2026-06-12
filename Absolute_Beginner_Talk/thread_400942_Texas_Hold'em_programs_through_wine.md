---
title: "Texas Hold'em programs through wine"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-04-04
Hey, I was looking around for a texas hold'em game that runs on ubuntu but haven't been able to find any.  So I just figured to use wine to run PokerStars.net.

First make sure you have wine.  If you don't have wine installed, install it through the synaptics package manager. (Just search for "wine")

Once you have installed wine
All you have to do is download the installer from the website [www.pokerstars.net]("www.pokerstars.net").  (This could be replaced with several different websites based on preference) Once you have downloaded it, remember where you saved it to and change to that directory.

> cd <name of directory>

Once your in the directory, use wine to run the installed.

> wine <name-of-installer.exe>

This should install the program, it will most likely create a launcher on your desktop, but if not you can run it by typing:

> wine <application name>

Thats it, you should be good to go after that.  Goodluck, and don't spend all your chips on one hand ;) 

P.S. if there is something I have left out or written wrong, just leave a comment so I can revise it.

---

### Post by sloggerkhan on 2007-04-04
I've had poker stars working no problem, but have you had any luck with full tilt poker?

---

### Post by LuckyDem on 2007-04-04
As Soon As I Log Onto My Poker Account The Programme Disconnects.
Any Suggestions?
I Cant Seem To Get To Run Any Online Programmes Through Wine

---

### Post by familyjules74123 on 2007-04-04
> **sloggerkhan said:**
> I've had poker stars working no problem, but have you had any luck with full tilt poker?

I haven't tried full tilt, but I'd imagine it would work likewise as wine will just emulate it running in a windows environment  I will try out full tilt when I get some spare time.

> As Soon As I Log Onto My Poker Account The Programme Disconnects.
Any Suggestions?
I Cant Seem To Get To Run Any Online Programmes Through Wine

Is your wine up to date?  If it is, check all your wine settings by typing

> winecfg

And make sure all your settings are correct... if you don't know what a setting should be, just ask in here and I'll try and help you out.

---

### Post by familyjules74123 on 2007-04-05
I just tried FullTilt's poker program, It installed fine, but I could not connect to the server.  I will keep tinkering with it and see if I can get it to work, but for now I believe Pokerstars.net is a substantial substitute (<3 alliteration ;) )

---

### Post by mediax on 2007-04-05
Pokerroom.com has a Java client version that runs under Linux (subject to your having a suitable version of Java, of course).  There are a few bells and whistles missing compared to the download client, but it's perfectly playable.

I've managed to get EmpirePoker running pretty well in Edgy under wine - it took a couple of attempts to install it, but I didn't have to tinker about with any wine settings.  It's survived an automatic client update from the site, so I'm happy with it.  The only issue I have is that html rendering is disabled, which spoils the display a little, but I suspect that's fixable if if was enough of an issue for me.

I believe EmpirePoker is a PartyPoker site, so I suspect that PartyPoker would probably also run under wine?

---

### Post by Jussi01 on 2007-04-05
Partypoker runs under wine, but there is no need to as they have "party poker anywhere" now which runs in your browser.

---

### Post by familyjules74123 on 2007-04-05
didn't know about that party poker anywhere feature.  This wine installation seems a little more un-important now lol

---

### Post by broke on 2007-04-14
I just loaded pokerstars onto my computer, it all seems to run fine however I can only play with play money.  There are no options to see my account or any cash games.  Any ideas as to why and how to fix it?

Cheers

---

### Post by mhansen on 2007-04-14
> **broke said:**
> I just loaded pokerstars onto my computer, it all seems to run fine however I can only play with play money.  There are no options to see my account or any cash games.  Any ideas as to why and how to fix it?

Cheers

I don't know where you're from, but most of these sites stopped accepting US players due to a change in the law regarding online play.  But, rest easy, because it's coming back, as the US essentially lost in court regarding this issue.



Regards,
Mike

---

### Post by broke on 2007-04-14
Im from OZ but I have been following what has been happening in the US.  Anyway I got it to work by downloading another version of Pokerstars.  Happy Days:D

---

### Post by familyjules74123 on 2007-04-16
I hadn't really been following the case, I am glad to hear the US lost though, as I am from the US lol.  I am still willing to try out different versions of poker software to see if it works if anyone has any suggestions.  As of now I have gotten two out of three to work.  These include party poker (worked fine), full tilt poker (could not connect to the server), and Sportsbook.com (worked but buggy).

---

### Post by RenevE on 2007-04-22
I have problems running Partypoker using wine. I want to use wine because tournament are not accessible using the webinterface. I have installed wine successfully, partypoker also. When I run the partypoker app it looks likes it works fine, but after some time it just shuts down. Also the pokerrooms are not displayed fully, the right side is cut off. 

A review [here]("http://appdb.winehq.org/appview.php?iVersionId=2133") doesn't show these problems.

Does someone know a solution to these problems, thanks already

Rene

---

### Post by sloggerkhan on 2007-04-22
pokerstars works near perfect for me.

Party poker works, but some of the fonts are unreadable.

---

### Post by familyjules74123 on 2007-04-22
make sure that all your fonts are installed, also check and see whether all of your "winecfg" settings are right.  If some of the frame is being cutoff you can try to resize your wine resolution 800X600 or the next size up should be fine (is for me at least).  This should all be accesible through running the "winecfg" command in a terminal.  If you need further assistance please post back here with your wine settings and also any other important information that you feel may be affecting the problem.

---

### Post by sloggerkhan on 2007-04-22
MS core fonts and using a virtual desktop don't help with party poker. It also has the annoying habit of calling "wine internet explorer" which doesn't work very well. But Like I said, pokerstars has been perfect.

---

### Post by climbdahill on 2007-05-14
so, which version of wine are you guys using?  i tried the one from the repo and i can sit at a table, but when i leave it, the prog. closes (or minimizes to a weird small box in the lower left corner) wtf?  any ideas

---

### Post by sloggerkhan on 2007-05-14
latest feisty version from wine HQ's repos.

---

### Post by thom_raindog on 2007-06-30
I have the same problem. Or at least one thats a lot like it.. even using 0.9.40, which just came in this morning...

---

### Post by Gorbayov on 2007-11-12
Hello people

i have a problem with wine now

i had a NVidia videocard and i ran alot of wine programs perfectly.
my nvidia broke and the memory card broke with it..

now i bought a ATI Radeon 9250 (wich kinda sucks) and a new memory card
but now alot of apps that ran before wont work

PokerStars (which i had no single problem with it) stopped working - i can see the little connecting window at the startup of the program but nothing more.. I cant see the lobby anymore

FullTilt - starting up fine but when i press login the application gets a freeze, it is randomaly working after some tries.

anyone knows what the problem ?? is it the Videocard ??
is it possible that the problem is the new memory ??

---

### Post by tomsa on 2007-11-12
I just found this thread as I'm currently trying to get Doyle's Room working on my machne.  It installs just fine in wine and/or crossover- but it is horribly slow.  It spikes my processor usage immediately.  I'm really not sure what to do to stop that from happening. Do you have any ideas? 
    I've also tried to get full tilt and ultimate bet to work in crossover.  Full Tilt just doesn't work, and Ultimate Bet needs to see some sort of IE installation at the same time to install- I haven't tried that one with IE installed yet.  I'll let y'all know if I can get anything else to work.

---

### Post by elj4176 on 2007-11-12
why not just install pokerth from the repos? I find it to be a decent hold'em program. I haven't tried the network game functions yet tho - only local games.

---

### Post by tomsa on 2007-11-12
I just found another thing that might interest you.  Absolute Poker has a no-download client that you can use to play through your web browser.  There is also a web site that is tracking online poker info for Mac and Linux Users.  It is here:

 [http://www.compatiblepoker.com/Linux+Poker+Online.cms.htm]("http://www.compatiblepoker.com/Linux+Poker+Online.cms.htm")

I hope that helps someone out!

---

### Post by TadH on 2007-11-12
> **mhansen said:**
> I don't know where you're from, but most of these sites stopped accepting US players due to a change in the law regarding online play.  But, rest easy, because it's coming back, as the US essentially lost in court regarding this issue.



Regards,
Mike


or maybe you downloaded from .net and not .com, go to the .com site and download it fom there.

I am having trouble with truepoker, i installed it but it wont even start up, im going to check to see if wine is up to date, any suggestions?

---

### Post by TadH on 2007-11-12
i just downloaded pokerth anyone want to start a network game with me??

---

### Post by elj4176 on 2007-11-13
I like it so far but haven't even tried the networking yet. Let me know how it goes

---

### Post by USFMD82 on 2007-11-14
Has there been any more luck getting Sportsbook.com to work in ths environment, thats really the only reason i insist on keeping windows on this machine so I can play poker at my sports book. I see someone tried it and it worked but its buggy, has that changed at all or is it still weird?

---

### Post by jude999 on 2007-11-26
FYI

I have been playing for a while on Titan Poker (titanpoker.com). Since Drapper actually.

installation through wine works perfectly. The only 2 problems I had were:

- I could not use the program to set up an account (no problem signing in if you already have an account), so I used a friend's windows computer to create my account, then no more problems.

- When I close a window (poker table for example), the whole program crashes. So I usually play one or 2 tables at a time (more is absolutely possible) but only close them when I am done playing. This actually no big problem.

For now I only played Play money, I am seriously thinking of making the step to real money, but I'd like to be sure it actually works on Titan.

Well I do have an other problem... but nothing to do with linux. Gambling is totally illegal in the country I live in... but it's either that, or I move back to France (not in this life!)!

---

