---
title: "Fat32 priveledges, interfering with running apache [403 forbidden]. please help?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Pizzarth on 2007-11-15
Hello, thanks thanks for looking.

I'm running an apache2 server, with the latest stable packages AFAIK.

Although I doubt the problem is with Apache.

I would like to have an external hard drive as the root folder for the site.

I've edited the
```
/etc/apache2/sites-enabled/000-default
```
file and changed the root directory to

"/media/My Book/"

everything up to this point works. The problem i'm having is withe permissions

when trying to access my "site" I'm getting a 403 error (forbidden). So I went back to /media and as root typed
chmod 766 "My Book"
it seemed to work, except it didn't do anything. 
then I went down to
/dev
and changed sdb's permissions
(sdb is the drive, this I'm almost certain of)
so that worked. However, it did nothing for the /media/My Book.

I tried changing the file and then restarting apache (because the permissions reset everytime I restarted) but me being the noob that I am, don't know how to restart the apache server.

I attempted to eject /media/My Book and mount /dev/sdb, but when I tried it gave me this:
> 
mount: you must specify the filesystem type

and I drew a blank. I ran man mount and looked for vfstype, but I couldn't find fat32 in there.

sorry if this post is all over the place. It's late.

I hope I've explained my situation. I want to get apache to run it's root directory off of a fat32 external hard drive, which is at /dev/sdb or "/media/My Book", and that I'm not able to change the permissions for these files. I'd really like to get around the 403 forbidden error apache is giving me.

Thank You,
         Paarth

---

### Post by delphiguy on 2007-11-15
are you sure that its /dev/sdb? if your sure that this is indeed the drive then
the first partition should be /dev/sdb1, and this is what you want to mount.

off the top of my head, can you try this.
sudo mount /dev/sdb1 /media/My Book -t msdos
if this doesnt work try changing msdos with vfat.

of course there must be a directory named My Book in your media directory.

hope this makes sense.

---

### Post by Pizzarth on 2007-11-15
yes it does, thank you.

how would I start apache server once I mount the file? it's just always been on. or can I leave it up while I'm making these changes

---

