---
title: "Startup chaos"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-11-20
Hi,
Although I was using preferences > sessions to manage my startup programmes, certain programmes were not responding and starting, like avant navigator and one odd more.
Then I followed the instrunctions from this site:
> [http://ubuntuforums.org/showthread.php?t=587709](http://ubuntuforums.org/showthread.php?t=587709)
I removed the autostart from ~/.config. However in my case it was a directory rather than a file.
Now whenever I start gutsy I am provided with 2 terminals(everything else starts o.k. otherwise)
One terminal is in the .config directory i.e ~/.config/autostart: cursor
Other terminal in in my home directory i.e. ~/home: cursor.
How can I get rid of these 2 terminals to start everytime?
Thanks for any help

---

### Post by gupta_sumesh63 on 2007-11-20
bump!!

---

### Post by gupta_sumesh63 on 2007-11-20
No Help here?
Where do I go now?

---

### Post by por100pre1 on 2007-11-20
It was unnecessary to remove the whole ~/.config/autostart folder. Create the folder if it is no longer there and try checking for some weird entries in Sessions. If the problem persists check using Bootup Manager:

```
sudo apt-get install bum
```

Don't disable anything if you don't know what it is. Please don't bump the threads, I can't find unanswered posts if they are bumped.

---

