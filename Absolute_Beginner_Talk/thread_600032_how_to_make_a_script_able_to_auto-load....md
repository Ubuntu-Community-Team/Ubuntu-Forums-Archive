---
title: "how to make a script able to auto-load..."
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-11-01
Before, I wrote an rsync script. It's just a simple thing in text editor. 

sudo rsync -a --delete --progress ~/ /media/Backup1

Well, before when I'd go to terminal I'd type "sudo backup" and it'd just run. Backup was the name of the script then.

Now that I have two hard drives I figured I'd make two scripts. One called Backup1, the other Backup2. Both of them yield "command not found."

It was recommended to me originally to keep the scripts in my /usr/local/bin folder, so they are there this time as well.

Maybe I forgot a step, but I can't figure out how to get the scripts to work by typing "sudo Backup1" in terminal...

---

### Post by taurus on 2007-11-01
Is /usr/local/bin in your path?  What is the output of this command from a terminal?

```
set
```
Also, make sure they both have an executable permission.

---

### Post by Roasted on 2007-11-02
Did you want the output from the directory /usr/local/bin or just with a freshly opened terminal? They seem really long so I figured I'd wait so I only post one.

---

### Post by brennydoogles on 2007-11-02
> **Roasted said:**
> Did you want the output from the directory /usr/local/bin or just with a freshly opened terminal? They seem really long so I figured I'd wait so I only post one.

Make sure to run ```
sudo chmod+x /usr/local/bin/backup1 /usr/local/bin/backup1
```
to give each script executable permission, and I suspect your problem will be fixed.

---

### Post by Roasted on 2007-11-02
It says command not found, but what you just said to me sounds familiar.

---

