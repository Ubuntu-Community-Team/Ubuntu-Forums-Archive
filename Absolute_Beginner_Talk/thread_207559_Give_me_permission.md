---
title: "Give me permission???"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-07-02
Hello,

I'm trying to install Quake 4 and need to install certain files from my Quake 4 disc into a specified file within Ubuntu.  However, each time I try I am reminded that I do not have prmission.  Please could someone tell me if there is a simple piece of code that will remove this restriction from the whole of this system?  I am and will be the only user so there is no issue of anyone disrupting important system files.

Again thanks in advance for any help and suggestions provided.


Mark

---

### Post by GuitarHero on 2006-07-02
It isnt advised to run as root at all times, its very unsecure.  Use sudo in the terminal before a command to temorarily use root.  I dont know about this cd(it is a linux version isnt it?)

---

### Post by Norfolk 'n' Good on 2006-07-02
I appreciate the advice about running my system as root.  If I fowl the system up then I'll be the only one to blame!  In the meantime, in order to run the Quake 4 game, there are certain pak files on the CD that are required in the q4base file on my system, which at this moment I am unable to copy them accross.  Is there a simple piece of code that will give me the pemission to read/write to the files on my system?

Thanks once again.

---

### Post by Shampyon on 2006-07-02
I think entering *sudo nautilus* in the console will open up the file browser with root permissions. Just keep the console open while you're browsing, or it'll shut the file browser.

---

### Post by Absurd on 2006-07-02
If it's a directory you want premission for, use the following in the terminal

```
sudo chown <username>:<username> <directory>
```

That ought to let you install the files to the directory you want.

---

### Post by ubuntu_demon on 2006-07-02
If a command doesn't succeed and says something about a permissions problem. Make sure you understand what the command wants to do and you agree to it. If so then try putting "sudo' in front of it.

---

### Post by aysiu on 2006-07-02
[QUOTE=Shampyon]I think entering *sudo nautilus* in the console will open up the file browser with root permissions. Just keep the console open while you're browsing, or it'll shut the file browser.[/QUOTE]
Please do not use *sudo nautilus*. Use ```
gksudo nautilus
``` instead.

Reasons why: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

