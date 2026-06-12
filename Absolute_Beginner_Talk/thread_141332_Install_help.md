---
title: "Install help"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-08
Hi 

At last I might have found the necessary drivers to run my Radeon X550 PCI-express card.  However, they are *.rpm.  I am absolutely brand spanking new to Linux and so far have had little success installing Ubuntu on my system.  Please explain to me in 'Lady Bird' language how I convert *.rpm to *.deb and then how do I go about installing the drivers.  I know that I can copy them to a folder in the 'home' directory and I think I have figured out how to remove the padlock emblem (what is that for anyway?) and that is about as far as I have got.  I can't access the internet from Ubuntu because I still haven't figured out how to get the system to see my Dongle device.

Thank you all in advance.

---

### Post by Perfect Storm on 2006-03-08
Open the terminal.

```
sudo apt-get install alien
cd /to/the/.rpm/file
sudo alien XXXXXXXX.rpm
sudo dpkg -i XXXXXXXXX.deb

```

That doesn't mean it will works, but you can try.

---

