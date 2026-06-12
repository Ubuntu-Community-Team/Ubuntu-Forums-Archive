---
title: "Permission and ownership issues"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by clinto on 2007-08-18
THIS WAS ORIGINALLY A RESPONSE TO ANOTHER THREAD

Well, you know you can get more information on certain commands by putting "man" or "info" in front of it, right? I did info chown and found this in the examples:
```
chown -hR root /u
              Change the owner of /u and subfiles to "root".

```

I'm just having a hard time trying to figure out how to change all the files' owners under a certain directory.

I used **sudo nautilus** to edit the permissions(since I'm an amateur to all this), and in the permissions tab, there is a button to apply all permissions to sub files. However, when I did this, it applied the "root" as owner, instead of my account. Now, only root can even access those files. I'm trying to find a way to change the owner for all those files.

Also, I have a shared directory that I would like to allow all users to access. I was thinking that I would change the owner to "all," but just realized that this doesn't make sense, since their isn't a user called "all." I guess I could give the directory into my ownership and just change it's permissions to allow all to read/write to it. Right?

---

### Post by aysiu on 2007-08-18
**Correction** ```
gksudo nautilus
``` is the proper command, not *sudo nautilus*

**Fix change of ownership to root**
To change ownership back to user from root, type ```
sudo chown -R clinto:clinto /path/to/folder
``` The *-R* should be capitalized.

**Permissions on a shared directory**
If you want a directory to be accessible to all, make its permissions read/write/execute for everyone: ```
sudo chmod -R 777 /path/to/folder
``` If that doesn't work, try [this](http://ubuntuforums.org/showpost.php?p=832721&amp%3bpostcount=9).

---

### Post by clinto on 2007-08-18
So I would use...
```

sudo chown -uR clinto:clinto /path/to/folder

```
...if I wanted to apply this permission to all files and directories underneath this directory. Correct? The following out of the same man page confused me...
```

 -h, --no-dereference
              affect each symbolic link instead of any referenced file (useful only on systems that can change the ownership of a symlink)

```

Thanks aysiu!

---

### Post by Ek0nomik on 2007-08-18
> **clinto said:**
> So I would use...
```

sudo chown -uR clinto:clinto /path/to/folder

```
...if I wanted to apply this permission to all files and directories underneath this directory. Correct? The following out of the same man page confused me...
```

 -h, --no-dereference
              affect each symbolic link instead of any referenced file (useful only on systems that can change the ownership of a symlink)

```

Thanks aysiu!

The -h argument, if I am not mistaken will simply change the symbolic link in your directory specified and not the actual file the symbolic link is pointing to.

Chown:  [http://www.opengroup.org/onlinepubs/000095399/utilities/chown.html](http://www.opengroup.org/onlinepubs/000095399/utilities/chown.html)

Symbolic Links:  [http://www.tdl.com/~netex/linux-doc-project/install-guide/node131.html](http://www.tdl.com/~netex/linux-doc-project/install-guide/node131.html)

---

