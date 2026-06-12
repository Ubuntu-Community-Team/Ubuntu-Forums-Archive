---
title: "Glipper error on startup"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by bcasanov on 2008-04-19
Hi, 

I have an error that pops up every time I start up.  The error is: > The panel encountered a problem while loading "OAFIID:Glipper".
It then asks me if I want to delete the applet from my configuration.
What can I do to fix this so that I am not annoyed with it every time I start up?  I have no particular plugins enabled.  I am using Ubuntu Hardy Heron.

---

### Post by linfidel on 2008-04-20
Glipper isn't added directly to the panel, it's run on startup in the Sessions control panel (menu - System/preferences/sessions).  So, you should go to that, and find the entry, press the Edit button, and see what it says.

Mine says:
Name:  Glipper
Command:  /usr/bin/glipper
Comment:  Clipboard Manager

If you don't see anything obvious, then you can remove it, and add it back.  Or, try running it from a terminal (/usr/bin/glipper).

---

### Post by sayakb on 2008-04-20
Select Delete applet and it will be removed. Delete applet doesnot delete it from the drive but removes it from the panel.

---

### Post by linfidel on 2008-04-20
> **LinuxIsInnovation said:**
> Select Delete applet and it will be removed. Delete applet doesnot delete it from the drive but removes it from the panel.
glipper isn't actually a panel applet. :(

---

### Post by bcasanov on 2008-04-20
Actually, when I right-click on the panel and go to Add to Panel, Glipper is listed as an applet to add to the panel, under the name of Clipboard Manager.  I had installed Glipper in Gutsy, and I think in Hardy, Glipper has become an applet.

---

### Post by linfidel on 2008-04-20
> **bcasanov said:**
> Actually, when I right-click on the panel and go to Add to Panel, Glipper is listed as an applet to add to the panel, under the name of Clipboard Manager.  I had installed Glipper in Gutsy, and I think in Hardy, Glipper has become an applet.
Damn, I'll bet someone went back in time and added it just to make me look bad! :)

Sorry.  Looking back at the original post, I guess this was a Hardy error.  Perhaps removing
it, then adding it back will fix it.  Or, running it the old way, assuming it runs from a command line.

---

### Post by bcasanov on 2008-04-21
Hi linfidel,

I tried removing it from the panel and then adding it back in, but still, oddly, the error keeps coming back up.  When I input "glipper" in the console, it says that it is not a valid command.

---

### Post by matthias_k on 2008-04-22
I can confirm this bug for Hardy RC.

Deleting and re-adding the glipper applet does not help.

And no, glipper can no more be run from the command line, as there is no glipper exe in /usr/bin.

---

### Post by matthias_k on 2008-04-22
See [https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/181435](https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/181435)

they say it is fixed by removing and re-adding the applet. I'm pretty sure I already did this and it just crashed again. I'll run it a few more days before reopening the bug report.

---

### Post by matthias_k on 2008-04-23
Can now definitely confirm that removing and readding the applet does not resolve the problem. I have reopened the bug on Launchpad as unresolved.

---

### Post by bcasanov on 2008-04-24
Thank you, matthias_k!

---

### Post by muadnu on 2008-04-28
I've been suffering the same since upgrading to Hardy beta. But now I found Parcellite, which does the same (I think it does not have all the features of Glipper, but the basic clipboard managing works, which is the only thing I need). Simply install it from the repositories. It is not a panel applet, it needs to be run on startup.

---

### Post by vitamin on 2008-04-29
I had the same problem with Glipper, it became an panel applet, but I was not able to add it on my panel. I resolved the issue by deleting the .glipper from my home directory. Then after logging off and on I was able to add it to the panel and since then no problems so far.

---

### Post by matthias_k on 2008-04-29
> **muadnu said:**
> I've been suffering the same since upgrading to Hardy beta. But now I found Parcellite, which does the same (I think it does not have all the features of Glipper, but the basic clipboard managing works, which is the only thing I need). Simply install it from the repositories. It is not a panel applet, it needs to be run on startup.

I believe it is not in any of the official Hardy repositories though?

---

### Post by muadnu on 2008-04-29
I think I installed it from the repositories. It is in getdeb.net in any case [http://www.getdeb.net/app/Parcellite]("http://www.getdeb.net/app/Parcellite").

I figured out now, though, that Parcellite doesn't save the "select - mark/middle mouse button" clipboard as Glipper does, which makes it much less useful, at least to me.

---

### Post by bcasanov on 2008-04-29
> **vitamin said:**
> I had the same problem with Glipper, it became an panel applet, but I was not able to add it on my panel. I resolved the issue by deleting the .glipper from my home directory. Then after logging off and on I was able to add it to the panel and since then no problems so far.

I deleted glipper from the panel, and tried your solution just now, and when I restarted and logged in, the same error still appears, unfortunately.

---

### Post by Mangust22 on 2008-05-04
It seems like it isn't glipper's bug. At first login (first start Hardy) glipper crashs. And gnome layout switcher don't work correctly too. Just: log out & log in - all work fine. I think it's new gnome bug is, not glipper or layout switcher.

---

### Post by matthias_k on 2008-05-04
> **bcasanov said:**
> I deleted glipper from the panel, and tried your solution just now, and when I restarted and logged in, the same error still appears, unfortunately.

+1

didn't work for me either.

---

### Post by speedsix on 2008-05-05
I get this error I'd say 50% of every start up. Removing and re-adding doesn't help.

---

### Post by cszikszoy on 2008-05-08
> **speedsix said:**
> I get this error I'd say 50% of every start up. Removing and re-adding doesn't help.

I can confirm this.  Removing ad re-adding makes no difference.  Glipper still crashes on startup.  Hope this can get fixed because deleting and re-adding glipper every time I start a new session is not what I'd call a "solution".

---

### Post by gcastell on 2008-06-01
> **cszikszoy said:**
> I can confirm this.  Removing ad re-adding makes no difference.  Glipper still crashes on startup.  Hope this can get fixed because deleting and re-adding glipper every time I start a new session is not what I'd call a "solution".

I found a solution [here]("https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/213494")

Basically it seems that glipper starts before a service it needs but by adding a delay before it starts (8 secs was enough for me) allows it to start without a problem. :)

Gabriel

---

### Post by nrayever on 2008-06-28
> **gcastell said:**
> I found a solution [here]("https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/213494")

Basically it seems that glipper starts before a service it needs but by adding a delay before it starts (8 secs was enough for me) allows it to start without a problem. :)

Gabriel

i will try this solution, glipper is a great app...let xD!! feedback until next reboot!

UPDATE

Thanks gabriel it worked, ok!

---

