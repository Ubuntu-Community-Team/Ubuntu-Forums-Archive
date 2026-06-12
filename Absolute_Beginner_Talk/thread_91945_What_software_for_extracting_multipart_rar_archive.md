---
title: "What software for extracting multipart rar archives?"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2005-11-18
What need to know which software to install for reading/extracting multipart rar archives? Archive Manager doesn't seem to support them.

---

### Post by Kyral on 2005-11-18
I think the rar and unrar-nonfree packages will automagically do it (somehow..I haven't touched them in a while but I recall reading the manpage about it)

---

### Post by claydoh on 2005-11-18
unrar-nonfree is available in the Universe repositories. Once installed, the archive manager should be able to extract rar files with no problem.

---

### Post by matthew on 2005-11-18
From the command line you can use
```
unrar e <filename>.rar
``` **you may have to install unrar first. I can't remember if I did or not. You might do a search in synaptic for rar or unrar and see if it is even installed.

I usually don't have a problem using Archive Manager to do multipart rars, though. Once in a while I encounter a rar (single or multi) that it balks at so I use the command line. 

One other thing to check that may not apply here is if the rar file has a password...that can be entered using either method, but if the archive requires one and you don't enter it you will get an error.

---

### Post by tomski on 2005-11-18
also with multi part rar files you should unrar the one with the lowest number or letter in the file name IE:
file00.rar file01.rar 
filea1.rar filea2.rar

so you would start with file00.rar and when that finishes it should automaticaly ask for the next in series file01.rar

if you have to extract them separtely you will not be able to join them yourself and therefore are not multipart

hope this helps

---

### Post by cafevincent on 2005-11-18
[QUOTE=matthew]From the command line you can use
```
unrar e <filename>.rar
``` **you may have to install unrar first. I can't remember if I did or not. You might do a search in synaptic for rar or unrar and see if it is even installed.

I usually don't have a problem using Archive Manager to do multipart rars, though. Once in a while I encounter a rar (single or multi) that it balks at so I use the command line. 

One other thing to check that may not apply here is if the rar file has a password...that can be entered using either method, but if the archive requires one and you don't enter it you will get an error.[/QUOTE]

I didn't have unrar by default so I tried *apt-get install unrar* that was the end of my problems. It seems you can apt-get more stuff than by selecting from the add applications gui, is there a complete list to apt-get or do I have to try my luck every time?

---

### Post by cafevincent on 2005-11-18
Oh, and thanks for all your help!

---

### Post by matthew on 2005-11-18
[quote=cafevincent]I didn't have unrar by default so I tried *apt-get install unrar* that was the end of my problems. It seems you can apt-get more stuff than by selecting from the add applications gui, is there a complete list to apt-get or do I have to try my luck every time?[/quote]
System->Administration->Synaptic Package Manager
will give you a list of all software available for you to choose from as well as an easy way to install it.

Also, if you haven't yet done so you will want to enable some extra software respoitories. This link explains how: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by cafevincent on 2005-11-19
[QUOTE=matthew]System->Administration->Synaptic Package Manager
will give you a list of all software available for you to choose from as well as an easy way to install it.

Also, if you haven't yet done so you will want to enable some extra software respoitories. This link explains how: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)[/QUOTE]

I followed instructions in that link and I'm receiving this error message in the end of apt-get update:

```

Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Fetched 5B in 4s (1B/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Running apt-get update again makes no difference.

---

### Post by cafevincent on 2005-11-19
Never mind, I emptied out the sources.list and tried to fill it again and it worked, no errors during update.

---

### Post by matthew on 2005-11-19
[quote=cafevincent]Never mind, I emptied out the sources.list and tried to fill it again and it worked, no errors during update.[/quote]
Glad it worked. It always feels good to have a problem and figure it out before someone has a chance to give you the answer. Enjoy the sense of accomplishment! :D

---

### Post by BlackHero on 2006-12-04
thks =)

---

