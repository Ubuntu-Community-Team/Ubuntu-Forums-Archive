---
title: "K3b"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-10-24
can someone help me/ provide a link in order to be able to install k3n?

TIA

J

---

### Post by Maestro23 on 2007-10-24
k3B?

Available in the repositories.

> sudo apt-get install k3b

---

### Post by ubuntu27 on 2007-10-24
Hello johnnyw. Debian, Ubuntu and other Debian based distro use repositories or repo for short. Repository is a library of application software in which you can just install by pointing the package name.

There are many ways to install a program in Ubuntu. The most easiest route is to use Synaptic Package Manager which you can find it at System/Administration/Synaptic.

In Synaptic, Click on search and type the name or description of the program. Select the application that you want to install by clicking on the white box next to the name, and then click on Apply. Synaptic will automatically download and install the select programs for you.

Another way is by using the terminal or Konsole.  in Ubuntu (GNOME) can by found at  Applications menu/Accessories/Terminal

and type the following:

```
sudo apt-get install package-name
```

or 

```
sudo aptitude install package-name
```


In your current case, you want to install k3b, the CD/DVD burning program.

```
sudo apt-get install k3b
```

or 

```
sudo aptitude install k3b
```

For more Information, visit the site in my signature that says [How-to Install Apps/Software in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by johnnyw on 2007-10-24
thx guys...

nothing showed up in synaptic..

I am going the command line route :)

---

### Post by Maestro23 on 2007-10-24
> **johnnyw said:**
> thx guys...

nothing showed up in synaptic..

I am going the command line route :)

Make sure you have Universe and Multiverse repos enabled.

System>>Admin>>Software Sources

---

