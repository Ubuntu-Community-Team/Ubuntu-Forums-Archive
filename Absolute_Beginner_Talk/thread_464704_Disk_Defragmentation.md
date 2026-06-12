---
title: "Disk Defragmentation?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-06-04
Is disk defragmentation required under Ubuntu? If it is, how do I do it and which application do I use??:confused:

---

### Post by Songwind on 2007-06-05
Nope, not really.  The way ext3 works, it won't start fragmenting files until the drive is nearly full.

---

### Post by Wake Rider on 2007-06-05
> **Songwind said:**
> Nope, not really.  The way ext3 works, it won't start fragmenting files until the drive is nearly full.

Thanks for your reply Songwind. This is another great advantage of Feisty over Windows.:D Those Windows defrags usually take hours....

---

### Post by jonward0690 on 2007-06-05
Yea the only bad thing is when Ubuntu frags there is not a thing you can do about it.

---

### Post by Wake Rider on 2007-06-05
> **jonward0690 said:**
> Yea the only bad thing is when Ubuntu frags there is not a thing you can do about it.

:confused:

Can you expand into a little bit more detail please? I have been using Ubuntu with the KDE desktop (NOT Kubuntu, I installed the KDE desktop separately) for the last few months and everything so far has been running smoothly. I do backup the entire system using the command line, in case I ever need to restore the system. Would I be restoring fragmented files as well?

---

### Post by jrusso2 on 2007-06-05
I think he is saying this because there is not really a working defrag utility for ext3.. Also once a drive gets so full that it has to fragment there is nothing you can do about it except to make room on the disc.

---

### Post by jfinkels on 2007-06-05
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by jonward0690 on 2007-06-05
> **Wake Rider said:**
> :confused:

Can you expand into a little bit more detail please? I have been using Ubuntu with the KDE desktop (NOT Kubuntu, I installed the KDE desktop separately) for the last few months and everything so far has been running smoothly. I do backup the entire system using the command line, in case I ever need to restore the system. Would I be restoring fragmented files as well?

Well some poor guy was talking about how his system was 22% fraged so to me I would think that that is a littole high.

---

### Post by Wim Sturkenboom on 2007-06-05
> **Wake Rider said:**
> :I do backup the entire system using the command line, in case I ever need to restore the system. Would I be restoring fragmented files as well?It depends on the commands that you use. If you make an image, it will contain the defrag. If you use something like tar or cp, it does not contain the fragmentation; in that cae it depends how you put it back. Wiping the disk clean before restoring will give you a defragged system; overwriting a fragmented file with the same non-fragmented file might still result in a fragmented file (not 100% sure).

---

### Post by Marsolin on 2007-06-05
If you do get to a fragmented state you could try [Shake Defragmenter]("http://linuxappfinder.com/package/shakedefragmenter").

---

