---
title: "Ubuntu Version"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by StevenP9891 on 2007-01-06
I just installed Ubuntu  5.10, but I realized that it isnt the latest version .Is there any way for me to update to the latest version of ubuntu?????

---

### Post by taurus on 2007-01-06
Since you just installed, it's best to install Edgy from fresh; otherwise, you have to upgrade your Breezy to Dapper first and then from Dapper to Edgy.  You can't skip and go from Breezy to Edgy right away...

---

### Post by benuski on 2007-01-06
Try 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by obsidion on 2007-01-06
> **benuski said:**
> Try 

```
sudo apt-get update
sudo apt-get dist-upgrade
```


  This would upgrade from 5.10 to 6.06 or 6.10 how ?
All it would do is make sure the latest security patches and other upgrades relevant to 5.10 are installed.


Since it is a new install I would go the route sugested and download a later iso and burn it.
  Otherwise you will probably end up downloading probably a lot more than the 600 od Meg of the new iso.
There are ways of doing without the new install of course and if you do want to go that way come back and ask.

---

### Post by dannystaple on 2007-01-06
Sorry for the me too post, but I strongly recommend the advice of taurus and obsidion here. Downloading a 6.10 ISO, burning it and booting from that is a much better plan.

Cheers,
Danny

---

### Post by Ramses de Norre on 2007-01-06
> **benuski said:**
> Try 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

That wont work, you have to change your sources first.
(dist-upgrade isn't a command to switch to a new release! Read it's man page for more info)

It's highly recommended to reinstall with 6.10, as already mentioned.

---

### Post by obsidion on 2007-01-06
> **StevenP9891 said:**
> I just installed Ubuntu  5.10, but I realized that it isnt the latest version .Is there any way for me to update to the latest version of ubuntu?????

  Just spotted this post by you in another thread and it got me wondering why and where you would download such an old version of ubuntu, even finding that old a version is not  easy.

> Hi, Im a brand new Linux user, having switched from WindowsXP. I just downloaded Ubuntu about a couple of > days ago and I'm still attempting to get used to the dramatic change in the system management.

  I suggest you visit [www.ubuntu.com](www.ubuntu.com) and have a look at the FAQs etc before you go any further if you haven't already. It seems like you have been visiting/using a very outdated archive.

---

