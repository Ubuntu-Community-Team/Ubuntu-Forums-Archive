---
title: "Installing ubuntu-desktop on ubuntu server with no network? [Resolved]"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Don Carcharo on 2007-03-06
I want to deploy Ubuntu server in my office however I want Gnome as well since I'm just far more comfortable with the GUI (eg. I'd rather sudo nautilus and gedit than do stuff via the CLI). The problem is although Ubuntu desktop will install properly and supports my wireless adapter (Belkin Wireless G Desktop Adapter) via the Network preference, Ubuntu server can't see the adapter at all. So upon install of Ubuntu server I've got no network connection and no ability to sudo apt-install anything.

Can anyone offer some advice? I'm very shaky when it comes to the CLI. So far I tried adding the CD to /etc/apt/sources.list however that didn't seem to work. I can also boot via the live CD and get a network connection but can't actually seem to install anything to my hard drive that way. I can also mount the cd from within Ubuntu server but can't do anything with the contents.

I'm sure there's a simple way to do this however I have no idea what it is. Can anyone help?

---

### Post by aysiu on 2007-03-06
I don't know the exact solution to your problem, but I can tell you why adding the CD to your sources.list doesn't work. The live CD (also known as the Desktop CD) doesn't contain all the packages it installs. I know that doesn't seem to make sense, but it's true. The Alternate CD, however, actually contains all the packages it installs, so you can use the Alternate CD as a repository and get more than just *build-essential* and *ndiswrapper-utils*.

---

### Post by Don Carcharo on 2007-03-07
Thanks, that seemed to do the trick. ubuntu-desktop is installing now. Much appreciated. :)

---

