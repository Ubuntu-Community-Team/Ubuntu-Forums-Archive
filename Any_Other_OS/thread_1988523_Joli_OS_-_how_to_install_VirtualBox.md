---
title: "Joli OS - how to install VirtualBox"
date: 2012-05-27
forum: Any Other OS
---

### Post by qwertyjjj on 2012-05-27
How can I install VirtualBox on the Joli OS?
Also, where do I copy my existing .thunderbird and .mozilla profiles from ubuntu?

---

### Post by wilee-nilee on 2012-05-27
> **qwertyjjj said:**
> How can I install VirtualBox on the Joli OS?
Also, where do I copy my existing .thunderbird and .mozilla profiles from ubuntu?

Virtualbox @oracle has multiple download types, I suspect the .deb will install in it. In ubuntu you add the host to the guests group, to do this post #2. 

[https://forums.virtualbox.org/viewtopic.php?f=7&t=49529](https://forums.virtualbox.org/viewtopic.php?f=7&t=49529)

I just save my thunderbird and mozilla which are hidden and slip them to  other ubuntu's you will have to experiment I suspect with jolicloud, you can do the same.

---

### Post by uRock on 2012-05-27
Moved to Other OS/Distro Talk, as this isn't an ubuntu support request.

---

### Post by PhantomTurtle on 2012-05-27
Joli OS is based off Ubuntu 9.10 or 9.04 (I can't remember, sorry). Virtualbox does not support this version of Ubuntu any more. You are going to have to get the version of All distributions at the bottom of the downloads list for Linux hosts on their site or get an older version of it. You are going to have to launch it from terminal, unless you know how to add it to that homepage thing (not sure what it's called).

---

### Post by wilee-nilee on 2012-05-27
> **PhantomTurtle said:**
> Joli OS is based off Ubuntu 9.10 or 9.04 (I can't remember, sorry). Virtualbox does not support this version of Ubuntu any more. You are going to have to get the version of All distributions at the bottom of the downloads list for Linux hosts on their site or get an older version of it. You are going to have to launch it from terminal, unless you know how to add it to that homepage thing (not sure what it's called).

I suspect joli has been updated to at least the 10.04 version of ubuntu at the least.

---

### Post by PhantomTurtle on 2012-05-27
> **wilee-nilee said:**
> I suspect joli has been updated to at least the 10.04 version of ubuntu at the least.

According to Wikipedia the last stable release was 14 months ago, so maybe. The last time I used Joli OS (which was pretty recently), it looked like it was 9.10(I could be wrong though).

EDIT: Nevermind, I was wrong, it is based off of 10.04. So the deb file for 10.04 should be fine.

---

### Post by qwertyjjj on 2012-05-28
hmm
what dependencies?

> 
j@j-jolicloud:/tmp$ sudo dpkg -i virtualbox-4.1_4.1.16-78094~Ubuntu~lucid_i386.deb
[sudo] password for j: 
Selecting previously deselected package virtualbox-4.1.
(Reading database ... 106647 files and directories currently installed.)
Unpacking virtualbox-4.1 (from virtualbox-4.1_4.1.16-78094~Ubuntu~lucid_i386.deb) ...
dpkg: dependency problems prevent configuration of virtualbox-4.1:
 virtualbox-4.1 depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not installed.
 virtualbox-4.1 depends on libqt4-opengl (>= 4:4.5.3); however:
  Package libqt4-opengl is not installed.
dpkg: error processing virtualbox-4.1 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 virtualbox-4.1
j@j-jolicloud:/tmp$ 


---

### Post by uRock on 2012-05-28
> **qwertyjjj said:**
> hmm
what dependencies?

[s]What do you mean? There was no mention of dependancies in other posts, nor in the code with quote tags?[/s]
Oops. Apologies for my failure to read.

---

### Post by PhantomTurtle on 2012-05-28
> **uRock said:**
> What do you mean? There was no mention of dependancies in other posts, nor in the code with quote tags?

You might want to check again,
```
dpkg: dependency problems prevent configuration of virtualbox-4.1:
virtualbox-4.1 depends on libcurl3 (>= 7.16.2-1); however:
Package libcurl3 is not installed.
virtualbox-4.1 depends on libqt4-opengl (>= 4:4.5.3); however:
Package libqt4-opengl is not installed.
```

libcurl3 and libqt4-opengl should be in the lucid repositories. Try,
```
sudo apt-get install libqt4-opengl libcurl3
```

---

### Post by uRock on 2012-05-28
Oops. Apologies for my failure to read.

---

