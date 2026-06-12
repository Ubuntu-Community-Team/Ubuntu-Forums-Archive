---
title: "need help adding live cd to list of apt repositories"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by kvorion on 2007-02-04
Hi all.

I have installed Xubuntu 6.10 on my machine. I am trying to get connected to the internet by using RP-PPPOE. I tried to install the same, but when I started to build it, then ./configure gave me an error saying that gcc cannot create and executable or something of that sort. I believe I need to have autoconf installed first (which apparently is not installed by default).

The only want to install the build-essential package was through apt-get. But I still dont have internet connectivity; so I cannot use apt. I assumed that the package would be included on the cd, but I somehow cannot add the live cd to the list of repositories. What I tried to do is add a 3rd party repository through synaptic by clicking on add cd. It scans the cd and says unmounting cd rom. The progress bar completes and the close button is shown. At this point I cannot figure out whether the cd has actually been added to the list of repositories.

I clearly remember that I have installed a couple of packages from the cd using apt while I was using Breezy Badger, but I cant quite remember how I added the cd as a repo, it was probably by editing my sources.list; I just cant seem to be getting that now.

Please tell me if there is a way to install the build essential package using the live cd?

Thanks in advance

---

### Post by deadgobby on 2007-02-04
If you have a nice friend to DL this for you
[https://wiki.ubuntu.com/APTonCD?highlight=%28apt%29](https://wiki.ubuntu.com/APTonCD?highlight=%28apt%29)

Gobby

---

### Post by kvorion on 2007-02-04
So are there no packages on the live cd?

---

### Post by taurus on 2007-02-04
Insert the CD into the drive, open a terminal, and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```
Now, run your ./configure again and see what happens.

---

### Post by kvorion on 2007-02-04
Yes, that was the one I was looking for. Thanks, it worked.

---

