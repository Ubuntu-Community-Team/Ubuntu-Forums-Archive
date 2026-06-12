---
title: "Animated true-daylight wallpaper for Gnome"
date: 2009-11-12
forum: Art &amp; Design
---

### Post by lyncis on 2009-11-12
That's all about animated wallpapers: having heard that Gnome 2.22+ can use time-lapsed wallpapers, and having heard also about existence of day and night versions of same wallpaper, I've been wondering of automatic synchronization of wallpaper's day and night time with real sunrise and sunset.

So, I've decided, using Geocoding API and time-lapsed wallpaper ability of Gnome, to write a small script, that will synchronize wallpaper's day-to-night-transition-time according to real sunrise and sunset time.

What it does:
[LIST]
[*]Calculates your true sunset and sunrise time
[*]Updates background file to make Gnome understand when to start transition from day to night;
[*]Then Gnome automatically makes smooth transition (apx. 30-60min) &#8212; like out of your windows;
[*]And it doesn't make a use of any of your system resource (it even goes to Yahoo! Geocoding API only once, at installation);
[/LIST]

That's a small Perl script, with great examples of [Yoritsuki]("http://hybridworks.jp") daytime and night wallpapers (and 3 more). As soon as this script is suitable to any of wallpaper pairs, you can download it from Google Code ([http://code.google.com/p/gnome-yoritsuki/](http://code.google.com/p/gnome-yoritsuki/)) and adjust for your needs (very small Perl knowledge is required). That looks like:

[IMG]http://lyncis.info/img/gnome-yoritsuki/yoritsuki_daytime_sml.jpg[/IMG] [IMG]http://lyncis.info/img/gnome-yoritsuki/yoritsuki_night_sml.jpg[/IMG] 

But anyway, the original program comes with 4 predefined wallpapers (high-quality, I must say), so it will be enough to enjoy what the program does. 

To install, follow my [**Gnome Animated Wallpaper Installation Guide**]("http://lyncis.info/en/gnome-yoritsuki-animated-background-wallpaper")

I wrote the whole thing in one day, so I would appreciate any feedback, either bug-reports, suggestions or wallpapers to include. So I wait for your feedback here, on my blog ([http://lyncis.info/en/post/339]("http://lyncis.info/en/post/339")), or on Google Code ([http://code.google.com/p/gnome-yoritsuki/issues/list]("http://code.google.com/p/gnome-yoritsuki/issues/list")) 

I've tested it only on Ubuntu 9.10 (Karmic) Final, and it worked (and works) fine for me, so if you test it on other Gnome installation, please let me know.

Also, if you're interested in how it works, please let me know.

Thank you.

P.S. Not sure that I've chosen the right thread on forums.

---

### Post by Glucklich on 2009-11-12
You did chose the right section for your topic and I have to say that it is absolutely brilliant!
Unfortunately, I don't have the time to test it but its genius. Great idea indeed.

---

### Post by oedipuss on 2009-11-13
Thank you, that's fantastic! 
It should be included in gnome by default, with a couple of nice examples!
Will it cycle between just two images (per set), or can more steps be added theoretically ?

---

### Post by lyncis on 2009-11-13
Theoretically there could be as many as you want images. I think about weather-based ones — based on NOAA data, as soon as we already have calculated coordinates — but I still haven't found weather variations of the same wallpaper (

---

### Post by lyncis on 2009-11-13
Definitely, it will be much easier and usabe to have:
[LIST]
[*]GUI;
[*].deb — installer (maybe based on PPA);
[*]More Day/Night wallpapers (of course allowed to use).
[/LIST]
Unfortunately, I'm keen only on Java-based GUIs, which is not preferable because of Java JRE dependency (15-16Mb BTW, can't remember if any JRE is installed on basic Ubuntu installation).

So, your help is welcome. Let's make our OS better together.

---

### Post by coldReactive on 2009-11-13
After doing the installation instructions, my wallpapers are still the same (homestar runner dangeresque bg). Do I have to run some command to start the animation?

Also, here's the output of what happened at the end:

```
ian@psumi:~/Backgrounds/gnome-yoritsuki$ ./bin/update.pl --res=1440x900 --install
Wallpaper resolution: 1440x900
Found your location: Chicago
Trying to geocode it... Got positive reply.
Trying to parse geoXML... Done.
Your calculated coordinates are 41.884150:-87.632409
Updating XML for wallpaper id: yoritsuki
Your resolution: 1920x1200
Background location: /home/ian/Backgrounds/gnome-yoritsuki/data/background-yoritsuki.xml
Invalid offset: CST
```
Also, the Daylight Time thing isn't in startup applications, so apparently, it failed somewhere.

---

### Post by lyncis on 2009-11-14
Updated the code, see rev. 6: [http://code.google.com/p/gnome-yoritsuki/downloads/list]("http://code.google.com/p/gnome-yoritsuki/downloads/list"). Installation remains the same ([http://lyncis.info/en/gnome-yoritsuki-animated-background-wallpaper]("http://lyncis.info/en/gnome-yoritsuki-animated-background-wallpaper")).

What's new:
[LIST]
[*]Fixed timezone detection (thanks *coldReactive*, *ttilberg* for issues);
[*]Now you can edit timezone in config, in case of wrong detection;
[*]Enhanced installation diagnostic output;
[*]Minor error-handling fixes.
[/LIST]

---

### Post by coldReactive on 2009-11-14
lyncis: You may want to tell people this:

**Updating The Installation**

* Use SVN checkout If possible, as it checks for changes only rather than to extract over every file again.

* Do the **./bin/update.pl --res=YYYYxYYY --install** over again.

That's it, you're done updating!

I can't wait to see it change at like 4 some odd time PM.

---

### Post by oedipuss on 2009-11-14
Quick question: 
If the update script calculates the transition at startup, and then it's done by gnome, will it stop after one cycle if you happen to leave the pc running ?
If that's the case perhaps it would be better for the installation script to schedule a cron job or something to that effect, once per day, in addition to running at startup. 

As for a GUI, I don't think it's really necessary. Ideally I'd like to see it as part of the default gnome appearance dialog, but other than that, the script is really fine as it is, quick and easy =D

---

### Post by coldReactive on 2009-11-14
> **oedipuss said:**
> Quick question: 
If the update script calculates the transition at startup, and then it's done by gnome, will it stop after one cycle if you happen to leave the pc running ?
If that's the case perhaps it would be better for the installation script to schedule a cron job or something to that effect, once per day, in addition to running at startup. 

Yes, that's the case. I purposely changed my time to 5 PM to see if it would change ON ITS OWN (immediately however). But, it didn't. We need a cron job or something.

---

### Post by lyncis on 2009-11-14
Yes, update runs only on login, *yet*. 

I will do some research on cron (and possibility of creating cron tasks under non-privileged user) — or, I suppose, we would need to migrate from user-home to «sudo'ed» system-wide installation.

*P.S. Anyway, who knows, is any Java JRE exist in Ubuntu out-of-the-box? Community documentation says there must be GCJ, is it true for 9.10? And, if you have other Linux flavor, is there Java?*

---

### Post by oedipuss on 2009-11-14
Adding to cron seems easy enough :

```

crontab -l | grep -v "@daily <script>" > oldcrontab
echo "@daily <script>" >> oldcrontab
crontab oldcrontab 

```

to get the old list of jobs minus any duplicates , append the new job to it, and reload it. <script> would be a command, without the < > of course, and it would run every day at midnight. No need to sudo, all as a regular user, jobs added for that user only.

I seem to have a problem with update.pl, though. It can run correctly only with .../gnome-yoritsuki/ as its working dir. I suspect the start-up applications entry might fail silently. As a simple solution, I just run it through a script that cds to where I've placed it, but that's not good enough for automatic installation. I can't think of a quick way it could detect where the files are without requiring user input ...

---

### Post by coldReactive on 2009-11-14
Scheduled Tasks gives this error when you try to execute the command /home/<user>/Backgrounds/gnome-yoritsuki/bin/update.pl -silent

Error:
```
Can't locate /home/ian/bin/wallpapers.pl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/ian/Backgrounds/gnome-yoritsuki/bin/update.pl line 56.
```

---

### Post by oedipuss on 2009-11-14
Exactly what happens to me too. 
update.pl can only run from /home/user/.../gnome-yoritsuki/

Try a shell script that cds to there before executing update.pl. I'm sure there are much better ways to do this, but oh well :P

for example : 
#!/bin/bash
cd ~/Backgrounds/gnome-yoritsuki
./update.pl --silent

and run this script instead of update.pl directly.

---

### Post by coldReactive on 2009-11-14
> **oedipuss said:**
> Exactly what happens to me too. 
update.pl can only run from /home/user/.../gnome-yoritsuki/

Try a shell script that cds to there before executing update.pl. I'm sure there are much better ways to do this, but oh well :P

for example : 
#!/bin/bash
cd ~/Backgrounds/gnome-yoritsuki
./update.pl --silent

and run this script instead of update.pl directly.

Doesn't work either:
```
./update-wallpaper: line 3: ./update.pl: No such file or directory
```

Edit: It has to be:
```
#!/bin/bash
cd ~/Backgrounds/gnome-yoritsuki
./bin/update.pl --silent
```

---

### Post by MrBorsa on 2009-11-15
> **oedipuss said:**
> Exactly what happens to me too. 
update.pl can only run from /home/user/.../gnome-yoritsuki/

Try a shell script that cds to there before executing update.pl. I'm sure there are much better ways to do this, but oh well :P

for example : 
#!/bin/bash
cd ~/Backgrounds/gnome-yoritsuki
./update.pl --silent

and run this script instead of update.pl directly.

me too :(

---

### Post by lyncis on 2009-11-16
Thank you for your reports.

Added an issue: [http://code.google.com/p/gnome-yoritsuki/issues/detail?id=2](http://code.google.com/p/gnome-yoritsuki/issues/detail?id=2)

Will update soon.

---

