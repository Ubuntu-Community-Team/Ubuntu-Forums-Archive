---
title: "Installing Kubuntu(KDE) on Ubuntu.."
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by zexoc on 2006-03-14
is it possible to install?

ive tried:

sudo apt-get install kubuntu-desktop 

but it couldnt find the package.

thanks for any help

---

### Post by taurus on 2006-03-14
Perhaps you need to uncomment out by removing the # signs for universe & multiverse...

---

### Post by zexoc on 2006-03-14
im not sure if i understood you correctly but i havent used # with sudo apt-get

---

### Post by meborc on 2006-03-14
no.... the point is you have to have extra repositories enabled...

try this: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

and then

[B]sudo apt-get update
sudo apt-get install kubuntu-desktop[/B]

---

### Post by zexoc on 2006-03-14
ok just added the multiverse repository and it now installs.

is the cli the same in kubuntu as ubuntu?

---

### Post by aysiu on 2006-03-14
[QUOTE=zexoc]
is the cli the same in kubuntu as ubuntu?[/QUOTE] Yes.

---

### Post by zexoc on 2006-03-14
after downloading unpacking and rebooting, i get a kubuntu log in screen but once logged in - it reverts back to ubuntu.

any suggestions?

---

### Post by taurus on 2006-03-14
May sure you pick KDE in the Sessions...

---

### Post by zexoc on 2006-03-14
ive added kde on the sessions name, but there arent any configuration options.

another question:

what are the 'Order' numbers?

---

### Post by zexoc on 2006-03-14
should've logged out and then picked sessions.. anyway i did that and managed to load the KDE. is there any way to create a button for the cli on the menu bar?

thanks for all the help folks.

---

### Post by Adrian on 2006-03-14
[QUOTE=zexoc]is there any way to create a button for the cli on the menu bar?[/QUOTE]

Right-click on the menu panel and add a terminal (Konsole) from the "Panel Menu -> Add to Panel" menu.

In SUSE (that I'm using right now), you do it like this:
Right-click on panel -> Panel Menu -> Add to Panel -> Application -> System -> Terminal -> Terminal Program (Konsole)

The menu structure of Kubuntu is a little different though. Unfortunately, I can't access any Kubuntu install right now.

---

### Post by zexoc on 2006-03-14
thanks adrian, I managed to do it.

although when I tried running synaptic (in kubuntu) and entered the password, it denied access.

---

