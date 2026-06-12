---
title: "Terminal Commands"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by azkehmm on 2006-11-24
Hi everyone

I've revently installed ubuntu on my PC, and I must say, so far I really like it. Being a long time Windows user, the whole Linux-pc concept is a little new to me (e.g. that my harddrives are listed as /media/hda1 and so on :)). But I really like what i see. Especially, the terminal concept brings back good memories from the good old DOS days. So, now I need to figure out if I've got the terminal concept right.

 - If i use "sudo" in front of any command, I'm operating as admin/root.

- Anything i can do in the graphical interface, I can do in the terminal, and a good deal more?

- If I want to operate as admin/root the only way to do it is using the terminal (considering the "gksudo nautilus" bug present in both Dapper and edgy)?

- Finally, can someone please point me in the direction of a guide/list with terminal commands. Like how to create directories and navigating around and stuff (like "cd ****","md ****" and "dir" and stuff like that :))

Thanks in advance.

---

### Post by nickburns on 2006-11-24
To make a directory it is 'mkdir /home/yourname/newfolder/'

To move up a directory it is 'cd thenNextFolder/'

To move down a directory it is 'cd ..' (don't forget the space)

Your right about sudo, it does run as root permissions, 

for all other commands, I usually will come back to this forums for specific needs, I don't know of a better place to look for good help :)

---

### Post by bodhi.zazen on 2006-11-24
> **azkehmm said:**
> Hi everyone

I've revently installed ubuntu on my PC, and I must say, so far I really like it. Being a long time Windows user, the whole Linux-pc concept is a little new to me (e.g. that my harddrives are listed as /media/hda1 and so on :)). But I really like what i see. Especially, the terminal concept brings back good memories from the good old DOS days. So, now I need to figure out if I've got the terminal concept right.

>  - If i use "sudo" in front of any command, I'm operating as admin/root.For a single command. For more then 1 sudo su

> - Anything i can do in the graphical interface, I can do in the terminal, and a good deal more?Emphasis on **good deal more**

The CLI has a number of advantages. It is relatively uniform across distros, including dapper/edgy. If never crashes. GUI configuration tools can be buggy, can change, can fail, and at times do not give you the full set of available options.

> - If I want to operate as admin/root the only way to do it is using the terminal (considering the "gksudo nautilus" bug present in both Dapper and edgy)?

I did not know about that bug. Score another victory for the CLI.

> - Finally, can someone please point me in the direction of a guide/list with terminal commands. Like how to create directories and navigating around and stuff (like "cd ****","md ****" and "dir" and stuff like that :)) 

[Command Line Beginners](http://doc.gwos.org/index.php/CommandLineBeginners)

[Command line tips](http://www.pixelbeat.org/cmdline.html)

[Basic CLI](http://www.reallylinux.com/docs/admin.shtml)


Thanks in advance.[/QUOTE]

---

### Post by azkehmm on 2006-11-24
Thanks mate...

So if I want to make a directory on one of my storage drives it'd be somehting like this:
```
sudo mkdir /media/hda1/whateveriwanttocallthatdirectory
```

---

### Post by infoseeker on 2006-11-24
Useful site

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

---

