---
title: "How to access permission denied folders with sudo command"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2006-12-15
How do you access folders that you don't have permission to with the sudo command?

For example, a folder called test that I am not a part of. I tried sudo cd /home/test but it said the command was not recognized. However I can do a sudo chmod and grant myself permission to it. Basically I want to see if there is a way like in windows with just having admin access to all folders or at least the sudo command to view folders as needed.

Thhanks.

---

### Post by bodhi.zazen on 2006-12-15
> **JohnnyAvocado said:**
> How do you access folders that you don't have permission to with the sudo command?

For example, a folder called test that I am not a part of. I tried sudo cd /home/test but it said the command was not recognized. However I can do a sudo chmod and grant myself permission to it. Basically I want to see if there is a way like in windows with just having admin access to all folders or at least the sudo command to view folders as needed.

Thhanks.

Root has such access.

If needed ```
sudo su
```

Enter commands needed as root.

Don't forget to ```
exit
``` when done.

There is a way to change the permissions of your files system wide, but I will not advise it or give it to you, most people regret it :(

---

### Post by hotbrainz on 2006-12-15
the commands in the above post will do the job. But if you want a fuller understanding, you might wanna read this:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")


Cheers

---

### Post by JohnnyAvocado on 2006-12-15
Thanks so much gents. I really appreciate it.

---

### Post by Ben Sprinkle on 2006-12-15
Try:
```

gksudo nautilus

```
Will run nautilus in root. ;)

---

