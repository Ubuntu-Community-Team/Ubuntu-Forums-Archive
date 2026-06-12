---
title: "[SOLVED] Proiblems moving file"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-12-27
I moved a folder earlier from home/ubuntu/shared to home/linux/ prematurely, using sudo nautilus. However, I don't seem to be able to move it back again. I get an error telling me I don't have permissions to change it or its parent folder.
Any ideas.
I also have a proiblem with my dvd drive. It will not mount.

---

### Post by iris-n on 2007-12-27
My hunch is that you should have done it with gksudo, might be the problem.
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

If that doesn't work, though, you can always use chown.

What exactly you get when you try to mount the dvd?

---

### Post by wormser on 2007-12-27
You should use gksudo with graphical applications like nautilus.  We should check the permissions of the file now.

```
cd /home/linux
```
```
ls -l
```

Post the results.

---

### Post by axamax on 2007-12-27
ubuntu@ubuntu-desktop:~$ cd /home/linux
ubuntu@ubuntu-desktop:/home/linux$ ls -l
total 4
drwxrwxrwx 2 ubuntu ubuntu 4096 2007-12-11 12:23 Elvis Presley Frankie.And.Johnny.pal.Nordic.dvdr-NorrPower
ubuntu@ubuntu-desktop:/home/linux$

---

### Post by axamax on 2007-12-27
Thanks guys I've managed to do it by opening TWO lots of  gksudo nautilus and dragging from one to the other.
I still need to mount the dvd drive though

---

### Post by wormser on 2007-12-27
You should start a new thread for your DVD issue and mark this one as Solved.

---

### Post by iris-n on 2007-12-27
That's weird, there are permissions to write, read and execute.
You can try to move them through the terminal, if you're willing:

```
sudo mv  /home/linux/<yourfolder> home/ubuntu/shared/<yourfolder>
```

But that isn't the ideal, 'cos you still have the problem.

---

