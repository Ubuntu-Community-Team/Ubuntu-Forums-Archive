---
title: "Ubuntu doesn't see certain files on CD"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by evny on 2007-07-02
I'm running Ubuntu Feisty on an HP Pavilion laptop and have encountered a strange problem.  When I put in a CD of JPEG images created on my iMac, some of the files are not seen.  For example, today I put in a CD with a folder holding 190 JPEGs.  Ubuntu sees 179 of them.  The missing files all have names that end with either a 9, as in "img_029.jpg," or a 4, "img_044.jpg."  But it's not that every file with a 9 or a 4 disappears, just a few random ones.  The same thing happened last week with another CD of images.

Has anyone explain this?

---

### Post by overdrank on 2007-07-02
> **evny said:**
> I'm running Ubuntu Feisty on an HP Pavilion laptop and have encountered a strange problem.  When I put in a CD of JPEG images created on my iMac, some of the files are not seen.  For example, today I put in a CD with a folder holding 190 JPEGs.  Ubuntu sees 179 of them.  The missing files all have names that end with either a 9, as in "img_029.jpg," or a 4, "img_044.jpg."  But it's not that every file with a 9 or a 4 disappears, just a few random ones.  The same thing happened last week with another CD of images.

Has anyone explain this?

HI, you may try under edit show hidden files, or ctrl + H. I hope this helps. :KS

---

### Post by John.Michael.Kane on 2007-07-02
Could the cd be corrupt?

Can the mac you made it on see all 190 JPEGs?

Are they hidden? edit: overdrank covered this one.

I would try converting thoes images which can't be read or seen under ubuntu to .png format, and see if ubuntu can pick them up in that format.

---

### Post by evny on 2007-07-02
Thanks, overdrive and SD-Plisskin.  I love how helpful people are on this forum!  I tried "show hidden files" but it didn't reveal the missing files.  I looked at the CD on another Mac and on the Windows partition of this computer,  and saw all 190 files, so I don't think the CD is corrupted.  Maybe Ubuntu is more picky about CDs.

It's not vital that Ubuntu see all the files, but when I get a chance, I'll try and convert some of them to png and see what happens.

---

### Post by evny on 2007-07-02
I changed a couple of the problem files to png and I also copied the jpegs to a USB pen drive.  Ubuntu sees them all and I was able to copy them.  It's definitely something about the CD.  Maybe Ubuntu doesn't like the budget brand CDs.

---

### Post by Rocket2DMn on 2007-07-02
Have you simply tried refreshing the view in nautilus, that has sometimes helped me in the past, esp. with mounted media.
Try changing to the directory in terminal and running an ls and seeing if some of the files are there that weren't before.  The "du" command may be useful here, too, so you can see the total usage.
try ```
du -ch
```

---

### Post by evny on 2007-07-03
Thanks, Rocket2DM.  I tried to cd into the folder but I'm getting an error message that there's no such directory.  I must be doing something wrong.  The total size of the folder looks about right, though.


```
dany@dany-laptop:/media$ cd /cdrom
dany@dany-laptop:/cdrom$ ls
rapleejpegs
dany@dany-laptop:/cdrom$ cd /rapleejpegs
bash: cd: /rapleejpegs: No such file or directory
dany@dany-laptop:/cdrom$ pwd
/cdrom
dany@dany-laptop:/cdrom$ ls
rapleejpegs
dany@dany-laptop:/cdrom$ cd /rapleejpegs
bash: cd: /rapleejpegs: No such file or directory
dany@dany-laptop:/cdrom$ du -ch
470M    ./rapleejpegs
470M    .
470M    total

```

---

