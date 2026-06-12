---
title: "[SOLVED] my computer doesn't let me edit files"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by crazyfuturamanoob on 2008-02-18
I got this folder:
> /usr/share/games/scorched3d

My problem is, that it doesn't let me do anything to that folder.
I want to edit the files. It says the owner is "root". I don't know root's pass,
so I can't log in as root and edit them. Please, tell me, what is root's pass or
tell me how to edit the rights so "arho" owns the files.
edit: PS. my acc is arho and it is set to admin. im the only user of this computer

Thanks.

---

### Post by randy78 on 2008-02-18
> **crazyfuturamanoob said:**
> I got this folder:


My problem is, that it doesn't let me do anything to that folder.
I want to edit the files. It says the owner is "root". I don't know root's pass,
so I can't log in as root and edit them. Please, tell me, what is root's pass or
tell me how to edit the rights so "arho" owns the files.
edit: PS. my acc is arho and it is set to admin. im the only user of this computer

Thanks.

In a terminal, type:
gksudo nautilus

then enter YOUR password

Then navigate to the folder with the files you'd like to edit ;)

---

### Post by brokenhachi on 2008-02-18
if you are the only user on the computer, then root pw is your pw.

---

### Post by crazyfuturamanoob on 2008-02-18
> if you are the only user on the computer, then root pw is your pw.
I tried it already, but MY pw isn't same than root's pw.
> In a terminal, type:
gksudo nautilus
Thanks, that worked.

Now my latest problem is, that how can I chance the folder's rights
so I can everytime edit its contents with _MY OWN PERSONAL_ account.
Im too lazy to do that everytime.

---

### Post by Joeb454 on 2008-02-18
You can't.

It's a built in security feature of Linux. It means no system files can be edited without your explicit permission.

And as far as I'm aware, my root pw is the same as my user pw (And I'm the only user)

---

### Post by brokenhachi on 2008-02-19
remember, linux is case sensitive. you might have accidentally put on caps lock and thats why your pw didnt work. like i said, if you are the one who installed ubuntu on the comp, root pw is your user pw.

---

