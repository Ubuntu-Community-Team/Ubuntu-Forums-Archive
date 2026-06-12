---
title: "[SOLVED] Problem updating azureus"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2007-11-21
Hi people!

I install azureus a few minuites ago following a guide from the ubuntu forums. I download it from azureus site and installed it following the gude. Every time azureus start it prompts me to dowload an update but after i download it i get the following message:

```
Downloading: [http://torrents.aelitis.com:88/torrents/azupnpav_0.1.7.zip.torrent: torrent,http://azureus.sourceforge.net/plugins/azupnpav_0.1.7.zip]
      Downloading: azupnpav_0.1.7.zip
Torrent download complete
Installing plugin azupnpav, version 0.1.7
    Data verification stage complete
Version 0.1.7 of plugin 'azupnpav' failed to install - /opt/azureus/plugins/azupnpav/azupnpav_0.1.7.zip (Permission denied)

```

as you can see azureus is downloading a .zip file witch i think is the problem. Does anybody know how to fix this???

---

### Post by MrFSL on 2007-11-21
Please post a link to the guide you followed.

It appears that you might be able to change some permissions to get it to work.

---

### Post by MeanderingCode on 2007-11-24
> **G. Cotgreave said:**
> as you can see azureus is downloading a .zip file witch i think is the problem. Does anybody know how to fix this???

Linux handles zip files just fine with most of the major archiving programs.

I encountered this problem, too, a while back and am running into it again, so found your post while looking for a solution.

The reason is because you are running azureus as your user, not root, and the update is trying to install in azureus' folder under the /opt directory, in which your user does not have write permission.

When i find the method of updating, i will check back here and post those findings.

---

### Post by MeanderingCode on 2007-11-24
I, as well as Mr.FSL, am curious about which guide you used.

I just found and succeeded with [this]("http://ubuntuforums.org/showthread.php?t=529431") one.

If you encounter errors like the one you describe above:


> ```
Downloading: [http://torrents.aelitis.com:88/torrents/azupnpav_0.1.7.zip.torrent: torrent,http://azureus.sourceforge.net/plugins/azupnpav_0.1.7.zip]
      Downloading: azupnpav_0.1.7.zip
Torrent download complete
Installing plugin azupnpav, version 0.1.7
    Data verification stage complete
Version 0.1.7 of plugin 'azupnpav' failed to install - /opt/azureus/plugins/azupnpav/azupnpav_0.1.7.zip (Permission denied)
```

but instead of /opt/ , it mentions your ~/.azureus folder (this happened to me, don't know how), do this:```
sudo chown -R <username>:<username> ~/.azureus
``` and restart azureus.

Let us know if you get your problem solved!!

---

### Post by G. Cotgreave on 2007-11-24
I cannot remember the guide i used but i found it in the forum somewhere (please don't ask where!!!) I tried the code you gave me but i still get the same message:( What if i log as root and try to update it as root would that work?

---

### Post by Majorix on 2007-11-24
You pointed in the correct direction. That would most likely work. Please try and update us.

---

### Post by G. Cotgreave on 2007-11-24
Yes it worked!!!! Thank you all for the help!!!

---

### Post by jonnyalpha on 2007-12-06
> **MeanderingCode said:**
> I, as well as Mr.FSL, am curious about which guide you used.

I just found and succeeded with [this]("http://ubuntuforums.org/showthread.php?t=529431") one.

If you encounter errors like the one you describe above:




but instead of /opt/ , it mentions your ~/.azureus folder (this happened to me, don't know how), do this:```
sudo chown -R <username>:<username> ~/.azureus
``` and restart azureus.

Let us know if you get your problem solved!!

Worked for me. :)

---

