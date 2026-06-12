---
title: "What Adobe Reader version do I need?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-10
Found the Adobe Reader download for Linux but it asks if I want tar.gz or rpm. Which one do I need. They're both around 40 megs so on dialup, I'd like to get the right one. Thanks.

---

### Post by Maestro23 on 2007-04-10
> **jacatone said:**
> Found the Adobe Reader download for Linux but it asks if I want tar.gz or rpm. Which one do I need. They're both around 40 megs so on dialup, I'd like to get the right one. Thanks.

Why don't you try the repositories first?  What version of Ubuntu are you running?

> sudo aptitude install acroread

If you still want to get the package from the site, read one of  the following links on installing:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by miggols99 on 2007-04-10
You should use add/remove programs. Go to Applications >> Add/Remove and search for Adobe Reader

---

### Post by Dekunuts on 2007-04-10
you don't need anyhting from the adobe website, it may seem weird if you're new to linux, but go to the applications menu and click add/remove. There you can find several porgrams for reading pdf, including one from adobe. Just select the one you want and the computer will automatically download what you need and ad the program entry in the programs menu.

---

### Post by jacatone on 2007-04-10
I'm running v6.06. Where would I look for reader in Synaptic Package Manager? I'm not online yet with Ubuntu so I haven't been able to update anything. I notice SPM doesn't let me add applications. It only shows remove applications.

---

### Post by Maestro23 on 2007-04-10
> **jacatone said:**
> I'm running v6.06. Where would I look for reader in Synaptic Package Manager? I'm not online yet with Ubuntu so I haven't been able to update anything. I notice SPM doesn't let me add applications. It only shows remove applications.

Hmm.. Either way, you are going to have dependency issues with the .tar or .rpm package.  Going to be rough without access to the repositories.  For the .rpm you will need a package called "alien".  It is covered in those links I provided for you.

You can go to Ubuntu packges:[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Download all the packages(+their dependencies) and do it that way.  Save to a flash drive and fire up Ubuntu and install that way.

---

### Post by jem7v on 2007-04-10
On the other hand, Ubuntu already has Evince installed, which is a document reader that handles .pdfs perfectly well.  It's under Applications->Graphics->Document Viewer.  Try to open an acrobat file and you'll see what I mean.

The reason Synaptic wouldn't give you any packages to add is that if you aren't online it won't have access to the online repositories, which means it doesn't have anything to install.

---

### Post by alliantdevil on 2007-04-16
"sudo aptitude install acroread " dosnt find a package to install. The only reason I want to install Adobe reader is because none of the OSS options i have tried can open a password protected PDF even though I am 100% sure i've typed in teh correct password (my own PDF's that I made on windows). Also, I have made sure that all repos (multiverse, etc) are enabled. I am also currently on Ubuntu 7.04

---

### Post by jonathan21 on 2007-04-16
you can open pdf files with evince which already comes with ubuntu.

---

### Post by mcduck on 2007-04-16
> **alliantdevil said:**
> "sudo aptitude install acroread " dosnt find a package to install. The only reason I want to install Adobe reader is because none of the OSS options i have tried can open a password protected PDF even though I am 100% sure i've typed in teh correct password (my own PDF's that I made on windows). Also, I have made sure that all repos (multiverse, etc) are enabled. I am also currently on Ubuntu 7.04
You'll have to enable Universe & Multiverse repositories first, as Adobe's PDF reader is not free software..

Just go to System/Administration/Software Sources, you can enable them there.

---

### Post by TheLive1 on 2007-04-16
I second using Evince, it is that DAMN fast... But if you really want Acrobat just follow the instructions/comments above.

---

### Post by Man_Beach on 2007-04-16
Evince is fine for viewing, but if you want to _print_ pdfs properly you really need Acrobat Reader.

---

### Post by 3rdalbum on 2007-04-16
Don't use the RPM on the Adobe website - it causes problems with Apt.

In Ubuntu 6.06, the program isn't called Software Sources, it's called Software Properties. You may need to click the Edit button when Ubuntu 6.06 LTS (binary) is selected, and then add the checkbox for "Multiverse". Reload the package list when it asks you, and you should be ready to install Acrobat.

---

