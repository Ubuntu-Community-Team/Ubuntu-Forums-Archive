---
title: "Do not have permission to move files"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Noctiferis on 2007-05-19
Hi I'm new and I'm having a problem: I need to copy to /usr/lib but I don't have permission it tells me. I'm the administrator so how do I get permission??

---

### Post by richaoj on 2007-05-19
hit Alt + F2

enter gksu nautilus, 

browse to the files you want to move, and then change the ownership on them.

---

### Post by halitech on 2007-05-19
run this

```
gksu nautilus
```

but be very careful what you do here.

you could also open a terminal and use
```
sudo cp /location/of/file /location/where/you/want/it
```

---

### Post by bobplano on 2007-05-19
```
gksudo nautilus
```
for the GUI way (make sure i spelled nautilus right)
```
sudo cp /file/location /usr/lib
```

---

### Post by halitech on 2007-05-19
> **richaoj said:**
> 

browse to the files you want to move, and then change the ownership on them.

if he changes permission on the folder where he wants to move files to he'll end up with alot more problems then he has now. it's a case that he doesn't have write permission to the folder he wants to put them in, not the file he wants to move

---

### Post by richaoj on 2007-05-19
you are not logged in as root, and shouldn't be.  it presents inherent vulnerability problems.  this is one of the things it took a little bit of getting used to when switching from windows.  in win, when you are logged in as an administrator, you are logged in as root, and thus it is inherently unsafe. 
in ubuntu, when you are logged in as administrator, you have the ability to do root functions, but only after you enter your password.  

sudo and gksu are telling the computer to change you temporarily to a root user and thus can change stuff and thus perform administrative activities.  the session will time out after a bit, and then you are back to your normal user rights.

---

### Post by Noctiferis on 2007-05-19
Thanks guys!! all works now!!

---

