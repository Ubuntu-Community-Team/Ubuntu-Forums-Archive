---
title: "Trouble installing Ubuntu while preserving Home"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by henrywm on 2007-07-16
I installed Ubuntu onto a computer which was using Fedora Core 6. I replaced all of the partitions except the one containing Home. I followed the instructions at [http://ubuntuforums.org/showthread.php?t=429023](http://ubuntuforums.org/showthread.php?t=429023)

Now I cannot access my old home directory, because I do not have the permissions.

---

### Post by mrgnash on 2007-07-16
Did you set the mountpoint as /home during your install?

---

### Post by Tomshaq on 2007-07-16
Is your username the same as it was before? actually, that might not matter, as i think UID is what determines it.
Did you try 
```
 sudo chown username /home 
```

---

### Post by henrywm on 2007-07-27
I did not reformat the home partition. I do not know if it was unmounted in the process. I used the same username.

---

### Post by Mornedhel on 2007-07-27
It is the UID that determines permissions, so unless you had exactly the same users, added in the same order, and FC managed them the exact same way, you have lost the rights to these folders.

Now, you can chown your /home/username folder back to you, as Tomshaq has pointed out, but unless you want to do this for every file, I'd recommend using chown -R (for recursive). The problem is you will change ownership for all the files, including possibly config ones that did not belong to you (unlikely in a /home/username folder, but can anyone confirm this ?).

And you may retain .hidden folders from FC that you do not need anymore.

---

### Post by DJiNN on 2007-07-27
> **Mornedhel said:**
>  And you may retain .hidden folders from FC that you do not need anymore.  Regarding the above which i feel is important..... I'm assuming here that you're now using a completely new & fresh /home dir?   If this is the case then why not just change the permissions of the whole (old) home dir, then copy ONLY the pertinent data that you really need, manually? ie: Thunderbird/Evolution stuff, Mozilla Firefox, gftp folder etc etc..... whatever you were using that is "Program specific" as in the above examples, should be OK (I've done it this way myself loads of times) and also you'll avoid the possible hassles of having files from the previous distro that may cause problems.    You can use the cli to change the permissions or just gksudo nautilus and do it from there.   DJiNN

---

