---
title: "Can't load Ubuntu 6.06 after installing Kubuntu 6.06"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-20
Thought I'd give Kubuntu a try so I installed it onto an already dual boot of WinXP and Ubuntu 6.06. Now it doesn't show Ubuntu in the boot loader. How would I fix that? Thanks.

---

### Post by Kingsley on 2007-04-20
You probably installed Kubuntu over Ubuntu. 

Just run 
```
sudo apt-get install ubuntu-desktop
```
And you'll have an option to log into Gnome (Ubuntu).

---

### Post by teddybairs1 on 2007-04-20
If you don't want to use the command line, go into adept_manager. It's in the Kmenu under System. Find the package marked ubuntu-dektop and mark it for install. Apply the changes. Let Adept do the rest.

---

### Post by jacatone on 2007-04-21
I don't want to reinstall Ubuntu, I simply want to access it using Grub. It's still there on my HDD (ext 3). Right now just Windows and Kubuntu appear in Grub.  Please see snapshot. Thanks.

---

### Post by teddybairs1 on 2007-04-21
Ubuntu and Kubuntu are the same OS. The difference between them is the desktop environment, Ubuntu is Gnome by default, and Kubuntu is KDE by default. You didn't have to install Kubuntu in a separate partition in order to get the Kubuntu experience. All you had to do was go into Synaptic and check the kubuntu-desktop package to get the Kubuntu desktop. On the GDM login screen there are options to switch between desktops. I used to do this on my laptop all the time. Some days I would feel like Gnome, other days I would feel like KDE. But it's the same OS on the same partition using the same filesystem.

Most likely, the reason why grub isn't seeing them both is because, to GRUB, it's the same OS with the same identifiers. When you did the install, Grub just probably overwrote its initial Ubuntu entry with the new one. This is why you probably can't see it. It would be like having two copies of XP installed onto the same hard disk on separate partitions. I'm making an educated guess, but from what I understand of GRUB and it's config files, this is probably what happened.

At one time I had the Gnome, KDE, IceWM, Enlightenment, XFCE, and a few other desktops all installed on my laptop just for fun. It was the same OS, same filesystem, same home files, same partition, just different desktop environments which I could switch back and forth from in the login screen.

I don't know what else to tell you about your system. What you did was totally unnecessary to have access to both desktops. Honestly, if it were me, I would burn all my files to a cd, and then start over again by trashing both partitions back into one and doing a clean install. Someone else on the site can probably give you more technical know-how, but the way you've described it, "trash and burn" might just be the easiest route to go.

---

