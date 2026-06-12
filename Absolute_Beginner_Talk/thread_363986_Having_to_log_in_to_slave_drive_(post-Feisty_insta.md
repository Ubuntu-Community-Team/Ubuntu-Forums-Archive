---
title: "Having to log in to slave drive (post-Feisty install)"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-02-17
Under Edgy I installed a slave internal hard drive, with a mount point in /mnt and a symbolic link in my Home folder. Now I've installed Feisty (not an upgrade - wiped Edgy entirely), and it detects the disk every time, but when I click on it Feisty asks me to login, saying only root or administrator has access. After that it appears on my desktop as "disk" (before that it was named by it's capacity in the Nautilus "sidebar").

Here's the thing... I kind of like having it on the desktop, and I like restricting access to it, should I one day add accounts for a co-worker, for example. What I don't like is having to log in every time i reboot. What's the best route for me here? Thanks in advance.

---

### Post by ricardisimo on 2007-02-23
Is there a way for me to chmod the entire slave hard disk? Would it look anything like this:
```
sudo chmod 700 '/media/disk'
```
That seems too simple, but who knows? You do, hopefully :)  Thanks in advance.

---

### Post by v8YKxgHe on 2007-02-23
If you're trying Feisty and posting in the Beginner section ... I highly suggest you don't use Feisty. Feisty is in heavy development and it **will** break, or loose all you're important files etc.

---

### Post by ricardisimo on 2007-02-23
Thanks for your concern, but it was Edgy that gave me problems, not Feisty. Any ideas on the hard drive question?

---

