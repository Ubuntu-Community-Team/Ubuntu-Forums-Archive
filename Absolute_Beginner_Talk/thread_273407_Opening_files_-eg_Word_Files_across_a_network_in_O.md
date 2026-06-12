---
title: "Opening files -eg Word Files across a network in Open Office"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Stephen Shellard on 2006-10-08
I can find files on my Home Network via  places/network/windows network/etc but if I try to open one of these files in Open Office (or indeed any application) there seems to be no option available for linking to files on the network.

Of course I can copy files onto the local drive and then load them, but this seems cumbersome.  Surely I should be able to open these files from an application?  Help appreciated.

---

### Post by kidders on 2006-10-09
Hi there,

If you mount your network shares someplace, you can access them normally, with any application.

---

### Post by Tux Aubrey on 2006-10-09
kidders,

Can you elaborate for us NOOBS - do you mean put an entry for the smb:/* directories in fstab? and create a mount point in, say, /media?

Could you give an example? Or point us to a "how to".

Sorry, but this is still a bit new, to me at least.

---

### Post by lemonsCC on 2006-10-09
I think he is talking more along the lines of Places > Connect to server > Windows share.

After filling out that info an icon will be created on your desktop and the files within will be treated like normal.

---

### Post by lemonsCC on 2006-10-09
Tux:  You would only create an entry in fstab if you wanted it to mount automatically everytime.

---

### Post by kidders on 2006-10-09
> **Tux Aubrey said:**
> kidders,
Can you elaborate for us NOOBS

Hehe sorry. Basically, Linux is much happier when things are integrated into the filesystem, which is what I meant by "normal" before. What you want to do is plug remote shares into local directories, somplace like /media or /mnt.

If it were me, I'd start with a **sudo mount -t smbfs //server/share.....** and get things working for myself. Quite often, like lemonsCC suggests, people like to be able to access the same locations quickly over and over, so adding a line to /etc/fstab would be worth considering. You can use the "auto" directive to have your share mount automagically at boot, or the "noauto" keyword to suppress that behaviour. You could then do the mount manually with something like **mount /mnt/myshare**, without having to specify username/password/filesystem type/etc.

lemonsCC also describes a pretty-looking way of achieving the same effect, without dropping to a terminal. Much nicer for Linux virgins hehe :-P

What you want to avoid is over-using smb:// style paths. These can confuse some applications.

---

### Post by Tux Aubrey on 2006-10-10
Many thanks!

Will try it both ways.

---

### Post by lemonsCC on 2006-10-10
> You can use the "auto" directive to have your share mount automagically at boot, or the "noauto" keyword to suppress that behaviour.

ROFL...I just deleted the entire entry in fstab.  I only use the windows partition to sync my Dell Axim 51v (Windows Mobile 5 is actually very nice.)  And to run crazy old games like jumpstart for my little sister.  :mrgreen:

---

