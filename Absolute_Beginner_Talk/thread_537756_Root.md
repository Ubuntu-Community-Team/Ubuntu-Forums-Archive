---
title: "Root"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by zoohouse on 2007-08-29
Hi.

I'm new to Ubuntu. I have tried to install clamav and it succeeded :-)
But now that i try to update it, it tells me that i need to be root.
What is root? And how can i get it?

Kim.

---

### Post by forestpixie on 2007-08-29
use sudo in front of the command

to update sources for example

sudo apt-get update

---

### Post by Dr Small on 2007-08-29
Are you trying to upgrade clamav in the command line or in GUI (Graphical User Interface)?

If in the command line, type "sudo" before the command, to run that command as "super user", or "root".

If in the GUI, you will need to open the upgrading screen (I have no idea how) by going to ALT+F2 and type "gksudo" before the actual name of the app. Like "gksudo clamav" and then upgrade inside of there or something.

Dr Small

---

### Post by asmoore82 on 2007-08-29
> **zoohouse said:**
> Hi.

I'm new to Ubuntu. I have tried to install clamav and it succeeded :-)
But now that i try to update it, it tells me that i need to be root.
What is root? And how can i get it?

Kim.

FYI
[https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2](https://wiki.ubuntu.com/CriticismFAQ#head-1663544b421081799ed551bdfa891411191121f2)

and Welcome to GNU/Linux, great to have you!!

---

### Post by zoohouse on 2007-08-29
Hi.

Im only using the terminal Alt+F2 Don't know how to use other things yet.

It just wont let me be root. I have tryed to tyoe  gksudo clamav and sudo root, but it does not help.

Think of me as someone who has never used Ubuntu before and please learn me how to take control over the programs :-)

---

### Post by forestpixie on 2007-08-29
try to use the terminal for it then

it's in applications > accessories >terminal

try in there, can't be much help with clamav because I don't use it

---

### Post by zoohouse on 2007-08-29
But i am using the terminal. Alt+F2 gets you to the terminal (as far as i know)
I have a danish version. Wish i had it on english, then it would probably be much more easy

---

### Post by ddrichardson on 2007-08-29
Open System/Administration/Users & Groups. Have a look for a clamav group, if there is one then add your username to it.

I can't be sure but that's how AVG gives permission for updates.

---

### Post by zoohouse on 2007-08-29
Sorry for the quick reply. I found out i could change the language.  Now its much more easy- 
Can you tell me how i get root? I still havnt figured out yet:(
#8 It didn't worked.

---

### Post by forestpixie on 2007-08-29
to be root you need to preface a command either with sudo, or if it's a graphical app you're running gksudo

for instance to use apt-get to install without sudo gives this result
```

kevin@kevin-desktop:~$ apt-get install exaile
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

to run as root you need to 

```
sudo apt-get install exaile
```

---

### Post by zoohouse on 2007-08-29
#10
Thank you so much:)

Will i need to do the command every time i log in?

---

### Post by forestpixie on 2007-08-29
I really have no idea - as I said at the beginning I don't use clamav - maybe. 

and you can when you're replying - paste someones post or bit of it and click the  quote icon - looks like a speech bubble :)

---

### Post by zoohouse on 2007-08-29
Hmm i found out that i still have problems with the clamv.
It still wants me to be root, but i did as you told me to do. But it's probably not necessary anyway to have anti virus program for Ubuntu?
But i still would like to get root. Just don't know why i can't.

---

### Post by forestpixie on 2007-08-29
it really depends what you mean, what you're trying to do and how you're trying to do 

> But i still would like to get root. Just don't know why i can't.

this doesn't make a great deal of sense to me

as far as viruses go - I believe the only problem you're likely to get is if you pass one on to others or to yourself if you're dual booting.

---

### Post by bodhi.zazen on 2007-08-29
To perform admin activities as root preceed the command with sudo


	[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to run graphical applications as root (nautilus for example) use gksu (kdesu for kde users)

```
gksu nautilus
```

If you want to perform a number of activities as root use sudo -i

```
sudo -i
```

---

