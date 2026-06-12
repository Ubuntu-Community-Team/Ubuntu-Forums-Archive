---
title: "Installing pygame in ubuntu"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by purplearcanist on 2006-12-13
I know this is a newbie question but...

How do you install pygame in ubuntu?

Here is the website for pygame.

[http://www.pygame.org]("http://www.pygame.org")

Curious, but I saw a download for Debian.:???:   I bet that is similar to Ubuntu.

---

### Post by md5 on 2006-12-13
Everything is written in [http://www.pygame.org/install.html](http://www.pygame.org/install.html)

---

### Post by po0f on 2006-12-14
purplearcanist,

Make sure you have universe repos enabled and run this from the terminal (or use Synaptic):
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install python-pygame[/FONT]
```

You can search either through Synaptic, the command-line or [packages.ubuntu.com](http://packages.ubuntu.com/) to see if a particular package resides in the repos, just for future reference.

---

### Post by SuperCow56 on 2007-02-28
Thanks a ton po0f you helped me out also :p

---

