---
title: "directory structure query"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by maclenin on 2007-01-19
Maybe it's because it's late - but I am having trouble getting my last brain cell around (this particular aspect of) the linux directory concept....

With specific reference to the following examples:

1. I made a directory called "home" in my "/home" or "~" or "~/" directory:

```
ubuntu@ubuntu:~$ mkdir home
```

2. While taking a quick peek at the Thunar File Manager ("Thunar"), I found my new "home" directory in (the way in which I navigated the GUI) /home/ubuntu/home. I then changed directories, via the terminal, in the following manner:

```
ubuntu@ubuntu:~$ cd /home/ubuntu/home
```

**3.** With the following result:

```
ubuntu@ubuntu:~/home$
```

4. After another glance at Thunar, with a similar result, I then changed directories, again, in a slightly different manner:

```
ubuntu@ubuntu:~/home$ cd /home/ubuntu
```

**5.** With this slightly different result:

```
ubuntu@ubuntu:~$
```

My post-midnight logic (coupled with what I witnessed via Thunar) tells me (perhaps naively) that the results of **3.** and **5.**, respectively, should read:

my **3.**

```
ubuntu@ubuntu:~/ubuntu/home$
```

my. **5.**

```
ubuntu@ubuntu:~/ubuntu$
```

Where does the /ubuntu "directory" appear in either of the actual output examples (**3.** and **5.**)? Is /ubuntu not a real "location"? Is this not the way to perceive it: /home/ubuntu?

I am trying to get a handle on this issue (among a handful of other issues), before I cut the livecd umbilical and begin the installation / partitioning process....

---

### Post by pizzutz on 2007-01-19
the ~/ directory is equal to /home/<username>/

You set your username to ubuntu, so your ~/ directory is /home/ubuntu/  if you had multiple users on your os, they would each have thier own "home directory"  in the /home directory.  so the short answer to your question is that /ubuntu is already included in ~.

---

### Post by maclenin on 2007-01-19
So, for example:

User "tom" logs is as "tom" and his /home command prompt looks like this:

tom@umbuntu:~$

If "tom" were to add a "home" directory, as I did, in my example, and he were to cd into that directory (cd home), it would look like this:

tom@umbunti:~/home$

Where ~ is the "collective" equivalent to: /home/tom....

---

### Post by bodhi.zazen on 2007-01-19
> **maclenin said:**
> So, for example:

User "tom" logs is as "tom" and his /home command prompt looks like this:

tom@umbuntu:~$

If "tom" were to add a "home" directory, as I did, in my example, and he were to cd into that directory (cd home), it would look like this:

tom@umbunti:~/home$

Where ~ is the "collective" equivalent to: /home/tom....

That's it :twisted:

---

### Post by maclenin on 2007-01-19
Eureka!

(Thanks!)

---

