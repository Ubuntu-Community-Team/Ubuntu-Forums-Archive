---
title: "[SOLVED] Needing terminal command to open Epiphany Web Browser to open new tab and go"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-16
I'm wanting to set my Mail Watcher to open a new tab in epiphany and to go [http://gmail.com](http://gmail.com). I found a guide to configuring it here:

[http://xubuntublog.wordpress.com/2007/04/27/email-notification/](http://xubuntublog.wordpress.com/2007/04/27/email-notification/)

All the directions are great and easy to follow, except when it comes to setting that part as it gives directions on how to do it with firefox

```
firefox -new-tab http://gmail.com
```

i tried replacing firefox with "epiphany-browser" but it didn't work

So in short, does anyone know the terminal command to opening a new tab in epiphany?

---

### Post by jakupl on 2008-03-16
manually open Epiphany

in the terminal write 
```
ps -A
```
"remember, it is case sensitive"

now you should see a list of all running processes, including the process name of Epiphani.

now try to write
```
"process name of epiphani" -new-tab http://gmail.com
```

where "process name of epiphani" is the exact name given to you in the list

---

### Post by whoscheesemine on 2008-03-16
Actually, I should have added that I already tried replacing firefox with "epiphany-browser" which is the process name of Epiphany Web Browser. Thank you anyways.

---

### Post by Lord Illidan on 2008-03-16
Try ```
epiphany-browser --new-tab
``` or else just ```
epiphany-browser -n
```

```
man epiphany-browser
``` is also helpful

---

### Post by whoscheesemine on 2008-03-16
> **Lord Illidan said:**
> Try ```
epiphany-browser --new-tab
``` or else just ```
epiphany-browser -n
```

```
man epiphany-browser
``` is also helpful

Thank you, the first code, worked. That lil dash made all the difference!

---

