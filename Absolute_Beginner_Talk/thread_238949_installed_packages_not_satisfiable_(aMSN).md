---
title: "installed packages not satisfiable? (aMSN)"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2006-08-18
I'm trying to get aMSN installed. I try to use the GDebi installer on the .deb files. aMSN installer tells me that the tcltls dependency is not satisfiable, tcltls (when I try to install) tells me libc6 is not satisfiable, libc6 tells me tzdata is not satisfiable, and tzdata won't install because (as far as I can tell) it already exists. Anyone know why this is happening to me?

*Edit: *By the way, I'm using the Live CD version right now. Nothing's on my hard drive yet.

---

### Post by Cone on 2006-08-18
It's generally preferable to see if you can find a program you're looking for in Syanptic Package Manager or in Menu < Add/Remove Programs.

In a terminal you should be able to install it by typing . . .
```
sudo aptitude install amsn
```

Hope this helps :),
~Cone

---

### Post by ramcosca on 2006-09-11
Uuuhhhhmmmmm, nope. I'm having the same problem as he is having. It's FRUSTRATING!

```
ramcosca@ramcosca-laptop:~$ sudo aptitude install amsn
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for amsn
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by Cone on 2006-09-12
Oh, it appears that it's in the universe repositories.

There's lots of info on setting those up [here]("https://help.ubuntu.com/community/Repositories/Ubuntu#what").

Try that and tell me if it works. :)

---

### Post by ramcosca on 2006-09-12
Yeah, thanks. Last night I had a one-on-one session with a member of the forums and it ended up being that the universe repos were commented. Thanks!!

---

