---
title: "install wine plz help im suicidal"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-07
right, i have the extra repositorys installed.
i have the repository from the wine website.
i have the to repositorys that i manualy installed in text editor for the gedit command.
none of the repositorys will work.
says e: blah blah blah
no package available.

tryed aptitude 
tryed gedit
tryed downloading source code. this downloaded but it got an error right at the last 2 or 3 lines.
then when i tryed to compile it with the code line thats on the website more errors and no success.
i then went the read-me and that told me to configure it with a different command.i tryed this command and it said permission denied.
so i went to the files and gave them all a check next to the write permission.(the two that shouldnt really need to be checked)
tried again said permission denied.
ok, must be sudo right?
tried that and it said you are logged in as root this is not recommended , try again as user.
has anyone got a sure-fire way of installing wine??
whoever helps me will be securing another ubuntu user as i am on the virge of giving up on ubuntu.
im suicidal.
life shouldnt be this hard.

---

### Post by jordanmthomas on 2006-10-07
Have you done
```
sudo apt-get update
```

oh...and don't kill yourself

---

### Post by uk_sphinx on 2006-10-07
yes i have m8
im on 8 pills so far, quick help before its too late

---

### Post by crazymonkey on 2006-10-07
[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=internet+explorer+wine]("http://www.ubuntuforums.org/showthread.php?t=149585&highlight=internet+explorer+wine")
I strongly recommend you this guide, it got my Wine running easily.

---

### Post by xpod on 2006-10-07
[http://www.samaratins.com/](http://www.samaratins.com/)

If all else fails;)

---

### Post by jordanmthomas on 2006-10-07
Try this
```
wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.5-6-6.06dapper1_i386.deb
sudo dpkg -i automatix_6.5-6-6.06dapper1_i386.deb
automatix

```

Use it to install Wine, then back in your terminal, run winecfg

---

### Post by shanepardue on 2006-10-07
i think winetools is a little outdated, but whatever works for ya! i just installed the latest wine from the repository and it worked fine.

---

