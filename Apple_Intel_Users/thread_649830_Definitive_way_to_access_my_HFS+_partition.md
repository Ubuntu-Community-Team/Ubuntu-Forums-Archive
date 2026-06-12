---
title: "Definitive way to access my HFS+ partition?"
date: 2007-12-25
forum: Apple Intel Users
---

### Post by Tu13erhead on 2007-12-25
I can mount my HFS+ partition and view most files/directories, however, as many others have seen, things inside directories withing /Users and whatnot on my Leopard partition can't be accessed (permission denied).  I've seen quite a few places with hacks on how to get it working, but I haven't found anything definitive and most seem to run into problems.  

I've fiddled with this in the past and fubar'd one of my partitions and ended up reformatting and scrapping Ubuntu.  So I'm trying again now, I'd just like to not screw up my OS X partitions.

I disabled Journaling on the HFS+ partition.

Any help would be greatly appreciated.

Thanks!

EDIT: This is a non-SantaRosa C2D MacBook.

---

### Post by changuito on 2007-12-29
hey there. I hope this helps, i tried to give details before, for the record. 

[http://ubuntuforums.org/showpost.php?p=3795088&postcount=7](http://ubuntuforums.org/showpost.php?p=3795088&postcount=7)

one nice thing is that this shouldnt threaten you osx drive in anyway, you're simply modifying the user number and name in linux to match that in osx.

---

### Post by Tu13erhead on 2008-01-04
So, I've decided all I _really_ need is to be able to read my HFS+ partition, at least for now.  After fighting for a while with no success reading inside my /Users directory, I tried running Nautilus as root and realized that would let me into my Music directory and such.

So, I know I can get inside my /Users folder.  Now I'd just like to be able to do so with things like Amarok.

Any thoughts?

Thanks!

---

### Post by cyberdork33 on 2008-01-04
> **Tu13erhead said:**
> So, I've decided all I _really_ need is to be able to read my HFS+ partition, at least for now.  After fighting for a while with no success reading inside my /Users directory, I tried running Nautilus as root and realized that would let me into my Music directory and such.

So, I know I can get inside my /Users folder.  Now I'd just like to be able to do so with things like Amarok.

Any thoughts?

Thanks!

It is a permissions issue. Ubuntu sees the OSX user as a different user. Thus, those files are owned by another user and have permission set to deny access to other. becoming root by passes this because, well, you are root, and root can do whatever it feels like.

You have to go into OSX and change the permissions of all the folder that you want to grant access to, or do as mentioned previously and change your user ID's around so that they match (thus causing the system to see them as the same user). There are not "hacks" they are the normal operation of a *nix system.

---

### Post by Tu13erhead on 2008-01-04
> **cyberdork33 said:**
> It is a permissions issue. Ubuntu sees the OSX user as a different user. Thus, those files are owned by another user and have permission set to deny access to other. becoming root by passes this because, well, you are root, and root can do whatever it feels like.

You have to go into OSX and change the permissions of all the folder that you want to grant access to, or do as mentioned previously and change your user ID's around so that they match (thus causing the system to see them as the same user). There are not "hacks" they are the normal operation of a *nix system.

I just went into OS X and changed the "everyone" permissions of my /Movies directory to RO.  Booting back into Ubuntu, I still can't access the folder.

I suppose I'll give the UID stuff a shot.

---

### Post by Tu13erhead on 2008-01-07
Yeah, I fubar'd something really badly.  I did

```
sudo groupmod -g 501 brandon
sudo usermod -g 501 brandon
sudo usermod -u 501 brandon
```

as per changuito's link.  Immediately after, compiz died, I couldn't sudo anything, couldn't shut down or reboot, etc.  After a hard reboot and logging in, I get about 50,000 errors.

So, two things.

What did I do wrong?
Can I fix it?  Or should I just reinstall?

---

### Post by cyberdork33 on 2008-01-07
I would guess that you changed your UID/GID, and now you don't own any files on the system, so you get lots of problems. I think I heard that Ubuntu IDs have to be > 1000 or something now... It is probably easier to reinstall, but if you can just login as root and change the IDs back to the number they used to be, that (theoretically) will work.

Either way, this is really not a fun thing to mess with. If you can get it working, congrats, but personally, I would never attempt it.

---

### Post by Tu13erhead on 2008-01-07
> **cyberdork33 said:**
> I would guess that you changed your UID/GID, and now you don't own any files on the system, so you get lots of problems. I think I heard that Ubuntu IDs have to be > 1000 or something now... It is probably easier to reinstall, but if you can just login as root and change the IDs back to the number they used to be, that (theoretically) will work.

Either way, this is really not a fun thing to mess with. If you can get it working, congrats, but personally, I would never attempt it.

Yeah. If it was my desktop I'd just put all my data on a separate partition, but it's kind of a pain for my laptop.

I'll reinstall.

---

