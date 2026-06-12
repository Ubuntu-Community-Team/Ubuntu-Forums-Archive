---
title: "sudo operations from Konqueror?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Optiker on 2006-06-29
I've finally managed to get comfortable with using sudo from the command line to do various things. However, for day-to-day work, I'd rather work from a GUI. Today  I DLed a tar file and wanted to create a new folder for the app in /usr/local/bin using Konqueror, but I was denied. I created the folder in the command line, but when I then tried to move the DLed tar file from my home folder, untar, etc., I was again denied in Konqueror. Rather than try to figure out the syntax to do it all in the command line, I took the coward's way out and went back to Windows and using the ext2 utility, did all of that manipulation from Windows.

I don't want to have to do that all the time, and I don't want to have to work from the command line for all of those relatively trivial operations that pop up all day long. I suppose I could login as root, but would rather not to that either.

Is there a way to launch Konqueror in a sudo mode? If I recall, back when I was trying to learn Linux on Mandrake 10, I could, from the KMenu, enter Konqueror (or some other file management app - don't recall) as root to do these kinds of things. Anything like that possible in Kubuntu? In my  environment, I'm not overly concerned about working in root for security reasons, but would rather not since I don't want to risk doing something dumb and messing the whole works up.

Thanks!
Optiker

---

### Post by tonyr on 2006-06-29
On the command line:
```

sudo konqueror

```

You will get a password prompt; enter **your** password.  When
I do this,  I get some of complaints/reports in the terminal, but **konqueror** comes
up and will let me create files which show up owned by root in directories owned
by root.

---

### Post by Optiker on 2006-06-29
tonyr...thanks! exactly the kind of thing I was looking for!

Optiker

---

### Post by Jucato on 2006-06-29
Just a little correction:
when launching graphical apps, use kdesu instead of sudo. So it will be
```
kdesu konqueror
```

Another thing, you don't have to do it in the command line. Just hit Alt+F2 (Run command) and type in the same command (kdesu konqueror). It will also ask for your password.

---

### Post by Optiker on 2006-07-03
[QUOTE=Fenyx]Just a little correction:
when launching graphical apps, use kdesu instead of sudo. So it will be
```
kdesu konqueror
```

Another thing, you don't have to do it in the command line. Just hit Alt+F2 (Run command) and type in the same command (kdesu konqueror). It will also ask for your password.[/QUOTE]

Just curious...why kdesu instead of sudo, since sudo works fine?

Thanks for the Alt-F2 comment...saves a little.

Optiker

---

### Post by Jucato on 2006-07-03
From [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **NEVER** use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

---

### Post by aysiu on 2006-07-03
[QUOTE=Optiker]Just curious...why kdesu instead of sudo, since sudo works fine?

Thanks for the Alt-F2 comment...saves a little.

Optiker[/QUOTE]
This is why:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Optiker on 2006-07-03
aysiu...OK...understand. I'll use kdesu.

Thanks!
Optiker

---

### Post by editrix on 2006-07-03
> Quote:
NEVER use sudo to start graphical programs....

Could someone explain how we can tell what's a graphical program? Anything we launch is going to have a pretty frame around it, with Xs and arrows at the top to size or close the window. Or at least give us a list of what's safe to use sudo for. Talk about Absolute Beginner questions!

---

### Post by aysiu on 2006-07-03
Well, any program you can see anything for besides numbers, letters, and symbols within the terminal is a graphical program.

Not anything you launch is going to have a pretty frame around it with Xs and arrows, etc. For example, *aptitude*. Go ahead type ```
sudo aptitude update
``` and tell me if it launches a pretty frame. Or you can also try ```
mogrify -resize 50x50 *.jpg
``` and see if there's a pretty frame. Or ```
sudo nano /etc/fstab
``` and see if there's a pretty frame.

Many programs are terminal programs, not graphical ones.

---

### Post by editrix on 2006-07-04
[QUOTE=aysiu]Well, any program you can see anything for besides numbers, letters, and symbols within the terminal is a graphical program. ...
Many programs are terminal programs, not graphical ones.[/QUOTE]

Thanks for this. I had a time getting my head around it, and this is how I explain it to myself: If what you're typing **doesn't** launch something with a pretty frame around it, it's a non-graphical program, and you use sudo. Otherwise, kdesu.

---

