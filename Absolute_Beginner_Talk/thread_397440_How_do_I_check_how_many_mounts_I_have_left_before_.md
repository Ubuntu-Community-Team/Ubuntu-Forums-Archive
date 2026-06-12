---
title: "How do I check how many mounts I have left before fsck?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by encompass on 2007-03-30
I am creating a little popup program to tell me how many mounts I have left if it is under five and give me the chance to delay it or do it on next reboot.
But I can't find the file that is used to keep track of that "count down".
Does anyone know where that is located.
As a prize I will give you my little python applet. ;P
Thanks for all your help!

---

### Post by mac.ryan on 2007-03-30
I don't know where this info is written. My knowledge of filesystems is extremely shallow, but IMO opinion it might even be stored in the FAT (or whatever is its name under ext3) rather than in a file...

Anyhow, I don't know if this is sufficient for your purposes, but you can get that information runnning a grep for "Mount count" on the output of:

```
sudo tune2fs -l /dev/....
```Hope this helps at least a bit! ;)

---

### Post by encompass on 2007-03-30
Yup, I think that is similar to what I need.  Dang if it isn't in a file somewhere.  Hopefully someone out there could figure out that one.
Or maybe I could do some kind of search all text files for that statement.  Probably get a lot of results but willing to look.
If you have any other ideas throw me them as I don't want to have the normal use have to use root all the time.  And I don't want to make a program to run at each boot just to check things and write it to a file.  :P  That's just a little dirty.

---

### Post by ramjet_1953 on 2007-03-31
It's already been done, guys!

The program is called Bonager, and it's really useful, as it also allows you to postone a scan.

I have attached the .deb file.

Regards,
Roger :cool:

---

### Post by encompass on 2007-03-31
COOL!
I will look into it... for some reason it doesn't seem to be in ubuntu yet. I will figure out why.  Otherwise, it "looks" good.  It is almost exactly what I want.

---

