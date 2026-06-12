---
title: "Can not find synaptic on newly installed Ubuntu"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by MichaelontheFly on 2008-01-07
When i look under "system/Administration" on the tool panel, I do not see Synaptic...  Just installed 7.10.  Any info - advise would be appreciated.  I am trying to find packages - Update mgr comes up, but there are no new updates.

Thanks,
Michael

---

### Post by wolfen69 on 2008-01-07
run in terminal
```
synaptic
```
to see if it installed correctly. if it opens, go to system>preferences>main menu to add it to the admin menu.
if not installed, run in terminal:
```
sudo apt-get install synaptic
```

---

### Post by ellis rowell on 2008-01-07
It sounds like something is wrong with the installation, I would try reinstalling. It should be there.

---

### Post by MichaelontheFly on 2008-01-07
simple enough.  Looks like it's working now.  Thanks a lot.

Michael

---

