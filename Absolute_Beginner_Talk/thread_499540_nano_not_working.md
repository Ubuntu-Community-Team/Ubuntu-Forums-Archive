---
title: "nano not working"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2007-07-12
ok i tried adding syntax color to my nano while programming and now whenever i type nano -w it brings up unknown symbals... i can still program its just unreadable.. please someone help!!!!:confused:    

i have tried mulitple things such as 
```
sudo apt-get remove nano
```
and 
```
apt-get install nano
```

neither have worked and the link below is the directions i followed to try and get syntax color in terminal 

[http://ubuntuforums.org/showthread.php?t=62250&highlight=how+to+add+color+terminal+while+programming]("http://ubuntuforums.org/showthread.php?t=62250&highlight=how+to+add+color+terminal+while+programming")

can anyone help :confused:

---

### Post by Al3xK3aton on 2007-07-12
Clearly the problem is that you tried to put syntax color in. What you need to do is to take it back out. Then it should work.

---

### Post by tennvolsmb on 2007-07-12
how do i do that

---

### Post by diatribe on 2007-07-12
the opposite of the way you tried to enable it?

---

### Post by tennvolsmb on 2007-07-12
can you be more specific.. im very new to linux i mean like detailed instructions.. if you have the time that is...

---

### Post by diatribe on 2007-07-12
ok i tried adding syntax color to my nano


ok what did you do to accomplish this?  just undo the changes you made

---

### Post by tennvolsmb on 2007-07-12
ok basically what i did was change around my nanorc file in the nano examples folder and it says i dont have access to the root file file it says permission denied.. the one step i couldn't do in the whole thing was move the nanorc file to the home directory.. now what should i do?

---

### Post by Al3xK3aton on 2007-07-12
You need to log in as the root user so that you can change it back. Root users can do pretty much anything, so I'd advise using a root account as your primary account in case this happens again.

---

### Post by tennvolsmb on 2007-07-12
how to i log into the root account i thought the account that is created when i dual booted it was the root account???

---

### Post by Al3xK3aton on 2007-07-12
The root account AFAIK has the username root, but I think the user specifies the password. If your username isn't root, it's probably not the root account.

---

### Post by tennvolsmb on 2007-07-12
ok thanks ill try that

---

### Post by tennvolsmb on 2007-07-12
ok well i cant find out how to access the root user... does anyone know the default for roots...

---

### Post by jsmiith on 2007-07-12
Ubuntu does not create a root account by default. You will need to create one with full permissions to login as root.

---

### Post by tennvolsmb on 2007-07-12
ok thanks

---

### Post by tennvolsmb on 2007-07-12
ok so i attempt to create the root account and it says user already exists how do i access it when there is no root account being shown.. please be specific with me. thanks

---

### Post by twiceasworn on 2007-07-12
First of all, ubuntu doesnt have a root account for a reason.  You can do everything you would do as a root user by typing sudo before whatever the command is.  So, to edit a text file you would use something like```
 sudo nano /path/of/file
```  This allows you to access superuser powers only when you need to so you don't accidently bork something.  I highly suggest leaving the root account and using sudo instead.

---

### Post by tennvolsmb on 2007-07-12
ok ill try that

---

### Post by tennvolsmb on 2007-07-12
but assuming i wanted to acess root how would i?

---

### Post by tennvolsmb on 2007-07-12
also when i tried the sudo command to access it, it did the same thing as before, give me characters that are unreadable

---

### Post by ReverendJ1 on 2007-07-13
Accessing the root account in Ubuntu is possible, but it is hard and really not a good idea. Ubuntu was designed to just use sudo instead. 
I am not positive, but I am sure if you move that file you couldn't it would probably work. Use sudo if it is giving you permissions errors. i.e.
```
sudo mv /path/to/nanorc.example ~/.nanorc
```

If that doesn't work, start over. :-)
```
sudo apt-get remove nano
```

Make sure it got rid of everything. Do a 
```
cd /
sudo find -name nano
```

If any folders show up then delete them. i.e.
```
sudo rm -rf /bin/nano
```

Now also doublecheck there are no nano configs in your home directory (where all your settings are stored).

```
cd ~
find -name *nano*
```

If there are any files, delete them.

Now reinstall.

```
sudo apt-get install nano
```

I hope that helps!

---

### Post by tennvolsmb on 2007-07-13
that was the problem thanks but i just decided to take a live cd of feisty fawn and replace my old version with that it. but thanks anyways

---

### Post by ReverendJ1 on 2007-07-13
You're welcome. I'm just trying to help out a little. :-)

---

