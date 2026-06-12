---
title: "swithing from Gnome to KDE"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-09-01
Is there a way to change from GNOME to KDE without having to reload the system and start from scratch?

Thanks 

Tobmeister

---

### Post by Klaidas on 2006-09-01
yes.
First, [http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
And then, [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by Anonii on 2006-09-01
EDIT: Check Klaidas instructions they are far more helpful :)

[SIZE="2"]
You basicaly want to change from Ubuntu to Kubuntu :)

Install the “kubuntu-desktop” meta-package with Synaptic or apt-get, then pick KDE on next login.[/SIZE]

---

### Post by tobmeister on 2006-09-01
I have a Kubuntu CD (6.06), is there any way that I can load KDE from the CD?  I'm on dial-up so it would take me a better half of a month (hehehe) to download it from the reposetories.

---

### Post by comppsyco on 2006-09-01
I don't actually know how to do this, but I'm guessing that you could add the cd to your sources.list then install from there. Unfortunately, I don't know the proper line to put into the sources.list, nor to I know whether the kubuntu-desktop meta-package is on there.

---

### Post by aysiu on 2006-09-01
You can add it using the CD if you have the **Alternate CD**.

You cannot do it with the **Desktop CD**

---

### Post by tobmeister on 2006-09-01
The only CD that I have is the new 6.06 Live CD that can be installed if you choose.  This is what I originally did but the Kubuntu 6.06 has a bug that won't allow it to load passed the *install apt* (bug #56725 ubiquity (KDE) fails configuring APT portion of the install).  Lucky for me I also got the Ubuntu CD and was able to just load that over my Ubun 5.05.

I could possibley download KDE from work and put it on my USB drve and then put it on my sys.  Does anyone off hand know how big it is?

Thanks

Tobmeister

---

### Post by Paul133 on 2006-09-01
I just want to add that you should use aptitude not apt-get when installing kubuntu-desktop to avoid unmet dependencies (I think). At any rate, it told me I needed to ahev a package installed, and when I installed that package, I had to install another one, so I just used aptitude and everything "just worked"!

---

### Post by aysiu on 2006-09-02
Theoretically, *apt-get* should be able to meet dependencies just as well as *aptitude*, but *aptitude* makes removal of those dependencies easier.
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by hellfried on 2006-09-02
i have been itching to try out kde and this thread is really useful. before i take the plunge though i have a doubt. i am now running xgl/compiz inside gnome ubuntu 6.06. everything is really going well. do i have to do another install of xgl/compiz in kde? will my ati driver work the same in kde?

---

