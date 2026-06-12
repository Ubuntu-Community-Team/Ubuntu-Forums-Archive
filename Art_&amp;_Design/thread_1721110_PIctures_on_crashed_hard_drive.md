---
title: "PIctures on crashed hard drive"
date: 2011-04-04
forum: Art &amp; Design
---

### Post by wembleyboy on 2011-04-04
Hi All , 

Just had a friend who's hard drive crashed. 

He had a lots pictures scattered all over his windows xp machine. 

I can browse the hard drive when I connect to my Ubuntu machine using a caddy. 

Is there a command that I can run that will allow me to look for all the pictures on the hard drive no matter what the format ??

Thanks in advance !!!

Chan

---

### Post by ronnielsen1 on 2011-04-04
You could hook the hard drive back up and use picasa, gphoto or another photo software to import pictures from the hard drive

---

### Post by Telengard C64 on 2011-04-04
> **wembleyboy said:**
> Is there a command that I can run that will allow me to look for all the pictures on the hard drive no matter what the format ??


Assuming the filesystem is not damaged, you can use the **find** command to locate image files by their extensions.

[http://linux.die.net/man/1/find](http://linux.die.net/man/1/find)

```
find /PATH/TO/SEARCH -iregex '.*\(png\|gif\|jpg\|jpeg\|bmp\|xcf\|tiff\)'
```

I probably forgot some picture file extensions in there, but I think you get the idea.

If you like, **find** can automatically copy the files to another location.

```
find /PATH/TO/SEARCH -iregex '.*\(png\|gif\|jpg\|jpeg\|bmp\|xcf\|tiff\)' -exec cp -t /PATH/TO/TARGET '{}' \;
```

One drawback of that would be if two files happen to have the same name then the second file overwrites the first silently.

If the filesystem has been damaged, then I think [photorec](http://www.cgsecurity.org/wiki/PhotoRec) is for you.

---

### Post by wembleyboy on 2011-05-20
Thanks for this guys I used a combination of both ides to get the photos off the Hard Drive. 

:p

---

### Post by Megaptera on 2011-05-20
> **wembleyboy said:**
> Thanks for this guys I used a combination of both ides to get the photos off the Hard Drive. 

:p

I bet your friend was pleased, relieved and impressed!!! Don't forget to get your friend to backup the backup's backup now!

---

### Post by sectshun8 on 2011-05-27
> **Telengard C64 said:**
> ...

If the filesystem has been damaged, then I think [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") is for you.

I second that on the use of photorec for the damaged filesystem... has saved me much heartache when retrieving images from damaged or formatted flash media ;)

---

