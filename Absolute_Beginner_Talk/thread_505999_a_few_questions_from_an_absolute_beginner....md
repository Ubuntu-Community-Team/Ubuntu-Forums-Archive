---
title: "a few questions from an absolute beginner..."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by buntu23 on 2007-07-21
Hello, I have switched from WINDOWS XP for 2 weeks now, in the two weeks I got almost everything up and running, right now it seems like I’m an ubuntu user for good. (even if I will have to switch back for work – I work in communication design, there are no doubts ubuntu is better than what I had)


I have a few problems that I cant figure out, may be someone can help me…here goes:

1.	I need to figure out how to sync folders – I have 4 hd’s 2 extrnal and 2 internal. With windows I used 1 for everything and synced to others as backup – design projects etc… - so how do I sync in Ubuntu? Is there a reliable sync software i can download? 
  
One of the hd’s is NTFS but I did figured out how to write to it – thanks to this forum. 

2.	How do I undo MOVE or undo DELETE in gnome????? This is a big problem for me, many folders and I do sometimes move things by accident. If there is no way to do this in gnome, how do I do it via the terminal? 
3.	Is there a way to get out of the FORCED CHECK at startup? And run it on my own time?
4.	What kind of maintenance do I need to perform for my system to last longer? In windows I did defrag, cleanup, and reinstalled it every few months, sometimes weeks – you know how it is… 
I read on the forum that Ubuntu doesn’t need defrag, do I need to do anything else? 
5. cant get Photoshop 7 to work stable in wine – and cant get Illustrator CS to work at all, so I use WMworkstation Windows XP and run it there, is there a better way around it? – I need adobe, illustrator, dreamweaver, flash, etc for work, 

Thanks. 

Any general comments would be appreciated as well, I’m absolutely new to Linux in general and Ubuntu in particular. Thank you.

---

### Post by Al3xK3aton on 2007-07-21
> **buntu23 said:**
> I use WMworkstation Windows XP and run it there

You should be using a Vista virtual machine, not XP, unless you WANT to be on outdated software. Vista is better because it's newer.

---

### Post by ravenwere on 2007-07-21
Re: question 5 you may want to check out Crossover.........and see if it is applicable to your Adobe suite.......but be warned it is not free (much cheaper than Adobe though ;))

See [http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

Regards,
R

---

### Post by mlentink on 2007-07-21
> **Al3xK3aton said:**
> You should be using a Vista virtual machine, not XP, unless you WANT to be on outdated software. Vista is better because it's newer.

I would strongly, **strongly** advise against this. One of my customers is a company that sells ICT solutions to dentists, unfortunately all Windows. They actively downgrade all systems sold to XP, because Vista is such a pain. Many drivers are not supported, there are many incompatibilities. In short, to prevent problems, wait at least until Vista SP2 before you migrate to it, if at all.

---

### Post by Hund on 2007-07-21
4. No maintenance is needed. :)

---

### Post by kvonb on 2007-07-21
One thing you really ought to keep in mind is this:  Linux is NOT WIndows, nor is it a replacement for WIndows.

For all your WIndows progs to run, the simplest way is to run a Virtual Machine.  Things like WINE/Crossover Office/Cedega can run some things, but are very patchy.

There is no "housekeeping" to be done under Linux/Ubuntu, we don't really have to worry about defrag/virus'/spyware etc' which is hard to get used to, but once you gain confidence you will enjoy the freedom.

Be VERY careful when deleting a file!  Once it's deleted it is gone forever!

I've been using Linux full time for several years now and I still make the occasional mistake!

I'm quite sure that files are "forensically" deleted (or rather over-written) nearly straight away.

It's one feature of the format we use, it's extremely secure and efficient (hence no need to defrag etc'), and the lack of undeletion can be seen from both sides, it's extremely secure, but at the same time extremely unforgiving!

I would suggest disabling the delete button, and use only the rubbish bin instead.


The disk check thing is a bit of a niusance, you can set it for longer intervals, and disable it completely, but that is about the extent of it unfortunately.

There was a nice little app for Dapper and Edgy called "bonager", which showed you when it was scheduled to run, and you could change it.  I'm not sure if the author re-wrote it for Feisty though, maybe search the forums and Google.

I just set mine to 100 mounts, it seems to be ok at that :).

---

### Post by ugm6hr on 2007-07-21
> **buntu23 said:**
> 1.	I need to figure out how to sync folders &#8211; I have 4 hd&#8217;s 2 extrnal and 2 internal. With windows I used 1 for everything and synced to others as backup &#8211; design projects etc&#8230; - so how do I sync in Ubuntu? Is there a reliable sync software i can download?

3. Is there a way to get out of the FORCED CHECK at startup? And run it on my own time?

4. What kind of maintenance do I need to perform for my system to last longer? In windows I did defrag, cleanup, and reinstalled it every few months, sometimes weeks &#8211; you know how it is&#8230;

1.  Have a look at *sbackup* (find it in Synaptic Package Manager).

It will backup which ever drive paths you ask it to.  I don't think it is possible to get it to do that with 3 separate drives though (unless you manually enter each drive as the path each time you backup).  Worth a look....

Although, I suspect *rsync* is closer to what you need - I just haven't used it.  I'm not sure there is a GUI for it either.

3/4.  I believe the forced check is the only maintenance required...  It should only go through it every 30-40 times you boot though (hopefully not too inconvenient).  Not sure if a manual check is possible, or if it is sensible to abort a forced check.

---

### Post by buntu23 on 2007-07-21
thanks for the answers

---

### Post by Kevbert on 2008-01-27
Ref: Maintenance and log files.
Yup, I'm a newbie.
Do the logfiles get deleted regularly, new ones generated or do they just get bigger ?
I've tried using bootchart and every time I boot the PC a new file is added.  I'm now going to remove the program and purge the configuration files (if any).  
One thing I've noticed with update/upgrade is that these look for any redundant software related to new installed files and remove them.  This is a great feature of Linux.

---

### Post by scorp123 on 2008-01-27
> **Kevbert said:**
> Ref: Maintenance and log files. Do the logfiles get deleted regularly, new ones generated or do they just get bigger ? There is a mechanism called **"logrotate"** which will collect and compress old logfiles and move them into **gzip (GNU Zip)** (file extension: ***.gz**) archives. If you want to do some maintenance: Open a terminal and go to this folder: **/var/log** and then check if there are many ***.gz** files: ```
cd /var/log/
ls -al *.gz
``` You can also check how much disk space they use: ```
du -hc *.gz
``` .... **"du"** stands for **"disk usage"**, the **"-h"** switch produces "human readable" output and the **"-c"** switch calculates the total ... Example from my system here: ```
/var/log > du -hc *.gz
4.0K    acpid.1.gz
4.0K    acpid.2.gz
4.0K    acpid.3.gz
4.0K    acpid.4.gz
4.0K    apport.log.2.gz
4.0K    auth.log.1.gz
4.0K    auth.log.2.gz
4.0K    auth.log.3.gz
16K     daemon.log.1.gz
36K     daemon.log.2.gz
12K     daemon.log.3.gz
8.0K    debug.1.gz
20K     debug.2.gz
8.0K    debug.3.gz
12K     dmesg.1.gz
12K     dmesg.2.gz
12K     dmesg.3.gz
12K     dmesg.4.gz
92K     dpkg.log.2.gz
28K     kern.log.1.gz
84K     kern.log.2.gz
36K     kern.log.3.gz
28K     messages.1.gz
76K     messages.2.gz
32K     messages.3.gz
56K     syslog.1.gz
40K     syslog.2.gz
36K     syslog.3.gz
16K     syslog.4.gz
4.0K    syslog.5.gz
4.0K    syslog.6.gz
4.0K    user.log.1.gz
4.0K    user.log.2.gz
4.0K    user.log.3.gz
724K    total 
``` So as you can see the old logs here only take a total of 724 Kilobytes .... which is next to nothing. You may want to check this on your system too.

If you think you have to delete the old logs (e.g. they really take up lots of space in your case), you have to do this with "root" priviledges: ```
cd /var/log
sudo rm -i *.gz
```

**Just don't delete anything else in there! (or anywhere else for that matter!)**

Hope this helped :)

---

### Post by Kevbert on 2008-01-27
Brilliant thanks.  I'll try it out.

---

### Post by scorp123 on 2008-01-27
> **buntu23 said:**
>  1.	I need to figure out how to sync folders  Take a look at **unison.**  This can sync folders even across computers and platforms if you want to, the program exists for Linux, Mac and Windows. The **unison** program is available via the repos, so you can install it via Synaptic's GUI or via the command line: ```
sudo apt-get update
sudo apt-get install unison
```

Infos and a few screenshots here:
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

"unison" User manual is here:
[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html)

"unison" Tutorial is here:
[http://www.stanford.edu/~pgbovine/unison_guide.htm](http://www.stanford.edu/~pgbovine/unison_guide.htm)

I myself only use UNIX and Linux systems, for me **rsync** (a CLI tool) does all I need. Maybe you'd want to take a look at that too? The manual is here: ```
man rsync
``` So let's suppose I want to sync my "Music" folder across two of my machines ... All that's needed is that the two systems can talk via SSH to each other, **rsync** will do the rest for me: ```
rsync -av Music myaccount@remotesystem:~/Music 
``` ... or the other way around: ```
rsync -av myaccount@remotesystem:~/Music ./Music
```

> **buntu23 said:**
>  2.	How do I undo MOVE or undo DELETE in gnome?????  Move it back out from the trash can. **If you deleted stuff by any other method it is *gone* forever. [COLOR="Red"]*There is no undelete here*[/COLOR]**

> **buntu23 said:**
>  This is a big problem for me, many folders and I do sometimes move things by accident.  That's why hopefully you were already told to never ever work as "root" (= the super-user administrator account), and only use the infinite God-like powers of the "root" account for specific administrative tasks, e.g. when you install a program ("sudo apt-get install .... ") but never ever run a GUI as "root" ... One accidental drag & drop over the wrong places and your system is gone! 

With your normal user account you shouldn't be able to hose your entire system, you can only harm your own files in your **/home** directory. So having backups would be a good idea. 

> **buntu23 said:**
>  If there is no way to do this in gnome, how do I do it via the terminal?  Not at all.

> **buntu23 said:**
>  3.	Is there a way to get out of the FORCED CHECK at startup?  Not recommended. Let the system do its checks.

> **buntu23 said:**
>  4.	What kind of maintenance do I need to perform for my system to last longer?  "last longer" is maybe the wrong term here. The only thing I could think of is that you here and there (every six months or so) may want to clean up old log files, but that's it. See my other posting about this.

---

### Post by j2fraser on 2008-01-31
...or if, like me, you like your GUI, you could also install and use a graphical front-end for rsync, like [grsync]("http://www.opbyte.it/grsync/"). Works great!

---

### Post by darkworld on 2008-01-31
Hi

I never really used photoshop much myself so what I may suggest might be wrong, but if you havent discovered all the joys of GIMP give it a long look. I love it.

Ive been on Ubuntu over a year now and I found these sort of pages a great help when I was starting off. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy")

---

