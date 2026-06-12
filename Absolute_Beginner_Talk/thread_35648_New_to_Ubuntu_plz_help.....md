---
title: "New to Ubuntu plz help...."
date: 2005-05-19
forum: Absolute Beginner Talk
---

### Post by wowbuntu on 2005-05-19
Dear Ubuntu people

I have some questions....

1. In Synaptic, while removing installed packages
I'm given the option to remove config files as well.
Is there ANY harm in removing them? And is there any
good in keeping them? 

2. If I do sudo apt get upgrade of my Ubuntu system
manually, where will those new packages come from?
From the official Ubuntu repository OR the repositories
containing latest unstable versions of packages?

3. Will a manual uprade in this manner have any
undesirable side-effects? Is this the same as
upgrading to a newer release that is dist-upgrading?

4. Can I safely install & run KDE edutainment (kdeedu package)
apps on Gnome Ubuntu?

5. There's perl 5.8.4 installed with Ubuntu. Its latest
version is 5.8.6 and is available as a .tar.gz file
from its website. Is there any way to upgrade the
5.8.4 to 5.8.6 or do I have to manually remove 5.8.4
and install 5.8.6?

6. I can't find emacs or vim in the menus!
Where is it? I saw at distrowatch that its
there in Ubuntu as well as Kubuntu!

Thanks in advance..

Take care
Wowbuntu

---

### Post by bored2k on 2005-05-19
1. No harm. Good thing is, should you decide to reinstall applicationX, your settings are all setup.

2. Depends on the repositories you have on your system. If they are Ubuntu's, you will always download the official stable product.

3. Synaptic is just a graphic  representation of apt-get. It's all the same. 

4. Most likely. They won't run as fast as running them on Kubuntu, but you could.

5. You should get a .deb or wait for an upgrade if it's not that important.

6. You can run vim from a terminal or install menu menu-xdg so a menu with them appears. I think you have to install emacs.

---

### Post by poofyhairguy on 2005-05-19
B2K did a good job, I just want to say one thing:

[QUOTE=wowbuntu]
5. There's perl 5.8.4 installed with Ubuntu. Its latest
version is 5.8.6 and is available as a .tar.gz file
from its website. Is there any way to upgrade the
5.8.4 to 5.8.6 or do I have to manually remove 5.8.4
and install 5.8.6?[/QUOTE]


Unless you are a developer, that would be very hard to do and could make many things unstable. You would be better off using Breezy if you want new Perl and you don't value stability.

---

