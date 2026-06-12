---
title: "trackerd?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by nave.notnilc on 2007-10-25
I just upgraded to 7.10 from 7.04, and there is a process called 'trackerd' that is eating up a fair chunk of processing power.  What does it do?  Is it necessary?

---

### Post by caffienefree on 2007-10-25
I believe trackerd is the indexing daemon for the tracker search tool. Execute tracker-search-tool in the terminal to bring up the search prompt.

---

### Post by shad0w_walker on 2007-10-25
Trackerd is a background process that indexs your files for quicker searches, It's not needed as the normal search tool works fine with out. If you want disable it you can do with out any harm, but the usage should settle down to be very low after its finished its first run.

---

### Post by victorgreen on 2007-10-28
How do I disable it?

---

### Post by FuturePilot on 2007-10-28
It will eventually settle itself down after it indexes everything. But if you want to disable it. System>Preferences>Indexing Preferences. Uncheck the two check boxes in the first tab. You can also go System>Preferences>Sessions and uncheck the Tracker entry.

---

### Post by Frak on 2007-10-28
It indexes then shuts down, but you can end process if you want to, as it isn't essential to the computer itself in anyway.

---

### Post by daicoden on 2007-10-28
It does not seem to be listening to the priority.  It may have a nice of 19 but it is constantly hogging 1 CPU on a dual core system and making everything else run through the other one.  The memory is constantly through the roof, 896 MB.  I turned up the priority so it would finish overnight but it is not ending.

It says it's status is constantly sleeping but it also has a processor and memory percentage.

Is this a bug?

Thanks

---

### Post by cuby on 2007-10-28
There's a bug report in lunchpad:  

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/153319](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/153319)

And a lot of other bugs in:

[https://bugs.launchpad.net/ubuntu/+source/tracker](https://bugs.launchpad.net/ubuntu/+source/tracker)

It seems this tracker was not so ready to be released in the wild.

---

### Post by Frak on 2007-10-28
2 things
1) Tracker is **Alpha**, which means it probably has some problems (beagle was stable)
2) Ubuntu usually runs at 95% RAM (though this is probably a tracker bug), but when memory is available, Ubuntu caches it so other programs will run faster.

---

### Post by n3tfury on 2007-10-28
disable/get rid of it.  my laptop was rendered almost useless when i installed Gutsy.

---

### Post by auxilum on 2007-10-28
[http://www.tracker-project.org](http://www.tracker-project.org)

I've uninstalled it and haven't noticed any problems.

---

### Post by por100pre1 on 2007-10-28
> **victorgreen said:**
> How do I disable it?

**System> Preferences> Sessions** or use this command:

```
gnome-session-properties
```

and then uncheck **Tracker**

Be sure remove the Deskbar applet from the panel. :)

---

### Post by FuturePilot on 2007-10-28
> **por100pre1 said:**
> **System> Preferences> Sessions** or use this command:

```
gnome-session-properties
```

and then uncheck **Tracker**

Be sure remove the Deskbar applet from the panel. :)

Not necessary to remove Deskbar. It's more than a search tool. ;)

---

### Post by por100pre1 on 2007-10-28
> **FuturePilot said:**
> Not necessary to remove Deskbar. It's more than a search tool. ;)

Oh, ok. Thanks for the advice! :)

---

### Post by dugh on 2007-11-06
Thanks for the tip

---

### Post by Photonic Nature on 2007-11-17
**[COLOR="Red"]!! WARNING !![/COLOR]**
Danger!, Danger!, Will Robinson...
[COLOR="Red"]** Do NOT try to remove it !!**[/COLOR] [-X

Removing ' libtrackerclient0 '  in Synaptics will ALSO remove Nautilus and the ubuntu Desktop!! - Bye Bye computer #-o

---

### Post by Frak on 2007-11-17
> **Photonic Nature said:**
> **[COLOR="Red"]!! WARNING !![/COLOR]**
Danger!, Danger!, Will Robinson...
[COLOR="Red"]** Do NOT try to remove it !!**[/COLOR] [-X

Removing ' libtrackerclient0 '  in Synaptics will ALSO remove Nautilus and the ubuntu Desktop!! - Bye Bye computer #-o
You need to put nautilus on hold, then remove libtrackerclient0, while allowing it to skip holds. Not a big deal.

ubuntu-desktop is a metapackage

---

### Post by charlieg on 2007-11-22
> **Frak said:**
> 2 things
1) Tracker is **Alpha**, which means it probably has some problems (beagle was stable)
I sincerely hope that is not the official stance.  (In fact I'm pretty sure it's not the official stance.)

Still, I hate tracker, and even after deselecting it (AGAIN!!! IT RESELECTED ITSELF AFTER A MONTH OF BEING UNSELECTED!!!!) it still is running.

---

### Post by jfdill_2 on 2007-12-20
man tracker.cfg

There are several options to throttle memory / cpu usage of trackerd.  I just noticed it because I was trying to "fusermount -u" an sshfs and it kept saying "in use" then I found that trackerd was the process locking the mounted directory.

I just added that directory to NoWatchDirectory= to exclude it from being indexed by trackerd.

---

### Post by perdubug on 2007-12-23
I also have this problem on my DELL nb. After disabled Trackerd by going to System> Preferences> Sessions and System> Preferences> Indexing Preferences, everything is ok - CPU history down to 20%-30%.

---

### Post by sloggerkhan on 2007-12-23
I deleted tracker via synaptic and still have my desktop and everything, no problems...

---

### Post by Yellow Onion on 2008-01-11
I found This only after tracker.log became 700mb in size!!!! it filled my hard drive
"ERROR: execution of prepared query SelectSubFileIDs failed due to database disk image is malformed with return code 11" thats the error that is repeated in the log over and over. thank for help removing it

---

### Post by ahuffman on 2008-01-20
Thanks for the verification of what this is.  I have an Intel Core 2 Quad with 4 Gigs of RAM and trackerd was slowing the entire machine down.  It was using 1 Gig of RAM and 1 entire processor periodically for long periods of time.  I disabled it.

---

### Post by CostaKat on 2008-01-20
I opened the tracker's preferences (Performance tab) and set the performance to the slowest - the CPU usage fell from 70% to 3%. Care to do the same?

---

### Post by unclejac on 2008-01-20
Curiously I also noticed this process running earlier today after i realised my machine seemed to be working "hard". Think I'll disable it.

---

### Post by saphil on 2008-02-01
trackerd was taking as much as 98% of my processor, and generally ate all the cpu cycles that nothing else was using.  It never isn't running, sucking up those tasty cycles.  I still had it left over from Gutsy that I dist-upgraded

---

### Post by gianluca.pettinello on 2008-02-05
I installed tracker and includedinto the deskbar to have something similar to Leopard mac os. It works fine but sometimes the deskbar closes unexpectly. I installed also beagle but the utility powertop suggested me to disable it because it eats a lot of battery. What do you think is the best for the quick searches?
How do I disable beagle?

Gianluca:lolflag:

---

### Post by saphil on 2008-02-05
Fastest search is command locate done in terminal window
I don't know why there isn't a gui for it..  or there may be one, and I don't know what it is..

Wolf

example
```
$ locate search-string
``` which gets you a scrolling text river
```
$ locate search-string | less
``` which gets you a paged terminal readout
```
locate search-string > savefile.txt
```which gets you a text log of your search
```
wolf@prospero:~$ locate rock
/var/www/PowerScripts/scripts/supercart/rocket.jpg
/opt/SDK/blueprints/petstore/web/images/rockfish-thumb.jpg
/opt/SDK/blueprints/petstore/web/images/rockfish-med.jpg
/home/wolf/Desktop/dt/117gifts07/1download/4july/fireworks---rockets.php

``` -- see?  it searches the whole hard drive regardless of your current directory position

---

### Post by dbera on 2008-02-05
> **gianluca.pettinello said:**
> I installed tracker and includedinto the deskbar to have something similar to Leopard mac os. It works fine but sometimes the deskbar closes unexpectly. I installed also beagle but the utility powertop suggested me to disable it because it eats a lot of battery. What do you think is the best for the quick searches?
How do I disable beagle?

Gianluca:lolflag:

How about uninstalling it :)

---

### Post by kevmaster on 2008-02-13
Same problem here. When I tried to login, the system freezed and my harddrive was spinning like crazy. Only thing I could do was switch to terminal with CTRL ALT F2, and run top.

Saw a process: trackerd causing a load of 7 on my system.
So I killed it, and slowly but surely my system came to live again.

I've recently added an smb mount using /etc/fstab, I wonder if it's related to that. Trackerd should not be scanning network resources unless specificly told to do so I think. 

If you run df, you can filter to show only local filesystems, so this shouldn't be too hard to detect in trackerd either, I guess?

---

### Post by kpkeerthi on 2008-02-13
Its pretty useless if you ask me. To uninstall, 
```

sudo apt-get remove --purge tracker-search-tool tracker-utils

```

Also delete the index stored here. 
```

du -sh ~/.config/tracker
rm -rf ~/.config/tracker

```

---

### Post by kevinlam on 2008-02-19
yeah i mount smb drives as well.. so i uninstalled it but kept the .config/tracker as its taking only 8k of space for me .. so far nothing bad has happened yet

---

### Post by MagnusL on 2008-02-23
Hi!

I found the index in ~/.cache/tracker, not ~/.config/tracker. Some 200 MB of space. 

Magnus L

---

### Post by ekh on 2008-02-25
I have made a complete removal of tracker in all my computers. Today one computer was very slow when it has booted.

The guilty process showed up after a while in System Monitor (computer nearly frozen), it was trackerd.

How can trackerd run, when I have made a complete removal ?
What mechanism reinstalls it ?
I have certainly not done this by intention.

I simply hate that program, it eats my resources.

I also noticed that my freshly booted computer has sent 10 MByte of data to the net, what happens here ?

Any ideas ?

---

### Post by speirint on 2008-02-28
> **kpkeerthi said:**
> Its pretty useless if you ask me. To uninstall, 
Also delete the index stored here. 
```

du -sh ~/.config/tracker
rm -rf ~/.config/tracker

```

Hi, may I ask how do you access the indexes indicated above and then proceed to delete them using terminal?  I've tried deleting the tracker through synaptic, but it is still running which leads me to believe that what you put up is the only thing I'm missing from the purge process now.

---

### Post by jcoffland on 2008-03-17
Gutsy currently uses version 0.6.3.  I built 0.6.6 from source from the trackerd website.  It seems to work a lot better.

```

wget http://www.gnome.org/~jamiemcc/tracker/tracker-0.6.6.tar.bz2
tar xjvf tracker-0.6.6.tar.bz2
cd tracker-0.6.6

sudo apt-get install libnotify-dev libxine-dev libunac1-dev libgstreamer0.10-dev libgamin-dev libpoppler-glib-dev libexif-dev libsqlite3-dev libgmime-2.0-2-dev

```

Make sure you configure it to overwrite the system version with:

```

./configure --prefix=/usr

make
sudo make install

```

This way you don't have to worry about uninstalling the Ubuntu version.  However, if Ubuntu gets around to upgrading the package it will overwrite your built version.

Also run:

```

tracker-preferences

```

Under the performance tab you may want to make some adjustments.

Then run:

```

tracker-search-tool

```

Because that is the whole point.

---

### Post by timjohn7 on 2008-03-20
Can I safely delete cache/tracker?  I have limited disk space and it is eating up over 200 Mb.

---

### Post by FuturePilot on 2008-03-20
Yes but you won't be able to search with Tracker until it re-indexes. But if you don't need Tracker you can turn it off under System&#8594;Preferences&#8594;Indexing Preferences

---

### Post by timjohn7 on 2008-03-22
Thanks... except I don't have Indexing Preferences under Preferences.  Nor is it available in Edit Menus.
I recently installed and then uninstalled Google Desktop.  Could something residual and hidden from this be eating up my 20Gb disk space?  I keep getting 100% disk space used messages.
I uninstalled tracker as per this thread, but it still seems to be here somehow...

---

### Post by exactopposite on 2008-03-23
jcoffland  

thanks so much for that. things are MUCH better for me now with the updated version of tracker.

---

### Post by elewton on 2008-03-27
This is incredible.
My laptop has gone from barely usable to lightning quick in one move.

Thanks!

Using Hardy.

---

### Post by kevmaster on 2008-03-29
I've seen this on multiple machines now.
Tracker makes Ubuntu so slow sometimes.

It's not so weird either cause if you look at System->Preferences->Indexing Preferences, the defaults are to:
 - Enable Indexing
 - Fastest Throttling (maybe this is a 'nice' setting which I believe also ranges from 0(not nice) to 20(very nice) )
- Use additional memory for faster indexing
- Index mounted directories (oh no! not my 1TB samba share!)
- Index and watch my home directory
- Enable Evolution email indexing

I wonder why the default isn't more polite. And you're using hardy you say, so my guess is they're not changing it either?

---

### Post by phyrewall on 2008-03-30
removing tracker from Hardy doesn't require removing the ubuntu-desktop or nautilus. So apparently someone's looking at this thing in the right way...

---

### Post by lnostdal on 2008-04-02
this thing is silly .. why do they add things like this?

if i needed an "improved search" i'd install it myself ....

---

### Post by Mr_Ada on 2008-04-19
Well this is driving me nuts.  I tried disabling it and even removing it and my systems still acts badly.  I am trying to do recording with audacity and it stops or stutters.  I have a quad core system and this shouldn't be happening.

chris

---

### Post by Mr_Ada on 2008-04-19
Anothing thing I noticed is that firebox (32) is creating many 137mb versions (like 9) and I only have 1 window up.

Ubuntu is such a hog on memory.

chris

---

### Post by saphil on 2008-04-20
I am still happy with CLI locate command.  It works for what I do. trackerd just seems like a waste of energy, at this point.  Maybe it could be made an optional rather than required part of the install.

---

### Post by Frak on 2008-04-20
Has anybody else noticed that the locate -u command is gone?

Just me, but that's quite annoying.

---

### Post by zeifertstc on 2008-05-22
Overall, I'm just glad to see that I'm not the only one on these forums with the same problems. I've manually killed the processes, disabled them and modified the config file to (hopefully) never start on boot again. 

Thank you very much for all of your advice on how to disable the processes. I don't think I necessarily want to get rid of trackerd at this point, but we'll see if it gets a bit of revamping from the repository teams. 

Thanks again!

---

### Post by fktt on 2008-05-22
trackerd is an evil tard. >: (

---

### Post by janfsd on 2008-05-25
You can always try beagle, for me it works better than tracker.

---

### Post by nekroskoma on 2008-05-25
i was wondering for awhile why this prog was taking 100% of my processor and making my hard drive lose it

its gone, computers happy now

now why exactly was this demon included in the first place

---

