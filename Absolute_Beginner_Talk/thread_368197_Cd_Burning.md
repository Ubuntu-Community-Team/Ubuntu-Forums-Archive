---
title: "Cd Burning"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by kilroy423 on 2007-02-23
What is the best iso burner for ubuntu?

---

### Post by elyk on 2007-02-23
If you click on the "places" menu and click "CD/DVD Creator", you will be given a folder (similar to the Windows XP native burning support) where you can drag files, then click "write to disk".
However, this will not burn ISO images. For this, you will need one of two programs, K3B or gnomebaker. I personally prefer K3B, but there is nothing preventing you from installing both to see which fits your needs better. 
To install these, click Applications, go to Accessories, then select "terminal". Type the following command:
For K3B: sudo aptitude install K3B
For Gnomebaker: sudo aptitude install gnomebaker
When it prompts you, enter the password you use to login. If it asks you any other questions, type "y" and hit enter. When installation completes, both should show up under "Sound & Video" in the applications menu.

---

### Post by tubasoldier on 2007-02-23
I second the vote for K3B. It is by far the most developed and mature of the CD/DVD burning applications.

---

### Post by jethro10 on 2007-02-23
> **kilroy423 said:**
> What is the best iso burner for ubuntu?

If you mean you have a .iso file which is a disk image, just right click it, there is an option there.

J

---

### Post by kinson on 2007-02-23
I've been using K3B for a while, and recently tried GnomeBaker, and didn't like it.

It(GnomeBaker) didn't have data verification, and I wasn't able to expand the folders I put into the explorer(maybe this is just me).

**My vote: K3B**

Cheers,
Kinson.

---

### Post by paydaydaddy on 2007-02-23
Does K3B work with all versions of Ubuntu? I took a look at it and it seems to be geared toward the KDE desktop.

---

### Post by kinson on 2007-02-23
> **paydaydaddy said:**
> Does K3B work with all versions of Ubuntu? I took a look at it and it seems to be geared toward the KDE desktop.

Its mainly for KDE, but it works just fine in Gnome. I'm using it in Ubuntu(Gnome) myself.

I think ```
sudo aptitude install k3b
``` should do it. (I'm not very good at the command line *yet* :( Installed it a few months back)

Cheers,
Kinson.

---

### Post by paydaydaddy on 2007-02-23
I looked at it in Synaptic. It will install through Synaptic but advises that it will add file and libraries. My guess is that you get the same package by installing through the terminal. I think I'll try it and see what happens.

---

### Post by kinson on 2007-02-23
The benefit of installing using aptitude would be that it resolves dependencies(probably better for when you uninstall stuff).

[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

Cheers,
Kinson

---

### Post by geirha on 2007-02-23
It's just apt-get that's not as good on dependencies. Aptitude and Synaptics will do the same, it's just a matter of what you like the best, your keyboard or your mouse? ;)

---

### Post by shoaibi on 2007-02-23
i would suggest Gnome-baker for ubuntu, or K3b for Kubuntu...

---

### Post by gurgle on 2007-03-08
I like Brasero personally.

---

