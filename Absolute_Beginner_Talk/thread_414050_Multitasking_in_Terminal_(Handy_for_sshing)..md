---
title: "Multitasking in Terminal (Handy for sshing)."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-04-19
I'm putting this here as a reference for myself, and because information on the program I'm going to describe to hard to find just because of it's name.

Ok so have you ever been working on a machine with no desktop environment, and wanted to do more than one thing at a time.

Say your at the terminal and you do an update. Now while the update is running would it not be cool to go and preform some other task.

Or how about if your at work and the new Ubuntu Feisty Fawn 7.04 has come out, would it not be awesome if you could start the download at home via ssh? So it will be ready when you got home.

The program your after is screen. If you don't have it:
```
sudo aptitude install screen
```

Ok so how about I describe the Ubuntu Feisty Fawn 7.04 download. So I would.
```

ssh me@myhomecomputer
screen

```
Now we have a new terminal season. 
```

wget http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso

```
Now Ubuntu is downloading. To exit the season without closing it press
```
<CTRL> d
```
Now you back to the first season.

You can now do some other task etc. And you download will still be continuing. Now to check on your download you would go
```

screen -r

```

You can also have more than one screen.

Try [http://www.electricmonk.nl/index.php?page=TipsTricks#programs]("http://www.electricmonk.nl/index.php?page=TipsTricks#programs") and scroll down to "Screen - Console multitasking" for more information.

**Edit:** Also if you have a screen running in the background you can exit the ssh season and the screen will still be active.

---

### Post by Bachstelze on 2007-04-19
```
man screen
```

not very hard to find ;)

---

### Post by guysmiley25 on 2007-04-19
The man was not very clear to me. However the information is here for anyone who wants it.

---

