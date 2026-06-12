---
title: "Desktop Shortcut to a program"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by marko_4454 on 2006-07-28
I have searched around the forums but cant find anything like my program. Some are really close but none get it completely right :s

I have a program called HO.sh in the path /usr/lib/HO/HO.sh and I would like to make a desktop shortcut (launcher). I tried this:

```

ln /usr/lib/HO/HO.sh /Desktop/HOshortcut

```

But it doesnt seem to work. I know that in the terminal you have to use the command "sh" but I dont know if I have to put it in the command for the launcher somewhere.
Thanks for your help,
Marco

---

### Post by hw-tph on 2006-07-28
First make the file executable: **sudo chmod +x /usr/lib/HO/HO.sh**

Then, you should create a symbolic link rather than a hard link. You create a symbolic link by passing the -s option to the ln command: **cd** to ~/Desktop and type **ln -s /usr/lib/HO/HO.sh .** (observe the final dot, meaning "right here" or this directory).


Håkan

---

### Post by marko_4454 on 2007-03-22
thanks...

---

