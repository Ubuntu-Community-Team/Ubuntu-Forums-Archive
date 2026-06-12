---
title: "Hacking Windows and Ubuntu"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by tay on 2005-11-21
Can somebody give me some good pointers on hacking windows or ubuntu.    I would love to backup my friends me installition with a phone line from my computer to their's.    and I would  love to hack my own, because I get the ongoing message of  GDM cannot login to gnome etc. etc.  ..  I want to hack my desktop and erase some data so that i have temp cache space to login.   Write now i am running a live cd, so i  really need to hack my own computer first, so that i can get my upgrade started.   

I believe the harddrive for ubuntu 5.04 is on /.dev/hda1   but.. i could be wrong.
i know that i was in the middle of programming a server in when the mem got maxed and fried gnome.    So i am not quite sure what to look for..  either my
rootname@home
or my rootservername@servername@home  how can i check hda1 for that information?

I guess i will be using the words:  mount  , to mount the partition.  and  rem to delete some files.   right? 

any help is appreciated, i should have just asked the community sooner, as searching the archives for days is not quite getting my own situation there.

---

### Post by MarcDM on 2005-11-21
First question is, what happens when you try to boot your PC? Or login? What do you mean you want to hack it?

To mount hda1 so that you can see it in the /mnt folder you would use :
 
Assuming it's formatted as ext3 (default in Ubuntu), and you're using an Ubuntu Live cd :

```
sudo mount -t ext3 /dev/hda1 /mnt
```

You could also try it without the -t option. And allow mount (5) to guess what type of partition it is. 

Next, backup over phone line? I don't recommend that at all. Not only do I not know how to do it, but at best you'll get 56k. That'll be frustrating. 

Borrow/buy/steal a couple of network (ethernet) cards and a single cable. If you have no crimping tools, and know nothing about network cables, just follow my foolish advice :
[list]
[*]Cut the cable. 
[*]using a nail-clip or scissors or something just as small strip the orange and green wires on your freshly cut ends to expose the raw copper. 
[*]Now connect the orange ones to it's green counterpart. So Orange/White goes to Green/White and Green to orange. You'll be essentially switching pins 3 to 1 and 2 to 6 by doing this. That is, you're making a cross over cable. 

It's not very sturdy, but should be enough for an hour or three as you backup your friend's computer. Plug it into each computer, and give each one a static IP address. 

```
10.0.0.1/255.255.255.0  <---> 10.0.0.2/255.255.255.0 
```
works pretty well. 

Hope this helps.

---

### Post by tay on 2005-11-21
o.k.  i have the mount part down.  quite easy
after mounting, i just cd to the /mnt directory, and i am accessing the hard drive.
Now to clean up some space so GDM can login...

for example.  

/mnt$ remove- /mnt/home/sahai/shared

is not the right way..  but i would like to remove the whole shared directory, that would free up a couple GB's.

i remember this lesson kind of..  but i think i need a refresher.

because neither rem or remove- are possible command lines.

---

### Post by Ruso on 2005-11-21
rm -rf /mnt/home/sahai/shared/*

This should remove all files from the directory named shared. But be sure u want to delete those files before pressing enter :D

---

### Post by MarcDM on 2005-11-21
```
rm -rdf /mnt/home/sahai/share
```would work. 

```
man rm 
```
would tell you what it does. 

[here]("http://resist.ca/shell") is a quick primer to Linux commands.

You should also check out [The Linux Documentation Project. (tldp.org)]("http://tldp.org") they have some really nice info that's generally not distro specific. 

Also, there's some amazingly good info to be found in the files located on your hard drive in the /usr/share/doc directory.

---

### Post by tay on 2005-11-22
thanks so much. GDM successfully logged in.  

i guess i got alot more studying to do.   Thanks for the quick fix, i needed it.

I guess limewire overstepped some boundaries in my harddrive.

---

