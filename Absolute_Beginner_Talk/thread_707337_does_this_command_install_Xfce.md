---
title: "does this command install Xfce?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by frito on 2008-02-25
does this command just install Xfce or what does it do?

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

i found it here. [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by SOULRiDER on 2008-02-25
First it will refresh your sources and then install the xubuntu-desktop package. Installing the xubuntu-desktop package is pretty much like installing Xubuntu. You will still ahve GNOMe and allt he applications you currently have.

---

### Post by Pandemic187 on 2008-02-25
It probably will, although someone else could confirm that for you.

Do you know what Xubuntu is? If not, Xubuntu is the Ubuntu release that has Xfce installed by default. Similarly, I do know for a fact that running the command:
```
sudo apt-get install kubuntu-desktop
```
will install KDE, as Kubuntu is the release of Ubuntu that has KDE installed by default. As such, I would image installing xubuntu-desktop would install Xfce.

---

### Post by neurostu on 2008-02-25
can't you just type
```

sudo apt-get install xfce

```

---

### Post by frito on 2008-02-25
does it install all of the other programs that come with ubuntu as well? such as the GIMP replacement? or just Xfce?

---

### Post by Syndacate on 2008-02-25
> **frito said:**
> does this command just install Xfce or what does it do?

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

i found it here. [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Yes, it will work.

It's the same for all of them.

You can also use **apt-get** instead of **aptitude**, that's what I do, I like it better, but whatever, either way it'll work.

the **sudo** just gives you full admin power (full privileges to everything, sudo can own a hard drive easy on a UNIX based system)

**apt-get update** or **aptitude update** just updates your sources list.

Then the "**install**" is pretty self-explanatatory, it downloads and installs, you can do that for kubunutu, ubuntu, or xubuntu, "***buntu*-desktop**"

Once it's installed you can just log out, hit the "**options**" button,  you can switch from KDE (Kubuntu) to GNome (Ubuntu) to XFCE (Xubuntu) at any time, then just log back in.

May I ask why you want to use the XFCE interface?  I thought I loved the KDE interface - now I hate it, I love the GNome interface but sometimes the brownness gets to me ;).  You just trying to keep the OS light or something?

---

### Post by gali98 on 2008-02-25
basically it installs the Xfce packages on the Xubuntu distro. It WILL NOT remove Gnome or KDE or anything. It will give you the option of when you first log in to select Xfce as your desktop. It will also add a lot of dual programs. You already have nautilus as the file manager, but it will add thunar. Not a big deal, you will just have more programs that do basically the same thing. You could try it and if you don't like it you could just remove it. I actually suggest going into synaptic and go to Edit>Mark packages by Task and select the xubuntu-desktop. Then to uninstall all you have to do is unselect it.
Kory

---

### Post by -Phoenix- on 2008-02-25
In short: Yes. In long: no.

It will install Xfce, however it may not install all the needed packages on its own.

[http://wiki.freespire.org/index.php/Xfce4]("http://wiki.freespire.org/index.php/Xfce4")

That page should get you started.

---

### Post by SOULRiDER on 2008-02-25
> **frito said:**
> does it install all of the other programs that come with ubuntu as well? such as the GIMP replacement? or just Xfce?

It  installs everything, it will  leave your system as if you had just installed Xubuntu (it will keep everything else already there too).

---

### Post by perlluver on 2008-02-25
It has all of the prgrams that came with Ubuntu, it adds Xfce, and other Xfce realted things.

---

### Post by northern lights on 2008-02-25
> **gali98 said:**
> I actually suggest going into synaptic and go to Edit>Mark packages by Task and select the xubuntu-desktop

> **-Phoenix- said:**
> It will install Xfce, however it may not install all the needed packages on its own.

Synaptic will for sure. Aptitude & apt-get should handle dependencies fine also...

---

### Post by gali98 on 2008-02-25
> **northern lights said:**
> Synaptic will for sure. Aptitude & apt-get should handle dependencies fine also...
It is all the same system so yes aptitude and apt-get will do the same exact thing.

As far as programs go it will install any program that Xbuntu has. That being said if Xubuntu has gimp which I believe it does it will install gimp when you run that command or do whatever. However since you already have gimp with ubuntu, it will not reinstall it and you will not have two gimps.
Kory

---

### Post by northern lights on 2008-02-25
> **gali98 said:**
> That being said if Xubuntu has gimp which I believe it does it will install gimp when you run that command or do whatever

Should that "whatever" happen to be "sudo apt-get install gimp", then duh, it will install gimp.

Should "that command" mean "sudo apt-get install xubuntu-desktop", then no, it won't install the GIMP (whether it was previously installed or not), since xfce is not dependent on the GIMP. It will install all sorts of xfce plugins, thunar (file manager, does the job of nautilus) and for instance thunderbird (cause evolution is a gnome app).

[EDIT]
Hope I didn't come off as too much of a wiseacre...
[/EDIT]

---

### Post by frito on 2008-02-25
what about other xubuntu programs like abiword?

---

### Post by northern lights on 2008-02-25
abiword, abiword-common & abiword-plugins will be automatically installed...

---

