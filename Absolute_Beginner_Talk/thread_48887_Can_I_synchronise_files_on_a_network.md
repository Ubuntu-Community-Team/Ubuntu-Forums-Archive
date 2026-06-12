---
title: "Can I synchronise files on a network?"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by Darkscot on 2005-07-14
On Windows XP Pro there is a function where you can select a network folder and 'make available offline'.  I use this at work to synchronise files on my laptop with those on the server.  If I disconnect from the server I can still edit the copies on my laptop and synchronise them later when I reconnect to the network.

On Windows XP Home you can use the 'My Briefcase' function which is similar but not as good.

So my question is there something similar in Linux?  I have two dual boot systems running Ubuntu & MS connected on a wired network.  I would like to synchronise the /home folders on each.  Partly as a backup and partly to allow access when one or the other PCs is switched off. 

I havent really looked at the networking functions of Linux yet, other than to confirm that both PCs can see each other.

---

### Post by dave9191 on 2005-07-14
Have you looked into rsync? Ive not used it yet, but that how I am planning on doing my backups (if i ever get round to doing them). It only syncs the differences between files on your computer and another file location. 

" The rsync remote-update protocol allows rsync to transfer just the  differences  between two sets of files across the network connection, using an efficient checksum-search algorithm described in the technical report that accompanies this package"


You can read more about it by typing 

man rsync

into a command line. Im sure you can find more about it on google as well :) 

Dave

---

### Post by jeremy on 2005-07-15
Unison:
info, [http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)
you can install it from the repo's.

---

### Post by Darkscot on 2005-07-15
Thanks for the advice.  Unison seems closest to what i am looking for.  I will give it go when I have few hours to spare.

---

### Post by coreymc on 2005-07-22
Hi-

I followed the suggestion to use Unison to sync files between my USB pendrive and selected folders in my /home drive.  In order to do so I:

-Created a folder called /unihome

-Created a symbolic link in /unihome to folders I want to regularly sync.  To do this I typed "ln -s /home/experiments /unihome/experiments".

- I then synced drives ("unison unihome/ /media/sdb1/unihome/") and everything seems OK.

However, I have since modified what is in /home/experiments and it no longer matches the contents of the symbolic link in /unihome/experiments.  See below:

coreymc@wilco:~$ ls -l ~/experiments/
total 268
drwxr-xr-x  2 coreymc coreymc   4096 2005-07-18 18:53 coding
-rwx------  1 coreymc coreymc 130751 2004-11-19 15:08 corey_ps.csv
drwxr-xr-x  3 coreymc coreymc   4096 2005-07-18 18:53 epg
drwxr-xr-x  2 coreymc coreymc   4096 2005-07-20 13:27 hcm05
-rwx------  1 coreymc coreymc 105984 2004-11-17 09:45 jo_items.xls
drwxr-xr-x  6 coreymc coreymc   4096 2005-07-18 18:53 msc
drwxr-xr-x  2 coreymc coreymc   4096 2005-07-19 18:17 Suzy_WOC
drwxr-xr-x  5 coreymc coreymc   4096 2005-07-20 09:51 woc
drwxr-xr-x  2 coreymc coreymc   4096 2005-07-22 09:53 woc2

coreymc@wilco:~$ ls -l unihome/experiments/
total 260
drwx------  2 coreymc coreymc   4096 2005-07-19 13:15 coding
-rwx------  1 coreymc coreymc 130751 2005-07-19 13:15 corey_ps.csv
drwx------  3 coreymc coreymc   4096 2005-07-19 13:15 epg
drwx------  2 coreymc coreymc   4096 2005-07-19 13:15 hcm05
-rwx------  1 coreymc coreymc 105984 2005-07-19 13:15 jo_items.xls
drwx------  6 coreymc coreymc   4096 2005-07-19 13:15 msc
drwx------  5 coreymc coreymc   4096 2005-07-19 13:15 woc

So, my "symbolic links" don't appear to be "symbolic" afterall.  Does anyone know (a) why the contents of these folders don't match and (b) if there is better way to do what I am trying to do.  If the latter, can I delete the "symbolic links" without deleting the contents.

Cheers,
coreymc

---

### Post by dave9191 on 2005-07-22
I don't use unison, but I'm sure that there is a way to tell it to preserve sym links. In the case of rsync it will not preserve them unless you explicity tell it to. 

Dave

---

