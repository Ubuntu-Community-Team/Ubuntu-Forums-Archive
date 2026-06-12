---
title: "permissions query"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by rob7391 on 2008-03-25
I have an external hard drive to which I have written heaps of stuff.
No problem.
Every now and then it won't let me write saying I don't have permission. I check the permissions and I have read, write and execute permission. Why does it do this?
Anyone help?

---

### Post by kpkeerthi on 2008-03-25
Can you post the output of
```
ls -ld /media/<mount-point>
```?

* **/media/<mount-point>** is where your external drive is mounted.

---

### Post by rob7391 on 2008-03-25
how do I look at that exactly????
:)

---

### Post by wormser on 2008-03-25
Just run this command and post the output.

```
ls -la /media/
```

---

### Post by sarum on 2008-03-25
'
how do I do that exactly

Go to Applications then Accessories then Terminal and type in what 'wormser' said and press 'enter'
High light the contents by left-click-hold-down over the page. Then right click, press 'copy'
Open up this thread again and left-click and find paste; Click and what you copied should be printed.
Hope this helps.

---

### Post by ssmokey on 2008-03-25
sorry to hijack the thread, I didn't want to create another one. 

I am having a similar issue with writing to my IRiver X20 - I am able to copy files off of it, however I cannot paste. I did the above command and this is the outcome

/media/:
[COLOR="Cyan"]cdrom [/COLOR] [COLOR="Blue"]cdrom0  iriver X20[/COLOR]

---

### Post by jan quark on 2008-03-25
open the terminal

applications > accessories > terminal and copy and paste this commands and hit enter

```
ls -la /media/
```

the output should be something like this:
**this is my ls -la /media output**
> jan@ubuntu:~$ ls -la /media/
total 12
drwxr-xr-x  3 root root 4096 2008-03-25 12:30 .
drwxr-xr-x 21 root root 4096 2008-03-17 23:04 ..
lrwxrwxrwx  1 root root    6 2008-03-13 04:35 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-03-13 04:35 cdrom0
-rw-r--r--  1 root root    0 2008-03-25 12:30 .hal-mtab


---

### Post by ssmokey on 2008-03-26
so how do  you set the permissions

---

### Post by jan quark on 2008-03-26
you change the permissions with this code

```
sudo chown -R usr:usr CU

sudo chmod -R 755 CU
```

first line changes the user. you have to change usr:usr to your username for instance john:john 
change the CU to the path of the folder or file you want to change

for instance
```

sudo chown -R john:john /path/to/folder
```

the second line changes the actual permissions, change CU to the path to folder or file

---

