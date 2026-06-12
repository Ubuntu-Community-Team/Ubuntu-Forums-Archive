---
title: "Adding repositories issue"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by rjcube on 2006-06-04
I have been follwing the [Unoffical Ubuntu 5.04 Starter Guide]("http://ubuntuguide.org/"), although I dont think i have 5.04, I am using 6.06 (just downloaded today) and I was trying to add new repositories, it was saying to modify the sources.list, but it wasnt the same so I used the [Sample]("http://ubuntuguide.org/sample/sources.list_extrarepositories") that they had provided. So that is what the file looks like now.

When I go to the termenal and try to install java, heres what goes on.
```
rjcube@rjcube-desktop:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

```

What do I need to do to get Java (and other repositories) capable of being installed?

Edit: Also, Is it possible to connect my Phillips HDD1630/17 (MP3 Player) to Ubuntu Linux?

---

### Post by Kuraboy on 2006-06-04
I dont know about apt-get, but try Synaptic.

open Synaptic -> Settings -> Repositiories 

a new windows opens, then choose Ubuntu 6.X (binary)

press edit, and mark the universe and multiverse options.

then go bakc to main and search after java.

hope it helps...

---

### Post by rjcube on 2006-06-04
[QUOTE=Kuraboy]I dont know about apt-get, but try Synaptic.

open Synaptic -> Settings -> Repositiories 

a new windows opens, then choose Ubuntu 6.X (binary)

press edit, and mark the universe and multiverse options.

then go bakc to main and search after java.

hope it helps...[/QUOTE]

Well considering I blindly replaced the sample on the Ubuntu 5.04 Starter guide, everything in that file is wrong, so it effects the list of repositories in Synaptic.

Also, when I click edit on one of those in the list in Synaptic, I dont see anything about Universe and multiverse.

---

### Post by Kuraboy on 2006-06-04
hmm, I dont know buy you have ubunutu 6 right?

I attached a picture of the options I choose...

---

### Post by rjcube on 2006-06-04
this is what mine looks like.
[[IMG]http://img228.imageshack.us/img228/7704/screenshot0hg.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshot0hg.png)

well i think my main problem here is the sources.list file. 

It seems that in your screen shot, the repositories list shows version 6 on everything, mine may not be working considering i used that Guide with the wrong version, here is my idea open up /etc/apt/sources.list, and paste everything that is in there, because i think everything is off in that, so its making it not work.

---

### Post by Kuraboy on 2006-06-04
you have maybe old ubunutu?

but type universe and multiverse in the Components field beside main and restricted with space inbetween

---

### Post by rjcube on 2006-06-04
[QUOTE=Kuraboy]you have maybe old ubunutu?

but type universe and multiverse in the Components field beside main and restricted with space inbetween[/QUOTE]

I just downloaded it today so theres no way I could have old, i know i have 6.06, also im pretty sure the main problem is because the sources.list file is so messed up

---

### Post by ubuntu_demon on 2006-06-04
here's a clean sources.list :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

---

### Post by rjcube on 2006-06-04
[QUOTE=ubuntu_demon]here's a clean sources.list :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)[/QUOTE]

That worked perfectly, thanks, but when I try installing Java (installing using Synaptic)  it comes up with these errors:

```
E: emacs21: subprocess post-installation script returned error exit status 1
E: cedet-common: dependency problems - leaving unconfigured
E: eieio: dependency problems - leaving unconfigured
E: speedbar: dependency problems - leaving unconfigured
```

The packages I was trying to install were: sun-java5-bin, sun-java5-jre, and sun-java5-plugin

---

