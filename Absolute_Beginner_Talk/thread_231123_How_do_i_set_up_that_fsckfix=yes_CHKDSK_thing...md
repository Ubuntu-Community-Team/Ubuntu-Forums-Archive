---
title: "How do i set up that fsckfix=yes CHKDSK thing..??"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-08-07
It's something like:

```
edit/etc/default/rcs
fsckfix=yes
```

Is that preaty close to being right..???

Do you know what i'm talking about..??

:confused:

---

### Post by 5-HT on 2006-08-07
Yup, there's a line for that already in /etc/default/rcS.
All you need to do is change it from no to yes.

---

### Post by jason.b.c on 2006-08-07
> **5-HT said:**
> Yup, there's a line for that already in /etc/default/rcS.
All you need to do is change it from no to yes.

So how do i get to it..???    What do i type in the terminal.?

I had part of that  written down on a piece of paper but i just  don't know how to do it..:-k

---

### Post by jason.b.c on 2006-08-07
*Bump*

---

### Post by jason.b.c on 2006-08-07
So i guess nobody knows....](*,)

---

### Post by jason.b.c on 2006-08-07
```
jason@Hp-Vectra-VL:~$ sudo edit /etc/default/rcs
Warning: unknown mime-type for "/etc/default/rcs" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
jason@Hp-Vectra-VL:~$

```


So what did i do wrong..???

---

### Post by mlind on 2006-08-07
> **jason.b.c said:**
> ```
jason@Hp-Vectra-VL:~$ sudo edit /etc/default/rcs
Warning: unknown mime-type for "/etc/default/rcs" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
jason@Hp-Vectra-VL:~$

```


So what did i do wrong..???

```

sudo **gedit**

```

or use nano.



I hope you know what you're doing, from rcS manual page
```

FSCKFIX=no
              When  the  root  and all other filesystems are checked, this happens with the -a flag which
              means autorepair. If there are really big inconsistencies, the fsck will bail out. The sys&#8208;
              tem  will  print  a  message  asking the administrator to repair the filesystem maually and
              present a root shell prompt (actually a sulogin prompt) on the console. [B]Setting this option
              to   yes[/B]  causes  the  fsck commands to be run with the -y option instead of the -a option.
              This will always repair the filesystems without any interaction but might irreversibly dam&#8208;
              age your file system(s).

```

---

### Post by jason.b.c on 2006-08-07
> **mlind said:**
> ```

sudo **gedit**

```

or use nano.



I hope you know what you're doing, from rcS manual page
```

FSCKFIX=no
              When  the  root  and all other filesystems are checked, this happens with the -a flag which
              means autorepair. If there are really big inconsistencies, the fsck will bail out. The sys&#8208;
              tem  will  print  a  message  asking the administrator to repair the filesystem maually and
              present a root shell prompt (actually a sulogin prompt) on the console. [B]Setting this option
              to   yes[/B]  causes  the  fsck commands to be run with the -y option instead of the -a option.
              This will always repair the filesystems without any interaction but might irreversibly dam&#8208;
              age your file system(s).

```

So then why have a how to thread for it...???   If it "can" possibly cause irreparable damage..[( Link ) HOW TO]("http://www.ubuntuforums.org/showthread.php?t=118260&highlight=fsckfix%3Dyes")

---

### Post by mlind on 2006-08-07
> **jason.b.c said:**
> So then why have a how to thread for it...???   If it "can" possibly cause irreparable damage..[( Link ) HOW TO]("http://www.ubuntuforums.org/showthread.php?t=118260&highlight=fsckfix%3Dyes")

I think you should ask this from the author of that thread or the writer of rcS manual page. 

Some of the e2fsprogs package manual pages are bit paranoid, but I'm sure there's a reason for that.. 
Usually it's not a good thing to mess with system wide settings without reading their corresponding manual page first.

---

### Post by jason.b.c on 2006-08-13
Well i thought i would actually just go for it and try this , But why oh why do i get a blank screen when i do this:
```
jason@Hp-Vectra-VL:~$ sudo gedit /etc/default/rcs
Password:
```


Am i supposed to get a blank screen...????      Did i do that right ..???

Could somebody please help me with this..??

---

### Post by jason.b.c on 2006-08-13
*bump*

---

### Post by sebbe1991 on 2006-08-13
> **jason.b.c said:**
> Well i thought i would actually just go for it and try this , But why oh why do i get a blank screen when i do this:
```
jason@Hp-Vectra-VL:~$ sudo gedit /etc/default/rcs
Password:
```


Am i supposed to get a blank screen...????      Did i do that right ..???

Could somebody please help me with this..??

Because it is case-sensitive

```
sudo gedit /etc/default/rcS
```

---

