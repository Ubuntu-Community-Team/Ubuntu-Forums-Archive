---
title: "HFS+ Disk Permissions Issue"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by Arnie Tchelakian on 2009-01-05
So I'm using a regular PC running 8.10, and I took my old HFS+ formatted drive out of my old PPC Mac / setting it as a slave drive / and plugged it into the extra IDE plug on my motherboard. Start up in Ubuntu; running off of a USB drive, and I can see my old Mac files perfectly. It mounts and I can navigate around in there fine.

Only problem is actually opening the various files themselves (like video or music) or trying to copy to my Ubuntu drive.

I think it may just be a permissions thing?

I've been poking around the forums looking for someone with a solution to this problem, anyone know what I need to do here?

Thanks.

---

### Post by tiresia on 2009-01-05
```
gksudo nautilus
```

---

### Post by bryonak on 2009-01-05
> **tiresia said:**
> ```
gksudo nautilus
```

After hitting Alt+F2


Yay, nitpicking! ;D

---

### Post by Arnie Tchelakian on 2009-01-05
You both saved the day! Whoo !! :)

---

### Post by bryonak on 2009-01-05
You're welcome... but it's not all peachy.

This command lets you browse the files as super user (administrator), so after you copy them over, these copies will belong to the super user.
Which means that your normal user (when opening nautilus without gksudo) will be able to read the files, but not move or rename them.

Now Nautilus in super user mode supports changing the owner of a single file (right click -> Properties -> owner), but not of a bunch of folders and files. This will hopefully get fixed in future.
Now you can either open a normal Nautilus and copy those files already copied to a new location, where they will be created fully under your users control, which is kind of cumbersome... or use the terminal to change the ownership (chown) of those files.
If you are uncomfortable with the terminal, the first approach is probably the "simplest". Otherwise, just ask ;)

---

### Post by Arnie Tchelakian on 2009-01-07
wow thats terrific, so is it then possible to simply "chown" my entire mac home directory?, or even the whole disk?? and never again have to worry about sudo'ing again???

---

### Post by cyberdork33 on 2009-01-07
> **Arnie Tchelakian said:**
> wow thats terrific, so is it then possible to simply "chown" my entire mac home directory?, or even the whole disk?? and never again have to worry about sudo'ing again???

I would copy the files off, reformat the external to a filesystem that is mor compatible with Linux, then copy things back. Then you don't have to worry about dealing with HFS+ and permissions.

Anyway, unless you turned off journaling, you can't write to HFS+ partitions anyway, and that means you cannot edit permissions.

---

### Post by bryonak on 2009-01-07
You could, however I don't know how that will affect the HFS+ system... maybe you wouldn't be able to boot it again with OSX.
Try to change the ownership of a single file on the HFS+ partition and see how it works out.
Chances are that you can't even write to HFS+ if it's journaled (you can if the journaling has been turned off when the partition was formated). One option would be to copy everything over, reformat the drive with ext3 and then store the things back.

There's a [nice looking script]("http://ubuntuforums.org/showthread.php?t=925121") which allows you to change the owner from within a normal user's Nautilus. I haven't tested it though.
You can use it if you want to copy the files to your partition (with super user Nautilus) and quickly change the ownership.


EDIT: cyberdork's on the fast lane :D

---

