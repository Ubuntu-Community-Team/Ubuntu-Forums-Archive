---
title: "How do I update this program?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by sdim on 2007-08-31
Dear friends

I have installed AVG free and all is well,but when I try to run UPDATE,it tells me I have no right to update it.Could it be that it requires anything with SUDO (meaning that it wants to be updated by the owner)? And how is that done?

Thank you for any views on the subject.

---

### Post by ronocdh on 2007-08-31
> **sdim said:**
> Dear friends

I have installed AVG free and all is well,but when I try to run UPDATE,it tells me I have no right to update it.Could it be that it requires anything with SUDO (meaning that it wants to be updated by the owner)? And how is that done?

Thank you for any views on the subject.
In order to run something as root (or "use sudo"), just add "sudo" before the command in the terminal. Example:
```
apt-get install vlc
sudo apt-get install vlc
```
That's it! Hope this is what you needed.

---

### Post by por100pre1 on 2007-08-31
It is a bug in AVG. I mentioned it in [this thread]("http://ubuntuforums.org/showthread.php?t=539791").

---

### Post by mocoloco on 2007-08-31
I'm not familiar with AVG for Linux, you may have better luck on their forums.  Just a couple of suggestions.  One, I try to stick to what I can get from the Ubuntu repositories, unless there's nothing there that does what I need, so in this case you could use one of the two in the repos, just go to Add/Remove and search for virus.
Two, you probably don't really need antivirus software because a) there are very few viruses for Linux, b) They couldn't do much to your system because of file permissions, and c) anything you download or get in an e-mail is NOT executable by default, so you can't accidentally execute a virus like you can very easily on Windows.

---

### Post by sdim on 2007-09-01
Thanks for all the answers.So,how can I remove AVG (installed it as a .deb package from their site)?

---

### Post by Steveway on 2007-09-01
If you used a .deb package then you can use Synaptic to remove it.
And if you really need an an antivirus-prog on your Linux-box then use ClamAV, it's one of the best for Linux.

---

### Post by Outrunner on 2007-09-01
If you installed it from a .deb file, I think(not really sure) that you can remove it from Synaptic(or Adept if you're on Kubuntu). Simply go into Synaptic and search for 'avg' and remove it.

EDIT: Hehe, I was too slow!

---

### Post by por100pre1 on 2007-09-01
I'm not sure, but try this and let me know:

```
sudo apt-get remove avg75fld
```

---

### Post by Malibu Illusion on 2007-09-01
Anti-virus has no place on Linux boxes unless they are serving content somehow to Windows machines.  Otherwise, they're basically redundant.

---

### Post by sdim on 2007-09-01
Thank you for all your answers.
To : por100pre1-->it really worked! Thanks.

To : Malibu Illusion-->What about downloading from potentially "dangerous" places?
                               Wouldn't you say we must be guarded against them?

---

### Post by por100pre1 on 2007-09-01
Glad to help. 8)

---

