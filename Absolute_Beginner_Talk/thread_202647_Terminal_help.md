---
title: "Terminal help"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by watto_one on 2006-06-23
Since updating to Dapper my terminal screen now shows the following
[COLOR="Red"]bash: gpg-agent: command not found[/COLOR]
bash: source: /home/peter/: is a directory
peter@watto:~$
Is there anything wrong here, and if so can it be fixed.

Thank you 
Peter

---

### Post by aysiu on 2006-06-24
Maybe [make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install gnupg-agent
``` might work?

Or even just ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by watto_one on 2006-06-25
Thank you for your reply. I have followed your directions and the message has now changed to.
bash: source: /home/peter/: is a directory
peter@watto:~$

As I said earlier I'm not sure if it made any difference, but it looks better not to have an error message.

---

