---
title: "how does one..."
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by urbaneezer on 2006-07-18
...do this?

> Cut and past an 'ls -l' of that directory

---

### Post by linuxnewbie946 on 2006-07-18
select the whole thing in console, right click, click copy, and paste it wherever!

---

### Post by xtacocorex on 2006-07-18
You could do this:
```

cd /go/to/directory
ls -l > ~/dirlist.txt

``` 
What this does is:
1) Changes directory to the directory you want to be in
2) Runs the ls -l command and then sends the output to dirlist.txt in /home/username

Then you can open the file up with your favorite text editor.

---

### Post by jvdowney on 2006-07-18
To get a copy of a directory listing, navigate to the directory in the terminal, then type ls -l. Right click and drag the mouse to highlight the contents of the list, choose 'cut', then paste the listing into the document (e-mail? forum reply?) you want to send.

---

### Post by jvdowney on 2006-07-18
Great, that's even better than my way. Still learning-

---

### Post by hellmet on 2006-07-18
dude just select and hit copy with ur mouse!!

---

### Post by urbaneezer on 2006-07-18
Alright...so here's the deal.  

I'm have a disc in my cdrom drive.  Where would the directory for this disc be located and how do I cd from a terminal window into it?

---

### Post by Arisna on 2006-07-18
Click Applications in the top-left corner of your screen.  Go to Accessories, and click Terminal (assuming you're using Ubuntu/GNOME).  Now type in the following:

```
ls -l /media/cdrom
```

Highlight the output and go to Edit -> Copy.  Go wherever you want to send it and hit Ctrl+V.

---

### Post by urbaneezer on 2006-07-18
Thanks folks!

---

