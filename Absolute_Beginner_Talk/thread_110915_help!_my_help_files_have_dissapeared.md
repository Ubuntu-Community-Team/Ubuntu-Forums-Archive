---
title: "help! my help files have dissapeared"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2006-01-01
this may be the wierdest problem i've seen so far. my life saver icon that leads to all the preinstalled help stuff doesn't bring up any text or links or anything. the help browser just opens, and then nothing shows up.

It may sound odd, but I really want the help stuff back. How can i fix this?

---

### Post by rjwood on 2006-01-01
The first thing I would try is ```
sudo apt-get install yelp
```and see what it say's.Did you do anything to make it disappear?

---

### Post by iand675@gmail.com on 2006-01-01
i just installed a copy on this computer, and i couldn't remember how to mount fat32 partitions, and i opened the help file and there was nothing there. I just did a basic install.

```

ian@ubuntu:~$ sudo apt-get install yelp
Password:
Reading package lists... Done
Building dependency tree... Done
yelp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And apparently that didn't work either.
Any way to remove and reinstall? Or is there something else that's wrong maybe?

---

### Post by anil_robo on 2006-01-01
```
sudo apt-get remove yelp --purge
```
and then
```
sudo apt-get install yelp
```

---

### Post by iand675@gmail.com on 2006-01-01
it still isnt showing up

---

### Post by rjwood on 2006-01-01
sorry I don't have experience with partitioned drives.

---

### Post by iand675@gmail.com on 2006-01-01
im more concerned about getting my help back. I've only been consistently using ubuntu for a couple of days.

---

### Post by shebuwa on 2008-07-02
Thank you RJWood. :)

sudo apt-get install yelp

Worked for me! I now have help files.

---

### Post by goforlinux on 2008-07-02
If the things have dissapeared and they were files on your computer which is what i guess im understand then they should be on your hard drive id go in and look at your drives and then basically track it down like for example find the hard drive partition that the HELP may be on see if access is possible that way. It will at least confirm they arent like gone from your comp.


..... HOPE IM NOT TOTALLY MISSING THE POINT HAHAHALOL

---

