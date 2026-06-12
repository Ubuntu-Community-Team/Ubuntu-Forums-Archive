---
title: "Installing programs/Skype"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Ched on 2006-05-24
Im new to Ubuntu, I just installed it a few days ago. I have been trying to install a program named Skype, and for the life of me, I just can't figure out how. My friend said something about using the terminal, but im not sure what to do. Any help with installing Skype, or any programs in general would be greatly apprciated. 

Thanks in advance :)

---

### Post by aysiu on 2006-05-24
This and my signature should help:
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

---

### Post by tuxcantfly on 2006-05-24
fetch it from here:

[http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)

now, open up the terminal and type:

sudo dpkg -i skype_version_i386.deb

run with the command skype

---

### Post by an.echte.trilingue on 2006-05-24
If you have not already, familiarize yourself with this page in the wiki:

[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware)

And then this page:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)


(Another useful page is called restricted formats but that is off topic)

Then go here:
[http://plf.zarb.org/mirrors.php](http://plf.zarb.org/mirrors.php) and either add one of his repositories (the one in France works best) or download skype and use dpkg to install it.

Good Luck!

---

### Post by Ched on 2006-05-24
When I do this, im asked to insert "'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)"

Is this the CD i installed Ubuntu with?

---

### Post by aysiu on 2006-05-24
Go to System > Administration > Synaptic Package Manager > Settings > Repositories and uncheck the box  for the CD-ROM repository. Then click Reload.

Then, read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by Ched on 2006-05-24
I love you Aysiu <3

---

### Post by user1397 on 2006-05-24
[quote=Ched]I love you Aysiu <3[/quote]
lol, who doesn't :p

---

### Post by grace on 2006-05-25
i've also just installed skype on fresh ubuntu, but it seems to not be working very well.  i'll call, get 1 second of talk-time, and then i won't be able to make another call again.  

can anybody help please?  thanks in advance

also, why is skype so ugly in linux?? :-k

---

### Post by Sef on 2006-05-25
Grace > Could you please start another thread for your problem with skype.  

1) Likely you will get more help.

2) Otherwise it looks like you're hijacking the thread, which i am sure is not your intention.

---

### Post by bluenova on 2006-05-25
[QUOTE=grace]i've also just installed skype on fresh ubuntu, but it seems to not be working very well.  i'll call, get 1 second of talk-time, and then i won't be able to make another call again.  

can anybody help please?  thanks in advance

also, why is skype so ugly in linux?? :-k[/QUOTE]

[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

---

