---
title: "Agent newsreader under Wine stopped working"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by bob12564 on 2008-03-15
I've been running Ubuntu for a few weeks and managed to install Wine from the Ubuntu repository.  I installed Agent Newsreader v1.93 under Wine and it was working very well up until yesterday when I accepted a large set of updates from the Ubuntu update manager.  Now when I try to run Agent, the Agent splash screen appears and then Agent disappears.  I assume this is the Linux version of a crash.  It's obvious that something in the update packages caused the problem.

I tried uninstalling Agent and reinstalling it, but the same thing happens.  I don't know if I want to bother trying to uninstall/reinstall Wine.  It's hard enough just trying to learn Ubuntu without having to figure out how to do that.

Has anyone else had a problem with the latest updates and packages running under Wine?

I need to hang onto Agent because it still is the best overall newsreader.  I've tried PAN but it needs more work before it can challenge Agent.  For one thing, I can't figure out how to get PAN to manually join multiple segments.  It can automatically join segments but sometimes it can't.  When I have that problem in Agent, I can manually join the segments.

Any help is appreciated, but please keep it simple because I'm still learning!

Thanks!

---

### Post by Xiong Chiamiov on 2008-03-17
It is quite possible that the recent Wine update broke that.  If you don't use Wine for anything else, you can downgrade to a previous version.  You should be able to do that by following (with slight modifications) the instructions in [this post]("http://ubuntuforums.org/archive/index.php/t-641065.html").  If that fails, we can of course lead you through compiling an old version from source (don't worry, it's not nearly as scary as it sounds!).

---

### Post by Oldsoldier2003 on 2008-03-17
> **Xiong Chiamiov said:**
> It is quite possible that the recent Wine update broke that.  If you don't use Wine for anything else, you can downgrade to a previous version.  You should be able to do that by following (with slight modifications) the instructions in [this post]("http://ubuntuforums.org/archive/index.php/t-641065.html").  If that fails, we can of course lead you through compiling an old version from source (don't worry, it's not nearly as scary as it sounds!).

or unless the OP is completely stuck on using that specific newsreader, he might want to check out some Linux newsreaders.: Pan comes to mind and there are somelinks to look at in this thread:
[http://ubuntuforums.org/showthread.php?t=512110](http://ubuntuforums.org/showthread.php?t=512110)

---

### Post by Xiong Chiamiov on 2008-03-17
He did say he tried PAN and didn't like it.

---

### Post by Oldsoldier2003 on 2008-03-17
> **Xiong Chiamiov said:**
> He did say he tried PAN and didn't like it.

yeah the Pan Beta is better but its not really the best advice to give a new user :)

---

### Post by bob12564 on 2008-03-21
"It is quite possible that the recent Wine update broke that. If you don't use Wine for anything else, you can downgrade to a previous version. You should be able to do that by following (with slight modifications) the instructions in this post. If that fails, we can of course lead you through compiling an old version from source (don't worry, it's not nearly as scary as it sounds!)."

--------------

I used the WINE version from the Ubuntu repository, which is not the latest version according to my understanding.  I'm also using an old version of Agent because other posts on these forums state that the new versions don't work with Wine.  I didn't notice any Wine updates in the package of updates sent by Ubuntu.  They seemed to be more core modules, some Evince modules, maybe some multimedia modules and things like that.  

I'm not using Wine for anything else, but I may in the future.  As good as the open source software may be, many aren't as good as I need for me to completely abandon Windows just yet.  If some Windows software will run under Wine, then maybe I can get more use out of Linux

I'm thinking of waiting for release 8.04 to see what happens with both Wine and Agent.  So for now, this thread is not resolved.  I know this is tough to diagnose.  I was hoping that someone else had a similar problem and may have determined the cause.

Thanks for all the replies!

---

### Post by Oldsoldier2003 on 2008-03-21
Bob, have you condiered installing virtualbox and running a copy of windows for your must have programs? VMs do a much better Job than wine except for gaming...

---

### Post by Dilligaf on 2008-03-21
I'm running Agent 4.2 in wine with no problems. I don't know where you read that newer versions wont work. I have a dual boot setup with Agent installed on a fat32 partition which is drive E:/ in windows. I mapped my drives in winecfg so that they have the same drive letters as windows, I can then browse to the Agent executable in Winefile and launch with no problems. I made a shortcut to launch Agent which looks like this....
wine "e:\Agent3\agent.exe" "e:\Agent3\Data"
The key was pointing the shortcut to the correct data folder. Agent installs all needed files within its directory and not in other windows folders this makes it portable by simply changing the paths in the .ini file. I do not know if Agent will handle drives with the sda, sdb, sdc notations but I suspect it won't thats why you have to map the drives in winecfg and use drive letters in the shortcut. I've had this setup running for about a year with no problems and many Wine updates, the current wine version I'm using is 0.9.57 which I think is the latest. The only issue I experience is a memory access violation when closing Agent but this has no affect on the program or it's database. I hope this is of some help to someone, any questions feel free to ask.

Mike

---

### Post by bob12564 on 2008-03-23
Mike and others,

You're doing exactly what I was doing and that's why it all worked...until I accepted some "recommended" updates from Ubuntu.  After the various updates installed Agent was hosed.

I did a search on "Agent" on the Ubuntu forums and there were posts that said the older versions of Agent worked better on Wine than the new ones.  I also understand that Ubuntu supports an older version of Wine but I used it because it is the "official" version supported by Ubuntu.  Besides, it worked!  

I'm not interested in a dual boot with Windows.  I have another computer running Windows so I have a production machine.  The second computer is dedicated to Ubuntu Linux as an experiment to see if I could make a clean break from Microsoft.  So far Linux has promise but I still need the Windows machine as far as I can see.

I'll research the Wine alternative that was suggested.

---

