---
title: "Questions on how programs and plug-ins work in Gnome/7.1"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by devilchrist on 2008-02-28
I come from windows back ground.  Before windows I was pretty knowledgeable in use of MS DOS 5.0 and up,  I was editing autoexec.bat and config.sys files almost every day to get program to run.

most of that I have not touched the days of window98 SP2  when MS actaully it running smoothly.

So a few questions on how linux or Gnome, or any linux GUI oS for that matter

1.  How does a program get installed in a Linus environment?  I understand the whole respository part. But My question really is regarding how Gnome associates the program?  In windows Program installs DLL's and modifies the registry to let windows know what files to use and how to use them.  So you can't simply just copy and past the program folder and expect it to run like you could in old MS DOS 

How does programs work in linux?   If I was to say install a non repository program?  How are files installed, are the DLL's that program installs in the OS folders/directories? or does the program just run from it's extracted folder.

2.  How does plug ins work.  Above comments apply.  Say for instance Java, realplayer or Accrobat.  I need to be able to read Acrobat files, as well have Firefox be able to play Realplayer within the browser to use Gnome for Devry School work.

If I can understand the concept of how linux associated the files and programs I'll have better understanding of how to install, remove, and manupliate

there are alot of answers to these questions but no explanations.  I really want to learn linux but answers without explanations of what each command does and how it effect the program, I'm just getting more confused.

---

### Post by celticbhoy on 2008-02-28
Not that technical myself, but you might find some of the info you want here :-

[http://tldp.org/guides.html](http://tldp.org/guides.html)

---

### Post by northern lights on 2008-02-28
Dynamic link libraries are really not a Windows or Microsoft specific idea -  it's simply a shared or remote library that is not placed in the executable during compilation, but a separate library called upon as needed. In GNU/Linux, those are found in "/lib/" and "/usr/lib/".

There is no (thank the Lord) real eqivalent to the Windows registry. Most system related configuration files are stored in "/etc/" and sometimes "/usr/local/etc/". For the configuration of the gnome desktop and a few built-in gnome apps, there's "gconf", run ```
gconf-editor
```
to check it out. This interface will be the most registry-like Linux has to offer. Again, thank godness.

---

### Post by philinux on 2008-02-28
Some of it is explained here.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

