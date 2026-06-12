---
title: "Error... I think"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-08-24
When I'm in the terminal, the following happens:

alex@ubuntu:~$ cd Music
alex@ubuntu:/Music~$ cd Shared Music
>

Nothing happens after this (even when I type commands).  Why did the ">" show up and what can I do?

Thanks for your help.

---

### Post by izmaelis on 2005-08-24
[QUOTE=apmcavoy]When I'm in the terminal, the following happens:

alex@ubuntu:~$ cd Music
alex@ubuntu:/Music~$ cd Shared Music
>

Nothing happens after this (even when I type commands).  Why did the ">" show up and what can I do?

Thanks for your help.[/QUOTE]
It must be
```

alex@ubuntu:/Music~$ cd Shared\ Music/

```
You are wellcome.  :grin:

EDIT: Try using **Tab** button while browsing through folders in a command line or terminal.

---

### Post by TristanMike on 2005-08-24
The reason that you are not getting where you want is because you used a space in the Shared(space)Music name. When running from the terminal, a space to it is the start of a new argument/directory/file.  If you wish to change directory to a folder with a space in it, either rename the folder and put an underscore "_" to seperate the two words(ie. Shared_Music) ....or you can just use quotation marks.```
cd Music
cd "Shared Music"
```This should be all you need.

---

