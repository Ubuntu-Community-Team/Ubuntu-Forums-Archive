---
title: "Teachers need help (No Kidding)"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by glebreton on 2007-04-08
There are several thousand teachers out there using a program called Markbook. This allows us to keep record of our class marks, students, etc.

I would love to switch my life to Ubuntu but I cannot get Markbook to install or run in Wine and therefore have to keep XP on my laptop. I know that there are a number of other teachers on my staff in the same position.

Is there anyone out there with more skills at this than me who could take a crack at this?

You can download an evaluation version of Markbook at Markbook.com.  

I'd be interested hearing if anyone can get this to run.
Best regards.

---

### Post by trent dillman on 2007-04-08
...

---

### Post by aysiu on 2007-04-08
These links may help:
[http://www.linuxforums.org/forum/wine/58788-markbook-2005-wine-install-issues-post329756.html](http://www.linuxforums.org/forum/wine/58788-markbook-2005-wine-install-issues-post329756.html)
[http://linux.softpedia.com/get/Information-Management/ClaSS-7440.shtml](http://linux.softpedia.com/get/Information-Management/ClaSS-7440.shtml)

---

### Post by david_kt on 2007-04-09
> **glebreton said:**
> 

You can download an evaluation version of Markbook at Markbook.com.  

I'd be interested hearing if anyone can get this to run.
Best regards.

Dear Glebreton,

I have downloaded the trial version, and I am able to run it with wine without any error message at all (run perfectly). Please follow the steps below:

Download mfc40.dll and oleaut32.dll from below link:

[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/mfc40.dll]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/mfc40.dll")

[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/O/OLEAUT32.DLL]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/O/OLEAUT32.DLL")


Put those 2 files on below folder:
```

/.wine/drive_c/windows/system32
```

Install the program:

```
wine MB06_Vista.exe
```

Set dlloverrides for mfc40.dll and oleaut32.dll  for MkBk2006.exe to native then builtin.

That is all. You could double click the launcher on your desktop or go to your menu:

```
Application>Wine>Program>Markbook 2006>Markbook 2006
```

to launch it.

Please let me know if you have problems.

DK

---

### Post by mac.ryan on 2007-04-13
It just happened I stumbled on this:
[http://code.google.com/soc/ubuntu/appinfo.html?csaid=361DBAB13AE22965](http://code.google.com/soc/ubuntu/appinfo.html?csaid=361DBAB13AE22965)

i couldn't figure out if the project has been approved or not (I think they only published the approved ones, though). Maybe it would be worth to get in touch with the student/mentor and see if they need or appreciate ideas for the project specifications...

---

