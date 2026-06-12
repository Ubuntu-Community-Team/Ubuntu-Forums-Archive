---
title: "Running X Windows under sudo -l"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2008-02-29
Hi.

I generally log into my main account, and use su -l to work as another user from the terminal.

Problem is, I want to be able to run X Window apps (like gedit) from that other user. However, when I try to do that, I get the following error:

```

cedric@cedric-desktop:~$ su -l webadmin
Password:
webadmin@cedric-desktop:~$ gedit
cannot open display:
Run 'gedit --help' to see a full list of available command line options.

```

Do I need to add this user to an x11 group or something?

Thanks.

---

### Post by WelshChris on 2008-02-29
Two steps are required.

1.  Enable other users to start X clients on cedric's Xserver.
2.  Start an X client, e.g. gedit on the correct display.

1. Run, as cedric, 'xhost +'.
    This allows *any user* to open clients on cedric's X server.  Note that this may 
    be a security risk.
2. As webadmin, start the X client, specifying the required display, i.e.
    $gedit textfile.txt --display :0
    (note the TWO hyphens.)

(At some point I'll learn how to enter code into this thing =/ )

---

### Post by glennric on 2008-02-29
Type
```
su -p -l webadmin
```
instead.

Edit:  You will still need to do what WelshCris said and type "xhost +" before you su in as the other user.  But then you don't have to add the --display option.

---

### Post by WelshChris on 2008-02-29
Ah, more elegant.  Even the working directory is preserved.

---

### Post by glennric on 2008-02-29
One thing about it is not quite as nice as your solution.  That is there is an annoying Gnome UI authentication warning in the terminal.

---

### Post by WelshChris on 2008-02-29
This appears to be a harmless bug according to many forums.  However, more worrying is this
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

So, using sudo and graphical X clients may have some unexpected side effects.  Probably not a problem with gedit, though.

---

