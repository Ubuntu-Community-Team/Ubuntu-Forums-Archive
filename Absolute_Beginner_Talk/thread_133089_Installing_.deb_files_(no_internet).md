---
title: "Installing .deb files (no internet)"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by SlackerHacker12 on 2006-02-19
Hello,

I came home from a vacation today to find that my computer, which I usually keep in Standby mode, had been shut down by a power outage the occurred while I was away.  So, I boot up my Windows, only to discover that it's suddenly asking for me to activate windows.  I recieved this computer from my grandfather after he passed away, and therefore it came with no product key with which I could get a activation code.  Also, the Micro$oft customer service person was kind enough to not help me at all.  Therefore, the Windows XP on my computer is now completely useless. 

So, I'm now forced to use Linux.  I already had Ubuntu installed on my machine, but I didn't use it much.  Now I have to.  I remember from the last time I used it (back in December of 2005), I had issues installing packages, because I don't have that computer connected to the internet, and I cannot use Synaptic.  I remembered using the "sudo dpkg -i package.deb" command to install programs, but now, whenever I try that it asks me for a password.  I  have no idea what this password is, and when I try to type anything, no characters appear on the terminal screen.

If anyone could help me, it would be nice, and I would appreciate it.  

=SlackerHacker=

PS.  If you anyone could tell me how to access files on the other Windows partition, that would be nice too.

---

### Post by knalle on 2006-02-19
the password is the password you wrote twice during install of ubuntu. its the password that you use to log in as mostl likely

---

### Post by nalmeth on 2006-02-19
Unfortunately installing .deb files requires the root password. What exactly are you trying to install? How old is this version of ubuntu?

PS To access the windows filesystem (probably ntfs, and thus read-only), open up a nautilus or a konqueror (using gnome or kde?), go to filesytem, and the harddrive and its partitions should be either in /mnt or /media. You should be able to copy files from the windows over to ubuntu, but you won't likely be able to write anything to windows, unless its a fat32 partition

EDIT: fortunately installing apps requires the password! Only unfortunate when you get locked out

---

### Post by knalle on 2006-02-19
you can just do

sudo su -
install deb
exit

---

### Post by SlackerHacker12 on 2006-02-19
Ok, I got the password.

But now, it gives me a "-bash: No such file or directory."

---

### Post by darkmatter on 2006-02-19
You need to open the terminal in the directory the .deb is in... or change to that directory from terminal.

example: if the deb is on you desktop... open a terminal and

```
cd ~/Desktop
```

or... if they were in your home directory in a folder named packages

```
cd ~/packages
```

or

```
cd /home/<username>/packages
```

the '~' is just a short way of representing the current users home directory.

then issue

```
sudo dpkg -i <name of package>.deb
```

If you want to install multiple debs at the same time... put them all in the same folder... open a terminal in that folder and issue a

```
sudo dpkg -i *.deb
```

---

