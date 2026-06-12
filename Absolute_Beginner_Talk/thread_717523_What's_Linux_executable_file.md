---
title: "What's Linux executable file"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by LinuxNewbieSnake on 2008-03-07
Can Linux run .exe file? If not, what's Linux executable file? 
Onemore question, i just install Linux Ubuntu in my Acer laptop, but i can't hear any sound :confused::confused::confused:. How can i fix it?

---

### Post by celticbhoy on 2008-03-07
.EXE files are for windows, you can run them under wine, but some with limited success.

For sound try opening a terminal and running alsamixer to set your sound.

---

### Post by kesman on 2008-03-07
.bin is usually the common executable for linux. I don't think you ever need to download any of them, all the applications you need are in applications -> add/remove program. 
Also check system -> administration -> software sources and enable all sources, and remove the cdrom.
For sound, I have no idea. Do you have the speaker icon in the top-right corner? Double click on it and ensure that no channels are muted.

---

### Post by celticbhoy on 2008-03-07
[http://www.winehq.org/](http://www.winehq.org/)

Will show you how it works

---

### Post by kpkeerthi on 2008-03-07
> **LinuxNewbieSnake said:**
> 
Onemore question, i just install Linux Ubuntu in my Acer laptop, but i can't hear any sound :confused::confused::confused:. How can i fix it?

Copy/Paste the below command in a terminal window and post the output here.
```
lspci | grep -i audio
```

---

### Post by kpkeerthi on 2008-03-07
> **LinuxNewbieSnake said:**
>  what's Linux executable file? 
You may want to read the last 4 paragraphs from [http://www.bellevuelinux.org/executable.html](http://www.bellevuelinux.org/executable.html)

As a side note, linux does not use file extension to guess the file type. Linux is smart. See ```
man file
``` command.

---

### Post by The Cog on 2008-03-07
Linux (and any unix-like OS) has no naming requirement for program files. Any file can be executable regardless of its name. In fact, the filesystem stores a flag that indicates whether a file is executable, so being executable is a file property just like whether it is readable or writeable, or its name.

An executble file might be a binary executable or might be a script file. If it is a script file, then the first few bytes of the file will be "#!" followed by the name of the interpreter program, e.g.
#!/usr/bin/python
#!/usr/bin/perl

---

### Post by blendo on 2008-03-07
have a look on the permissions of a file

if you chmod a file whith 700 it is executable for its owner. Then you can run the file with ./filename

---

### Post by LinuxNewbieSnake on 2008-03-08
Thanks everybody!

---

### Post by timbounceback on 2008-03-08
Techincally, the executable format used is ELF (PE in Windows). But most people don't need to know that. As a general rule, it doesn't have a file extension.

---

