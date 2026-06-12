---
title: "Vista Home Premium and  Virstual Box"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-22
Is there a way to setup my Virtual Machine with VirtualBox and Vista Home Premium and have my network/LAN working in windows via VirtualBox?

I found a guide on these forums about seamless integration with VirtualBox, but it said it only worked with Vista Business and Ultimate.
I didn't think that made sense, but I'm a Ubuntu/Linux noob, so what do I know.

Any ideas?

---

### Post by luisromangz on 2007-06-22
Well I think that the problem is a problem of licences, Windows Vista Home Premium's licence doesn't allow the user to virtualize it, but you are allowed to virtualize the Business and Ultimate version, which are more expensive you know... MS way of doing things.

Bye!

---

### Post by dannymichel on 2007-06-22
> **luisromangz said:**
> Well I think that the problem is a problem of licences, Windows Vista Home Premium's licence doesn't allow the user to virtualize it, but you are allowed to virtualize the Business and Ultimate version, which are more expensive you know... MS way of doing things.

Bye!
So the fact that my LAN/Network connection doesn't work in VirtualBox has nothing to do with the fact that my Vista version is home premium?
This virtual Machine is the ONLY place I will be running Vista anyway?
I pruchased Vista only for that purpose.

If the answer is yes, you CAN  get your LAN/Network working on Vista Home Premium via VirtualBox, then my question is how?

---

### Post by lazyart on 2007-06-22
There is a way put it's so freakin' convoluted that it's scary, and I broke the networking on my host machine trying to get it to work.  You can find some help here: [http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)


Very honestly, I would use VMWare instead.  You simply tick a box for NAT, Bridged or private networking and it's done.

Virtualbox is great but I give it a huge thumbs down on configuring networking.

---

### Post by dannymichel on 2007-06-22
> **lazyart said:**
> There is a way put it's so freakin' convoluted that it's scary, and I broke the networking on my host machine trying to get it to work.  You can find some help here: [http://doc.gwos.org/index.php/VirtualBox#Networking](http://doc.gwos.org/index.php/VirtualBox#Networking)


Very honestly, I would use VMWare instead.  You simply tick a box for NAT, Bridged or private networking and it's done.

Virtualbox is great but I give it a huge thumbs down on configuring networking.
I had some SERIOUS issues installing VMWare. I ran 
```
sudo vmware-install.pl
```
and I got an error message saying command no tfound.
I asked in IRC rooms for hours and NOONE could help me.

I WOULD LOVE to run VMWare.
If you can help me get past this error message it'd be greatly appreciated.

---

### Post by dannymichel on 2007-06-24
I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts. 

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

---

