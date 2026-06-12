---
title: "wine error"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-15
whenever I run wine it displays this in the terminal window
```
wineserver: could not save registry branch to /home/user/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/user/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/user/.wine/user.reg : Permission denied

```
What might be the problem?

---

### Post by Ensnared on 2006-04-15
Well, since the errors say "permission denied", my first guess would be wrong permissions on directories and/or files ;) This might happen if you, say, ran Wine with sudo the first time, which means your .wine-directory and all its content is most likely owned by root.

To fix it, try this:
```
sudo chown user.user /home/user/.wine -R
```

Where 'user' in all cases is, of course, your username.

---

### Post by rameez on 2006-04-16
Now I am having another problem, I am trying to run a game and it starts it and then says cannot find file Data/xx.x although the data directory is there and the files are there, I have noticed that wine is not accessing files in subdirectories.
Can someone please help me with this.

Thanks.

---

### Post by htinn on 2006-04-16
Looks like you ran winecfg/winetools as root. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=28097](http://www.ubuntuforums.org/showthread.php?t=28097)

---

### Post by rameez on 2006-04-16
I got the root problem figured out now the problem is:
I am trying to run a game and it starts it and then says cannot find file Data/xx.x although the Data directory is there and the files are there.

---

### Post by htinn on 2006-04-16
Which game? You should probably check this out:

[http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php)

---

