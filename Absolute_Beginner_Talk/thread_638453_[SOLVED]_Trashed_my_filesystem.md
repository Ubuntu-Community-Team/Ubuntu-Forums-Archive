---
title: "[SOLVED] Trashed my filesystem ?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Silvain on 2007-12-12
Directory fails to change from terminal , always get no such directory exist, currently I am unfamiliar with the Ubuntu file directory hierarchy.Still did manage to change it earlier today.Later it fails to change.  I have looked up the Ubuntu directory change commands but still no positive results. Is it possible that I have managed to trash my directory structure? :confused:

---

### Post by shadow-of-sin on 2007-12-12
You use the "cd" command to change directories in Linux. Also, remember that path names are case sensitive in Linux.

And I highly doubt you trashed your directory structure.

---

### Post by Rocket2DMn on 2007-12-12
Use the command "ls -l" to see what is in your directory - if the very first character on the line is a "d" then it's a directory.  If you trying to change to a directory starting in the root of the file system (say navigate to the /media folder), you would type
```
cd /media
```
To get to your home directory you can type
```
cd /home/(yourusernamehere)
or just
cd ~
```

I'm sure your fileysystem is intact
Check out [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by el escocés on 2007-12-12
> cd /home/(yourusernamehere)
or just
cd ~

Even easier:

```
cd [ENTER] 
```

---

### Post by Silvain on 2007-12-12
Problem solved! I was leaving the space off between the cd command and the / I was entering it like this cd/path . This is correct method

 cd"space here"/path. Thanks for the reply s :)

---

### Post by Silvain on 2007-12-12
> **Rocket2DMn said:**
> 
I'm sure your fileysystem is intact
Check out [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Thanks for that link, Rocket2DMn,  will have to get that one printed out :)

---

### Post by gubemton on 2007-12-12
You are but a fool!

---

### Post by thelatinist on 2007-12-12
Please set mark your thread solved so people don't think you still need help.

---

