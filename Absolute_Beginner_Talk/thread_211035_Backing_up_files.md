---
title: "Backing up files"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-07-07
Is there someway of backing up all the files and folders on my home directory? I am currently using Breezy and having problems upgrading to Dapper. So I want to back up all my files on my home directory and re-install Ubuntu Dapper Drake. The size of my home folder is about 6GB.
Any ideas?

---

### Post by Klaidas on 2006-07-07
Well, you could create a partition, backup your /home there and reinstall. 
Or, you could simply use 2 DVDs.
And when installing dapper, you could create a seperate home partition for future ionstalls: [http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html)

---

### Post by aysiu on 2006-07-07
You have several options.

I would highly recommend doing a image backup of your entire partition: [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

That way, if your upgrade screws up, you can restore Breezy to exactly the way it was before.

If you want do just a regular backup, *rsync* is a great tool. ```
rsync -av /home /destination/directory
``` Once you do upgrade to Dapper, you'll find it has a graphical frontend called *grsync*.

---

### Post by aam-aadmi on 2006-07-07
Thanks for the suggestions guys.

---

### Post by T700 on 2006-07-07
For those of us using KDE instead of Gnome, Konserve is a nice little graphical backup application.  Of course, if you have US$50,000 and up to spend, email me since backup software is what my company sells!

Paul  :-)

---

### Post by aysiu on 2006-07-08
Your company charges $50,000 for backup software...?

---

### Post by T700 on 2006-07-08
[I'm pointedly not mentioning the name of my employer because I don't want violate the guidelines and plug them on the forum, even when joking.]

Sure does and sometimes for many, many times more than that.  It is very specialized software and is used in extremely large, complex networks and server farms for management and data protection.  

Paul

---

### Post by PriceChild on 2006-07-08
I don't really think that restoring your entire home partition is a good idea after an upgrade. :S

It will have loads of old settings from Breezy.

Maybe be more selective in what you copy, only your own work etc. none of the hidden files.

Pricey

---

### Post by aysiu on 2006-07-08
> **PriceChild said:**
> I don't really think that restoring your entire home partition is a good idea after an upgrade. :S

It will have loads of old settings from Breezy. I partially agree. It's not a *terrible* idea. Your system won't be broken. It's not a dangerous thing to do.

But sometimes you might have empty icons or something. That's why I've moved away from having a separate /home partition, and now I just have a separate documents partition, and I symlink my .thunderbird and .mozilla profiles to my /home directory.

---

### Post by noynac on 2006-07-08
I've also been trying to find an easy way to backup just the home directory (and all directories and files in the home directory). I'm new to linux, and the best I could do so far is to type the following in terminal:

sudo cp -r /home /media/usbdisk-1

When restoring, I only restore (copy back with Nautilus) those hidden files that contain important data (such as my password manager data file).

Hopefully a more experienced member of the forum will have a better suggestion.

---

### Post by jeremy on 2006-07-08
Check out 'Unison'
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)
It is in the repositories.

---

### Post by bluntu on 2006-08-24
What's the best way to backup your firefox Extensions/Pref/Settings?

I'm thinking of: /home/.mozilla/firefox/_randomletter_.default

Will that do it?

---

