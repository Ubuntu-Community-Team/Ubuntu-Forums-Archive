---
title: "Installing java"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by neoltlink on 2005-12-19
Hi
I'm trying to install java. So I download to desktop, then type in the terminal:
```
chmod a+x jre-1_5_0-linux-i586.bin
```
which is the directions from the java site. 
It ends up saying:
```
neoltlink@ubuntu:~$ chmod a+x jre-1_5_0-linux-i586.bin
chmod: cannot access `jre-1_5_0-linux-i586.bin': No such file or directory
```
Any ideas?
Oh, I tried it after doing 'cd ~/Desktop', didn't work. Also tried with sudo at the beggining.

---

### Post by Evil Whisper on 2005-12-19
try doing it like this :-)

```

cd ~/Desktop

```

Then Type This and hit your tab key before hitting enter

```

chmod a+x jre-1

```

It should then automatically complete the file name for you.

---

### Post by Rackerz on 2005-12-19
If that fails try doing this instead; [http://www.ubuntuforums.org/showthread.php?t=76702](http://www.ubuntuforums.org/showthread.php?t=76702)

---

### Post by neoltlink on 2005-12-19
> **Rackerz]If that fails try doing this instead said:**
> http://www.ubuntuforums.org/showthread.php?t=76702[/url]
Alright, gonna try that, but could you also link a how-to on how to add all the extra repositories for ubuntu? Can't find anything on that, thanks. :)

---

### Post by Evil Whisper on 2005-12-19
To add the extra repositories (Universe & Multiverse)  goto System --> Administration --> Synaptic Package Manager 

Then in Synaptic goto Settings --> Repositories 

Then click Add and check the boxes for Universe & Multiverse then click OK.

---

