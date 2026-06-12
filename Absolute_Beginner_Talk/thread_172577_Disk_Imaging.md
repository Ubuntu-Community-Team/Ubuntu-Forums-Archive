---
title: "Disk Imaging"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by kc0eak on 2006-05-08
Hello,

I don't know if this is the right forum to post this on, but I'm new to linux, so I thought this should work.

I would like to know if there is a program out there that will allow me to image my entire disk and send it to a file on another computer on my network.

It would be nice if the program allowed me to image every partition into the same file (I'll be dual booting Windows XP & Ubuntu, so I'll have multiple partitions).  If I get this far, I'd like to take the file, use a Windows program (File Splitter) to break it up and burn it to DVD.  What I'd like to do after that is have the ability, if my hard drive crashed and I had to put a new one in, to take those DVDs, somehow boot my computer (whether it be through a Linux live CD, a rescue disk, or whatever), and copy the files to the hard drive, rebuild the original image, then copy that image to the new hard drive so that my system was back at the state it was in at the time of the last image.

I do have an internal DVD/CD-RW drive in my laptop, and I've also got an external DVD-RW drive, so if I had to boot off of a live CD, I would still have another drive to put a DVD into to read from.

If anyone knows of any programs that would be able to do something similar to this, or if there are any commands that would do this, please let me know.

Thanks

---

### Post by cilynx on 2006-05-08
Look into the "mondo" backup system.

---

### Post by FryerFox on 2006-05-09
The 'dd' command can copy raw data from the blocks on a drive. For example, to copy / on /dev/hda1 to a /dev/hdb1 ( backup disk), type:
```
dd if=/dev/hda1 of=/dev/hdb1 bs=1024k
```

You might want to check out some articles on the topic:
[http://www.techbuilder.org/recipes/171200478](http://www.techbuilder.org/recipes/171200478)
[http://www.antipope.org/charlie/linux/shopper/171.backups.html](http://www.antipope.org/charlie/linux/shopper/171.backups.html)
[http://www.faqs.org/docs/gazette/backup.html](http://www.faqs.org/docs/gazette/backup.html)

All in all, though, it does seem that Mondo Rescue and Mindi ([http://www.mondorescue.org/](http://www.mondorescue.org/)) are what you're looking for.

---

