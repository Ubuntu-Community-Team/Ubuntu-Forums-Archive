---
title: "OpenBox vs XFCE+Compiz and memory"
date: 2009-01-20
forum: Arch and derivatives
---

### Post by SomeGuyDude on 2009-01-20
Found this interesting. On Openbox with almost everything rolling, I use ~320MB of RAM, more depending on what FireFox is up to. XFCE+Compiz, 400MB, and a whole lot of that is Firefox's... 12 tabs.

I'm impressed with how light this is on here. I would have expected it to be noticeably heavier.

---

### Post by smartboyathome on 2009-01-20
Have you tried LXDE+Compiz? That should even the playing field a lot more. ;)

---

### Post by Cope57 on 2009-01-20
Openbox + Ubuntu = [#!CrunchBang]("http://distrowatch.com/?newsid=05288")

[[IMG]http://crunchbanglinux.org/wiki/_media/screenshots/crunchbang-linux-clean-desktop-8.10.01.png?w=450&h=&cache=cache[/IMG]]("http://crunchbanglinux.org/wiki/screenshots/8.10.01")
> CrunchBang Linux is an Ubuntu based distribution featuring the lightweight Openbox window manager and GTK+ applications. The distribution is developed from a minimal Ubuntu install and has been designed to offer a good balance of speed and functionality.
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by Pogeymanz on 2009-01-20
Try doing it without Firefox at all. It's hard to predict how much memory it will use.

Instead, try booting up, opening an image (the same both times) with GIMP and editing something about it (the same both times). Then create an Office document and delete it, etc...

Then I think you'll have a more fair comparison.

Honestly, XFCE alone barely uses more memory than Openbox on my machine. Compiz does add a good 20-30 MB upon login, though.

---

### Post by SomeGuyDude on 2009-01-20
That I'd even have to do it to that extent shows how little of a difference there is. I just CANNOT STAND EMERALD. Hate it. Hatehatehate. On Ubuntu I used Compiz+Metacity and I wish I had a way to use Compiz but keep my OB theme. Impossible, sure, but it'd be nice.

And wait, LXDE can work with Compiz? How? I thought LXDE was just OB with a smattering of extra packages like PCManFM and a panel.

---

### Post by smartboyathome on 2009-01-20
> **SomeGuyDude said:**
> That I'd even have to do it to that extent shows how little of a difference there is. I just CANNOT STAND EMERALD. Hate it. Hatehatehate. On Ubuntu I used Compiz+Metacity and I wish I had a way to use Compiz but keep my OB theme. Impossible, sure, but it'd be nice.

And wait, LXDE can work with Compiz? How? I thought LXDE was just OB with a smattering of extra packages like PCManFM and a panel.

LXDE is very modular, so you can use everything but change the window manager from Openbox to Compiz. I've done it before. :)

---

### Post by SomeGuyDude on 2009-01-20
> **smartboyathome said:**
> LXDE is very modular, so you can use everything but change the window manager from Openbox to Compiz. I've done it before. :)

Sounds to me like it'd just be Compiz as a standalone with the LXDE apps, unless I'm misunderstanding something.

NOTE: I'm not trying to be contradictory, I just never saw what LXDE was outside of a package of lightweight applications using OB as its window manager, it's not a full-fledged DE a la XFCE or something, right? I mean, is LXDE something beyond PCmanFM, LXterminal, LXAppearance, LXpanel?

---

### Post by crimesaucer on 2009-01-20
I've used compiz with xfce4 since November of 2006.... (was beryl back then). I found that compiz-fusion seems more solid and stable than xfce4-compositing, while only being a bit slower and heavier on resources. Plus, emerald is such a nice window decorator....


I have also used xfce4 with only xfwm4-compositing. If they fix a few things for xfce4.4.6 then I will give it another try.

---

### Post by RiceMonster on 2009-01-20
I prefer to use the built in xfwm4 compositor, because I just like a few subtle effects like real transparency on my terminal, while dragging apps and for my panel. I like having the shadows for menus and windows too. Compiz is too overboard for me.

---

### Post by smartboyathome on 2009-01-20
> **SomeGuyDude said:**
> Sounds to me like it'd just be Compiz as a standalone with the LXDE apps, unless I'm misunderstanding something.

NOTE: I'm not trying to be contradictory, I just never saw what LXDE was outside of a package of lightweight applications using OB as its window manager, it's not a full-fledged DE a la XFCE or something, right? I mean, is LXDE something beyond PCmanFM, LXterminal, LXAppearance, LXpanel?

LXDE is just a desktop environment based on Openbox, yes. It is like GNOME, which is based off of Metacity with apps added in. Just because you take the Window Manager away, doesn't make it any less of a desktop environment. ;)

---

### Post by SomeGuyDude on 2009-01-20
> **smartboyathome said:**
> LXDE is just a desktop environment based on Openbox, yes. It is like GNOME, which is based off of Metacity with apps added in. Just because you take the Window Manager away, doesn't make it any less of a desktop environment. ;)

Hm. But would I lose my right-click menu? Really that's all I care about. I use conky/tint/trayer for most of the grunt work, but I -really- like my right-click menu and don't think I'd cope well without it. That and my alt-F2 window...

Right now I'm rolling XFCE/Compiz again, giving it the ol' college try for a while and see how she flies. I really realized how much I missed the smooth Compiz feel, but it IS a little sluggish just in terms of the time the animations take. We'll see if I keep 'er.

---

### Post by smartboyathome on 2009-01-21
> **SomeGuyDude said:**
> Hm. But would I lose my right-click menu? Really that's all I care about. I use conky/tint/trayer for most of the grunt work, but I -really- like my right-click menu and don't think I'd cope well without it. That and my alt-F2 window...

Right now I'm rolling XFCE/Compiz again, giving it the ol' college try for a while and see how she flies. I really realized how much I missed the smooth Compiz feel, but it IS a little sluggish just in terms of the time the animations take. We'll see if I keep 'er.

Yes, you would. I don't use the right click menu though (lxpanel has a menu which can be added to it ;)).

---

### Post by SomeGuyDude on 2009-01-21
> **smartboyathome said:**
> Yes, you would. I don't use the right click menu though (lxpanel has a menu which can be added to it ;)).

Well, I took your advice a step further. I'm running Compiz standalone. :D

Through some fancy editing, my Emerald theme looks EXACTLY like my old OB theme, and I got compiz-deskmenu from yaourt to look exactly like my old OB menu. Same look, same resource usage, eye candy! :KS :KS

One hiccup. My run dialog won't work. Alt-F2 or any other keybinding, I can't get a run dialog going. Maybe that thing is dependent on whatever DE it runs atop normally? I can live without it, it's just a pain.

---

### Post by fwojciec on 2009-01-21
You have to install a run dialog, for example gmrun or dmenu, then you need to create a keybinding for alf-f2 to run it.  Compiz has means of defining keybindings, but I think you are only limited to 10 total.  You can also use something like xbindkeys for this -- it works without issues with Compiz.

---

### Post by SomeGuyDude on 2009-01-21
Bwahahaha VICTORY. Oh lord I'mma be using this for a long time, I think. Slightly higher CPU usage, but only in the sense of 6% instead of 3%, memory usage the exact same. Plus the keybinding menu is way easier to use than the right-click.

---

### Post by mips on 2009-01-21
> **SomeGuyDude said:**
> XFCE+Compiz, 400MB, and a whole lot of that is Firefox's... 12 tabs.

I'm impressed with how light this is on here. I would have expected it to be noticeably heavier.


400MB sounds like a lot to me. I use less than than in KDEmod4.2RC with firefox & 12 tabs open..

Where do you get the 400MB from, free -m or htop and what is buffered?

---

### Post by SomeGuyDude on 2009-01-21
> **mips said:**
> 400MB sounds like a lot to me. I use less than than in KDEmod4.2RC with firefox & 12 tabs open..

Where do you get the 400MB from, free -m or htop and what is buffered?

1) Htop, how do I determine the buffer business?

2) This was also after the machine had been running a while. Firefox is great about memory leaks.

3) There were other things going, just that FF was using the lion's share.

---

### Post by mips on 2009-01-21
> **SomeGuyDude said:**
> 1) Htop, how do I determine the buffer business?

2) This was also after the machine had been running a while. Firefox is great about memory leaks.

3) There were other things going, just that FF was using the lion's share.



1) free -m

2) I tested on a laptop running for a few hours.

3) Mostly just firefox, shaman & a terminal

In htop I had 297MB used with 12tabs open. With xfce my usage is low (cannot remember) but then again it is not a finished install of xfce. xfce does feel snappier than kdemod though, with kdemod ai seem to have a lot of disk access which makes things slow. No idea whats going on though :)

---

### Post by SomeGuyDude on 2009-01-21
```
             total       used       free     shared    buffers     cached
Mem:          2017        533       1483          0          1        203
-/+ buffers/cache:        328       1688
Swap:         2063          0       2063

```

That's running Compiz by itself, WM-wise (I've got FF/Pidgin/GMPC/Kildclient going). I don't think I've got anything unnecessary running, but then I've never really cleaned out my daemons/modules because I figure all of that's needed. :?

---

### Post by hrod beraht on 2009-01-21
> **SomeGuyDude said:**
> Found this interesting. On Openbox with almost everything rolling, I use ~320MB of RAM, more depending on what FireFox is up to. XFCE+Compiz, 400MB, and a whole lot of that is Firefox's... 12 tabs.

I'm impressed with how light this is on here. I would have expected it to be noticeably heavier.

That actually seems a bit heavy to me. What else do you have running?
My Openbox is using ~175MB with Firefox and 12 tabs. (Daemons are: syslog-ng, network, crond, alsa, openntpd).

Bob

---

### Post by snowpine on 2009-01-21
The ram usage will depend on so many factors... My Openbox setup (Crunchbang) only uses about 65mb of ram, but that's on a computer with only 256mb. The identical install uses closer to 200mb on my more powerful desktop. You have to trust Linux to allocate resources wisely. ;)

(edit) Sorry, I just realized y'all are talking Arch...

---

### Post by SomeGuyDude on 2009-01-21
> **hrod beraht said:**
> That actually seems a bit heavy to me. What else do you have running?
My Openbox is using ~175MB with Firefox and 12 tabs. (Daemons are: syslog-ng, network, crond, alsa, openntpd).

Bob

Are those the only daemons? I've got...

```
DAEMONS=(syslog-ng !network @cups @netfs @crond @alsa @wicd @hal @fam @mpd @cpufreq  @openntpd @laptop-mode
```

How much of that could I scrap in a Compiz-only setup? The only likely candidates seem to be netfs, hal, or fam.

---

### Post by ghindo on 2009-01-21
What's the advantage of loading up all those daemons in the background?  (I.e., those with the "@.")

---

### Post by namegame on 2009-01-21
> **ghindo said:**
> What's the advantage of loading up all those daemons in the background?  (I.e., those with the "@.")

The boot times are slightly faster if you load the daemons in the background.

---

### Post by fwojciec on 2009-01-21
> **SomeGuyDude said:**
> ```
DAEMONS=(syslog-ng !network @cups @netfs @crond @alsa @wicd @hal @fam @mpd @cpufreq  @openntpd @laptop-mode
```

How much of that could I scrap in a Compiz-only setup? The only likely candidates seem to be netfs, hal, or fam.

You can use gamin instead of fam -- gamin is not a daemon, so that would mean you can get rid of fam from there.  Gamin is better anyways.

You most likely need hal -- for xorg hotplugging and auto-mounting and such.  Hal also loads dbus daemon, which is most likely needed as well.

You can get rid of netfs if you don't have any network shares that you want mounted on boot.

Openntpd is completely optional.  I just use cron to run it once a week or so to sync the clock (I use ntpdate for that, actually).

Cpufreq is probably redundant if you use laptop-mode-tools as well -- laptop mode is perfectly capable of setting cpu freqencies by itself.

---

### Post by handy on 2009-01-21
*@**fwojciec**:* Thanks for the heads up on Gamin. :-)

The following were on the iMac running Arch/Xfce, Firefox 12 tabs & Terminal with 2 tabs

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:           984        355        628          0          8        115
-/+ buffers/cache:        231        752
Swap:            0          0          0
```

My daemons line:

```
DAEMONS=(syslog-ng network portmap nfslock @netfs @crond @sshd @transmission-daemon @alsa @stb-adm$
```

For all its worth. ;-)

---

### Post by SomeGuyDude on 2009-01-22
Quick note: jiminy cricket Compiz slaughters my CPU. Thing spikes in usage just loading a webpage. It's annihilating my battery life more than I ever remember it doing before. Might cause me to rethink this on my sojourns, but while on AC power it's good. Still, kinda puts a damper on my feeling of victory.

---

### Post by cardinals_fan on 2009-01-22
> **ghindo said:**
> **What's the advantage of loading up all those daemons** [s]in the background?  (I.e., those with the "@.")[/s]
Fixed that for you ;)

---

### Post by mips on 2009-01-23
> **cardinals_fan said:**
> Fixed that for you ;)

roflmao!!!

I'm just as guilty, I actaully have more daemons running.

---

### Post by mips on 2009-01-23
> **SomeGuyDude said:**
> Quick note: jiminy cricket Compiz slaughters my CPU. Thing spikes in usage just loading a webpage. It's annihilating my battery life more than I ever remember it doing before. Might cause me to rethink this on my sojourns, but while on AC power it's good. Still, kinda puts a damper on my feeling of victory.

All these special effect wm eat cpu, some more than others. I was amazed how the default effect in xfce slowed things down. Some of the effects are usefull but generally the majority is just useless eyecandy. I usually end up turning them all off.

---

