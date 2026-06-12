---
title: "Please explain what this line means?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by paker on 2007-01-08
Please explain the following statement. Specifically, where do I enter this code in ubuntu Edgy?

[COLOR="DarkGreen"]you need to install the packages nabi and im-switch.

Code: sudo apt-get install nabi im-switch[/COLOR]

Thanks.

---

### Post by K.Mandla on 2007-01-08
Into the terminal. Click on Applications > Accessories > Terminal.

Uh-oh. It might not be Accessories. I haven't used Gnome in a while and I can't remember the submenu. It's the first one under Applications. 

I think I'll just be quiet now. :oops:

---

### Post by obsidion on 2007-01-08
> **paker said:**
> Please explain the following statement. Specifically, where do I enter this code in ubuntu Edgy?

[COLOR="DarkGreen"]you need to install the packages nabi and im-switch.

Code: sudo apt-get install nabi im-switch[/COLOR]

Thanks.

 Or you could just fire up synaptic do a search for nabi and im-switch to make sure that the packages are available and install them from there. If they aren't available then you might need to enable other repos.

---

### Post by mlissner on 2007-01-08
Yes, that's correct. Applications > Accessories > Terminal.

The code itself means: 
sudo > superuser (800 lb. gorilla) do
apt-get > the program that gets applications 
install > an argument to apt-get to install something
nabi > the application to be installed by apt-get

Good luck. Linux will allow you to download almost any program you could imagine by using only apt-get install. 

Makes life much easier than other OSes.

---

