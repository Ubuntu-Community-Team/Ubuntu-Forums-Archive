---
title: "How to backup data in linux"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by pravkaran on 2008-01-23
Hai all,

can anyone help me to take daily backup data.

---

### Post by hyper_ch on 2008-01-23
copy them onto another device and store that one in a safe place...

---

### Post by philinux on 2008-01-23
> **pravkaran said:**
> Hai all,

can anyone help me to take backup datas in linux

Ubuntu store all your personal stuff in  /home/yourusername

If you use the menus at the top Places> Home Folder you could hightlight all the folders theres and copy them to either a cd ,dvd, or usb stick the choice is yours.

My user folder is about 300 meg.

---

### Post by maybeway36 on 2008-01-23
Making a .tar.gz archive might help. It's like zip, in that it consolidates everything into one file (tar) and then compresses it (gz).

---

### Post by rustutzman on 2008-01-23
I'm pretty happy with FlyBack.
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

Russ

---

### Post by rhc on 2008-01-23
Remastersys is the best i think.
You backup all data or even you can make your own distro.
Here it is:
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

And a great howto about it : [http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

Very easy usage also.

---

### Post by mivo on 2008-01-23
There are some nifty tools, like Grsync (it is in the repos). Or you can do it manually from the command line (or a cron job, meaning it is done automatically at pre-defined times), like so:

```
rsync -r -t -v --progress --delete /home/username/ /media/disk/backup-calico/home/username/
```

The above example backups my home directory to an external USB drive (into a folder named backup-calico). It also synchronizes the two directories, meaning that if I delete a file on my hard drive, it will also be deleted on my backup disk (when I run it), and it will only newly backup files that have been changed since the last backup, so this is very time-efficient since you don't have to transfer all of your data every time.

GRsync offers a nice GUI for rsync, which is a Linux core tool (I think Ubuntu installs this by default, if not get the rsync package). You can backup data to external drives, via SSH to another computer (local or remote), or to a different disk/directory on the same computer. There are also tools to clone your entire disk.

If you tell us more about your backup needs, we can probably provide more detailed suggestions. :)

---

### Post by kleo skywalker on 2008-01-23
Take a look at [this]("http://www.ubuntu-unleashed.com/2007/09/remaster-and-clone-your-ubuntu-install.html").

Edit: 1) rhc beat me to it. 2) mivo is right, if you could be a little more specific about what exactly you want to backup, you'd get more solutions.

---

### Post by bwtranch on 2008-01-23
The basic tool here is already there. It's called tar. This stands for tape archive. But, we have things like CD's and DVD's now. The function of tar is still the same, though, to make archives. You don't have to download or install anything. It's been there since the beginning of Unix. Do you want a nifty utility or something that has a proven track record?

---

### Post by mdpalow on 2008-01-23
See the link in my signature below. It may be what you're looking for in a back-up.

---

### Post by pravkaran on 2008-01-25
thank u for your valid comments

---

### Post by vladu on 2008-01-27
Hi.

I'm also interested in a backup utility. 

I've used Picasa 2 in windows to backup my photo collection and i really liked it a lot. It was very straightforward, I just selected what i needed to backup and the software calculated how many cds/dvds i needed. The only thing i had to do was to feed it with dvds. It even remembers what is backed up and what is not.

I'm looking for a similar tool that does just that but regardless of the file type (Picasa only knows about pictures).

---

### Post by kleo skywalker on 2008-01-28
> **vladu said:**
> Hi.

I'm also interested in a backup utility. 

I've used Picasa 2 in windows to backup my photo collection and i really liked it a lot. It was very straightforward, I just selected what i needed to backup and the software calculated how many cds/dvds i needed. The only thing i had to do was to feed it with dvds. It even remembers what is backed up and what is not.

I'm looking for a similar tool that does just that but regardless of the file type (Picasa only knows about pictures).

I'd like something like that too!

---

### Post by highfructose327 on 2008-01-29
Mivo, Thanks! the rsync code you gave worked perfect. A good simple solution.

---

### Post by fourthofjuly on 2008-03-22
> **mdpalow said:**
> See the link in my signature below. It may be what you're looking for in a back-up.
wow, 

you Sir are a genius...!!! its so simple and easy...

full marks to you... & thanks, 

much appreciated...

---

### Post by timbounceback on 2008-03-22
[http://simplelinuxbkup.sourceforge.net/](http://simplelinuxbkup.sourceforge.net/)

---

### Post by bred on 2008-03-22
buy an external HDD and backup everything you want ;)

---

