---
title: "How to use dd command"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-09-03
I have looked up the dd command in the manual pages but I am a bit hesitant to try it all on my own. Basically what I want to do is copy one of my hard drives bit by bit to another one. Essentially what I want to do is create a  perfect copy of one of my hard drives and put it on another. It will save me a lot of time from having to completely re-install Ubuntu on the other hard drive and having to re-configure it all over again. I would like to know if I can do a bit-by-bit copy of one hard drive onto a hard drive that already has another operating system installed on it. In addition, can you do a bit-by-bit copy onto a hard drive that is blank? I would like to know the complete command to do a complete bit-by-bit copy. Any and all help related to the dd command and how to do a clone copy is greatly appreciated. Thank You.

:guitar:

---

### Post by cdsboy on 2007-09-03
I would suggest using the GParted Live cd. Its easy to use and will do everything you want for your copying needs. 
Cheers : )

---

### Post by bme on 2007-09-03
see this-http://www.debianhelp.co.uk/ddcommand.htm

---

### Post by Duck2006 on 2007-09-03
This is well worth the read

[http://www.linuxquestions.org/questions/showthread.php?t=362506](http://www.linuxquestions.org/questions/showthread.php?t=362506)

---

### Post by logos34 on 2007-09-03
here's another:
[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

If you want a ui use** Partimage** (found on most utility cds)

---

### Post by asmoore82 on 2007-09-03
> **jprb85 said:**
> I have looked up the dd command in the manual pages but I am a bit hesitant to try it all on my own. Basically what I want to do is copy one of my hard drives bit by bit to another one. Essentially what I want to do is create a  perfect copy of one of my hard drives and put it on another. It will save me a lot of time from having to completely re-install Ubuntu on the other hard drive and having to re-configure it all over again. I would like to know if I can do a bit-by-bit copy of one hard drive onto a hard drive that already has another operating system installed on it. In addition, can you do a bit-by-bit copy onto a hard drive that is blank? I would like to know the complete command to do a complete bit-by-bit copy. Any and all help related to the dd command and how to do a clone copy is greatly appreciated. Thank You.

:guitar:

the 'dd' command does perfect bit-for-bit copying which can be a good thing or a bad thing ...
depending on whether or not the 2 drives have exactly the same **logical geometry**

I haven't used the GParted LiveCD myself, but I would assume it is up to the task ...
Also, if you want to make a 'sparse' image of your install that takes up as little space as possible,
check out clonezilla.sf.net ... I just d/l it last week and it works well.

---

