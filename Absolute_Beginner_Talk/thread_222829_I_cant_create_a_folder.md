---
title: "I cant create a folder"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by erciesielski on 2006-07-25
I'm learning so slow with this. I can't even create a folder. If I try to right-click, the option is greyed out. If I try to do it in terminal, it says permission denied. What am I doing wrong? I'm sure it's just a simple answer.:confused:

---

### Post by jordilin on 2006-07-25
In a console:
```
cd ~
```
you are in your home directory, then:
```
mkdir nameoffolder
```
mkdir makes a directory. You can do it with Nautilus. Right click and create a folder.

---

### Post by taurus on 2006-07-25
Where did you plan to create that folder???  If you create under your home directory, then do it as (from a terminal)

```

mkdir temp

```
But if you want to create a folder outside of your home directory, $HOME or ~/, then you need to include sudo in front as

```

sudo mkdir /opt/temp

```

---

### Post by erciesielski on 2006-07-25
Perfect. I was trying to make a folder in my usr folder. The sudo thing worked. Thanks.

---

### Post by erciesielski on 2006-07-25
Wait, no. It didn't work. Ok, what I'm trying to do is set up a dedicated server for counter strike. The program is trying to extract itself into usr/steam, but that program doesn't exist. I went into the properties of the usr folder and it says I can't change it because I don't own it. What do I do?

Edit: I tried to log in under user name "root" but it says that the password is wrong

edit: I figured out how to change the password. I'm logged on as root now and I can make the changes I need to. Thanks

---

### Post by aysiu on 2006-07-25
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) should help you.

---

### Post by Dr. Nick on 2006-07-25
Logging in under root isnt the best idea, it will work but sudo is a littlle safer.

If the script couldnt create a folder in /usr then maybe running the script with sudo would fix it.

---

### Post by mostwanted on 2006-07-25
I'm recommend you take a look at what aysiu posted.

---

### Post by taurus on 2006-07-25
I think the problem is in usr/steam instead of /usr/steam.  Therefore, you must move the file you want to extract to / first so when you unpack it, it will go to usr/steam...

---

