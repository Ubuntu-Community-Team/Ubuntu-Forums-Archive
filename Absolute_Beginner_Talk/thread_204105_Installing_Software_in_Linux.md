---
title: "Installing Software in Linux?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by virtuexru on 2006-06-26
I know this may be a REALLY stupid question. 

But, how do I go about installing software? I have downloaded Azureus and Thunderbird and they have a .tar.bz2 and a .tar.gz file ext. I can double click to see a winzip-type program where I can extract to but even if I do extract where would I point it to? the BIN directory?

Any help would be appreciated.

---

### Post by T700 on 2006-06-26
Please check this thread for detailed instructions:

[http://www.ubuntuforums.org/showthread.php?t=204081](http://www.ubuntuforums.org/showthread.php?t=204081)

Paul

---

### Post by Brunellus on 2006-06-26
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

read aysiu's article above.  Summary:  Don't extract/compile/install manually unless you absolutely HAVE to.  Use the repositories and synaptic.

---

### Post by virtuexru on 2006-06-26
Ah great thank you both.

---

### Post by Ptero-4 on 2006-06-26
Those are sources that nned to be compiled. If you go to synaptic and enable the universe repositories, you'll be able to install both Azureus and Thunderbird off synaptic.

---

### Post by hajk on 2006-06-26
[QUOTE=virtuexru]I know this may be a REALLY stupid question. 

But, how do I go about installing software? I have downloaded Azureus and Thunderbird and they have a .tar.bz2 and a .tar.gz file ext. I can double click to see a winzip-type program where I can extract to but even if I do extract where would I point it to? the BIN directory?

Any help would be appreciated.[/QUOTE]

NO, only people not asking questions are stupid...;) 

Installing software in Ubuntu is normally done as .deb packages using Synaptic.
The two examples that you mention, Azureus and Thunderbird, are both available in the Dapper repositories (as "azureus" and 'mozilla-thunderbird"), but you may have to uncomment the universe and multiverse repositories with 
"sudo nano /etc/apt/sources.list" in a terminal. 

Once you get to be a bit more experienced, then you may wish to install software that is not available as .deb packages. A tar.gz archive can be extracted with the command "tar xvzf ....tar.gz"; and a tar.bz2 archive with "tar xvjf ....tar.bz2". That just unbundles the archive to a newly made subdirectory. You will then have to follow instructions (typically in a README file) for installing the software. In some cases this just means installing the compiled programme to some directory of choice -- the /usr/local directory tree is the proper location. In other cases, you just have source code that needs to be compiled -- I suggest that you leave that as a future project for now.

---

