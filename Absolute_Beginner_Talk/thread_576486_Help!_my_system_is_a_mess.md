---
title: "Help! my system is a mess"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by buntunub on 2007-10-15
Hi! I currently have Gutsy installed on an older computer, which is my file/LAMP server. At first, during the Feisty days, I had the default Ubuntu-desktop on it, but that was very slow and unresoponsive, so I installed the xubuntu-desktop via apt-get and have been using xfce ever since. My problem now is that after login the system seems to first load up GNOME, and then load up xfce. The GNOME desktop is visible after load in, with the xfce panels present. Every time I have to go into settings > desktop > allow xfce to manage desktop. Every time. I have the system set to "remember settings", so why does it keep doing this and how can I fix?

It also pulls in kde-base upgrades for some strange reason too, so my updates on Gutsy have been pretty painful, even though I do not have kde loaded (I have amarok only).

So, is my system borked? Do I need a fresh install again? Setting up LAMP was pretty painful the first time around; dont expect it to go much smoother if I have to do this again, but oh well.

---

### Post by Pumalite on 2007-10-15
I think you answered yourself.

---

### Post by PacketCollision on 2007-10-15
Yeah, your setup seems pretty b0rked.  It should be possible to fix it, but in a similar situation I eventually gave up and reinstalled.  If you're just using it as a LAMP server, download the Server Edition to avoid the unnecessary X cruft.  It also has options to install everything you need for a LAMP, DNS, Fileserver, etc.

---

### Post by mlentink on 2007-10-15
> **PacketCollision said:**
> If you're just using it as a LAMP server, download the Server Edition to avoid the unnecessary X cruft.  

+1 
At least, that's what I did for my server. To make it easier I just installed the xubuntu-desktop afterwards, which you could do too if you're not too comfortable with the terminal. 
I wouldn't run Amarok on my server. Much to resource-hungry. Btw, Amarok is a KDE app, so no wonder it needs a number of KDE-libraries. I wouldn't worry too much about that though, I know a number of people that run Amarok on Gnome and are perfectly happy with it.

---

### Post by buntunub on 2007-10-15
Thanks for the responses. Ill give it a fresh install after Gutsy release.

---

