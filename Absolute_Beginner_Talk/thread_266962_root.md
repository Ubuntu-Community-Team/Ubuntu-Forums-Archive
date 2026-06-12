---
title: "root"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-28
ok i know its not a good idea to activate the root acount
why cant i copy and paste a file into the filesytem?
i have given my user full priveleges including complete administritive tasks. yet when i try to paste something to root the "paste or delete" function is grey'd out on the right click menu
plzz help im getting fed up](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Madpilot on 2006-09-28
You shouldn't, as a general rule, be moving/pasting stuff into the FileSystem area. Fiddling with stuff there manually is a wonderful way to break your Ubuntu. (been there, done that...)

What are you trying to do, exactly?

---

### Post by encompass on 2006-09-28
It could be many things...
that are you copying and from where to where.
Have you tried just using sudo nautilus? and if you need root root, but not root root root, try...
```
sudo su
```

---

### Post by uk_sphinx on 2006-09-28
it started coz i wanted to download the flash plugin for mozilla.
the instructions on there site say...
extract the directory and type this at command line....

/flashplyer-installer

but i cant write to / coz administritive thing

the directory is on the desktop.

so / home / user / desktop / flash-directory / flash_installer

it dont work and gives me bash error directory dosnt exist

---

### Post by uk_sphinx on 2006-09-28
i basicly cant run the flash installer on my desktop.
i dont even want the installer on my desktop.
i want it neatly tooked away in the file system somewhere

---

### Post by aysiu on 2006-09-28
Forget your Flash player installer. In Ubuntu, package management is the deal.

Step 1: Enable extra repositories by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Step 2: Install Flash by pasting this command into the terminal: ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

Then, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

and this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ian.l on 2006-09-28
You can't copy into the filesystem because those folders are owned by root. You would have to be logged into the root account or do a command line cp operation using sudo (i.e. sudo cp /home/username/Desktop/filename /root)
Since Ubuntu uses sudo and doesn't ask for a root password during installation, you can set a password for root from the terminal by typing 'sudo passwd' and then entering the new root password twice. Then you can su from the terminal to get the root prompt #
Perform the cp command from this prompt.

---

### Post by uk_sphinx on 2006-09-28
thanks alot you two i needed that.
iv asked all over the shop to no avail.
believe it or not i was actually ](*,) 
need coffee before i learn that lot
thanks again

---

