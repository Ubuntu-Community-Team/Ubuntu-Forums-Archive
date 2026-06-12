---
title: "Installing Apps"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by NovaNine on 2007-01-08
Hey guys, some people over at OCN referred me to this forum (any other OCNers around ?)
Well, I'm a real noob for linux and ubuntu in general, and since OCN couldn't provide me for answers, I decided to ask you guys.
This maybe a stupid question but don't laugh at me... please... :p
How do you install anything on Ubuntu ? I've downloaded the .tar.gz format of Firefox but can't install it... I've extracted it, and there are a lot of files but I have no idea what to do now...
Any help appreciated, thanks !
PS : I'm using 6.06 LTS on PC

---

### Post by Bachstelze on 2007-01-08
Hi and welcome to Ubuntu :)

Everything you need to know about installing software in Ubuntu is [here](http://www.psychocats.net/ubuntu/installingsoftware) :)

---

### Post by NovaNine on 2007-01-08
Merci ! ( I saw you were from France lol, I'm french too BTW :))

---

### Post by NovaNine on 2007-01-08
Eh... I have a problem...
On the tar.gz part of the page you gave me, it was written that I should put the .tar.gz file on the desktop, and, with the terminal type this :
> tar -xvzf firefox-2.0.0.1
But it gives errors :
> gravity@gravity-desktop:~$ tar -xvzf firefox-2.0.0.1
tar: firefox-2.0.0.1: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
gravity@gravity-desktop:~$

What's the problem ?

---

### Post by RMorris78 on 2007-01-08
you know, you might be better off just using apt-get to download/install software. i have found compiling from source to be really frustrating

try this - from a terminal type..

```
sudo apt-get update
```

and then

```
sudo apt-get install firefox
```

---

### Post by quartzy on 2007-01-08
You have to be in the same directory as the file you are trying to unzip, if it's on your desktop then do 

```
cd Desktop
```

and try again, 'ls' without the quote will show you what is in your current directory.

---

### Post by NovaNine on 2007-01-08
Well, I would, the thing is that here in Indonesia, we don't have unlimited broadband, I have a one gig quota to respect each months, and would want to keep installation files of things... 
Of course I'd do apt-get if I'm forced to, but if I can compile from source, it'd be great !

---

### Post by Bachstelze on 2007-01-08
[This script](http://www.psychocats.net/ubuntu/firefox) will install the Firefox build from mozilla.com for you. If you want to do it yourself, manual installation instructions are [here](https://wiki.ubuntu.com/FirefoxNewVersion).

---

### Post by NovaNine on 2007-01-08
Ok thanks

---

