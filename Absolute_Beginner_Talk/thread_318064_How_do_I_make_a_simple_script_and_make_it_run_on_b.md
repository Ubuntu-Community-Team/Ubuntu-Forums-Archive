---
title: "How do I make a simple script and make it run on bootup??"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by elijahclarity on 2006-12-13
Every time when I get to my Dapper desktop I have to do the folowing to turn on the internet connection:

sudo -i (i give my password here)
/root/24onlineClient -u alfatek (this too asks for a password I've to give)

Is there anyway I can make all this happen automatically on every bootup?

I've heard that scripts can do such things.

So plz help me make such a script and get it to run automatically on login/bootup.

Thanks a lot for ur help:)

Btw "sudo /root/24onlineClient -u alfatek" does not do the task so I've to turn to the root user's path.

---

### Post by moshuptrail on 2006-12-13
A good question at this point might be:
Do you want it at bootup or when you log in?

---

### Post by moshuptrail on 2006-12-13
Here's an interesting result:

```
john@baggins:~$ echo $HOME
/home/john
john@baggins:~$ sudo -i echo $HOME
Password:
/bin/echo: /bin/echo: cannot execute binary file
john@baggins:~$
```

I have no idea what's going on.  Anyone else?

---

### Post by ciscosurfer on 2006-12-13
> **moshuptrail said:**
> Here's an interesting result:

```
john@baggins:~$ echo $HOME
/home/john
john@baggins:~$ sudo -i echo $HOME
Password:
/bin/echo: /bin/echo: cannot execute binary file
john@baggins:~$
```I have no idea what's going on.  Anyone else?The shell is trying to interpret running **echo** as **sudo**.  That won't work.  If you want to see what your $HOME is as root, you can issue ```
sudo -s -H
[I]enter your password
[/I]echo $HOME
```Or you issue this this little trick (othewise known as a bit of a hole ;))```
sudo /bin/bash
echo $HOME
```

---

### Post by elijahclarity on 2006-12-14
I want it to start up at bootup....I hope thats easy to do. Plz help me in this regard. Thanks

---

