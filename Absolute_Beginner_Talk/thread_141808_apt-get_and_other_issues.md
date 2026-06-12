---
title: "apt-get and other issues"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by senthil on 2006-03-09
Hello there,
Can anyone point me to a link/tutorial where apt-get is described in detail, i could not find information by googling. I also want to know how one can log in as root in gui mode. Unlike other distros, Ubuntu does not allow root to login in GUI. How then, I wonder a novice like me can configure network, sound etc after installation.

It would also be nice if someone can tell me if the beginners talk forum is searchable or not. This would be helpful if someone wants to find if the query had been already raised and answered, thus avoiding repetitions.


Thank You,

Senthil

---

### Post by codejunkie on 2006-03-09
[QUOTE=senthil]Hello there,
Can anyone point me to a link/tutorial where apt-get is described in detail, i could not find information by googling. I also want to know how one can log in as root in gui mode. Unlike other distros, Ubuntu does not allow root to login in GUI. How then, I wonder a novice like me can configure network, sound etc after installation.

It would also be nice if someone can tell me if the beginners talk forum is searchable or not. This would be helpful if someone wants to find if the query had been already raised and answered, thus avoiding repetitions.


Thank You,

Senthil[/QUOTE]
you shouldn't need to login as root via gui in Ubuntu, Ubuntu uses sudo instead of root this [**[COLOR="Sienna"]link[/COLOR]**]("https://wiki.ubuntu.com/RootSudo") will describe how sudo works and when things ask you for the administrator password enter the password of the first user you created.

---

### Post by meborc on 2006-03-09
there is a lot of info in wiki.ubuntu.com ... 

i found this [https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo](https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo) on ap-tget... hope it helps

---

### Post by senthil on 2006-03-09
Hi,
Thanks for the links. I need to install a new package called xfig. Here is what i am doing:
sudo apt-get update

and i get the following:
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hoary-updates/restricted Sources

Next, I do:
sudo apt-get install xfig

And I get the following error message:
Reading package lists... Done
Building dependency tree... Done
Package xfig is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xfig has no installation candidate


What am I doing wrong ? Am I missing something ? Please help, I need to install Xfig asap. Can I install a RPM for xfig in Ubuntu ?

Thanks in advance for your help,

Senthil

---

### Post by jasay on 2006-03-09
xfig is in the universe repo, which is not activated by default.  THis link tells you how to activate it.  [http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

---

### Post by aysiu on 2006-03-09
There's a "search this forum" link in each forum (in the upper-right, but not at the way top).

You can also do a Google search in this format: *site:ubuntuforums.org name of problem*. That works for me.

For apt-get, you can read this:
[http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

For up-to-date repositories:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

---

### Post by senthil on 2006-03-09
[QUOTE=jasay]xfig is in the universe repo, which is not activated by default.  THis link tells you how to activate it.  [http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)[/QUOTE]


Thanks a lot, It worked!!!!

Senthil

---

### Post by senthil on 2006-03-09
[QUOTE=aysiu]There's a "search this forum" link in each forum (in the upper-right, but not at the way top).

You can also do a Google search in this format: *site:ubuntuforums.org name of problem*. That works for me.

For apt-get, you can read this:
[http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

For up-to-date repositories:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)[/QUOTE]

Thanks for your help Aysiu, I will search google before posting.

senthil

---

### Post by aysiu on 2006-03-09
[QUOTE=senthil]Thanks for your help Aysiu, I will search google before posting.[/QUOTE] I wasn't trying to say you should search before posting. I was replying to this part of your original post: > It would also be nice if someone can tell me if the beginners talk forum is searchable or not. This would be helpful if someone wants to find if the query had been already raised and answered, thus avoiding repetitions.

---

### Post by senthil on 2006-03-09
[QUOTE=aysiu]I wasn't trying to say you should search before posting. I was replying to this part of your original post:[/QUOTE]

Hi,
Its ok, that was one of my original queries too. Your tip was nice and searching the google is the first and the best to find out anything.

Senthil

---

### Post by aysiu on 2006-03-09
I just didn't want you to think I was scolding you.

---

