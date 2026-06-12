---
title: "Where to find my $PATH variable."
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by chadbst on 2006-11-06
I am trying to install a program that says that there is no acceptable cc found in $PATH.  However, I have installed gcc by using Synaptic.

The question that I have is how do I check the $PATH variable or any global variables for that matter.  I have read a few threads that said that I should look in /etc/profile, but I have no directory named /etc/profile.   Is there somewhere else that I can go to check the $PATH environment variable.

I am running Dapper 6.06.

---

### Post by taurus on 2006-11-06
Did you install gcc or did you install build-essential?  

```
sudo aptitude install build-essential
```
You can add more directories to your path in ~/.bashrc...

```
gcc -v
```

---

### Post by marianom on 2006-11-06
Look for .bash_profile in your home directory. Might be of help.

---

### Post by bsussman on 2006-11-06
> **chadbst said:**
> but I have no directory named /etc/profile. 

Very true - but I bet you have a file with that name.

And the first line of it will tell you what it is meant for.

I don't think it is your problem though - it has all the standard locations on it.

More likely something is not installed correctly.  did you install build-essential?

---

### Post by chadbst on 2006-11-06
Thank you all very much for the replies.  This is why I love Ubuntu - because it has great users on the forums!  Taurus and Bsussman, I have installed build-essential and the ./configure is actually starting to run. 

Just so other newbies who are searching this thread know, I do have a file named profile in /etc/profile

Thank you very much folks.

---

