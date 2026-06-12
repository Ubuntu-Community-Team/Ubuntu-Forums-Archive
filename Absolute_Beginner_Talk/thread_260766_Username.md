---
title: "Username"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-09-19
How can i change my username but i need to keep my /home dir and the rest ofcourse.

---

### Post by Poeffie on 2006-09-19
Just change the name, change UID of your files and copy your home dir to /home/NEWUSERNAME

If somebody knows an easier way, please tell me..

---

### Post by roger99 on 2006-09-19
Try System -> Administration -> Users and Groups

---

### Post by Poeffie on 2006-09-19
You wont be able to change your username nor UID there, and when you change the /home dir, I dont think the files will be copied there.

---

### Post by Poeffie on 2006-09-19
1. Open your terminal
(! best is safe mode terminal (root preferred) or a root terminal in Ctrl+Alt+F1)
> nano /etc/passwd
(or sudo nano /etc/passwd if you're not root yet)
2. go to the line that starts with your old username
Change it to:
```
<NEW USERNAME>:x:<keep this>:<keep this>:<NEW FULL NAME>,,,:/home/<NEW USERNAME>:<keep this>
```
3. save and exit (Ctrl+O, enter, Ctrl+X)
4. > nano /etc/group
5. change the old name to the new one everywhere you find it
6. save and exit
7. Move the old files to your new home dir:
```
mv -r /home/<OLD USERNAME> /home/<NEW USERNAME>
```
8. Own the files to the right user:
```
chown -R <NEW USERNAME>:<NEW USERNAME> /home/<NEW USERNAME>
```

That should do the trick?
Check if the new home dir is really owned by the new user: ```
ls -alh /home 
```

[CENTER]*Can somebody please confirm this for me.. I'd hate it when I made a crucial mistake here*[/CENTER]

---

### Post by ignorance on 2006-09-19
I tried something like that today and the problem is my password or the new user isn't recognized. Wich is very unhandy :p.

---

### Post by Poeffie on 2006-09-19
Check if, after you've changed these things, users & groups also record these changes. Also restarting should make sure everything is according to the new settings.

---

