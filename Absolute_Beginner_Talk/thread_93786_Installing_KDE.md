---
title: "Installing KDE"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by Sagrath on 2005-11-22
i'm sorry for posting so often but i would like use KDE on my computer because i got sed to it in somewhay...

I would like to know how can i install KDE with all the programs it needs and if i dont succeed installing it and my X server wouldn't start how do i rollback the installation?

Thank you

---

### Post by narcolept on 2005-11-22
I'm not 100% sure, but I would imagine it's somewhere in the multiverse repository.  If not, you could add a kubuntu repository to /etc/apt/sources.list and apt-get install kde.  If you wanted to remove it, it's as simple as apt-get remove kde.  Of course, if you're unfamiliar with apt, you can always use synaptic.

---

### Post by Sagrath on 2005-11-22
hmm... just one question Kubuntu is actually Ubuntu but with KDE ?

---

### Post by narcolept on 2005-11-22
That is correct.  If you aren't going to use gnome, you could always just install kubuntu if you really wanted to.

---

### Post by Adrian on 2005-11-22
[QUOTE=Sagrath]
hmm... just one question Kubuntu is actually Ubuntu but with KDE ?
[/QUOTE]

That's right! The only difference between Ubuntu and Kubuntu is the desktop environments.

To install Kubuntu (i.e. KDE and the Kubuntu-specific desktop applications), you just need to install the metapackage "kubuntu-dekstop". This can be done in Synaptic or from a terminal by typing the following:

```

sudo apt-get install kubuntu-desktop

```

Just installing the "kde" package gives you KDE but not the applications.

---

### Post by narcolept on 2005-11-22
In previous ubuntu versions, just installing KDE will install all needed packages and update installed packages to the menu, which is what he's looking for, I believe.  Anything else can always be found with an 'apt-cache search kde" as well.

---

### Post by Sagrath on 2005-11-22
yes you are right...when i installed ubuntu it didnt asked me anything about wich desktop eviroment i would like to use it just installed Gnome...well ill try installing KDE with apt-get 
 hope i will get it right:P many thanx

---

### Post by narcolept on 2005-11-22
As Adrian said, if you would like all utilities installed as well, and kde specific programs, use apt-get install kubuntu-desktop

---

### Post by Sagrath on 2005-11-22
ok i executed the comand and now i have to wait because the download speed is only 30 kilos but when it will finnish how do i select to start KDE and not Gnome?

---

### Post by narcolept on 2005-11-22
In the gdm (login menu) just select KDE under "Session".

---

### Post by somody on 2005-11-22
So I would have a choice?  This is interesting!  A dual-boot's dual-boot :p!

---

### Post by narcolept on 2005-11-22
Well yeah. GDM will have all window managers you have installed listed under "Session" if you've installed others than Gnome or KDE, depending on if it's ubuntu or kubuntu

---

### Post by Sagrath on 2005-11-22
thank you a lot guys really apreciate the support ;)

---

### Post by somody on 2005-11-22
Can I install OTHER winmans for ubuntu? other than kde or gnome, i mean?

---

### Post by narcolept on 2005-11-22
You can install any you want. xfce, blackbox and fluxbox are in the repositories, I believe, as well as enlightenment16, and there's a page out there somewhere with ubntu repos for e17 from cvs as well.  Open a terminal and type

```
sudo apt-cache search window manager
```

and you'll see what's available.

---

