---
title: "How do I...?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-07-20
Hello,

I recently installed a small windows program into Dapper that opens via Wine.  The only way to launch it, however, was to go to 'Places' > 'Home Folder' > press 'Ctrl+h' and then I could see the '.wine' folder.  I would open that, select 'drive_c' then click on 'Program Files'.  Eventually I could find the desired program then I would navigate through that folder until I located the program .exe I wanted.  I could then run the program by clicking on that.  What a palaver!

In the end I decided to copy the .exe file and pasted it to my Ubuntu desktop.  My question is, how do I change the current icon (a binary file icon) to one that is a little more 'fit-for-purpose'?

Thank you

---

### Post by geco on 2006-07-20
Alternative suggestion.
From terminal:
```

editor my_wine_prog

```
where my_wine_prog is the name you want for your file
edit the file:
```

#!/bin/sh
wine "C:\Program Files\Program Directory\Program.exe" > /dev/null 2>&1

```
( "> /dev/null 2>&1" i soptional and redirects errors to the null device, so they don't bother you)
save it an make it executable with
```

chmod +x my_wine_prog

```
move it where you prefer (e.g. to your Desktop)
and lauch it by clicking!

byebye

---

### Post by matthew on 2006-07-20
To change the ***icon,*** right click on it and choose "properties." I believe there is a place in the dialog box that lets you change/choose whatever icon you want. (Hint: you might look in /usr/share/pixmaps for some to choose from if you don't already have one in mind)

EDIT: I just looked to confirm. In the dialog box that pops up, choose the "basic" tab. Click on the picture that contains the current icon to change it.

---

### Post by aeto on 2006-07-20
wont it help by just simply creating a launcher? i did that with Wine Firefox..just created a launcher on the desktop, put command as ```
wine "location/program.exe"
``` and 'twas done.

---

### Post by Norfolk 'n' Good on 2006-07-20
Hi Guys and Gals

Thank you very much for your suggestions, I kow have a link on my desktop and a much better icon.

This really is a very helpful site.  Keep up the good work


Regards


Mark

---

