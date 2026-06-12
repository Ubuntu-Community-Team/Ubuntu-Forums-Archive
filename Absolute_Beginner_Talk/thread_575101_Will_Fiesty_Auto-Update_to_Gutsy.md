---
title: "Will Fiesty Auto-Update to Gutsy?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-10-13
So it looks like 7.10 (Gutsy Gibbon) will be officially released this coming week and that brings a few questions to my mind.

1.  Will 7.04's (Fiesty Fawn) Synaptic Package Manager automatically make the upgrade for me?  If not, and I keep Fiesty, does that mean that my system will slowly become obsolete as the updates steadily come in for Gutsy and yet trickle down to nothing for Fiesty?

2.  If I decide to upgrade, and Synaptic won't handle it for me, would that equate to a fresh install?  Would that effectively eliminate all of my own personal customizations (window manager, keyboard-shortcuts, xorg.conf edits, etc.)?

3.  If the answers to 1. and 2. turn out to be no and yes, will it be worth it?  What does Gutsy have to offer that Fiesty doesn't?

-Mike

---

### Post by Pumalite on 2007-10-13
Save your data and do a clean install of Gutsy. I assure you, it's worth your while. Besides, support for Feisty ends next year, I think.

---

### Post by funrider on 2007-10-13
1 will work

---

### Post by mikeserv on 2007-10-13
Do you mean that Synaptic can handle it?  That would be awesome!

-Mike

---

### Post by anjilslaire on 2007-10-13
yup, 1 will work.
However, I recommend mounting /Home on it's own partition, so you can format / at will and reinstall your as whenever you feel like (to any version) and your personal settings (everything in /home) will be intact.

---

### Post by betweenthetines on 2007-10-13
> **mikeserv said:**
> Do you mean that Synaptic can handle it?  That would be awesome!

-Mike

I don't think Synaptic will "automatically" upgrade your OS to Gutsy, but you can certainly choose for it to upgrade for you without losing any of your customizing or /home files. A "clean" install is preferred by a lot of people on this forum, but is by no means necessary.

Also, it might not be a bad idea to go ahead and backup your xorg.conf file (and any similar edited scripts, etc.) just in case something does go wrong. Just my personal advice :)

---

### Post by PsycoGeek on 2007-10-13
> **anjilslaire said:**
> However, I recommend mounting /Home on it's own partition, so you can format / at will and reinstall your as whenever you feel like (to any version) and your personal settings (everything in /home) will be intact.

A Q about that method of partitioning...  Lets say, on a system with three 80gig hard drives (one for the OS all installed applications, and two drives for use in video/audio editing- trans coding/editing from one drive to another for a boost in speed), how much space should you use for "/home" and how much for "/(root)"... 20/60, 40/40, 30/50?  Under windows I could judge how much space would be needed in a similar configuration, but under Linux I don't know where information is stored and how much space should be allotted for each partition.

Also, swap partitions are split between the two secondary hard dives in my case.

---

### Post by Billy_McBong on 2007-10-13
[COLOR="Blue"]PsycoGeek, use most of it for /home
i set up 10 GB for / and have barley used one. 5 GB should be plenty for /

for the OP i would suggest backing up you data and doing a fresh install with a separate /home partion [/COLOR]

---

### Post by mikeserv on 2007-10-13
What would be a good process for backing up my /home folder, making a clean intstall of Gutsy with a separate /home partition, and then copying all of that /home folder to the new /home partition?

-Mike

---

### Post by Pumalite on 2007-10-13
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Kaptain Chaos on 2007-10-13
Hello mikeserv,
I suggest you look at psychcats easy to follow instructions on how to [ 'Create a separate home partition in Ubuntu']("http://www.psychocats.net/ubuntu/separatehome").

It's very straight forward - and a highly recommended practice - to have a seperate home partition, simply because all of your personal files are kept intact and any changes to your system (i.e. the 6 monthly Ubuntu upgrade) will not affect your Firefox or Thunderbird profiles and other essential, personal information that gets stored in home.

If there's ever the need to do a fresh install you simply mark that partition as /home in the disk partitioning menu of the install process and not format it.

---

### Post by mivo on 2007-10-13
> **Billy_McBong said:**
> [COLOR="Blue"]PsycoGeek, use most of it for /home
i set up 10 GB for / and have barley used one. 5 GB should be plenty for /[/COLOR]

10 GB here, too, and it uses 2.5 GB. I think it's 2 GB out of the box for Ubuntu (Kubuntu uses a little more). Well, I would still not do much less than 10 GB ... the system grows over time. But in no even should you dedicate a whole 80 GB disk just for /! This is Windows-thinking where Program Files alone can be dozens of GBs large, but Linux programs are much more compact and smaller. :)

---

### Post by Kaptain Chaos on 2007-10-13
Hello Psychogeek,

The whole area of partition sizes is very grey, it really does depend on what software you install over and above the basic Ubuntu installation and the size of files you expect to accumulate in your home partition (how long IS a piece of string anyway?)

A number of people seem to recommend between 5 and 10 Gb for your / (root) partition. With your disk sizes I'd err on the more generous 10 Gb, possibly 15; the 20/60 split may be too much. You may also want to consider another partition for back ups that can be transferred to DVD. A good place to start looking for further information is
[ Partitioning Windows and Ubuntu]("http://www.psychocats.net/ubuntu/partitioning"). There's also a link to Herman's excellent guide on the same page.

(ps well linked Pumalite - got there before me! - sorry for my spelling mistake, should have read psychocats)

---

### Post by alienexplorers on 2007-10-13
First I made a /home partition and moved everything associated with home to that partition.  Next I did a clean install of 7.10, formatting / and swap.  When everything was reloaded it was a breeze to get everything up and running.  This is my first upgrade since installing 6.06LTS when that first came out.  I see now why everyone is in a rush to get the new software.  Everything is so bright and shiney.  You will see me upgrading to every new version when they come out.

---

### Post by dwiedenfeld on 2007-10-13
Anjilslaire--
  To follow up--Are all of the personal settings stored in /home?

---

### Post by dwiedenfeld on 2007-10-13
Another question--
  What happens to drivers that have been installed? I have a printer driver for a Canon printer (which apparently is a lot more of a pain than any HP printer) that took me a while to set up. If I upgrade (as opposed to a clean install) will it keep the printer driver?

---

### Post by Orbital75 on 2007-10-13
Well, as far as backing up your Home, I'd highly recommend " hubackup "
This program can be found in the Repositories and works really well.
It will even backup to a CD if you wish.

---

### Post by PsycoGeek on 2007-10-13
Thank you all for a bit of clarification on the partitioning.

---

### Post by anjilslaire on 2007-10-13
> **dwiedenfeld said:**
> Anjilslaire--
  To follow up--Are all of the personal settings stored in /home?

Pretty much, yes.

I've even gone so far as to have kubuntu installed (separate /home), then on a whim formatted / and installed the standard Ubuntu desktop (no kde).

When I logged back in, it gave an error because I had no kde environment to log into (duh), so I switched to Gnome to log into (obviously). Since I didnt have Gnome before, the UI was standard Gnome settings, but of course all my files, bookmarks, etc were still intact.

A simple 'sudo apt-get install kubuntu-desktop' got my kde installed, and as soon as I switched my session to kde & logged back in, ALL of my kde configurations were intact, exactly as they were originally. Just like being back /home, lol :)

---

### Post by mikeserv on 2007-10-13
The question about the drivers, what's the answer?  Are the drivers stored in the home folder?  For instance, my ATI drivers?  I mean, I realize Gutsy is supposed to be preset for installing those drivers, but, if I remember right, I had a lot of difficulty getting that set up before...

-Mike

---

### Post by Billy_McBong on 2007-10-14
[COLOR="Blue"]you might have to reinstall drivers, but it will be much easier and faster in Gusty [/COLOR]

---

### Post by dwiedenfeld on 2007-10-16
> **anjilslaire said:**
> Pretty much, yes.

I've even gone so far as to have kubuntu installed (separate /home), then on a whim formatted / and installed the standard Ubuntu desktop (no kde).

When I logged back in, it gave an error because I had no kde environment to log into (duh), so I switched to Gnome to log into (obviously). Since I didnt have Gnome before, the UI was standard Gnome settings, but of course all my files, bookmarks, etc were still intact.

A simple 'sudo apt-get install kubuntu-desktop' got my kde installed, and as soon as I switched my session to kde & logged back in, ALL of my kde configurations were intact, exactly as they were originally. Just like being back /home, lol :)

Thanks, Anjilslaire.

---

### Post by dwiedenfeld on 2007-10-16
> **Billy_McBong said:**
> [COLOR="Blue"]you might have to reinstall drivers, but it will be much easier and faster in Gusty [/COLOR]

Why do you say that? Why will GG be so much better than FF? I had a time with that printer driver, and I don't want to repeat it. Why will Gutsy be so much faster, if Canon still doesn't produce an "official" driver?

---

### Post by sayuki288 on 2007-10-16
sudo update-manager -d

---

### Post by mikeserv on 2007-10-17
Well, I did the sudo updatemanager -d dealie, and, I have to say, my experience was less than pleasant.  Lots of things broke for me, and I think it had to do with third-party repos.  I guess I had installed some things from other repos while working in Fiesty and then, after upgrading to Gutsy, everything went to ****.  

This was compounded by the fact that I have an ATI video card - which is hard enough to get working in the first place - but I guess the FGLRX driver that I had was not the version that Gutsy was expecting, and I lost X.  I don't know if any of you have had this type of problem before, but, especially for us newbies, resolving it involves a lot of rebooting and lot of swearing.  But I got that fixed.

Then there was the Compiz issue.  I don't particularly remember what the original problem was exactly (by that time I had resorted to nursing my Linux woes with booze) but I remember that it didn't working.  After quite a lot of forum searching and uninstalling/reinstalling I had a workable, if somewhat older, version of Compiz-Fusion installed.  After getting it up and running though, I found that the only manageable way to use Emerald in conjunction with Compiz was to disable the Blur plugin (which is a solution I happened across on some thread here) - otherwise all computer processes slowed to a crawl.

Then I tried to get rid of the flash of brown screen that Gutsy was displaying between login and working desktop, which is apparently a known and documented bug, and I lost my desktop entirely.  I mean, it went away.  I still had a task-bar and Kiba and so on, but all desktop icons were gone, the wallpaper was gone and the desktop itself refused to respond to any amount or variation of clicks.  I did notice, however, that this issue had only affected my user account, and that my wife's account still worked as per usual.  So, after asking ubuntuforums.org and receiving no workable reply, I cheated and created a new account.  Kind of annoying, but with a little creative copying from one user's home folder to the other's, there was essentially no harm done.  Also, I'm not sure if I should blame this problem on Gutsy or on the increased risk of user error brought about by intoxicated computing.  Although, it's not like my risk of user error is all that low anyway: I am a newbie, and something of an idiot. 

So after all is said and done, I do have Gutsy up and running, but only after a few false starts.  What I'm confused about, though, is that I've yet to see any noticeable benefits of one over the other (meaning, Gutsy over Fiesty).  There was this new video hardware detection screen that kept popping up when I was having the FGLRX troubles.  Of course, it completely failed to detect anything and really only succeeded in muddling up my xorg.conf, which was solved easily enough since I have about 100 backup copies distributed in various areas of both harddrives having become irritated to the point of paranoia the first time I tried to get FGLRX working.  I guess the Appearances applet in the system menu is new, but it's hardly beneficial for me - I do all of that sort of adjusting in Compiz and Emerald, anyhow.  Has anyone else noticed any improvements worth mentioning?

-Mike

P.S.  I realize that a lot of that looks like grumbling, but I am only trying to share my Gutsy experiences so that others won't have to experience the same thing I did.  Really, I'm perfectly content now, even if Ubuntu did drive me to drink.  Actually, maybe I'm content because it did.

---

