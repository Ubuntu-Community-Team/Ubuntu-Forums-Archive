---
title: "Creating massive files for testing"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-12-27
hey all,

I know this may sound absurd but I need to create a massive single 35 GB file to fill a portable HD in order for testing. Any ideas on how to do that?


thanks

---

### Post by GGLucas on 2007-12-27
Try:
```
sudo cat /dev/zero >> ~/hugefile
```

This will start filling a file with zeroes, just press Control+C to stop it when you see the file has reached the correct size. It's crude, but simple :P There should be a way to automatically get it to cut off when it's reached a certain size, but it wouldn't know from the top of my head.

---

### Post by roaldz on 2007-12-27
Use the command ¨dd¨

see ¨dd -h¨
and
¨man dd¨

for help and options.

---

### Post by LowSky on 2007-12-27
this sounds dangerous... LOL

---

### Post by JasonBourneLinux on 2007-12-27
can I direct it to fill an external?

---

### Post by JasonBourneLinux on 2007-12-27
so does this create 1 massive file?

---

### Post by mellowd on 2007-12-27
[http://mellowd.co.uk/test2/index.php?m=11&y=07&entry=entry071116-231252](http://mellowd.co.uk/test2/index.php?m=11&y=07&entry=entry071116-231252)

```
dd if=/dev/zero of=myfile bs=1024 count=1024
```


This will create a new file with a size of exactly 1MB (1024k) You can easily change the count to reflect any value!

---

### Post by JasonBourneLinux on 2007-12-27
cool- can I direct it to make the file on an external hard drive?

---

### Post by JasonBourneLinux on 2007-12-27
and can I do an MD5 sum of the file afterwards

---

### Post by mellowd on 2007-12-27
You can direct it like so:

```
dd if=/dev/zero of=/dir_of_your_choice/myfile bs=1024 count=1024
```

As for a md5sum, you would first need to create an md5, then test it

---

### Post by JasonBourneLinux on 2007-12-27
awesome- thanks!

---

### Post by mellowd on 2007-12-27
np, let me know how it goes

---

### Post by JasonBourneLinux on 2007-12-27
when i enter the following command

dd if=/dev/zero of=/media/Drive_1_EE/bigfile bs=1024 count=35840000 

to make a 35 GB file it says 

dd: opening `/media/Drive_1_EE/bigfile': No such file or directory

do I have to have a file in place already?

---

### Post by mellowd on 2007-12-28
Just tried it out here and I got the same problem, strange. My suggestion is to CD to /media/Drive_1_EE/ first and then run the original command. The command will create the file in whichever directory you are currently in

---

### Post by eternicode on 2007-12-28
Hmm...you shouldn't *have* to pre-create the file, and you shouldn't *have* to cd into the destination directory, but if that's what works, use it :)

Also, just for clarification, dd ,without the "of=..." parameter, will automatically output its data to stdout (using /dev/zero without the of seems to just do nothing...but interesting results can be achieved with /dev/random ;) ).  You will have to specify the output file.

---

### Post by The Cog on 2007-12-28
I don't know where that output directory name came from, but I think that's the problem. To write a file on this hard disk, you must mount it first. Normally, just plugging the disk in will do that (if its a USB drive) and mount it under /media. You need to find the directory name where it is mounted, and use that in the dd command. The command **mount** will tell you the names of the mounted devices and directories, but so does **df -h** and I find df -h easier to read.

---

### Post by mellowd on 2007-12-28
> **The Cog said:**
> I don't know where that output directory name came from, but I think that's the problem. To write a file on this hard disk, you must mount it first. Normally, just plugging the disk in will do that (if its a USB drive) and mount it under /media. You need to find the directory name where it is mounted, and use that in the dd command. The command **mount** will tell you the names of the mounted devices and directories, but so does **df -h** and I find df -h easier to read.

It's not the problem because when I tried recreating the problem here on my server I tried writing a file to my home directory and simply wouldn't allow me. If I cd's to my home directory I could then create the file. Wierd.

---

### Post by JasonBourneLinux on 2007-12-28
k I got it to work- I just collapsed the drive name to Drive1EE in windows then redid the command- you dont need the file in advance


thanks for your help all!

---

### Post by SOULRiDER on 2007-12-28
> **JasonBourneLinux said:**
> and can I do an MD5 sum of the file afterwards

I think hashing that will take a long time :P

---

