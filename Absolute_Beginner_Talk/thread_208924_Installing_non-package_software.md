---
title: "Installing non-package software"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by herrdoktor330 on 2006-07-04
Hello. I have a total linux n00b question:

I'm having trouble installing non ubuntu/debian package software.

To explain the issue I'm having, I'm trying to install "gnormalize". I've already loaed the "normalize-audio" dependancy. I've tried running the install command, but I'm not sure as to where I should be installing the package so that it will run. I've pointing the install to the directory /etc/gnormalize-0.49. I made the directory as root and ran the install program with the sudo command but the install doesn't do anything that I can figure out.

So what am I doing wrong?

---

### Post by taurus on 2006-07-04
Is it in .deb format?  If you can tell me exactly where you download it, maybe I can have a look and tell you how to install it.  Usually, you want to install binaries in /bin, /usr/bin, or even /usr/local/bin...

---

### Post by Jagot on 2006-07-04
This should help you with installing pretty much anything:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by herrdoktor330 on 2006-07-04
[QUOTE=taurus]Is it in .deb format?  If you can tell me exactly where you download it, maybe I can have a look and tell you how to install it.  Usually, you want to install binaries in /bin, /usr/bin, or even /usr/local/bin...[/QUOTE]

[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/) <- this is where I got the tarball.

I'm going to do some more reading... I know that there's a little trick to get it to work with ubuntu as described in this thread:

[http://www.ubuntuforums.org/showthread.php?t=164610&highlight=gnormalize](http://www.ubuntuforums.org/showthread.php?t=164610&highlight=gnormalize)

but I'm trying to get to that point so I can make that link.

---

### Post by taurus on 2006-07-04
Well, the link to debian package is dead!!!  So, which one did you download:  the .tar.gz or the .rpm one?  If you can tell me which one you've downloaded, I can tell you how to install it...

---

### Post by herrdoktor330 on 2006-07-04
[QUOTE=taurus]Well, the link to debian package is dead!!!  So, which one did you download:  the .tar.gz or the .rpm one?  If you can tell me which one you've downloaded, I can tell you how to install it...[/QUOTE]

the .tar.gz. 

I've been getting all the dependent packages as you research.

---

### Post by herrdoktor330 on 2006-07-04
[QUOTE=herrdoktor330]the .tar.gz. 

I've been getting all the dependent packages as you research.[/QUOTE]

To explain, the reason why I'm asking this question is that I figure there's going to be other applications I'm going to want to install that there is no package for under Ubuntu's package manager... so I want to get comfortable installing new software on my own. I figure once I learn the ins and outs of seting up Gnormalize, this will make future programs much easier.

If it makes you feel any better, I did figure out how to compile my own Kernel... not perfect... but I did learn SOMETHING from it.

---

### Post by herrdoktor330 on 2006-07-05
Hey... I just did the easy thing and installed from the .RPM file using alien. That was too simple.

For the life of me, I can't figure out how the other install from the tarball didn't work. Oh well...

Thanks for the help, guys. It is appreciated.:-\"

---

