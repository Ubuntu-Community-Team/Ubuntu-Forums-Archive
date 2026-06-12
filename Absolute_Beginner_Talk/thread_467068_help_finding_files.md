---
title: "help finding files"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-07
Grateful for some help finding the files the kids made just now in Tuxpaint, a kids' drawing program, that just 'saves to the album' wherever that may be, as I need to copy it over to the PC with a printer.... Tux has no documentation I ca find about where it actually saves stuff... but I'm sure there must be a standard command to search system wide for a file made this afternoon, isn't there?

---

### Post by John.Michael.Kane on 2007-06-07
Unless you specified a direct folder the files might have just been saved to you home folder.

something like /home/your user name/filename

---

### Post by bashologist on 2007-06-07
utfm?! n_n
```
man tuxpaint
```
[QUOTE="man tuxpaint"]       --savedir DIR
               Specify where Tux Paint should save files.  By default, this is "~/.tuxpaint/saved" under Linux and Unix, and "userdata\" under  Windows.
[/QUOTE]

---

### Post by whizbaby on 2007-06-07
Though I dont know tuxpaint I know what I would do:
sudo updatedb
locate jpg
locate jpeg
locate tiff
locate png
locate <whatever-format-tux-may-have-used>

I guess theres also a folder .tuxpaint/ in your homedir (/home/YOURUSERNAME/.tuxpaint/) and perhaps the pics are somewhere in there...good luck

---

### Post by whizbaby on 2007-06-07
> --savedir DIR
Specify where Tux Paint should save files. By default, this is "~/.tuxpaint/saved" under Linux and Unix, and "userdata\" under Windows.
lol it exists :))

---

### Post by John.Michael.Kane on 2007-06-07
Open Nautilus, and  click on view-->show hidden folders. Now look in side /home/your user name/.tuxpaint/saved

---

### Post by ginestre on 2007-06-07
> **bashologist said:**
> utfm?! n_n
```
man tuxpaint
```

Thank you: you've shown me, and I hope  I've learned, a new thing.

---

### Post by bashologist on 2007-06-07
> **ginestre said:**
> Thank you: you've shown me, and I hope  I've learned, a new thing.

Your welcome. It can be hard to look though man pages sometimes, so I suggest maybe pressing the "/" key then typing a keyword followed by "enter". This will highlight the keyword, and make things much easier to find.

---

### Post by whizbaby on 2007-06-07
> **bashologist said:**
>  pressing the "/" key then typing a keyword followed by "enter". This will highlight the keyword, and make things much easier to find.
Additionally if you hit 'n' during search, you jump to the next occurence of the keyword. If you hit 'N' you jump back to the last occurence.

---

