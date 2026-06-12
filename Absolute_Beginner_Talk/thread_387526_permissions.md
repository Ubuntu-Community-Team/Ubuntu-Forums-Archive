---
title: "permissions"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by mills on 2007-03-18
hi all,

iam trying to make a new home partition and in the guide iam following i have to run this command
```
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```
but i get this response
```
cpio: /mnt/newhome//./alex/.mozilla/firefox/3ybfqziv.default/Cache/871BD7FEd01: No such file or directory
cpio: cannot make directory `/mnt/newhome//./alex': Permission denied
```
(the above response goes on for a while, i didn't see the point in putting it all in)

question is how do i give permission to make the directory, i,ve already tried the 1st code with sudo, 

thanks in advance

---

### Post by taurus on 2007-03-18
You mean something like this.

```
sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/newhome/
```

---

### Post by AtrejuT on 2007-03-18
I think there's a slash (/) too much if you look at your code:
newhome//.alex

try leaving out the last / in your command

---

### Post by mills on 2007-03-18
ok something's gone SERIOUSLY wrong:( 

ive had to boot up a live cd to write this, after i put in your code tuarus (which iam sure i'd tried already, must have had a typo) my home folder dissapeared and i couldnt open anything ,firefox, terminal, you name it, so i rebooted and got this messege when loggin in

> your home directory is listed as : '/home/alex '
but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory?
it is unlikely anything will work unless you use a failsafe session.

but after clickin yes a few times and loggin in, it logs me out straight away with another messege but didnt write that one down,

how can i repair what ive broken?

btw the guide i was following is this [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by mills on 2007-03-18
ok iam thinking if i cant even open a terminal then iam stuffed,

am i going to have to completely reinstall from fresh and lose everything in my home folder?

---

### Post by mills on 2007-03-18
shall i add this to my list of unresolved posts?

---

### Post by annda on 2007-03-18
am i right that you haven't finished the tutorial and mounted your new home partition? if so, you can do the remaining steps using live cd (after mounting your existing partitions).

also, check a modified version of the guide a aysiu's site:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

