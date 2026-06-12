---
title: "Cannot Log In"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-01-03
Last time, my computer froze so I had to force a shut down.

However, now, when I attempt to log in. I give my username and password. The screen flickers, and I am back to the welcome screen. I cannot log in! What should I do?

Also, I can access shared files though Windows XP on that computer using this login user and password.

---

### Post by taurus on 2007-01-03
Boot into the recovery mode from GRUB menu and paste the output of this command here.

```
df -h
```

---

### Post by amitroy5 on 2007-01-03
Filesystem		Size	Used	Aval	Use%	Mounted On
/dev/hda2/		75GB	73GB	0	100%	/

I won't list the rest. But I think I know what the culprit is. It has to do with using up all the space on the hard drive. How do I delete files on UbuntU?

---

### Post by taurus on 2007-01-03
Yip.  You ran out of space.  So, boot into recovery mode again and at the prompt, do some house cleaning with

```
aptitude clean
cd ~/.Trash
rm *
df -h
```

---

### Post by amitroy5 on 2007-01-03
Yup! That did the trick! This usually happens if you download a lot of torrents. I guess time to get a larger hard drive. Thank you so much!

---

### Post by taurus on 2007-01-03
Get a larger harddrive or clean out the torrent files more often...

And you're welcome.

---

