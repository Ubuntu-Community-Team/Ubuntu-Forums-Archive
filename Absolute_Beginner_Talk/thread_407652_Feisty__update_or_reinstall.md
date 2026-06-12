---
title: "Feisty:  update or reinstall?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-04-12
If you plan to move to Feisty, are you going to risk an update or do a complete reinstall?  I have heard that reinstalling generally means less trouble (compatibility issues) in the long run.  What's your take?

---

### Post by Rospo Zoppo on 2007-04-12
Reinstall :D

---

### Post by familyjules74123 on 2007-04-12
This is what I hear as well, reinstalling always seems to be better.  I don't have a problem with reinstalling because I do it occasionally anyway just to keep my computer running smoothly.  I suggest backing up your important files though.  I usually do that by moving stuff to my external hard drive.  From what I read upgrading to feisty hasn't gone so smoothly for many users so far, I don't know if they are working on that for the final release but in my opinion its always better to reinstall.

---

### Post by Obor on 2007-04-12
I've updated 2 PCs to feisty with no problems. Some might like starting from fresh but not me :D

---

### Post by familyjules74123 on 2007-04-12
yeah, I guess it really depends on what you have on your computer and how much time it would require to get those back with a fresh install.  I suggest upgrading if you don't have the time to install all the programs, drivers, etc that you have already.

---

### Post by aeon on 2007-04-12
hmm, might be time for a clean reinstall, i've been updating since warty :D
probably just keep doing updates and see how it goes, i dont mind the occasional breakage

---

### Post by zvacet on 2007-04-12
Both options have pro et contra.If you do upgrade you will save all programs you installed(drivers,codecs...),but you don´t have disc if something wrong happened and you need to reinstall.In other hand with fresh install you will lose all pprograms you downloaded and install.But this option has solution.Copy your var/cache/apt/archives and after you do fresh install add it to new  var/cache/apt/archives.After that
```
cd /var/cache/apt/archives
```
```
sudo dpkg -i *deb
```
```
sudo apt-get autoclean
```

After all it is your choice.

---

### Post by ciscosurfer on 2007-04-12
I've always had much better luck with a clean install.  Upgrading is fine when done incrementally during release cycles.  But from cycle to cycle, it's usually a good idea to start fresh.

Think of it like taking a shower.

Just my opinion though.

---

### Post by mahiyar on 2007-04-12
Update is always a problem if you have used scripts for nvidia card or automatix or any such thing, in that case it is better to reinstall.

---

### Post by jvc26 on 2007-04-12
I'm another for the clean install - if you keep a record of your apps when you do so and have a backup of bits and pieces like your bookmarks (AND OBVIOUSLY ALL YOUR DOCS, MUSIC ETC ;)), its nice and easy to wipe it, start again - even maybe repartition it exactly how you want, sorting out those things which may be slightly less than satisfactory - shave a bit more space from the / partition to add to the /home or whatever. The you can reinstall and simply sudo apt-get and input your list of apps there and it puts them all on nice and easily. Then apt-get update/dist-upgrade and you're on your way.

Within a release cycle updating is simple and convenient, but I have had occasion with Upgrades (Dapper to Edgy was a memorable one, on on pc it worked absolutely fine, on the other it caused a massive hassle) where I'd have rather just fresh installed it.

Again your call, just my opinion :)
Il

---

### Post by venik212 on 2007-04-12
Since this is an issue, why isn't there a script or a program that does all the necessary backing up, keeping tabs on which programs you have installed, and then, after a fresh install, reinstalls all those that you had originally on the previous version of Linux?  It seems like a needed tool.

---

### Post by quack on 2007-04-12
Can't you add the release CD as a repository and use that to assist in an upgrade? That would help in the "doing an upgrade but having a CD at hand in case you need a fresh install" scenario.

I have one PC that's running Feisty (but over 300MB behind in updates - I went on holiday then ran out of monthly bandwidth with my ISP so held everything back around Herd 4) and one that has no Ubuntu on it at all yet.

I was intending to download the final release CD, use it for the fresh install and to help save some extra download when I upgrade the out-of-date Feisty. Will that work?

---

### Post by zvacet on 2007-04-12
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by old_geekster on 2007-04-15
I will do an upgrade.  As a matter of fact, I did an upgrade from Edgy to Feisty last week.  It worked great.  Then, came -14/15 kernel updates.  This is what broke my system, not the upgrade.  I am back using Edgy.

I will try another upgrade this afternoon.  It worked great the first time.  I certainly hope that the kernel is updated.

**Update**:  I am performing an upgrade as I type.  I guess I will repeat something that I once heard: "Try that Microsoft"!

How many times have you ever been able to upgrade Windows and surf at the same time?  I am not a Microsoft hater, I simply like to acknowledge great feats when I see them.

Hopefully, this time will be a charm.  Maybe the kernel won't mess with my system.

**Re-Update:**  My upgrade is complete and everything went like clock work.  They definitely fixed the bug in -15 kernel.  It installed and booted perfectly the first time.  The new nVidia drivers (1.0-9631) appear to be far better, also.  Everything seems to be much more clear.

Here's to the Feisty developers for a job well-done!!:D :D

---

### Post by Mau on 2007-04-15
I'm going to do it an upgrade and if it becomes a problem, then I will just re-install. Basically just prepare for a fresh install, but do an upgrade first.

---

### Post by RomeReactor on 2007-04-15
Hi people. I usually back up all my important files, download the new version of Ubuntu (more often than not, the DVD) and try to upgrade through Synaptic; if that breaks my system, then i reinstall with the downloaded DVD. Upgrading has always been a _thrilling_ experience for me, to say the least! :popcorn:

---

### Post by Dirty Ole on 2007-04-17
I am currently running a Feisty upgraded from Edgy using a Alternate CD. 

 When I tried to upgrade from Dapper to Edgy the whole thing messed up real bad so I had to do a Reinstall.

So, my suggestion is try a upgrade first using an alternate CD preferably. If that fails reinstall.

---

### Post by stalker145 on 2007-04-17
Personally, I will be doing a wipe/reinstall. Sure, I'll need to reinstall all of my programs and some of my settings (some because I finally got smart and have a /home partition), but it's all part of the learning process. I get to practice, practice, practice and maybe pick up a couple of easier ways to do things.
I've tried going the upgrade route (Dapper to Edgy early on) and had problems with it failing for one reason or another. I've also found that it takes *forever* over my wireless link. It's far simpler for me to wipe, reinstall, and sit back while Ubuntu downloads all the updates in the background while I sleep :)

---

### Post by dannyboy79 on 2007-04-17
> **Dirty Ole said:**
> I am currently running a Feisty upgraded from Edgy using a Alternate CD. 

 When I tried to upgrade from Dapper to Edgy the whole thing messed up real bad so I had to do a Reinstall.

So, my suggestion is try a upgrade first using an alternate CD preferably. If that fails reinstall.

what do you mean upgrade using the alt cd? i have used the alternate cd to install dapper xubuntu and edgy xubuntu but I guess I never looked at all the options. is there an option that states, upgrade from previous version??? thanks for any info. I am thinking about going to edgy from dapper (on my main server) but wondering if I should just go right to fiesty. i am planning a mythtv box within the next week. how is the mythtv eperience with fiesty, anyone?

answered own questions about upgrading using alt cd. but still curious about other questions/comments I made. thanx

---

### Post by earobinson on 2007-04-17
I always do an update while im testing in but then a clean install of the release!

---

### Post by sailor2001 on 2007-04-17
> **dannyboy79 said:**
> what do you mean upgrade using the alt cd? i have used the alternate cd to install dapper xubuntu and edgy xubuntu but I guess I never looked at all the options. is there an option that states, upgrade from previous version??? thanks for any info. I am thinking about going to edgy from dapper (on my main server) but wondering if I should just go right to fiesty. i am planning a mythtv box within the next week. how is the mythtv eperience with fiesty, anyone?

answered own questions about upgrading using alt cd. but still curious about other questions/comments I made. thanx

from what I understand: NEVER jump updates........don't jump from dapper to feisty. go dapper to edgy to feisty

---

### Post by kpkeerthi on 2007-04-17
Its going to be a clean install for me. I've already got my /home backed up on to external drive. And this time I'm gonna have a separate /home partition.

---

### Post by Larkshall on 2007-04-17
I did a clean install, unfortunately I forgot to copy my latest files to the ext HDD and lost them. It caused me to have to juggle the settings on spreadsheets for the lost records, luckily its not desperately important.

I now keep ALL my data on the ext HDD in case I clean install again. I can also use it on both computers.

Having recently left Windows XP instead of upgrading(?) to Vista, I decided it was time to use the alternative. I am very pleased with the result.

---

### Post by motin on 2007-04-17
> **Blofeld said:**
> If you plan to move to Feisty, are you going to risk an update or do a complete reinstall?  I have heard that reinstalling generally means less trouble (compatibility issues) in the long run.  What's your take?

I just wrote: [Brief HOWTO: "Upgrade" (by reinstalling) from Dapper to Feisty]("http://ubuntuforums.org/showthread.php?p=2471012") in case it helps.

---

### Post by Sunflower1970 on 2007-04-17
I did two successful upgrades, and they went very smoothly...I'm going to go ahead and upgrade the other two computers I have as well, since I had no problems.

---

### Post by Chappy7777 on 2007-04-17
I have a program on a 3.5" floppy called Dban, which can be had at [www.sourceforge.com](www.sourceforge.com)  Or do a Google for Dban. It does a TOTAL erase of the HDD and it is easy and fast. So for myself, I think I will try doing an upgrade and see what happens. If it is acting like a Penquinista in the sahara, then I'll do a Dban. DBAN stands for Dave's Bomb and Nuke or something close. It is so complete in erasing that the CIA uses it, or so I was told. regardless, it works.

Chappy

---

### Post by TimelessRogue on 2007-04-18
Personally, my past experience with two computers moving to Edgy and more recently (last two evenings) with upgrading to Feisty leads me to favor upgrading.  Using "sudo apt-get update" followed by "sudo apt-get upgrade" on Edgy and the the same after changing my sources.list to reference the Feisty repositories (see [http://ubuntuforums.org/showthread.php?t=412477](http://ubuntuforums.org/showthread.php?t=412477)) got me an up-and-running Feisty system with absolutely no problems.

---

### Post by abcuser on 2007-04-18
Hi,
I intend to download new version and burn it on CD. Is it possible to upgrade from 6.10 to 7.4 from CD?
Thanks,
Abcuser

---

### Post by zba78 on 2007-04-18
download and burn the CD ISO, then do an upgrade, if all goes well then leave it at that. Otherwise put the CD in, reboot and install fresh

---

### Post by Seisen on 2007-04-18
I did a dapper<edgy<feisty dist-upgrade without any problems and this was done in the same day. All I had laying around was a dapper cd.

---

### Post by abcuser on 2007-04-18
> **zba78 said:**
> download and burn the CD ISO, then do an upgrade, if all goes well then leave it at that. Otherwise put the CD in, reboot and install fresh
Hi,
I know I can update from internet, but my friend has modem connection (64 kb/s) and he already has 6.10 Ubuntu and would like to upgrade to 7.4. Is it possible upgrade from CD?
Thanks

---

### Post by etnlIcarus on 2007-04-18
Okay, so after the Dapper-Edgy (dare I say) fiasco, we all know upgrading is risky but there's something that's never been made clear to me:

If I wait a couple of months after the Feisty release and then upgrade, can I expect many of the kinks to be ironed out when I do decide to upgrade?

---

### Post by bodhi.zazen on 2007-04-18
LOL you all.

FYI here is the **advised way to upgrade from edgy to feisty** :

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades) 


If you want to **upgrade manually**, ie updating /etc/apt/sources.list and then update && upgrade see here :

[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

[color=red]**Note**: *** Manual method is not advised[/color]


If you want to do a **fresh install, but preserve your user data and installed applications** see here :

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

viola

---

