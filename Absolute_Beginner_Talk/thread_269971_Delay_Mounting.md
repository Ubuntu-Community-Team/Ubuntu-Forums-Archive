---
title: "Delay Mounting"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by shagey36 on 2006-10-02
in my fstab i have two of my network shares getting mounted....and it works when i go to the terminal and type "sudo mount -a". but the shares dont get mounted automatically when i turn on my comp...i have to go to through the terminal every time
i think this is because when ubuntu is mounting whatever is in my fstab, im not connected to my network yet......so is it possible to delay the mounting until my network connection is up...oh and btw my connection is wireless if that matters

---

### Post by Chickencha on 2006-10-02
This is sort of a guess, but maybe your system's attempting to mount the shares before your wireless connection is established?

That said, I'm not really sure how to solve the problem.

---

### Post by shagey36 on 2006-10-02
yea im pretty sure that IS the problem...anybody know how i can have a delay before mounting.....or even just automatically run "sudo mount -a" after my network is connected??

---

### Post by CatKiller on 2006-10-03
You could potentially add it to one of your login scripts so that it only runs when you're ready to log in. You might need to make them not automount in /etc/fstab, and make it so that users can mount the devices. Don't really know. And I don't know which script you'd need to use, since I've not used any of them myself. Hunt for threads on cammands on login though, and you should get there.

---

### Post by shagey36 on 2006-10-04
How do i add something to the login scripts
wouldnt adding
```
sudo mount -a
```
work? because i run this command whenever i log into ubuntu and it works fine

---

### Post by jaboua on 2006-10-04
You don't need "sudo", as the initscripts run as root. In the file /etc/rc.local, add "mount -a" before the "exit 0" line, and that command should automaticly run at boot.

---

