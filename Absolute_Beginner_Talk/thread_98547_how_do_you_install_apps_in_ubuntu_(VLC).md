---
title: "how do you install apps in ubuntu (VLC)"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by jkblitz on 2005-12-03
hi i just started useing ubuntu yesterday and im trying to install vlc i downloaded the folder but thers just a  bunch of files so can anyone tell me what to do step by step would.

---

### Post by supergrapeman on 2005-12-03
[QUOTE=jkblitz]hi i just started useing ubuntu yesterday and im trying to install vlc i downloaded the folder but thers just a  bunch of files so can anyone tell me what to do step by step would.[/QUOTE]

Hey, jkblitz, it's really easy.

Go to the System menu, select Administration, then select Synaptic package manager.

Synaptic package manager will make it easy for you to install apps/ remove apps/ update your system etc.

---

### Post by jrib on 2005-12-03
You will also want to read [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) which will give you access to thousand of programs including vlc.

---

### Post by 23meg on 2005-12-03
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by jkblitz on 2005-12-03
any thing more dumed down?

---

### Post by 23meg on 2005-12-03
No, this is as simple as it gets. To install VLC, type ```
sudo apt-get install vlc
```

---

### Post by jkblitz on 2005-12-03
i typed that in the termanil and i got sunny@ubuntu:~$ sudo apt-get install vlc
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by 23meg on 2005-12-03
Try doing ```
sudo apt-get -f install
```and repeating the command. If it doesn't work, post the contents of your /etc/apt/sources.list file; there's probably something wrong with it.

---

### Post by jkblitz on 2005-12-03
this is the name of the file 
vlc-0.8.4.tar-1.bz2

---

### Post by jkblitz on 2005-12-03
ok maby i should try mplarer can i get help with that one i dont get linux at all

---

### Post by 23meg on 2005-12-03
You won't have much chance installing mplayer either unless you understand the fundamentals or at least follow the instructions given to you. The thing is, you don't need the archive file. You can just install VLC and pretty much every other app directly from the repositories. Take time to read the link I posted and you'll understand.

---

### Post by jrib on 2005-12-03
(offtopic, sorry jkblitz)
[QUOTE=23meg][http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)[/QUOTE]

I wish I had been referred to that site in my early ubuntu days, would have been very helpful.  I couldn't find any contact info on the page but if you are the maintainer(or can refer me to him) would you consider changing the "Installing from source" section to use checkinstall instead of make install?  I find checkinstall to be extremely helpful since it allows individuals to control the source content as though it was an actual package from the repos (easy to uninstall programs!).  I know the maintainer doesn't like the wiki but he could probably just copy some of the information in [https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall) .

---

### Post by aysiu on 2005-12-03
First you have to enable extra repositories (see the first link in my sig).

Please read the link in post #4 of this thread--that explains *everything*.

If even that's too complicated, see the second link of my signature but substitute *vlc* for *blender*.

---

