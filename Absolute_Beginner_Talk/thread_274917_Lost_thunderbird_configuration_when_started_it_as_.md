---
title: "Lost thunderbird configuration when started it as sudo"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-10-10
I wanted to check for updates in thunderbird but saw the option was grayed out. I solved this by starting thunderbird as sudo from the shell. 
However now when I start up thunderbird again I does not detect my profile anymore. I thought that it probably changed the ownership of some files so I did a chown -R on all files in my .mozilla-thunderbird folder but that did not help. How can I get my thunderbird working again?

---

### Post by Kateikyoushi on 2006-10-10
Maybe it created a new profile.
Try to start the profile manager to check it.

```
mozilla-thunderbird -profilemanager
```

---

### Post by lorre on 2006-10-10
thnx creating a new profile and moving some files solved it. Hope I don't have to do this everytime i want to 'check for updates'.

---

### Post by aysiu on 2006-10-10
Make sure you launch it with this command next time: ```
gksudo thunderbird
``` instead of ```
sudo thunderbird
``` More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lorre on 2006-10-10
thnx will do.

---

