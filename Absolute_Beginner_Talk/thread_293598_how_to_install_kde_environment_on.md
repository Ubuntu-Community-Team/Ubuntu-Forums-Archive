---
title: "how to install kde environment on"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by harsh87 on 2006-11-05
i'm not satisfied with gnome envvironment.
how can i install kde on my pc(ubuntu dapper) and use it?
does it slows down my system?
thanx in advance

---

### Post by tronica on 2006-11-05
you should be able to open the terminal and type

> sudo apt-get install kde

its a big download.

---

### Post by taurus on 2006-11-05
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
And it has nothing to do with slowing down your machine.  It would, however, take up a little more space since now you have both Gnome and KDE on your system...

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by bodhi.zazen on 2006-11-05
Yes. It will not slow down your computer, just take up more sapce any you will have multiple applications for any particular task.

[Installing KDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by NeoLithium on 2006-11-05
```
sudo aptitude install kubuntu-desktop
```

It will install the base Kubuntu system; and should you not like it; make it just as easy to remove.

---

### Post by mbv93 on 2006-11-05
is there a way to get rid of gnome and install kde?

---

### Post by sailor2001 on 2006-11-05
synaptics will give you all the kde and libraries

---

### Post by bodhi.zazen on 2006-11-05
> **mbv93 said:**
> is there a way to get rid of gnome and install kde?

Why not just install kubuntu ? It would seem less hassle.

You can get rid of Gnome if you like: 

[Remove Ubuntu Desktop](http://www.psychocats.net/ubuntu/purekdedapper)

---

### Post by Chayak on 2006-11-05
It could be worse.  I have Xfce, KDE, and Gnome installed and which one I use depends on which one I want at the time.

---

### Post by NeoLithium on 2006-11-05
> **bodhi.zazen said:**
> Why not just install kubuntu ? It would seem less hassle.

You can get rid of Gnome if you like: 

[Remove Ubuntu Desktop](http://www.psychocats.net/ubuntu/purekdedapper)

Well, this would actually be the less hassle; without having to backup /home contents, and such; when he can just install the KDE base system; and remove gnome another time.  Then again, that's just MHO

---

### Post by DraeLee on 2006-11-05
got a question i installed the kde from synaptic a while back but i havnt really fooled with it.  My question is this.  When i log into the kde session does that mean that i will have to reinstall the nvidia drivers and beryl into that kde of is it all there and i just have to do some configuring?  Im not sure if i worded it properly but i wanted to know cause i kind of like kde but i am getting used to gnome and i just wanted to know that if i decide to switch every now and then would i have to reinstall stuff for the kde environment or is it like another shell?

---

