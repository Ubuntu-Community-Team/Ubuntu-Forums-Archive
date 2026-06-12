---
title: "Installing Kubuntu *and* Ubuntu?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by toecutter on 2007-03-26
I know people have done this, but before I give Kubuntu a try I wanted to ask some questions:

- if I install both versions on my system, do they share users, programs, mounted drives, etc.? i.e., would I have to re-install all the programs I've installed, taking up slightly more disk space? 
- are there any conflicts having both systems installed? 
- assuming I like, say, Kubuntu a lot more than Ubuntu, could I just uninstall Ubuntu and everything should work okay (no missing program files, etc., from the uninstall)?
- is there an advantage/disadvantage to uninstalling Ubuntu?
- any other considerations I haven't mentioned?

---

### Post by mi_were on 2007-03-26
Ubuntu, Kubuntu, Edubuntu and Xubuntu all share the same underlying structure, the difference as I understand it in the applications that come standard with each for example  ubuntu comes standard with GEDIT (text editor) and Xubuntu comes with MOUSEPAD differnt applications same job. The bottom line is resource usage.

So if u had Ubuntu installed then added the Kubuntu desktop u would have a congested menu bar (like I do!)

U also cannot "uninstall" ubuntu just the desktop. Hope that has been helpful.

---

### Post by Kobalt on 2007-03-26
I'll try to make myself clear so that you understand me : when you install Ubuntu, it comes with a desktop environment, Gnome. And when you install Kubuntu it's KDE. But Ubuntu & Kubuntu share many things in common (kernels in example), Gnome & KDE are coming on top of these common parts. 
That means when you installed these common parts, whether from Ubuntu or Kubuntu, you can install on top of that the desktop environment you want, you can have two desktop environments, three... 
Right now, if you installed Ubuntu, you just need to type in a Terminal 
```
sudo aptitude install kubuntu-desktop
```
And it will install you the the desktop environment KDE, which you'll be able to chose at login screen. 
You won't lose your Gnome apps (you'll even be able to launch them in KDE), you won't lose your personal data (again accessible in KDE).

For further info about installing/uninstalling Gnome or KDE, I advise you to read aysiu's guides : [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

And if you have other questions, here we are :)

---

### Post by glotz on 2007-03-26
> **toecutter said:**
> I wanted to ask some questions [...]

Most programs are not shared by default. The thing is, when you write a program, you either write a GNOME or a KDE program. You can cross use programs though, they'll just have to load some extra libraries (taking disk space and memory when run) from the native DE and thus will likely be a bit more resource hungry and might have different looks. Users and mounts will be shared as far as I know. I currently run GNOME and Xfce alongside, just for kicks really. The thing there is to understand is, they're both interfaces to your computer, so you can mess up everything using either of them. In a foreign environment it's more likely but just be a bit more careful and alert.

And all this DE talk aside, with computers, if you care about something, you either back it up or lose it. Harddrive failure isn't too uncommon...

---

### Post by trancepose on 2007-03-26
in addition, kubuntu can recognize and add GNOME applications via adept manager. i am also a newbie but - thanx to my friend - a quick learner. i did many mistakes in my 6 days experience wth kubuntu and could fix them all, many by myself. i don't yet know if running both gnome and kde will gice you any advantage but i think there is no need. anyway, just do-and-see

---

### Post by mnasimh on 2007-03-26
Ubuntu, Kubuntu, Edubuntu, Xubuntu etc. are all same distro. The difference is with the Desktop Environment and the choice of default applications. If you installed , e.g., ubuntu, then you are running Gnome DE and gnome-based applications by default. Same applies for others. i.e.,
Kubuntu uses KDE
Xubuntu uses XFCE etc.

Your system is same. All your files and settings remain same. You don't need to install Ubuntu and Kubuntu as a different OS in different partitions. When you do
sudo apt-get install kubuntu-desktop
you just install KDE-flavoured desktop so that you can login to KDE from gdm/kdm/xdm (login window!). It's simply just that.

---

### Post by toecutter on 2007-03-27
Thanks very much guys! :) Looks like I'll be trying KDE - I ran it off the live CD last week and liked it...   I do like how everything is ultra-customizable but like anything with loads and loads of buttons sometimes the choices are overwhelming :) 

I'll read the link provided and give a go this week sometime!

---

### Post by sushii. on 2007-03-27
I've installed the kubuntu-desktop package, and it just messes up GNOME. It's good if you're just going to use KDE, but if you use both, I wouldn't reccomend it. (Unless you're really careful).

---

### Post by noob_saioke45601 on 2007-03-27
> sushii.  	I've installed the kubuntu-desktop package, and it just messes up GNOME. It's good if you're just going to use KDE, but if you use both, I wouldn't reccomend it. (Unless you're really careful).

no idea what you did wrong but it never messed up my gnome desktop..

---

### Post by girard on 2007-03-28
I also have ubuntu, kubuntu and xubuntu installed. i was still searching for the "right one" for me. i do like the kde DE better than the Gnome because it has a better GUI - more pleasing to the eye. Based on my experience, the problem is that you double up on applications that basically do the same thing. You'd have Konqueror and Firefox, KTorrent and BitTorrent, two archive managers, etc... As mentioned above, almost all functions of different applications are available on either DE (is everything really available on both?) So in essence, (also mentioned above) you just clog up your menu with two programs for a particular type of application. I plan on keeping xubuntu for times when you just want to do something really quick because it's supposed to be less demanding on system resources (right?). But the question is whether to keep both Gnome (ubuntu) and KDE (kubuntu)?

Questions:
1. Do you miss out on anything in choosing either Gnome or KDE? Are there certain applications, features, etc... that are only available on one and not both? Excluding those that simply do not come in the standard installation but you could actually install later of course.

2. Any particular advatage/disadvantage of either ubuntu or kubuntu?

3. Can installing ubuntu, adding Kubuntu, and then deciding to keep only kubuntu and uninstalling ubuntu (gnome DE) do harm to your system? And would it uninstall everything that came with the ubuntu install so you don't double up the programs you have?

---

### Post by tubunu on 2007-04-19
Having installed Ubuntu, can I add Kubuntu desktop from a Kubuntu CD (so that I don't have to spend two days downloading it?)

---

