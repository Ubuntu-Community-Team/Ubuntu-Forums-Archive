---
title: "Open Terminal @ Location"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by NeonSphinx on 2008-02-13
Is there a way to open the terminal at a specified directory.
In our computer science class at school we're using xp, and we installed an add-on that allows us to right-click on a folder and open the command prompt right at that location.  I really dislike having to use the dir and cd commands all the time.
I'm on Gibbon, if that makes a difference
-Thanks

---

### Post by Origin415 on 2008-02-13
I dont know if there is something more efficient, but creating a progam launcher with the command
```
gnome-terminal -e 'cd */path/to/dir*'
```
should work, I would think...


(btw, I used dir when I first came to linux too, but then learned ls is a lot better, better formatted, and with colors!)

---

### Post by emarkd on 2008-02-13
How about:

```
sudo apt-get install nautilus-open-terminal
```

You'll have to restart Nautilus for it to take effect, which probably mean logging out and back in, but it'll give you a nice "Open Terminal" link on your right-click menu.

---

### Post by NeonSphinx on 2008-02-14
Omg that's great, it's even got  a nice little icon to the left of it.
Thanks

---

### Post by emarkd on 2008-02-14
You're welcome.

---

