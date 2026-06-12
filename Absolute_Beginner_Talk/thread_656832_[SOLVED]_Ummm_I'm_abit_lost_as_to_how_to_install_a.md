---
title: "[SOLVED] Ummm I'm abit lost as to how to install amsn... any links?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Jim01 on 2008-01-03
ok basicly explained in topic title.... I'm abit lost.... I've played with terminal and its cool... pretty much like dos so I'm pretty up to that... but I've googled it and its coming up with problems that I dont understand....  any links as to where to where to go?

Thanks... just remember this is the first time I'm installing an app so once I've installed a few I should start getting the hang of it. ;)

---

### Post by Seti on 2008-01-03
```
sudo apt-get install amsn
```

---

### Post by Jim01 on 2008-01-03
> **Seti said:**
> ```
sudo apt-get install amsn
```
woah man you guys are on the ball when it comes to replying! lol

---

### Post by Jim01 on 2008-01-03
> **Seti said:**
> ```
sudo apt-get install amsn
```
ok it got an error.. :E: Couldn't find package amsn

---

### Post by Seti on 2008-01-03
What version of Ubuntu are you using?

also, go to System>Administration>Software Resources.

It will ask you for your password to authorize using system tools.

Make sure all the downloadable sources listed are checked. It should work.

---

### Post by ~LoKe on 2008-01-03
> **Jim01 said:**
> ok it got an error.. :E: Couldn't find package amsn

Enable the multiverse repository by typing this into the terminal:
```
gksu gedit /etc/apt/sources.list
```
Then look for these lines:
> deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
Make sure there's no # or ## in front of them, if there is, remove it.

**EDIT**: Seti's method is much more elegant and simple.

---

### Post by Seti on 2008-01-03
"EDIT: Seti's method is much more elegant and simple."

thanks, but it isn't really. I guess its just the GUI way of doing it, such that a new linux user would find easy to understand. Another (even better way to do it) would be to just:
```
sudo vim /etc/apt/sources.list
```
and then just key down to the commented-out multiverse repos and uncomment them. Save the file.
```
sudo apt-get update
```
and 
```
sudo apt-get install amsn
```

---

### Post by ~LoKe on 2008-01-03
> **Seti said:**
> "EDIT: Seti's method is much more elegant and simple."

thanks, but it isn't really. I guess its just the GUI way of doing it, such that a new linux user would find easy to understand.

GUI apps are nice and easy, but I guess it doesn't hurt to help people familiarize themselves with the terminal. ;)

---

### Post by Jim01 on 2008-01-03
lol well I got it going anyway ;) thanks again for your time and help :)

---

