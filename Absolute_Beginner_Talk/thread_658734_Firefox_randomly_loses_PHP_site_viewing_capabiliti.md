---
title: "Firefox randomly loses PHP site viewing capabilities"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Godmatik on 2008-01-05
I have no idea what is going on, but on certain websites I go to I can browse fine for 5 minutes, and then all of a sudden firefox wont let me click on any links. Links that would have brought me to a page before now firefox suddenly tries to download them and open them in an empty txt file. If i close firefox and restart it and clear the cache I can get another 5 minutes of web browsing before it craps out on me again, what do I need to do to fix this?

---

### Post by oliviacond on 2008-01-05
try Firefox 3, less memory usage.
[http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html](http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html)

(latest firefox 3 is beta 2, download it [here]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b2/linux-i686/en-US/firefox-3.0b2.tar.bz2"))

---

### Post by Godmatik on 2008-01-06
> **oliviacond said:**
> try Firefox 3, less memory usage.
[http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html](http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html)

(latest firefox 3 is beta 2, download it [here]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b2/linux-i686/en-US/firefox-3.0b2.tar.bz2"))

Ok I went into synaptic, marked my old version of firefox for complete removal and marked firefox 3.0 for installation. I installed 3.0 (now called granparadiso apparently) and restarted my computer just to be safe. After a few minutes of browsing the SAME problem occured. What exactly is causing this and how can I get rid of it? The only site that seems to be causing problems for me is waffles.fm. Then again I don't spend any time on any other php sites so it could be the fact that this is the only php site I browse. PLEASE help me fix this it is driving me insane. Clearing the cache doesn't always seem to work and I have to restart my computer constantly if I want to browse a website. PLEASE PLEASE HELP! :(

---

### Post by oliviacond on 2008-01-06
what about alternative browser? sorry, i donno what's wrong with your firefox.

Swiftweasel (optimized version of firefox)
Opera

---

### Post by louieb on 2008-01-06
Don't think the page being php has anything to do with the problem.  When a browser request a .php page - the php code runs on the server and writes html which is then sent from the server to the browser.  The browser does not care - html - php its all the same to the browser. 

Just a shot in the dark - wondering if your not running out of disk space. To check run ```
df -h 
```

---

### Post by Godmatik on 2008-01-06
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G   50G   85G  37% /
varrun               1014M  208K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   92K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile


85 gigs left that should be enough to view web pages I hope :(

---

### Post by Godmatik on 2008-01-06
I ran the error console until the problem started again and this is the error I get.

Error: [Exception... "'Component is not available' when calling method: [nsIHandlerService::getTypeFromExtension]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  location: "<unknown>"  data: no]

---

### Post by Godmatik on 2008-01-08
Anyone know what the above error means?

---

