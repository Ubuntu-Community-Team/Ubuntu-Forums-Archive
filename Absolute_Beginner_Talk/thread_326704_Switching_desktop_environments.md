---
title: "Switching desktop environments"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2006-12-28
Hey all. I'm sort of interested in switching desktop environments possibly from Gnome to either KDE or XFCE. Gnome is ok, but I think it's definitely the ugliest of the three. I like the Windows-esque look of Kubuntu, and I hear good things about the speed of Xubuntu.

I'm wondering if switching desktop environments would erase files/plugins/config files or anything else important. I've had Ubuntu for a couple of months now, and I think I've just about got all the plugins I want installed. Most importantly, after a long hard battle, I got wireless internet going to a WPA-encrypted network. Will switching desktops erase all this work, causing me to start all over again? Would this be similar to the entire installation process of Ubuntu, which would require formatting/partitioning?

---

### Post by riven0 on 2006-12-28
No way! You should preserve all your settings, but you can keep gnome just to be sure. To install kde do:

> sudo apt-get install kubuntu-desktop

Then **Log Out** >> **Sessions** >> **KDE** and log back in. 

For xubuntu:

> sudo apt-get install xubuntu-desktop

And then do the same to switch.

If you really want to get rid of Gnome:

> sudo apt-get remove ubuntu-desktop

---

### Post by lemonsCC on 2006-12-28
Nope, no, nada, nein.  Just install the Desktop/Window Manager of your choice and select it from the sessions menu on the login screen.  Enjoy.  Once you pick one, you can a) uninstall all the others b) set it as the default and leave gnome on your system.

Don't forget they are all themable.  The brown/orange is a bit ubly.  Check out Art Manager in Synaptic or Gnome-look.org

---

### Post by po0f on 2006-12-28
k1001001,

I would suggest installing the *-desktop packages via aptitude, not Synaptic/apt-get.  If you don't like the new DE, you can just get rid of all the packages pulled in with `sudo aptitude remove kubuntu-desktop` (or whichever one you decide on installing).

All of your program settings are for GNOME programs so those won't transfer to KDE/XFCE unless you use the GNOME program under those DEs.  I don't know about the wireless, sounds like system-level stuff.  You should still be able to connect with it.

---

### Post by k1001001 on 2006-12-28
> **po0f said:**
> k1001001,

I would suggest installing the *-desktop packages via aptitude, not Synaptic/apt-get.  If you don't like the new DE, you can just get rid of all the packages pulled in with `sudo aptitude remove kubuntu-desktop` (or whichever one you decide on installing).

All of your program settings are for GNOME programs so those won't transfer to KDE/XFCE unless you use the GNOME program under those DEs.  I don't know about the wireless, sounds like system-level stuff.  You should still be able to connect with it.
I use aptitude already. Some people like apt-get better, but I haven't seen a downside to using aptitude. Really the only difference is when you remove/purge programs. apt-get removes the program, but aptitude will also take the dependencies with it. But there's a couple of other nice things I like about aptitude, such as when you misspell a package name, or can't think of the exact title. Aptitude will respond with a "Did you mean:" sort of thing that usually has the package you're looking for. Anyways, that's off-topic.

Thanks for your answer though. It's the one I was looking for. I have a feeling my wireless won't work with my WPA network in KDE/XFCE without some configuring. If I do get it to work though, I'm definitely switching.

So all I have to do is download it, and I can switch back and forth between them? Sweet.

Oh yeah, will this be Dapper or Edgy? Currently I'm using Dapper.

---

### Post by Tux Aubrey on 2006-12-28
Shameless plug for bodhi.zazen's guide to running several different desktops in a single session.

Its like magic - [http://http://ubuntuforums.org/showthread.php?t=271674]("http://http://ubuntuforums.org/showthread.php?t=271674")

"I heartily endorse this product or service" - Krusty The Clown

HOWEVER - the latest Beryl upgrade seems to kill the ability to switch between different X sessions.

---

### Post by k1001001 on 2006-12-28
Update: I got all three installed. It works like a charm! Internet works wirelessly on all three desktop environments, as well as most other programs, much to my surprise.

Pros and cons of both, for anyone interested:
Kubuntu:
+ Friendly Windows-esque look
+ Many options
+ Only one taskbar (at the bottom)
+ Wine menu featured right in the Kubuntu "Start" menu (I never could figure out wine in Gnome)
- Bottom taskbar is rather cluttered
- Firefox didn't seem to work (though Konquerer was included)
- Videos on YouTube using Konquerer didn't seem to want to play, and player looked ugly
- Gnome applications run in KDE look ugly (but you're supposed to run the KDE applications instead, so this isn't really a valid point)
- Big download, long install compared to XCFE (450 MB download I believe, and then took about 5-10 minutes to configure on its own)
- Seemed to be even slower than Gnome

Xubuntu:
+ Small download, short install (45 MB download, took a couple of minutes to configure)
+ Look is sort of a combination of Gnome and KDE with a Mac look thrown in there as well (probably due to OS X background)
+ Blazing speed due to less system demand
+ Menu similar to KDE (which I prefer to Gnome's menus)
- Gnome-esque double taskbar at top and bottom (hogs a lot of monitor space if you ask me)
- Neither Konquerer nor Firefox were acknowledged to exist
- When I selected internet for the first time, I hit something about "Debian Viewer" instead of "Konquerer", which then brought up a terminal-based file browser. I couldn't reverse this, so I basically had no internet browser. (Got internet using w3m, but that is definitely not my preferred method.)

I think it's pretty sweet that you can just log out to the Ubuntu shell and select which desktop environment you want. This gives me a new interest in Ubuntu. Using the script, you can also run them all simultaneously, which is also awesome, but I don't think my laptop could handle the demand of both Gnome and KDE.

Thanks for your help guys! I know it was a rather simple issue, but I'm still new to Ubuntu and Linux both, and it's nice to have some good help because sometimes Linux can really piss me off.

---

### Post by Tux Aubrey on 2006-12-28
Strangely (or perhaps not) having multiple X sessions does not seem a great drain on resources - at least for me.  

Since you are doing the Desktop thing, I strongly suggest you try Fluxbox as well (although the install is a bit of a pain because the version in the repos is very old).  If you search for bodhi.zazzen's fluxbox posts, there is an upgrade guide and lots of cool stuff to try.  

Keep playing!

---

### Post by DougS on 2007-01-03
Everything was fine with this thread until I saw the lack of Internet browser when going from Kubuntu to Xubuntu!

I WANT to try the speed of Xubuntu (as this myth of speed with Linux vs Windows seems to me to be just that - no flames please it's just my experience so far!) without the bloat but I don't want to lose Firefox and other higher end apps (like VLC, OO etc.).

Can anyone confirm that you CAN have:
Multiple environments AND
selectable at logon AND
Retain Firefox or similar full featured browser along with bookmarks AND 
retain previously set up apps obtained due to the input of a substantial amount of time (OK OK I know I'm using a new OS and I expect that!)

And if so do you simply follow the advice above?

Thanks
Doug

---

### Post by aysiu on 2007-01-03
Xubuntu comes with Firefox, and it should still be using your same bookmarks and settings.

---

### Post by DougS on 2007-01-04
Thanks, I've now tried it and it was great.
Xubuntu does seem to suit my needs better in many ways.
More fun to be had!
Regards
Doug

---

### Post by goatflyer on 2007-01-04
I toggle frequently between Ubuntu and Xubuntu and I can confirm that all my apps (FF, OOo, Abiword, xmms, wine) work fine with both desktops and retain all their settings. (I speak for Dapper, I have not tried Edgy)

---

### Post by icedcheese on 2007-01-07
Hi Doug

Just letting you know I am now using Xbuntu with all my previous settings!

---

### Post by stengah on 2007-01-17
Just a quick response to the aptitude vs. apt-get approach to un/installing packages. True that using aptitude should take care of unwanted dependencies, packages etc, however apt-get should afaik do likewise in newer versions, just use the 'autoremove' command, e.g.:

[INDENT]sudo apt-get autoremove [packagename] [/INDENT] rather than 
the traditional 
[INDENT]sudo apt-get remove[/INDENT] command.

Just my 5c - cheers! ;)

---

### Post by aysiu on 2007-01-17
> **stengah said:**
> Just a quick response to the aptitude vs. apt-get approach to un/installing packages. True that using aptitude should take care of unwanted dependencies, packages etc, however apt-get should afaik do likewise in newer versions, just use the 'autoremove' command, e.g.:

[INDENT]sudo apt-get autoremove [packagename] [/INDENT] rather than 
the traditional 
[INDENT]sudo apt-get remove[/INDENT] command.

Just my 5c - cheers! ;)
Funny you should say that, since your profile says you're using Dapper. As far as I know, *autoremove* wasn't implemented until Edgy.

I still recommend *aptitude* unless I **know** the person asking the question is using Edgy.

---

