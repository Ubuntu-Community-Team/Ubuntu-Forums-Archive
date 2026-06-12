---
title: "[SOLVED] Everything works... How do I keep it this way?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-03-27
I know this is probably very unlikely, but it seems that I have all of the options I want functioning properly. 
What do I need to do to 'lock' it? I know about shutting off the auto-update manager. but is there something else I can do to keep it this way? (This is the first time in two years that I have everything functional at the same time.)

Any suggestions would be appreciated!

EDIT:
Solved in post # 6 He gave me this link: 
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

Thanks Tews!

---

### Post by jpkotta on 2008-03-27
Most settings are in /etc, so you could do
```
sudo tar jcf etc-$(date +%F).tar.bz2 -C / etc
```
This creates a tar archive of /etc that is named after today's date.

The almost all of the rest are in your home directory, in hidden directories and files (they begin with a dot (.)).  You should probably be backing up your home anyway, since that where all of *your* data is.

---

### Post by dmizer on 2008-03-27
how about making a complete backup of the machine: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

that way, you can continue to get updates and if anything breaks, you have a good base to restore to.

---

### Post by Papa-san on 2008-03-27
Thanks guys. I'll start those tomorrow!

---

### Post by cisforcojo on 2008-03-27
Hahaha, this thread is hilarious.

He brings up a good point though. It'd be an incredible feature if Ubuntu could get system "restore points". I've thought about setting up a system to back up my computer and compress it periodically but ... thinking is about as far as I've gotten.

---

### Post by Tews on 2008-03-28
Actually, there is an easy to do this now.  Quick-Start is a little program that allows you to backup/restore your system quickly.  It was developed specifically for Ubuntu.  Read about it here ..[http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by cisforcojo on 2008-03-28
Nice! Thanks for the app!

---

