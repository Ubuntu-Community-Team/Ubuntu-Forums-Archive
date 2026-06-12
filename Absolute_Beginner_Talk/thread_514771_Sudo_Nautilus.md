---
title: "Sudo Nautilus"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-08-01
Hi, 

I've been playing around with the new Avant and I like a visual for whatever I'm doing. So I use the "sudo nautilus" command if I need to delete a file. I needed to delete certain AWN related files from /usr/local/lib and when I did I noticed in Terminal some weird looking characters..I'm guessing errors or something

I usually use "sudo nautilus" when I need to delete, copy and paste and I realized that I always see output messages in Terminal, but never really thought about it. Usually the messages say something about "hash" or "meta" I can't remember..Is this bad?:confused: I only use "sudo nautilus" to delete, copy and paste and the like...Is there a log that I can copy and paste the outputs so you guys can better understand what I'm talking about...I really don't want to mess up my install. :(

---

### Post by ugm6hr on 2007-08-01
It should really be:
```
gksudo nautilus
```

Just make sure you don't delete / move any necessary files with this!

---

### Post by jombeewoof on 2007-08-01
sudo nautilus > ~username/Desktop/error.txt

will put a text file with the output in it on your desktop

---

### Post by isaacj87 on 2007-08-01
> **ugm6hr said:**
> It should really be:
```
gksudo nautilus
```

Just make sure you don't delete / move any necessary files with this!

What are the dangers??

---

### Post by ugm6hr on 2007-08-01
> **isaacj87 said:**
> What are the dangers??

For comparison - you know in Windows when you go to "My Computer" and browse through C:/ until you get to places like C:/Windows/System it warns you not to look there because there are important files necessary to run Windows (or something like that).

Same thing applies - gksudo nautilus gives you access to all system files etc.  Which, in the wrong hands, can be disastrous.  Deleting some of those files will break Ubuntu, just as deleting system files in Windows will break it too.

As long as you only edit / delete / move files that you know exactly what they do - it should be ok.  So just be aware.

---

### Post by forestpixie on 2007-08-01
I'd have a look at this too

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by isaacj87 on 2007-08-01
> **ugm6hr said:**
> For comparison - you know in Windows when you go to "My Computer" and browse through C:/ until you get to places like C:/Windows/System it warns you not to look there because there are important files necessary to run Windows (or something like that).

Same thing applies - gksudo nautilus gives you access to all system files etc.  Which, in the wrong hands, can be disastrous.  Deleting some of those files will break Ubuntu, just as deleting system files in Windows will break it too.

As long as you only edit / delete / move files that you know exactly what they do - it should be ok.  So just be aware.

Crystal clear explanation...thank you.

---

### Post by ugm6hr on 2007-08-01
No worries.  I think this is an important concept to appreciate.  

I actually have a panel quick-launcher for *gksudo thunar* (Xubuntu equivalent), so that I can edit system files: to put new icons etc into the /usr/share/ directory; edit xorg.conf; copy files to var/cache/apt/archives; do various other things.  

It is useful, but it is important to have a degree of respect for that level of control.  While Windows warns you not to look, it does allow you to edit all those files with a single click.  At least Ubuntu asks for a password.

---

### Post by isaacj87 on 2007-08-01
Just out of curiosity...why would there be an output at all in terminal when performing such simple tasks like delete or copying?

I wish I could give an example but I don't have a log of anything.

---

### Post by Outrunner on 2007-08-01
> **isaacj87 said:**
> Just out of curiosity...why would there be an output at all in terminal when performing such simple tasks like delete or copying?

I wish I could give an example but I don't have a log of anything.

Because there can be errors, and it's useful to know them if you want to fix the problem.

---

### Post by frodon on 2007-08-01
> **isaacj87 said:**
> What are the dangers??**If you use sudo nautilus instead of gksudo nautilus it can corrupt the IceAutority file for example** which prevent session login (it can be fixed easily just deleting the file)..
One should always use gksudo to open a graphical apps as root and sudo for command line tools.

e.g. :
[http://ubuntuforums.org/showthread.php?t=396992](http://ubuntuforums.org/showthread.php?t=396992)
[http://ubuntuforums.org/showthread.php?t=327673](http://ubuntuforums.org/showthread.php?t=327673)
[http://ubuntuforums.org/showthread.php?t=238311](http://ubuntuforums.org/showthread.php?t=238311)

---

### Post by asmoore82 on 2007-08-01
> **jombeewoof said:**
> sudo nautilus > ~username/Desktop/error.txt

will put a text file with the output in it on your desktop

the '>' redirector only redirect **Standard Output**; **Standard Error** ouput
messages will still show up in the terminal ...

'&>' is the catch-all operator to redirect both **stdout** and **stderr** messages to a file

---

