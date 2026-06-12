---
title: "Torrent--&gt;another drive"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Inhumane on 2006-09-04
Hey, is it possible to start downloading a torrent and then transfer it to another drive on the same computer once it is finished?
My current setup is this: 1 drive dedicated to windows, which is the main OS ATM, and a second drive dedicated just to Ubuntu.. Would it be possible to start downloading some torrents over at Ubuntu, but once they are finished access the windows drive and transfer the files there?

---

### Post by taurus on 2006-09-04
You use the "mv" command to move files around...  Let's assuming that you have filename.txt in ~/Desktop and would like to move that to ~/temp, then open a terminal and type

```
mv ~/Desktop/filename.txt ~/temp
```

---

### Post by jISh on 2006-09-04
Sure, why not? 
You could even download half of the torrent, move it over to the other drive, and resume it!

---

### Post by Inhumane on 2006-09-04
> **taurus said:**
> You use the "mv" command to move files around...  Let's assuming that you have filename.txt in ~/Desktop and would like to move that to ~/temp, then open a terminal and type

```
mv ~/Desktop/filename.txt ~/temp
```

Yeah, but doesn't that just move it to the same drive? The reason I'm asking is becuase I can't access my Linux drive through Windows, when I go to my computer and try accessing D: (the linux drive), it simply shows up as empty, so I thought it might be impossible as they are different formats or something

---

### Post by taurus on 2006-09-04
That IS just an example...  You can sub in whatever destination you want to!!!  :rolleyes:

```
man mv (for more info...)
```

---

