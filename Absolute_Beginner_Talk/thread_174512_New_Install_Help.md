---
title: "New Install Help"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by bparham on 2006-05-11
Perhaps I'm showing my ignorance, I just installed Kubuntu, had a few problems, but seemed to get past them; completed the installation and restarted the computer. 

The computer comes up to the login shell, I see the command line "ubuntu-brad login:" i enter my username and password, it logs me in with a warning that the programs are free software and therefore come with no warranty. 

I now see "brad@ubuntu-brad:~$"

Where do I go from here?

---

### Post by aysiu on 2006-05-11
Type these three commands ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
sudo /etc/init.d/kdm start
```

---

### Post by bparham on 2006-05-11
Nothing...  (It recognizes the commands, but the computer does nothing)

---

### Post by aysiu on 2006-05-11
[QUOTE=bparham]Nothing...  (It recognizes the commands, but the computer does nothing)[/QUOTE] In other words: ```
brad@ubuntu-brad:~$**sudo apt-get update**
brad@ubuntu-brad:~$**sudo apt-get install kubuntu-desktop**
brad@ubuntu-brad:~$**sudo /etc/init.d/kdm start**
brad@ubuntu-brad:~$
``` That's what you see when you type the commands in bold--it just goes to the next line?

---

### Post by bparham on 2006-05-11
Yes... exactly.

---

### Post by aysiu on 2006-05-12
That's after a fresh install? I've seen this problem once or twice before in these forums, but I don't remember what the solution is. I'll search around, see if I can find anything.

---

### Post by bparham on 2006-05-12
I think I got it, I logged out and logged back in as the root user and the commands are working. 

Thanks for the help...

---

### Post by aysiu on 2006-05-12
The simplest way to fix this would be a reinstall.

If you want to learn something, this may or may not fix it.

Print out the contents of the two config files posted [here](http://www.ubuntuforums.org/showpost.php?p=1004086&postcount=12).
Reboot and choose **recovery mode**.
Once that loads up, you will be logged in as root.

Type ```
cp /etc/sudoers /etc/sudoers_old
cp /etc/group /etc/group_old
nano /etc/sudoers
``` Compare your /etc/sudoers file to the printout. Adjust appropriately. To save, press **control-x, y,** then **Enter.** Then ```
nano /etc/group
``` Compare that file to the printout. Where it says *firstuser* in the printout, it should say *brad*.

If you made any changes, reboot to normal mode and see if that fixes it. If you didn't have to make any changes, then the problem lies elsewhere.

---

### Post by aysiu on 2006-05-12
[QUOTE=bparham]I think I got it, I logged out and logged back in as the root user and the commands are working. 

Thanks for the help...[/QUOTE] Oh, you set up a root user?

---

### Post by bparham on 2006-05-12
Yeah, I didn't see an option not to. 

I was able to get the system up and running. 

Thanks!

---

