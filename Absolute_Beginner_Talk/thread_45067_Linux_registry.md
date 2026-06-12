---
title: "Linux registry"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-28
I've come to realise that it has to be some kind of registry in Linux, 'cause if there weren't it wouldn't be possible to, for example, write "XMMS" in the terminal and to launch it, now would it?

Where do I find this registry?

---

### Post by wylfing on 2005-06-28
You are incorrect. There's no Registry. What you are experiencing is the many-decades-old tried-and-true method of finding stuff on a system called the $PATH variable. When you type 'xmms' your system merely searches all the directories listed in $PATH, looking for a match.

If you want to see what's in $PATH, type 'echo $PATH' in a terminal.

By the way, Windows has a $PATH variable too, and uses it the same way. Not everything is looked up through the Registry. And also by the way, Gnome has a "sort of" Registry-alike but it doesn't do what you're talking about.

---

### Post by Trojan1313 on 2005-06-28
[QUOTE=wylfing]You are incorrect. There's no Registry. What you are experiencing is the many-decades-old tried-and-true method of finding stuff on a system called the $PATH variable. When you type 'xmms' your system merely searches all the directories listed in $PATH, looking for a match.

If you want to see what's in $PATH, type 'echo $PATH' in a terminal.

By the way, Windows has a $PATH variable too, and uses it the same way. Not everything is looked up through the Registry. And also by the way, Gnome has a "sort of" Registry-alike but it doesn't do what you're talking about.[/QUOTE]
 How come it loads so quick then?

---

### Post by crashtest on 2005-06-28
[QUOTE=Trojan1313]How come it loads so quick then?[/QUOTE]

The computer can search a finite list of directories to find your app pretty quick.  My path has the following directories listed: echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

Here's a little more info on the path concept: [http://www.linux.ie/newusers/beginners-linux-guide/exe-path.php](http://www.linux.ie/newusers/beginners-linux-guide/exe-path.php)

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=wylfing]You are incorrect. There's no Registry. What you are experiencing is the many-decades-old tried-and-true method of finding stuff on a system called the $PATH variable. When you type 'xmms' your system merely searches all the directories listed in $PATH, looking for a match.

If you want to see what's in $PATH, type 'echo $PATH' in a terminal.

By the way, Windows has a $PATH variable too, and uses it the same way. Not everything is looked up through the Registry. And also by the way, Gnome has a "sort of" Registry-alike but it doesn't do what you're talking about.[/QUOTE]


Wow. Thats a good explination.

---

### Post by az on 2005-06-28
[QUOTE=Trojan1313]How come it loads so quick then?[/QUOTE]
How come windows doesn't?

The windows registry is a database.  It contains a very small amount of data in comparison to, say, the ubuntuforums database.  Why does a windows computer lock up for a minute or two when it goes fumbling around in the registry?

---

### Post by AntiDragon on 2005-06-29
The Windows registry is indeed a database. And considering what it's used for it's a rather heavy set up.  It came about because MS were concerned with the ever growing number of INI files dumped in the system folders by installed software. So they came up with the rather misguided idea of a centralised database and a set of programming functions (an API) to be used by software.

The up shot is that almost all aspects of Windows and it's installed software can be controlled by editing the registry - desktop colours, display settings, device driver details, file associations and so on all reside in the registry. Unfortunately they've [MS] thrown in a rather complex security model to boot and stored the database in a rather weird file format. For this reason accessing the registry is far slower than the Linux equivalent of reading a .conf file.

Also, the registry is physically 3 main files (not including a user's own ntuser.dat file and all the backups that MS create to make up for it's bugginess!). Lose one of them and your whole system goes down.  :| 

On Linux, each program is responsible for their own configuration files - usally just plain text files, sometimes a bit more exotic. There are also set locations that can be shared between all users and enable a program to have "global" settings (like the HKEY_Local_Machine in WIndows).

Both OS's use environment variables like PATH to control certain aspects like where to look for a file if it's not in the current directory. These variables are held in memory while the systems are running which is why it's so fast. Also, (personal opinion) Linux tends to have faster filesystems so the process of locating the file you type in is pretty damn quick.

(You can tell I've spent to much time working with MS stuff, can't you?  :razz: )


Just my contribution! :smile:

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=AntiDragon]The Windows registry is indeed a database. And considering what it's used for it's a rather heavy set up.  It came about because MS were concerned with the ever growing number of INI files dumped in the system folders by installed software. So they came up with the rather misguided idea of a centralised database and a set of programming functions (an API) to be used by software.

The up shot is that almost all aspects of Windows and it's installed software can be controlled by editing the registry - desktop colours, display settings, device driver details, file associations and so on all reside in the registry. Unfortunately they've [MS] thrown in a rather complex security model to boot and stored the database in a rather weird file format. For this reason accessing the registry is far slower than the Linux equivalent of reading a .conf file.

Also, the registry is physically 3 main files (not including a user's own ntuser.dat file and all the backups that MS create to make up for it's bugginess!). Lose one of them and your whole system goes down.  :| 

On Linux, each program is responsible for their own configuration files - usally just plain text files, sometimes a bit more exotic. There are also set locations that can be shared between all users and enable a program to have "global" settings (like the HKEY_Local_Machine in WIndows).

Both OS's use environment variables like PATH to control certain aspects like where to look for a file if it's not in the current directory. These variables are held in memory while the systems are running which is why it's so fast. Also, (personal opinion) Linux tends to have faster filesystems so the process of locating the file you type in is pretty damn quick.

(You can tell I've spent to much time working with MS stuff, can't you?  :razz: )


Just my contribution! :smile:[/QUOTE]


I'm bookmarking this, and showing it to Window's trolls in the future. Thanks.

---

### Post by wylfing on 2005-06-30
[QUOTE=Trojan1313]How come it loads so quick then?[/QUOTE]
(This has already been addressed but I thought it would be fun to add a few more technical details.)

Suppose $PATH lists six directories. That's a pretty typical number. Your computer, even if it's a Pentium 100, can iterate over six items quite quickly. Now even though each of those directories might contain over a thousand items ('ls /usr/bin | wc -w' reports 1301 on my system), through the magic of mathematics it doesn't matter. Way back in the 1960s very clever people gave us the algorithms *quick sort* and *binary search*, which make hunting through lists extremely efficient. You can learn more about binary search here: [http://en.wikipedia.org/wiki/Binary_search](http://en.wikipedia.org/wiki/Binary_search).

With binary search, you can search through 1301 items in 10 or fewer steps. Your computer can get through 10 search steps in mere microseconds. So, all told, the task of tracking down the file header takes hardly any time at all. Definitely no need for a "registry" to tell it where to look. In fact, merely establishing a connection to a database would probably take twice as many microseconds as searching with efficient algorithms, to say nothing of performing queries on the database afterward.

---

### Post by davahmet on 2005-06-30
[QUOTE=wylfing](This has already been addressed but I thought it would be fun to add a few more technical details.)

Suppose $PATH lists six directories. That's a pretty typical number. Your computer, even if it's a Pentium 100, can iterate over six items quite quickly. Now even though each of those directories might contain over a thousand items ('ls /usr/bin | wc -w' reports 1301 on my system), through the magic of mathematics it doesn't matter. Way back in the 1960s very clever people gave us the algorithms *quick sort* and *binary search*, which make hunting through lists extremely efficient. You can learn more about binary search here: [http://en.wikipedia.org/wiki/Binary_search](http://en.wikipedia.org/wiki/Binary_search).

With binary search, you can search through 1301 items in 10 or fewer steps. Your computer can get through 10 search steps in mere microseconds. So, all told, the task of tracking down the file header takes hardly any time at all. Definitely no need for a "registry" to tell it where to look. In fact, merely establishing a connection to a database would probably take twice as many microseconds as searching with efficient algorithms, to say nothing of performing queries on the database afterward.[/QUOTE]
 Also, IIRC, Linux uses a dynamic hash table for doing a very fast lookup of the command history, which combined with a heap sort results in a huge performance gain, especially since the theory of locality predicts a high probability of commands being frequently reused.

The Windows registry, while initially an elegant design to solve a difficult problem, was over-engineered to the point of becoming an absolute nightmare.

---

### Post by AntiDragon on 2005-07-01
Ooh - I'm bookmarked! Hehe...

[QUOTE=davahmet]The Windows registry, while initially an elegant design to solve a difficult problem, was over-engineered to the point of becoming an absolute nightmare.[/QUOTE]

That probably sums up my post better than the verbal diarreah I came out with. You might like to know that MS are now pushing developers *NOT* to use the registry and encouraging that programs use their own configuration files instead....another amazing Microsoft U-Turn (TM)  :smile: !

Incedentally, there are a few "registry-like" linux systems available as well ("GConf" I one I believe?) but it's down to developers wether they use them or not - as is right and proper!

---

