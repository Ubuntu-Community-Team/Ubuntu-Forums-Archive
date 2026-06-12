---
title: "from GNOME to KDE"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-13
how does one go from GNOME to KDE to GNOME environment

---

### Post by mlentink on 2007-06-13
You mean installing KDE in an already installed ubuntu system?
```
sudo apt-get install kubuntu-desktop
```
If you have already done this, then at login time you get the choice between the desktop-environments, or so I am told (I only have Gnome)

---

### Post by jhenager on 2007-06-13
If you mean freely switch between Gnome and KDE, I don't know. From what I understand, you install Ubuntu if you like Gnome, and Kubuntu if you prefer KDE.
I have used them both, and really have no preference. I used KDE for years under Red Hat, and liked it. I have only used Gnome with Ubuntu, and like it.
Someone correct me if I am mistaken about the switching.

---

### Post by taurus on 2007-06-13
And if you decide to remove Gnome (or KDE) later, this guide would help.

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by jhenager on 2007-06-13
> **mlentink said:**
> You mean installing KDE in an already installed ubuntu system?
```
sudo apt-get install kubuntu-desktop
```
If you have already done this, then at login time you get the choice between the desktop-environments, or so I am told (I only have Gnome)

I am trying this now on my VM. Thanks.

---

### Post by pardesi on 2007-06-13
when i read that i f i used 
```
aptitude
```
instead of

```
apt-get
```
while installing environments the n the procedure is much easier apparently ...i am a noob to all thsi can someone tell me how i can install KDE environment in Ubuntu 7.04 easily and remove it that easily:(

---

### Post by dptxp on 2007-06-13
Install kde-core instead of kubuntu-desktop. Much smaller download.
Select at time of log in. Set anyone as default.
Use aptitude.
Uninstall uses uninstall command instead of install.

kde has a few desktop effects.
And it is not light anymore.

---

### Post by pardesi on 2007-06-13
thanks...can you write the code exactly also do you say will i be given a option during login which environment to choose
do kde and kubuntu-desktop do same thing

---

### Post by dptxp on 2007-06-13
sudo aptitde update
sudo aptitude install kubuntu-desktop

For the lighter kde-core, replace kubuntu-desktop with kde-core in 2nd line.
Download will take some time, I think about 60-70 MB for kde-core.

Install and check the difference, keep both.

In the login page, click om OPTIONS at bottom left to choose after you boot. If you do not choose and login, you get the default. You will find your way.

---

### Post by mlentink on 2007-06-13
> **pardesi said:**
> thanks...can you write the code exactly also do you say will i be given a option during login which environment to choose
Yes. As I said earlier
> **pardesi said:**
> do kde and kubuntu-desktop do same thingYes. Kubuntu is Ubuntu with a KDE desktop environment.

---

### Post by pardesi on 2007-06-13
> **dptxp said:**
> sudo aptitde update
Install and check the difference, keep both.


i thin the first one was a typo so it is aptitude right
do u ask me to download both and see the difference

---

### Post by mlentink on 2007-06-13
> **pardesi said:**
> i thin the first one was a typo so it is aptitude right
do u ask me to download both and see the difference

Yes, that's what the man said. They won't be in the way, just eat up a little disk space and a little RAM overhead. You can try out both at your leisure

---

### Post by dptxp on 2007-06-13
apt-get also works.

Use my last post.

Update aptitude and install using aptitude.

Use kde-core, other will be too large. Unlikely to give much benefits.

---

### Post by pardesi on 2007-06-13
i not reading your previous post started installing kubuntu-desktop now can i stop it without any negative consequence ...it is presently at 5%

---

### Post by fastpakr on 2007-06-13
If you've already started, just let it finish.

---

### Post by pardesi on 2007-06-13
oh no i somehow checked that page off now it's gone

---

### Post by pardesi on 2007-06-13
i used this 
```
 sudo aptitude clean  kubuntu-desktop

```
i think it'd one for now

---

### Post by fastpakr on 2007-06-13
Can you try posting complete thoughts?  I have NO idea what you're saying in most of your posts.  Be specific in your descriptions of what you've done.

---

### Post by pardesi on 2007-06-13
i had started installing kubuntu-desktop before realising that they are tooo big it started.now i closed the download window and to remove any traces of it i wrote
```
 sudo aptitude clean  kubuntu-desktop
```

---

