---
title: "Add no-ip2 to startup"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by makko on 2007-02-23
Hi,
I have tried google, and searching this site but with no luck..
I have installed the linux update software from [www.no-ip.com](www.no-ip.com) but I want to get it to start automatically with linux..How exactly do I do this?
I've tried going to  sessions>and adding it there but I cant remember where it was installed to ( i haven't gotten a grasp of the filesystem yet..)

Any good links to an explanation of the linux filesystem??

Thanks,

Makko

---

### Post by taurus on 2007-02-23
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
whereis no-ip
```

Usually binaries are installed in /usr/bin.

---

### Post by makko on 2007-02-23
that was it..I remember seeing it somewhere but couldn't find it..thanks taurus!

Anyybody know about the main problem,adding a program to startup that is??

---

### Post by taurus on 2007-02-23
You mean like

System -> Preferences -> Sessions -> Startup Programs -> Add.

---

### Post by makko on 2007-02-23
yea you see I tried that..added the noip2 executable from the extracted tar archive (because it was all the system could find..) and rebooted.
after reboot from the terminal:
sudo ps axu
said that noip2 wasn't running...
what about making a script and putting it in etc/init.d or something like that??

---

### Post by taurus on 2007-02-23
First, can you run noip2 from a terminal?  Does it require you to be root, sudo, when you run it?

---

