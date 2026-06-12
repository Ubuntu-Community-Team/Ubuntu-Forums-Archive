---
title: "Need Command Line Help"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-08-09
I have a 40GB WD USB external drive with files in ntfs format. Using the NTFS Configurator I can access the files with read and write permission. I would like to chown from root to user. So far, none of my efforts have worked. Could someone give me an example of the proper command line to do this?

The drive is mounted at /media/MONSTER.

---

### Post by Rocket2DMn on 2007-08-09
You can run
```
sudo chown -R *yourusername* /media/MONSTER
```

---

### Post by Dr Small on 2007-08-09
I like commands, but you can also do it in nautilus also, by selecting the directory (as root) and settings the ownership under the permissions tab of properties.

Dr Small

---

### Post by rsnow on 2007-08-09
Rocket2Dmn,

I tried your example but as far as I can tell there was no change. When I look at the permissions tab it shows "root" as owner and the message at the bottom says" you are not the owner, you cannot change the permissions." This is after I typed

sudo chown -R ron-e /media/MONSTER

Dr Small,

I do not quite understand how to do what you are saying. How do I set myself as root other than using sudo?

And while I'm asking, what numbers do you use with chmod to allow full privileges? I have 3 books on linux but can't find this information.

---

### Post by Rocket2DMn on 2007-08-09
I don't think we quite understand your problem then - if you are able to read and write, what's the problem?  The mount point is typically owned by root, but allows you to access everything, so the ownership of the mount point is irrelevant.
NTFS permissions don't work quite the same as ext file system permissions do.  You are able to set the appropriate permissions when you mount - either from the command line or from the declared mount points in /etc/fstab

---

### Post by Dr Small on 2007-08-09
Go to the terminal and type 'gksudo nautilus'
This will log you in as 'root' or 'sudo' in nautilus, allowing you to browse the filesystem with all permissions.

Then browse to /media and right click on MONSTER, go to Properties > Permissions and set the owner and group to your user account.

Dr Small

---

### Post by Inxsible on 2007-08-09
are you sure the mount point is MONSTER and not Monster. Linux as you know is case sensitive. 

If you can read and write to it, why do you want to change the ownership from root to you ?

---

### Post by psusi on 2007-08-09
You can not set permissions or ownership on ntfs volumes; the filesystem does not store that information.

---

### Post by Dr Small on 2007-08-09
Why not just make a backup of it, and reformat it to fat32 so he can change permissions on it, if indeed that is what he is having problems with setting?

Dr Small

---

### Post by Rocket2DMn on 2007-08-09
> **psusi said:**
> You can not set permissions or ownership on ntfs volumes; the filesystem does not store that information.

That is true when you access through machines other than windows.  NTFS does have it's own set of permissions and owernship very similar to that of the extension file system, and in some ways more complex.
A good explanation here: [http://www.windowsecurity.com/articles/Understanding-Windows-NTFS-Permissions.html](http://www.windowsecurity.com/articles/Understanding-Windows-NTFS-Permissions.html)

---

### Post by rsnow on 2007-08-09
WOW! One can sure learn a lot here and in a short period of time. :)

I guess I was making an incorrect assumption that I needed to have ownership in order to have full control of the files. Now that you explained about the ntfs situation I can be content to let things stand in that area.

Yes it is MONSTER and not Monster. One of my weird moments when I first hooked up the drive to my windows machine. At that time (several years ago) I thought 40GB was a monstrous amount of disk space. In my enthusiasm I named the drive with all caps. Dumb, huh?

I sincerely want to thank all who responded. This kind of help is what makes learning Linux fun and worthwhile.

I'll close this thread now, but I'm sure I'll be back later with some more questions you can laugh about.

---

### Post by asmoore82 on 2007-08-09
> **Dr Small said:**
> Why not just make a backup of it, and reformat it to fat32 so he can change permissions on it, if indeed that is what he is having problems with setting?

Dr Small

fat32 doensn't store the permissions either.

---

### Post by Dr Small on 2007-08-09
It does on my drive.

---

### Post by psusi on 2007-08-09
> **Dr Small said:**
> It does on my drive.

No, it doesn't.  You choose what owner and mode all files on the drive should appear to have with mount options.

---

