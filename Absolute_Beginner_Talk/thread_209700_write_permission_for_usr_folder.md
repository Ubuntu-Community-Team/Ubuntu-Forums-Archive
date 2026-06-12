---
title: "write permission for usr folder"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Arthur Millar on 2006-07-05
How do i set write permitions to usr/local/games?

---

### Post by ed_d on 2006-07-05
Better to explain:

r=4, w=2, x=1
r=read, w=write, x=execute

man chmod

Use with caution!

sudo chmod -R 775 /usr/local/games 

which should give rwx to owner and group and r_x to user, IIRC. the -R will do it recursively within that directory, of all the files. Best way would be to do it for each game itself

---

### Post by LKRaider on 2006-07-05
Why would you want to? If you want to install for all users, use the sudo command.

If you want to install just for you, you can write on your home folder.

---

### Post by Arthur Millar on 2006-07-05
didnt work 
where can i install ?

---

### Post by Arthur Millar on 2006-07-05
im trying to install doom3 
doom3-linux-1.3.1302.x86.run
i managed to change the user permissions to run the file but now i cant copy the data anywhere
usr/local/games 
or my home folder

---

### Post by aysiu on 2006-07-05
Changing permissions on a /usr folder is a *really* bad idea. Those permissions are there for a reason.

Why not just run it with root privileges? ```
chmod +x doom3-linux-1.3.1302.x86.run
sudo ./doom3-linux-1.3.1302.x86.run
```

Further reading:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by steve.horsley on 2006-07-05
[QUOTE=aysiu]Changing permissions on a /usr folder is a *really* bad idea. Those permissions are there for a reason.
[/QUOTE]To put it another way, it's  really *really* **really** bad idea. You don't want to change peremissions permanently - just borrow root priviledge while you put doom3 there.> 
Why not just run it with root privileges? ```
chmod +x doom3-linux-1.3.1302.x86.run
sudo ./doom3-linux-1.3.1302.x86.run
```

I second this. It's how I installed doom3. Doom3 is excellent. Awesome, even.

---

### Post by LKRaider on 2006-07-05
I would even go further and say not to install non-debian packages on **/usr**, but instead put them on **/opt** ( I actually prefer _/home_, and install as a regular user even) for a better system managment.

---

