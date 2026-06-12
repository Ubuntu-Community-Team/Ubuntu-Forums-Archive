---
title: "[SOLVED] .rar extraction?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-11
Hey guys I have a .rar file that I need to extract what do I need to extract it and how do I get it, because the default extractor doesn't extract .rar which is pretty stupid.

---

### Post by jordanmthomas on 2008-02-11
```
sudo apt-get install unrar
```
Then, the default extractor can extract rars
rar is a "non-free" format which is why it isn't installed by default.

---

### Post by blasteryui on 2008-02-11
Thanks a lot!

---

### Post by Joeb454 on 2008-02-11
Not being able to extract rar's isn't stupid, when you take into account comment #2, and the fact that most people still use .zip

And most things for linux are .tar or .tar.bz or something like that :)

---

### Post by blasteryui on 2008-02-11
> **jordanmthomas said:**
> ```
sudo apt-get install unrar
```
Then, the default extractor can extract rars
rar is a "non-free" format which is why it isn't installed by default.

Wait this is what happens when I try that.
```
dexter@dexter-desktop:~$ sudo apt-get install unrar
[sudo] password for dexter:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unrar
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 97.0kB of archives.
After unpacking, 238kB of additional disk space will be used.
Err http://ca.archive.ubuntu.com gutsy/multiverse unrar 1:3.7.3-1.1
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
```

---

### Post by Joeb454 on 2008-02-11
What's your connection like?

---

### Post by jordanmthomas on 2008-02-11
Have you tried what it suggests?
```
 sudo apt-get update

``` then try again.

If it still fails, try
```
sudo apt-get --fix-missing
```

Most likely, the version you're trying to download not longer exists because you have an old package list.


edit:  actually, it's timing out...maybe try another mirror?

---

### Post by blasteryui on 2008-02-11
I did try the sudo update thing then tried again and still no go, what do you mean by try a different mirror.

---

### Post by jordanmthomas on 2008-02-11
In your /etc/apt/sources.list, you can change the address of where you get your packages from.  You appear to be using the canadian (ca) mirror.
I think it's just down at the moment, as I can't get the package from them either.
You should be able to download it from here and just double click it to install (you should already have all the dependencies).  This may be easier than selecting a new mirror.
[http://ftp.ussg.iu.edu/linux/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb](http://ftp.ussg.iu.edu/linux/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb)

---

### Post by Joeb454 on 2008-02-11
He means try getting the updates from a different server.

Like I said, what's your connection like? If it's not brilliant that might be your problem.

Also did you get a different error after you'd run ```
sudo apt-get update && sudo apt-get --fix-missing
```

*NOTE* the && means run the command before, then the command after :)

---

### Post by blasteryui on 2008-02-11
> **jordanmthomas said:**
> In your /etc/apt/sources.list, you can change the address of where you get your packages from.  You appear to be using the canadian (ca) mirror.
I think it's just down at the moment, as I can't get the package from them either.
You should be able to download it from here and just double click it to install (you should already have all the dependencies).  This may be easier than selecting a new mirror.
[http://ftp.ussg.iu.edu/linux/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb](http://ftp.ussg.iu.edu/linux/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.3-1.1_i386.deb)

Thanks it worked, but for future purposes, how do I change my servers from Canadian to American.

---

### Post by jordanmthomas on 2008-02-11
> **blasteryui said:**
> Thanks it worked, but for future purposes, how do I change my servers from Canadian to American.

I'd just change all lines that said ca.ubuntu......whatever to us.ubuntu.....whatever in my /etc/apt/sources.list

However, there appears to be a way to do it in System>Administration>Software Sources
I've not used Ubuntu in a long time, so you'd have to figure it out yourself from there but it should be easy.

---

### Post by blasteryui on 2008-02-11
Haha okay thanks, not used Ubuntu in a while? What do you use haha?

---

### Post by jordanmthomas on 2008-02-11
I've used Arch since January of 2007.
My Debain-ese is beginning to fail me.

---

### Post by blasteryui on 2008-02-11
Oh I see, what is this "Arch"

---

### Post by jordanmthomas on 2008-02-11
[http://archlinux.org/about/](http://archlinux.org/about/)
Read up.

---

