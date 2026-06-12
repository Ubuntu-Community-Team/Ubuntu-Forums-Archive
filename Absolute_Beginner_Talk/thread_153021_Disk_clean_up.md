---
title: "Disk clean up"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-31
Ok so linux has a good file system that does not need defraged. But what about "junk" files? How do I sort through cookies and other juck to free up hd space?
Is there software for this?

---

### Post by Perfect Storm on 2006-03-31
Well, if you remove an application through apt-get or synaptic, it removes all the files it installed. Except the ones it might make in your home folder. Just open thte file browser select view tab and press show hidden files. There you can see if it saved some settings etc.
Eg: You uninstall gimp, then you might check /home/<username>/ and check for a folder called .gimp2.2 then delete this folder if you don't want to save the settings to later.

Firefox you just go into settings and clean cache etc.

If you want to clean all the packages you downloaded through apt-get or synaptic:
```
sudo apt-get clean
```

That's it and that's that ;)

---

