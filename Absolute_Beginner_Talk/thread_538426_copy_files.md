---
title: "copy files"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by ryana on 2007-08-30
I have a dual boot ubuntu and windows xp and I want to copy files I downloaded in linux (drivers for windows) and want to copy them to the windows C:/programs but it tells me I dont have permissions...how do i get permission?

You do not have permissions to write to this folder. is the error

---

### Post by Hobo Joe on 2007-08-30
You need NTFS drivers for that.
I belive it's in the repos
```

sudo aptitude install ntfs-3g

```

---

### Post by ryana on 2007-08-30
Chances are it is user error here but I got that installed and am getting the same error message.

I drag the drivers for the network card onto the C directory and get:

"Error while copying to "/media/disk-1".
-You do not have permissions to write to this folder."

If it helps any, I can read any files off of my portable hard drive and the windows directories but not write to either of them.

---

### Post by Hobo Joe on 2007-08-30
Try getting a root browser by running this command in the run prompt(Alt + F2)
```

gksudo nautilus

```

---

### Post by wormser on 2007-08-30
I think you also need the ntfs-config package.

```
sudo apt-get install ntfs-config
```

Then Applications> System Tools> NTFS Configuration Tool

---

### Post by ryana on 2007-08-30
Thanks, with your advice and possibly sheer luck I have managed to copy those drivers over. Yay for getting the interwebs on Windows. Ubuntu has me converted, but sadly I still must have winXP for some apps :(

---

