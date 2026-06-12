---
title: "Switching form Ubuntu to Kubuntu"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by Abd-al-Karim on 2005-07-24
Hi I'm a Linux newbiwe an I've got some questions concernig switching desktop environments.

I am currently waiting for my Ubuntu Cds and because of my internet connection it would be very difficult to download a whole CD image off the net ](*,). This means I cannot download the Kubuntu CD image, although I would like to try both Gnome and KDE  :-|.

So here is my question: I can get the latest version of KDE on a CD, so can I just install that when I get Ubuntu? Will that be radically different form having Kubuntu?

Any advice would be appreciated and thanks a lot in advance.

---

### Post by manicka on 2005-07-24
Do you mean you have kde packages from kde.org. You're better off sticking with the specific kubuntu kde packages to avoid problems

---

### Post by PeP on 2005-07-24
[QUOTE=Abd-al-Karim]Hi I'm a Linux newbiwe an I've got some questions concernig switching desktop environments.

I am currently waiting for my Ubuntu Cds and because of my internet connection it would be very difficult to download a whole CD image off the net ](*,). This means I cannot download the Kubuntu CD image, although I would like to try both Gnome and KDE  :-|.

So here is my question: I can get the latest version of KDE on a CD, so can I just install that when I get Ubuntu? Will that be radically different form having Kubuntu?

Any advice would be appreciated and thanks a lot in advance.[/QUOTE]
 what do you mean by the latest version of kde?
If it is the sources files, hum, the compilation (transformation from source code to machine code) is long ..., and you will have to handle all the dependences

if it is .deb files it should not be a problem, but I don know where you can fid such a cd, but you still have to download dependances.

if it is another format (.rpm) it won't help you.

---

### Post by Abd-al-Karim on 2005-07-24
[QUOTE=PeP]what do you mean by the latest version of kde?
If it is the sources files, hum, the compilation (transformation from source code to machine code) is long ..., and you will have to handle all the dependences

if it is .deb files it should not be a problem, but I don know where you can fid such a cd, but you still have to download dependances.

if it is another format (.rpm) it won't help you.[/QUOTE]

Its CD from a Linux magazine (Linux format I think), a friend of mine has it and he told me that it has KDE & Gnome on it, though mind you he doesn't know much about Linux either.

I'm not sure what you mean by .deb files.

---

### Post by manicka on 2005-07-24
[QUOTE=Abd-al-Karim]Its CD from a Linux magazine (Linux format I think), a friend of mine has it and he told me that it has KDE & Gnome on it, though mind you he doesn't know much about Linux either.

I'm not sure what you mean by .deb files.[/QUOTE]
 If you don't know what a deb file is, then I think you're better off just waiting for your ubuntu CD's and experimentiing with them before attempting to add KDE. Adding KDE isn't that big a downlaod once your ubuntu system is up and running

deb files are way that packages are put together for debian based distributions like ubuntu. Some distros use deb's and others use rpm's. Those are the main two and there are others.

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=Abd-al-Karim]

So here is my question: I can get the latest version of KDE on a CD, so can I just install that when I get Ubuntu? Will that be radically different form having Kubuntu?

Any advice would be appreciated and thanks a lot in advance.[/QUOTE]

No. If you want Kubuntu (or hell...any KDE), the only way is to pay someone to ship you the Ubuntu DVD or the Kubuntu Cd (the second might reqire a reinstall).

[http://www.linuxcd.org/view_distro.php?lst=1&id_cate=22&id_distro=196](http://www.linuxcd.org/view_distro.php?lst=1&id_cate=22&id_distro=196)

---

### Post by aysiu on 2005-07-25
[QUOTE=poofyhairguy]No. If you want Kubuntu (or hell...any KDE), the only way is to pay someone to ship you the Ubuntu DVD or the Kubuntu Cd (the second might reqire a reinstall).[/quote] According to Kubuntu's website, the answer to the question, "I already have Ubuntu installed, how can I get Kubuntu?" is

   1. Make sure you are using hoary in your /etc/apt/sources.list
   2. apt-get install kubuntu-desktop

---

### Post by GreyFox503 on 2005-07-25
I'm a new Ubuntu user who recently wanted to do the same thing (that is, use the KDE environment).  Kubuntu is the same as regular Ubuntu, except it comes with KDE instead of GNOME.  But if you have some bandwidth (or can leave it on overnight if you're on dialup), these instructions worked really well for me.

 1. Make sure you are using hoary in your /etc/apt/sources.list
```

sudo apt-get install kubuntu-desktop
```

I don't remember exactly, but I had to download roughly 100MB of various packages to install it.  I don't know much about installing it through .deb packages, though.

After installing it, you can choose at each login which environment you'd like to enter.  It's really easy.

This command will let you choose which display manager you'd like the login screen to be set as:

```
sudo dpkg-reconfigure kdm
```

One other thing you could you try if you really didn't want to download it.  You could get your hands on a Kubuntu CD, then try to add it to the list of repositories, so it might let you install KDE from the CD without reinstalling everything.

Good luck!

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=aysiu]According to Kubuntu's website, the answer to the question, "I already have Ubuntu installed, how can I get Kubuntu?" is

   1. Make sure you are using hoary in your /etc/apt/sources.list
   2. apt-get install kubuntu-desktop[/QUOTE]

For computers with very slow or no internet, thats not always an option. Its nice to know there are other ways.

You can always get someone to download you the dvd.

---

