---
title: "Delete in terminal"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by mspainter on 2007-08-01
I was wondering how to delete something in terminal. 

Say I want to delete folder, /home/matt/example, what do I type into terminal, (tty1), to delete the folder and its contents?

---

### Post by Kingsley on 2007-08-01
```
rm -rf /home/matt/whatever
```

---

### Post by kevinlyfellow on 2007-08-01
rm (remove) is the command to delete something
rm -r can delete a folder

USE THIS CAREFULLY, ONCE SOMETHING IS DELETED THIS WAY, IT IS GONE FOREVER!!!

---

### Post by mspainter on 2007-08-01
> **kevinlyfellow said:**
> rm (remove) is the command to delete something
rm -r can delete a folder

USE THIS CAREFULLY, ONCE SOMETHING IS DELETED THIS WAY, IT IS GONE FOREVER!!!

Good haha. If you saw my other thread, you would see that I can't even log in to my computer because GDM is messed up. But I hope to delete my America's Army files and I should be able to log on.

---

### Post by kerry_s on 2007-08-01
> **mspainter said:**
> I was wondering how to delete something in terminal. 

Say I want to delete folder, /home/matt/example, what do I type into terminal, (tty1), to delete the folder and its contents?

you should install "mc" mc is a council file manager, it makes working in terminal easy and fast.> sudo apt-get install mc

[http://www.ibiblio.org/mc/images/mc-panels.png](http://www.ibiblio.org/mc/images/mc-panels.png)
[http://www.ibiblio.org/mc/images/mc-edit-perl.png](http://www.ibiblio.org/mc/images/mc-edit-perl.png)

---

### Post by eheyl on 2007-10-28
I deleted realplayer using this method now how do I get the entry out of the Sound and Video section of Ubuntu?

---

### Post by 5-HT on 2007-10-28
> **eheyl said:**
> I deleted realplayer using this method now how do I get the entry out of the Sound and Video section of Ubuntu?

Let the package manager...ummm....manage your packages! Realplayer will not be a single file, did you only delete the executable? Best is to reinstall and let your package manager take care of removing the application or remove all traces of it manually. To get rid of the entry use alacarte, but there's probably plenty left of the package on your system still.
cheers,

---

### Post by eheyl on 2007-10-28
you mean Synaptic? I looked and it didnt; find anything::??

---

