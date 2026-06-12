---
title: "Trash Won't Empty?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by dhtseany on 2008-02-15
Here is a weird one:

I have a bunch of crap in my Trash. When I empty it the files aren't going away. I know they're still there because my free space isn't changing afterwards.

I did a quick search on the forums and everything seems to point towards permission issues. None of the files in there were ever owned by root. Also, when I try to empty it no errors appear; it just sits there.

Any thoughts?

Thanks,
Sean

---

### Post by taurus on 2008-02-15
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la ~/.Trash
```

---

### Post by dhtseany on 2008-02-15
So yeah, I spoke too soon.

I think there are files with permissions issues.

Output:
```

drwx------  4 sean sean 53248 2008-02-15 13:33 .
drwxr-xr-x 52 sean sean  4096 2008-02-15 13:31 ..
drwxrwxrwx  4 sean sean  4096 2008-02-15 13:30 2
drwxr-xr-x  9 sean sean  4096 2008-02-15 13:30 pdraw

```

---

### Post by dhtseany on 2008-02-15
Nevermind, I fixed it; just changed the permissions.

Thanks though

Peace

Sean

---

### Post by mivo on 2008-02-15
Yes, that happens if you don't have sufficient permission for some files, i.e. after compiling some source using the sudo command.

You can safely fix this by typing in a terminal:

```
sudo nautilus
```

... and navigating to the .Trash folder in your username's home directory, then deleting the files in there.

Edit: Okay, too late. :p

---

