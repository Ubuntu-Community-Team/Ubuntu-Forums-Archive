---
title: "How Can I Update Pidgin?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-16
Hello!
I have Pidgin 2.2.1, but there is the 3rd version available. How can I update my Pidgin and why the updater didn't update it automatically?
Thanks.

---

### Post by mikeyphi on 2008-02-16
> **Hoom@n said:**
> Hello!
I have Pidgin 2.2.1, but there is the 3rd version available. How can I update my Pidgin and why the updater didn't update it automatically?
Thanks.

Pidgin is not solely an Ubuntu program - thus when a new version is produced Ubuntu users have to wait until Ubuntu programmers port it into the correct format and store it in the repos.
The latest version is not yet in the reops which is why you can't automatically update.
If you wanted to take the risk  - you could visit the Pidgin website and download the latest but be aware it is not in Ubuntu format.

---

### Post by fatdadkev on 2008-02-16
At the moment it appears you need to remove the previous version before installing it.

There are three packages available at 

[http://www.getdeb.net/release.php?id=1867](http://www.getdeb.net/release.php?id=1867)

Here's how I did it.

Go to the Synaptic package manager and search for pidgin.

Mark "Pidgin" and "pidgin-data" for removal, it will advise its removing a libpurple0 file as well.

Download the three files - pidgin, pidgin-data and libpurple0

Install the pidgin-data file first (right click and open with the GDebi package installer)

Once pidgin-data is installed then right click on the new libpurple0 installer and install that, then do the same for pidgin.

Start pidgin and it should be working fine.

I did this and it took about 3 minutes from start to finish.

---

### Post by Hoom@n on 2008-02-16
Thanks, but will ubuntu put it to update? Or ubuntu will do that in 8.04? If they'll do that I prefer to wait, but if not I gonna install it. Will they?

---

### Post by LaRoza on 2008-02-16
> **Hoom@n said:**
> Thanks, but will ubuntu put it to update? Or ubuntu will do that in 8.04? If they'll do that I prefer to wait, but if not I gonna install it. Will they?

It may be updated during the updates you get. The repositories don't get them at the same time as the release. They have to be packaged, and I imagine, tested first.

I don't know how far they follow, but it could be an update sooner.

---

### Post by AndyCooll on 2008-02-16
> **Hoom@n said:**
> Thanks, but will ubuntu put it to update? Or ubuntu will do that in 8.04? If they'll do that I prefer to wait, but if not I gonna install it. Will they?
Well, it's unlikely to reach the repos for the current release, these usually remain frozen apart from security and important patch releases. Occasionally some apps may be included in backports, but not many.

It may well however be included as part of Hardy, assuming it made the cut before the development freeze (which I believe was earlier this week).

Apart from that it's easy to install, as mentioned in one of the posts above.

:cool:

---

### Post by nikoPSK on 2008-02-16
This might help you:

```
**Get Updates on New Releases with Release Notification**

 If you're a Pidgin die-hard, you'll definitely want to enable the Release Notification plug-in, which periodically checks for updates to Pidgin and alerts you whenever one is available.
```

Sorry, I don't have the link right now, it's most likely a default plugin.


---

### Post by Hoom@n on 2008-02-16
Thanks, but I've to say that the 3rd newer version of pidgin is avalable for download! Ok, I wait a bit and then install pidgin (+in hardy there aren't news apps. e.g. there are firefox2 and pidgin 2.2.1)

---

### Post by Ardrias on 2008-02-16
I've been running Pidgin 2.3.1 from Getdeb for... a long while, and there's no real problems with it. 

2.3.1 is also included in Hardy.

---

### Post by kevdog on 2008-02-17
If you want the greatest and latest -- you need to compile from source -- which is a great learning experience if you have never compiled a program before - and actually its very easy also.  Here are the instructions:
[http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin)

---

