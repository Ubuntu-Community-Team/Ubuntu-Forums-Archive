---
title: "2 problems"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by lee45 on 2006-07-22
I am having trouble installing google earth (GoogleEarthLinux.bin).
I'm sure i'm just putting some command in wrong.
Also, i have got driver for my lexmarkz605 printer, and it is sucessfully installed. It prints the lexmark test page, the cups test page, but nothing else.Any suggestions on that would help as well, thanx

---

### Post by abowman on 2006-07-22
```

sudo sh GoogleEarthLinux.bin

```

---

### Post by lee45 on 2006-07-22
hi abowman
    I got this response from the terminal. I double checked that i'm on the desktop, and the file is also on the desktop.

lee@lee-desktop:~$ sudo sh GoogleEarthLinux.bin
Password:
sh: GoogleEarthLinux.bin: No such file or directory

---

### Post by taurus on 2006-07-22
You need to be in a directory where GoogleEarthLinux.bin is!  Most likely it will be in ~/Desktop so change to that first before you run it...

```

cd ~/Desktop

```

---

### Post by lee45 on 2006-07-27
hi taurus.

this is what i got re: install google earth.  

lee@lee-desktop:~$ sudo sh GoogleEarthLinux.bin
Password:
sh: GoogleEarthLinux.bin: No such file or directory

also, still no luck printing anything but test pages.

---

### Post by avtolle on 2006-07-27
[http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+z605](http://ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+z605) might be helpful to you, if you hven't already looked at it. As far as I can tell from your posts, you are not in the Desktop directory. As Taurus suggested, change to the Desktop directory (cd ~/Desktop), then run the command.

---

### Post by lee45 on 2006-07-27
ok, google earth now installed, thanks to the desktop thing (here i foolishly thought that desktop meant i was on the desktop)
i looked over the link to printers, but dosen't seem to address whatever the issue with mine is. Mine will print the test pages, so it's installed and all OK, but just won't print anything else.
thanx for the desktop help, glad to be googling earth :)

---

