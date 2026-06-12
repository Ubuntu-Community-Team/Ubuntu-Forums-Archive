---
title: "making a folder and subfolders read-only"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by | MM | on 2007-11-24
Here's my issue.  Rhythmbox seems to somehow munge my ID3 tags... which is annoying.

So i want to make My Music folder read-only to everyone except sudo/root.

so to do this, would i use :

```
chmod -R rwxrwxr-- /media/storage/My\ Music/
```

Will this make the directory writable only to root and keep rhythmbox from being able to manipulate the file ID3 tags...?

Also does it matter that it is an ntfs partition?

Finally, i notice that when you do *ls -l* on the folder the permissions start out with a *d*. 
Example: 
> **d**rwxrwxrwx 1 root root     0 2007-11-07 14:18 Anthony Milton

What does this *d* mean?  i haven't seen it mentioned in the couple of chmod tutorials i've looked at.

Many thanks for any advice.
Matt

---

### Post by Danikar on 2007-11-24
```
chmod -R 0444 ~/Music
```

should work

And the d means it is a directory.

---

### Post by Xavieran on 2007-11-24
You can just right cllick on the folder and select properties then Permissions and set the permissions how you want them to be.

---

### Post by Majorix on 2007-11-24
You can't change a folder that belongs to root like that. Copy&paste this in a terminal
```
gksudo nautilus
```
Then follow the procedure described above.

---

### Post by Hayden on 2007-11-24
> **| MM | said:**
> 
Also does it matter that it is an ntfs partition?


As far as I know you can't change file permissions/owner on a ntfs partition.

---

### Post by | MM | on 2007-11-25
> **Hayden said:**
> As far as I know you can't change file permissions/owner on a ntfs partition.

Ahh that explains allot.  I tried it the gui way and it just kept jumping back to its defaults.  Hrmmm...

---

