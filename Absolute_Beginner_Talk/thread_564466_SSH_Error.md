---
title: "SSH Error"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by mattc908 on 2007-10-01
I've been able to SSH into it for a couple of months now untill this popped up when I tried again:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
c6:7f:90:f6:b2:e4:6c:af:e6:c4:54:4b:86:89:34:d1.
Please contact your system administrator.
Add correct host key in /Users/MattC/.ssh/known_hosts to get rid of this message.
Offending key in /Users/MattC/.ssh/known_hosts:4
RSA host key for 192.168.1.104 has changed and you have requested strict checking.
Host key verification failed.

What should I do?

---

### Post by hyper_ch on 2007-10-01
Well, this error appears because the RSA key on the computer that you are trying to connect to has changed. This can be the case if the other computer was freshly installed...

It's a warning that something has changed (e.g. dns-poisoning). If you are 100% sure it's the right machine you want to connect to, open your known_hosts files ( ~/.ssh/known_hosts ) and delete the entries for that computer you are trying to connect to.

I don't really know how to filter the one entry the remote computer belongs to, so I normally delete them all.

---

### Post by justleen on 2007-10-01
you can open the file, and you should be able to see the different hosts..

But, its quicker to just delete the whole file. one scenario where you dont want to delete the know hosts file, is if you have already running batch jobs.. those will fail, since you have to accept the knew finger print.

---

### Post by ruibernardo on 2007-10-01
Of course he can delete the whole file, but if he has many fingerprints of many servers, he will have to accept them again, without knowing if those had changed too or not.

> **mattc908 said:**
> 
Offending key in /Users/MattC/.ssh/known_hosts:4


As the message says, the offending key is in line 4, so you can open the file with a text editor and delete that line. With nano:

```
nano ~/.ssh/known_hosts
```

Go to line 4, press Ctrl+k to delete that line, then exit with Ctrl+x and save pressing y.

---

### Post by mattc908 on 2007-10-03
I typed this in:
```

sudo nano /Users/MattC/.ssh/known_hosts

```

there was nothing in the file.......... and what is the remove command?

---

### Post by dwhitney67 on 2007-10-03
Do not use sudo.  If you do not know nano, then use vim, gvim, gedit, etc.  Delete line 4.

P.S.  Note that "line 4" may appear as many lines, but it is in fact just one line.

---

### Post by mattc908 on 2007-10-03
You can use sudo or not doesnt matter, but there IS NO file I access it and its completly blank.............. so I just wana remove it but I dont remeber the command see if that works.

---

### Post by llamakc on 2007-10-03
Are you in the correct directory?

In a Terminal type:

cd ~/.ssh && ls

and post the output here.

---

### Post by llamakc on 2007-10-03
Why does your first post have this:

Add correct host key in /Users/MattC/.ssh/known_hosts to get rid of this message.

--The /Users/ part? Why is that not /home? 

The error occurs on the machine you're trying to ssh FROM and not TO.

---

### Post by Bachstelze on 2007-10-03
> **llamakc said:**
> Why does your first post have this:

Add correct host key in /Users/MattC/.ssh/known_hosts to get rid of this message.

--The /Users/ part? Why is that not /home? 


[http://en.wikipedia.org/wiki/GoboLinux#The_GoboLinux_hierarchy](http://en.wikipedia.org/wiki/GoboLinux#The_GoboLinux_hierarchy)

---

### Post by llamakc on 2007-10-03
> **HymnToLife said:**
> [http://en.wikipedia.org/wiki/GoboLinux#The_GoboLinux_hierarchy](http://en.wikipedia.org/wiki/GoboLinux#The_GoboLinux_hierarchy)

Thanks. I've not run into that before.

---

