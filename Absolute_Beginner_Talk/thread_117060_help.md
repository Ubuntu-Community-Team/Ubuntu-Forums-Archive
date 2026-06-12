---
title: "help"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by russ1625 on 2006-01-14
help me please I am a new user I got sick of having to rebuild windows every month and my friend put me on to ubuntu breezy badger and I have enabled my repositories and can use my add remove programs.  but I am trying to install wine (if its not already i have tried before) I cant seem to get past the part where it says 0 new, 0 upgraded, 0 to remove and 36 not up graded. where do i go from here:???:

---

### Post by Perfect Storm on 2006-01-14
Have you:

[b]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
[/b]

In your sourcelist?

If you do:
```

sudo apt-get update
sudo apt-get install wine

```

more info: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by russ1625 on 2006-01-14
i have gotten to the part where I build the source but it says that it could not fetch the files and (13 permission denied)

---

### Post by bscbrit on 2006-01-14
If you do what Artificial Intelligence suggested, you do not have to build the program.  it simply installs itself and works....:p

However, you are trying to build as 'root' aren't you?

Try using the 'sudo' command to help during the build process.

---

### Post by russ1625 on 2006-01-14
how do i use the program once installed and what is it compatible with

---

### Post by bscbrit on 2006-01-14
[http://www.winehq.com/site/howto](http://www.winehq.com/site/howto)

[http://www.witch.westfalen.de/Wine-HOWTO/book1.html](http://www.witch.westfalen.de/Wine-HOWTO/book1.html)

---

