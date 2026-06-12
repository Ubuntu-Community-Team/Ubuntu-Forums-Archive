---
title: "FireFox has become like IE :S"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-07-05
Hi, lately my firefox has got real bad. it uses longer then IE to load a page and crashes many times. If i try to watch a video on you tube there is a 60 % (or something like that) for my firefox crashing :o . The only add dons i have is MediaPlayerConnectivity and norwegian word list. When firefox is slower then IE something most be seriously wrong

---

### Post by lbelloq on 2007-07-05
Which version of Firefox are you using?

---

### Post by moredhel on 2007-07-05
When you say it takes longer than IE, i take you are referring to running IE in Wine?

---

### Post by Seisen on 2007-07-05
I have noticed too that sometimes flash or java will crash firefox or make it unresponsive and then I have to kill it.
You could try iceweasel and see if you have any problems.

---

### Post by drpas2k on 2007-07-05
I too have a same problem with Firefox. I do not use wine. It is very slow and freezes.

If i use  any media player it becomes much worse . So I use Opera also. but it also freezes for a while.

mine is

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty).

please help.

---

### Post by Seisen on 2007-07-05
If Opera is doing the same thing that Firefox is then its not firefox but  Flash and Java.

---

### Post by igknighted on 2007-07-05
If you look at most browser tests, IE is in fact faster than FF quite often.  FF is probably the slowest browser out there.  However, if you feel it is slower than usual, try disabling add-ons and plugins one by one until you find the culprit.  If this doesn't work, back up your ~/.mozilla or ~/.firefox folder (not on linux box to check which it is ATM) and delete the original.  You will lose bookmarks and settings, but when FF starts the next time it will build a fresh set of config files, might solve your issues.  Then reimport your bookmarks from the backed-up folder.

---

### Post by ajmannen on 2007-07-05
When i mean slower then IE i mean IE  7 in vista.

Now manny programs have started to run slower, Opera, Open Office, Googel Earth and more. It seems as if have got a virus :o is that possible?

---

### Post by drpas2k on 2007-07-05
> **Seisen said:**
> If Opera is doing the same thing that Firefox is then its not firefox but  Flash and Java.

Please help me how to correct Flash and Java. thanks

---

### Post by Seisen on 2007-07-05
How did you install Flash and Java anyway?

---

### Post by igknighted on 2007-07-05
> **drpas2k said:**
> Please help me how to correct Flash and Java. thanks

Opera and flash tend not to work well together at all (It is a bug between adobe's linux flash plug-in and the browser, and both sides blame the other and wont do anything to fix it).  For flash, if you installed adobe's flash player from the repo that is about all you can do.  Flash is a really flakey format (windows and linux), so the best you can do for most of those issues is to email Adobe and have them get their act together.

Although, to be fair, so many people with no idea what they are doing put together the most horrid flash code imaginable, and then adobe is expected to support it, so I do feel bad for them in that regard.

---

### Post by southernman on 2007-07-05
How much free disk space, are in your partitions?

Have you ran "sudo aptitude autoclean" lately?

---

### Post by drpas2k on 2007-07-05
> **Seisen said:**
> How did you install Flash and Java anyway?

Through synaptic manager.

---

### Post by bashologist on 2007-07-05
I have the same problem with the crashing. I installed flash from adobes website manually. I have to kill firefox-bin at least once a day.

To speed up Firefox everyone uses this [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html").

---

### Post by ajmannen on 2007-07-05
Flash i installed by opening a flash game and let firefox do the job, java i used 
```
sudo apt-get install sun-java6-jdk
``` in terminal

---

### Post by Seisen on 2007-07-05
You can complain to Adobe about Flash and to Sun about Java like igknighted said  and going to here you can see if maybe its a bug in firefox or if anybody else has had the problem and how they fixed it.

[http://forums.mozillazine.org/](http://forums.mozillazine.org/)

---

### Post by bodhi.zazen on 2007-07-05
> **bashologist said:**
> I have the same problem with the crashing. I installed flash from adobes website manually. I have to kill firefox-bin at least once a day.

To speed up Firefox everyone uses this [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html").

Or install fasterfox, which does most of that out of the box :

[https://addons.mozilla.org/en-US/firefox/addon/1269](https://addons.mozilla.org/en-US/firefox/addon/1269)

---

### Post by mydrac on 2007-07-05
> I have the same problem with the crashing..... I have to kill firefox-bin at least once a day.
i have exactly the same problem.

---

### Post by orb9220 on 2007-07-05
> i have is MediaPlayerConnectivity and norwegian word list. 

Try disabling the  MediaPlayerConnectivity extension and see if it is better. I think I had a problem with that paticular extension in firefox on my winXP dark side as well.

Tho there are Firefox,java,flash issues in Linux don't forget that extensions can also cause instabilities.

---

### Post by frtegularius on 2007-07-06
I'd just like to add something not on the java/flash line.  Firefox was crashing on me on certain links and downloads that Konqueror could handle.  I tried using different themes for Firefox, and it worked.  Perhaps some of the problems y'all are having is related to the other extensions in Firefox.  Maybe, maybe not.

---

### Post by Lolicon on 2007-07-06
Clean your cache. Same thing happened to me.

---

### Post by Pikestaff on 2007-07-13
Firefox crashes all the time for me as well, often times it's after visiting a flash-based site or YouTube, but many other times it just crashes randomly or while doing "normal" things (like right clicking and saving a picture-- that has crashed it multiple times.)

It's been doing this essentially ever since I installed Kubuntu six months ago.  My Firefox and Flash are both up to date.  It's really irritating but seeing as I haven't been able to find a good fix yet I'm just sort of "living with it" right now... Firefox has a bunch of addons and stuff that I'm quite fond of so I'm afraid I won't be switching to another browser :p

---

### Post by Nussbaum on 2007-07-13
I think there is something wrong with the linux flash plugin. I remember on windows98 I could have countless youtube videos open in firefox without any problem but on linux even one video hogs alot of memory. The max I can open at the same time is 3 though its differnet per video. Some use more memory then others. More than 3 and my computer starts to periodicly freeze.

---

### Post by sailor2001 on 2007-07-13
I switched to swiftweasel and that seems to have speed ed up the browser problem........add-ons are the same

---

### Post by mgmiller on 2007-07-13
You can also try switching your Java runtime.  Just enter this in a terminal:
```
sudo update-alternatives --config java
```

and pick the one you want.  By default, there is a version 1.4 installed, I think.
 Anyway here is what mine looks like:

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/j2re1.5-sun/bin/java
          2    /usr/bin/gij-wrapper-4.0
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        4    /usr/lib/j2se/1.4/bin/java
          5    /usr/bin/gij-wrapper-4.1
          6    /usr/lib/jvm/java-gcj/jre/bin/java
*         7    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 


Note that the one with the * (line 7) is the one I am currently using.

I have run across some compatibility issues that have required switching to a different java version from time to time and this makes it easy to experiment.

---

### Post by jeffreyldavidson on 2007-07-13
I had the same problem lately with Firefox. It would crash constantly. I have installed Swiftweasle and have not had any problems at all. Basically it is a retoolded Firefox and works great.

JLD

---

### Post by crimesaucer on 2007-07-13
> **sailor2001 said:**
> I switched to swiftweasel and that seems to have speed ed up the browser problem........add-ons are the same


Yes, install Swiftweasel optimized for your processor, it's so fast: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

Then also tweak your about:config with this old guide: [http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)

...using these newer settings for 2.0.0.4:

[http://kb.mozillazine.org/Category:Tweaking_preferences](http://kb.mozillazine.org/Category:Tweaking_preferences)
[http://kb.mozillazine.org/Category:Preferences](http://kb.mozillazine.org/Category:Preferences)
[http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway](http://kb.mozillazine.org/index.php?title=Category:Preferences&from=Mail.db+timestamp+leeway)
[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

...and also deactivate IPV6, you need to edit the file: 

```
/etc/modprobe.d/aliases 
```

by adding the lines:

```


alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off 

```

and commenting / removing the line:

```
alias net-pf-10 ipv6 
```


This will noticeably speed up Internet applications, including Firefox and Google Earth as stated on this debian page: [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)

---

### Post by ramjet_1953 on 2007-07-14
Another thing to remember with Firefox, is that if you load it up with add-ons, it can slow things down, as well.

Two other things that can speed up your browsing:

1. Diable ipv6 (There are links on this forum you can search for)

2. If you are using a router, put the [COLOR="Blue"]Open DN[/COLOR]S ip adresses in at the top of the list.

Check out this link: [http://www.opendns.com/](http://www.opendns.com/)

Regards,
Roger :cool:

---

### Post by crimesaucer on 2007-07-14
> **ramjet_1953 said:**
> Another thing to remember with Firefox, is that if you load it up with add-ons, it can slow things down, as well.

Two other things that can speed up your browsing:

1. Diable ipv6 (There are links on this forum you can search for)

2. If you are using a router, put the [COLOR="Blue"]Open DN[/COLOR]S ip adresses in at the top of the list.

Check out this link: [http://www.opendns.com/](http://www.opendns.com/)

Regards,
Roger :cool:

To disable ipv6, look above your thread at my post...that is basically the way that most all of the searches for disabling ipv6 say to do it...it works for me.

also, go into your Firefox "about : config" and change the boolean of "network.dns.disableIPv6" to "TRUE".


And if you check out that debian link that I posted in the thread above yours, there are many good speed tips including a tip about OpenDNS (which does seem to help the speed a bit): [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)

...and this is from the OpenDNS page: [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)


But seriously, try Swiftweasel to really feel a difference.

---

