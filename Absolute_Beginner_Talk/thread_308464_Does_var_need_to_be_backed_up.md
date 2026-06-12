---
title: "Does /var need to be backed up?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-28
Hi,

I will use Norton Ghost to backup my system and I try to figure out what "parts" of Ubuntu need to be backed up. Is this important to backup /var?? Does Ubuntu still boot if I remove or erase the /var? As I could understand, /var stores variable data so it might not need to be backed-up. Also what is the difference between /var/tmp and /tmp? Is it possible to "route" /tmp in /var/tmp to have only one temporary folder? 

(I don't know if this is of any relevance here but my system will be single user).

---

### Post by xyz on 2006-11-28
Hi,
How about this way of backing up?
[Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive")
There are other ways to do it,too: Live CD, Partimage,rsync
I back up var.
Hope it helps.

---

### Post by kilou on 2006-11-28
Hey that's perfect! It seems Linux is even greater than what I originally thought :p I also found this when browsing the link you provided: [http://sourceforge.net/projects/sbackup](http://sourceforge.net/projects/sbackup) (seems even better!).

This would solve the backup concern but I generally prefer putting "variable or temporary data" in a separate partition to avoid fragmentation and slowdowns on the root partition. Is it possible to place both /var and /tmp on a separate partition? I know it's possible to place one or the other but what about both? How to do that?

Anyway what in /var needs to be backed up? Is there any important information there? Is the mailbox of Thunderbird stored on /var?

---

### Post by yota on 2006-11-28
Hi,

/var definetely needs to be backed up, all the informations of the package manager reside on /var/lib/dpkg/ for instance.
You can think at /var(iable) as "system-wide files that change often", but not as "temporary" files.
Another example can be a db like mysql that stores the db archives in /var and some mail servers that stores all mails there.

Hope this helps!

---

### Post by kilou on 2006-11-28
Thanks for the insight! But /var/tmp are temporary files...just like /tmp and thus do not require backup, right? Is it possible to have them on a separate partition to prevent fragmentation? What about /var/spool and /var/log as well?

---

### Post by Kurt` on 2006-11-28
/var/spool is for your mail system (yes, you can send mail locally between users on the system), and /var/log holds pretty much ALL the log files for all your programs/services.

Rule of thumb: If you're not sure if it should be backed up or not, go with the safe route and back it up. :)

---

### Post by kilou on 2006-11-28
Do you know what's the difference between /var/tmp and /tmp? Is there a way to put both (and probably /var/log as well) on the same separate partition?

---

### Post by yota on 2006-11-28
The difference between /tmp and /var/tmp is that the files in /tmp are cleaned at reboot, while those on /var/tmp are not.
It's up to the single application or service to decide if it's needed to preserve it's temp files; just as an example I can say that an (open)office applications should periodically save in /var/tmp a modified (but not already saved) document so it can be recovered even if a ac-loss occurs.

If you want you can have a different partition for /var/tmp or merge /tmp and /var/tmp with the 'mount --bind' command (see 'man mount' for details).

If you are interested in learning the deep reasoning under the filesystem layout please have a look at [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

One thing I do really like about linux is that almost everything is there for a very good reason... even when it doesn't seem so at all! ;)

---

### Post by kilou on 2006-11-28
Excellent link Yota! Will read through with great interest! I was thinking of binding var/tmp and /tmp on the same separate partition to prevent fragmentation on the root partition. Maybe I should simply put the whole /var and /tmp on the same partition. These two "folders" will probably get highly fragmented. Then I can backup the system as well as some relevant parts of /var (excluding /var/log, /var/tmp and of course /tmp from the backup). Would this be a good layout or would you recommend leaving the whole /var on the same partition as / and only put /tmp somewhere else?

---

### Post by yota on 2006-11-28
> 
Would this be a good layout or would you recommend leaving the whole /var on the same partition as / and only put /tmp somewhere else?

I suppose is a matter of personal taste... I've changed my mind many times about the "perfect" layout, not counting that it surely depends on the system destination usage.
So is up to you to choose what best suites your need, maybe after some time and experiments you'll find something even better!
Personally I'm not much concerned about fragmentation (at least since I left that "other" os...), ext3 seems pretty smart about it: my little server with everything on the root fs got under 5% fragmented in one year and a half of continuos uptime.
On my main box I choosed to put /opt, /var/tmp and /tmp on the same partition that's on a raid0.
The partition is mounted on /opt and then I
```

mount --bind /opt/vartmp /var/tmp
mount --bind /opt/tmp /tmp

```
(note that in fstab bind is an option)
in this way I have good performance, separate /var/tmp and /tmp and if the raid fails my system is still recoverable.
For me /var must be kept on the safe side, so it stays on the / fs on a raid5.

As stated before that's just my choice, another thing I really do like about linux is that's full of different possibilities. :-D

So study a bit the link (just to be sure that you are going to do what you really want), pick your choice... and let us know how it work for you!

---

### Post by kilou on 2006-11-28
From what I read on the link explaining Filesystem hierarchy, /opt is for add-on application software packages. Why then would you want both /var/tmp and /tmp to be "subfolders" of /opt and share the same partitions for all of these?

---

### Post by yota on 2006-11-28
First of all I didn't want to over complicate things on a home pc so I settled for a 2 volumes (plus 1 for boot) scheme: one with data integrity and one unsafe but performing.

My add-on applications are mainly games (UT2004, Quake4, Neverwinter Nights, Mame with plenty of roms) and multimedia files.
So, as temp files in my vision, they are all things in need of speed and space that I can eventually bear to lose if one single drive fails. 

I'm quite happy till now, but I don't pretend it to be a "good" solution by any mean, as I already tried to say it's just the solution that suites my needs on that machine.

Coming back to your original question, trying to speak in general, I think that using separate partition for /home, /tmp and /var/tmp can be advisable, but I would keep /var on the root filesystem because I don't think it will get fragmented that much to make the trouble of managing a separate partition/volume worth.

Hope this helps!

---

### Post by kilou on 2006-11-30
Thanks for your help Yota! Concerning the /opt being on a separate partition, does it mean that you can do a full clean install of Linux (when a new version comes out for example) and still have all your add-on programs working immediately without having to reinstall them?? I usually don't like to upgrade from one version to the next to avoid potential troubles so if a separate /opt saves me from having to reinstall all the add-ons it would definitely be a great plus. Now are the add-ons packages that are stored in /opt those that you download from Synaptic??

---

### Post by xyz on 2006-11-30
Hi,
> nd still have all your add-on programs working immediately without having to reinstall them?? 
This info may be found on ubuntuforums but I didn't find it. So I translated **Luckynow's HowTo** on the French Ubuntu forum:

I've been looking for a way to avoid spending a whole hour searching for my installed packages following a reinstall:
```
 dpkg --get-selections | grep -v deinstall > ubuntu-files
```
and then save that file where you'll be able to find it after your reinstall.
From here you simply:
```
sudo apt-get update
sudo apt-get dist-upgrade
dpkg –set-selections < ubuntu-files
sudo dselect
```
Have a good day![ The Original here]("http://forum.ubuntu-fr.org/viewtopic.php?id=64855")

---

### Post by kilou on 2006-11-30
Hey XYZ, thanks a lot for that great link! This is exactly what I was looking for in fact!

Just see you're in Fribourg....I'm close to Moudon :-D

---

### Post by kilou on 2006-12-02
What size should I give to a separate partition to hold the /var directory?

How can I mount both /var and /tmp on the same partition?

---

### Post by lamego on 2006-12-02
On a desktop system the only data you should care to backup is /home .
Unless you decide to break the good sense of having the users data on their /home and spread it across your filesystem.
In case you get into a disaster situation you can just install the system and restore all the system related dirs, /etc, /var... etc. taking the same time you would take to restore it.

---

