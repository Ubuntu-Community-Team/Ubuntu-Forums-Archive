---
title: "Strange new problem..."
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by stravinsky on 2006-04-05
Since I've used automatix, I get strange contents in my CDs...
Have a look at a screenshot of a cd that is supposed to contain 2 folders with MP3s in it. I've seen it working in Ubuntu before, but now it looks like this.
Any idea what did I do and what can be a solution?
Thanks.

---

### Post by mlind on 2006-04-05
is this problem only for cdroms?

what's the character encoding/locale defined for your cdrom/dvd drive on /etc/fstab ?

mine looks like
```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by stravinsky on 2006-04-05
It's exactly the same code in my fstab.
The language is normal English. It has worked before and I didn't do anything...
Maybe it's the automatix...
Any other idea?
Thanks.

---

### Post by TrendyDark on 2006-04-05
why make two threads?

---

### Post by Sandlst on 2006-04-05
When you ran automatix, did you select the 'Eject cd on button push' option?  On my computer, I get a similar result when I eject the cd by just pressing the button, the next cd I put in has all the files listed as ??????, to test, try to eject the cd with ```
eject
```Then re-enter it and see if the problem clears up.  Hope this helps!

---

### Post by stravinsky on 2006-04-06
[QUOTE=TrendyDark]why make two threads?[/QUOTE]
Sorry, it was a mistake...

Indeed I have used the "eject with the button" in automatix. Is there a way I could come back? Or a fix for this problem? I don't mind ejecting it without using the button...
I thought it was a problem because of the option "MS TTF fonts" of Automatix... I'll try it later, but if any one has a permanent solution, it would be great.

Thanks!

---

### Post by stravinsky on 2006-04-06
So I've tried again and it was working!
When inserting another cd, however, it didn't work anymore, so I ejected the CD through the "eject" menu, and it worked fine after.

Does anyone have a **permanent** solution?
Thanks.

---

### Post by Sandlst on 2006-04-06
The closest thing I have to a 'permanent' solution is creating an icon on my gnome panel for ejecting cds....or just right clicking the mounted cd and hitting 'eject' through the menu....I too would be interested in finding a way to eject via button on my cdrom correctly though, anyone know how?  Ill try and find a solution myself and post back if I do........

---

