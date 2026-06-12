---
title: "Small problem....How do I run this?"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-07-13
Ok...I got this file 
"tremulous-1.1.0-installer.x86.run".

How do I install it?
And how do I uninstall it once its installed?

---

### Post by digby on 2006-07-13
To run it, try sh tremulous-1.1.0-installer.x86.run  - if that doesn't work, run it as root (sudo sh tremulous-1.1.0-installer.x86.run).  As for uninstalling it?  You'll have to check the documentation, or ask someone w/ more familiarity with that program.

---

### Post by jayemef on 2006-07-13
You may also need to make it executable, which can be done with
```
$ chmod +x tremulous-1.1.0-installer.x86.run
```

---

### Post by geokok1981 on 2006-07-13
I got it in with sudo sh command....
But I cant find anything on the website on how to remove it...
Anyone???
Isnt there a standard procedure to do that?

---

### Post by geokok1981 on 2006-07-13
I found in their forums that there is an uninstall script in
usr/local/games/tremulous and that it uses the info in a .loki directory to do that.

I clicked on the file, I tried sudo sh command again from terminal but nothing. In terminal it says 
"Could not find a usable uninstall program. Aborting."

The script has no extension (ie .run like the install program did).

Any ideas on how to run the script?

---

### Post by geokok1981 on 2006-07-14
Perhaps if I just delete the files in :
usr/local/games/tremulous directory and deleting the /usr/local/bin/tremulous symlink that were created during install??

I know this is not an ubuntu issue only but I cant get help any place else for the time being.

---

