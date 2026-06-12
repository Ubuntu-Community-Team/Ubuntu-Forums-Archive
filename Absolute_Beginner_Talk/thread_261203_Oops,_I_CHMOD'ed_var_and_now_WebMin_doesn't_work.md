---
title: "Oops, I CHMOD'ed /var and now WebMin doesn't work"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-09-19
Background.

Well, the old PC that was running Windows Server 2003 died. What a shame :)

I had a "new"ish PC that I was given a couple of months back, so I installed ubuntu as a lamp server to be my webserver for my home/family blog. I wanted to use ubuntu because I like the ability of using Remote Desktop Connection with Server 2003, and I read that you can do the same thing with Ubuntu and VNC and Remote Desktop, plus I've always wanted to Linux a go, and this was a great opportunity.

So, I installed ubuntu LAMP server, and the desktop gui (because me and the linux command line don't get along yet).

Having done that, I installed webmin, and configured the apache2 bits that needed editing.

First off, when I look at localhost, it shows a directory with a acpache2-default directory. That directory should be the default, but according to posts I have seen at sourceforge, this is a bug. No issue, I'll just access my Windows network PCs and dump the old backed up PHP and HTML in the actual default directory instead (/var/www)

Huh? What do you mean I don't have permissions, only the root does? (I'm so used to having administrator rights to everything with Windows, but, I can see the good point of not having those rights too, but that's a different story). So in my sleepy idiotic phase, I 'sudo chmod 0777 /var' As soon as I did that, I thought 'WTF did I do that for?' Bugger, I've then chmod /var to 0644 and then 'sudo chmod 0777 /var/www'. I dumped the PHP and HTML to the /var/www and the accessed it from the outside world. Cool, it works, time for sleep.

I woke up this morning with a chill (not really but...) what about all the other stuff that was in the /var directory... maybe it wasn't 0644 rights to start off with, maybe it was something else. Maybe 0644 is completely wrong.

Uh-oh. I tried to access the webmin on 'localhost:10000'. Page cannot be found. Yeap, I think I've buggered it up well.

Is there a wonderful, special way of reversing what I did, back to the original state that /var was in before I stumbled across it? Or have a done a truely noobish thing and buggered up the whole /var permissions?

I've decided to seek help from you wonderful people before I kill something else. : )

Would it be quicker for me to just reinstall the whole thing (as it really doesn't have anything on it yet), and instead of just trying to drag and drop from PC to PC, to use a FTP client/server?

Any recommendations?

---

### Post by kidders on 2006-09-20
It *seems* as though this will be easy to set right ... provided your "chmod" wasn't a "chmod -R"!!

When applied to directories, the eXecute bit controls traversal. Say you make a little text file called "hello_world", chmod 777 it, and throw it in your home directory. Nobody else will be able to access it. Obvious? Maybe.

Now, if you chmod o+x your home directory, everyone gains the right to enter the directory (but not necessarily read its contents), and all of a sudden, the file is accessible (ie cat /home/whoever/hello_world works). Adding o+r permission would allow the world to see what's in your home ... ie "ls" would start to work.

What you seem to have done with /var is denied the whole world the right to traverse the directory. So, even if something has the right to write to something in it, it can't actually get there.

**The short answer:** chmod 755 /var

Here's mine:

```
$ ls -ld /var
drwxr-xr-x 14 root root 336 2006-08-30 02:16 /var
```

---

### Post by DarkKoopa on 2006-09-20
> **kidders said:**
> 

**The short answer:** chmod 755 /var

Here's mine:

```
$ ls -ld /var
drwxr-xr-x 14 root root 336 2006-08-30 02:16 /var
```

Cool.  Can't wait til I get home to try it. :D 
Thank you.

Q. Does this mean that unlike Windows OS, If I change the permissions on /var via CHMOD, it only changes /var, and not the files and sub-folders contained in it?

---

### Post by kidders on 2006-09-20
Well... kind of.

Afaik, Windows's security model has this ridiculous notion of inherited permission sets, which allows something to pass access rights down a directory tree. This means that you can all too easily create gaping huge security holes in your entire system, with a single ill-thought-out command.

Linux doesn't really use quite the same model, by and large, although it *does* know how to do something vaguely similar, which I'll get to in a sec. Basically, **chmod 777 /var** _only affects the directory_ itself. **chmod -R 777 /var** is a whole different ball game though.

Linux's (slightly safer) equivalent of inherited permissions is perhaps the SGID and SUID bits ... if you fancy, google those, and see what you find :-)

---

### Post by DarkKoopa on 2006-09-20
Cool, thanks for the info. :D

---

