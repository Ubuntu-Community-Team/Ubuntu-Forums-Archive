---
title: "URGENT! Need help making a script!"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by __a on 2005-12-21
Hi everyone, I would really appreciate if someone could tip me off..

I want to make a simple script or something that writes the current time to a log every fifteen minutes or so.

Its for a school experiment; I need to know if/when the computer crashes - if it crashes during the christmas holidays... :)

I was thinking if there is some easy way to run a code like this every fifteen minutes..
```
$ uptime > log.txt
```

I know this info can probably be found by seraching a bit more, but as said, im in a bit of a panic.. If someone can help me, I promise to post some images of the experiment which includes an aquarium, a computer and a lot of oli! (don't worry about the HD -it's is safe :)))

Thanks in advance!

---

### Post by ow50 on 2005-12-21
The script could look something like
```
#!/bin/sh
date +%Y-%m-%d--%H.%M.%S >> ~/LOG
```

To have it running at some intervals, read the cron HOWTO
[http://www.ubuntuforums.org/showthread.php?t=102626&highlight=cron](http://www.ubuntuforums.org/showthread.php?t=102626&highlight=cron)

---

### Post by ubuntumaneh on 2005-12-21
If you want something to be done periodically you can use cron. See the following:

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

or the man page "man cron" and "man crontab".

Now, I quite sure somewhere I don't remember there will be a log file with the information you want. Look at /var/log/, anyway.

edit: /var/log/user.log.0, also user.log.1.gz ..., and messages.0 .... Digging in these files you can gather the information you are after

---

### Post by __a on 2005-12-21
OK, thank you very much!

Did a little test - result:

I'll just add this to crontab
```

0,15,30,45 * * * * uptime >> /home/username/uptimelog.txt
```

Incredibly fast help.. thanks again, I'll just have to dig out my camera (from wherever it's at) and upload som pictures then ;)

---

### Post by nitricacid on 2005-12-21
just use the Snapshot app on your someputer.

---

