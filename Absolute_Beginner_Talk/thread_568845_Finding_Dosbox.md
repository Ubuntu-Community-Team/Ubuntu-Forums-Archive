---
title: "Finding Dosbox"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Arukas on 2007-10-06
Hello-

  I need to modify my dosbox cfg so it will boot up right, and when I was going to do that I realized...

  I have no clue where it is at on my harddrive?  I know so far all my programs are in my user folder, but i can't find a "dosbox" one.  Let alone, do i know what folder it installed too, like most other programs.  

  Anyone know how I can locate the dosbox directory, and other directories that I don't know where they are?  The search function doesn't seem to do a global search.

-Arukas

---

### Post by taurus on 2007-10-06
Not sure exactly what you mean boot up right?  Your machine is having a problem at boot?  Look in /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```
Better know what you are doing or you can trash it and then you can't boot your Ubuntu anymore.

---

### Post by klytu on 2007-10-06
> **Arukas said:**
> Hello-

  I need to modify my dosbox cfg so it will boot up right, and when I was going to do that I realized...

  I have no clue where it is at on my harddrive?  I know so far all my programs are in my user folder, but i can't find a "dosbox" one.  Let alone, do i know what folder it installed too, like most other programs.  

  Anyone know how I can locate the dosbox directory, and other directories that I don't know where they are?  The search function doesn't seem to do a global search.

-Arukas

Try this command (in a terminal console): ```
sudo updatedb
``` Let that finish running, and then```
 locate dosbox
``` You can also search for other directories or files with the **locate** command. For more information: ```
man locate
```

---

### Post by willz06jw on 2007-10-06
Yea I am looking for the dosbox directory also to change a file so I can use The Sierra Network.  Let me know if you find anything.

Thanks,
Will

---

### Post by mdebusk on 2007-10-06
> **Arukas said:**
>   I need to modify my dosbox cfg so it will boot up right, and when I was going to do that I realized...  I have no clue where it is at on my harddrive?

You probably don't have one. From what I understand from reading the README file (found at
/usr/share/doc/dosbox/README.gz on my system) you don't get a config file by default.

Short answer is to open a DosBox window and type: ```
CONFIG
```. That'll give you a config file with default settings. Read the README and it'll tell you in more detail what to do.

---

### Post by Arukas on 2007-10-07
Hello-

  the locate command is what let me found the dosbox.  And no, This is not a boot problem.

Thanks,
Arukas

BTW-
If you wanted to know where i found it, it was here

/usr/bin/dosbox

---

