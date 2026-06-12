---
title: "[SOLVED] Switching to xubuntu"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-21
Gnome is slowing down my computer, which is kind of funny because I have a 64-bit processor.  Anyway, I have heard that xubuntu is lightweight.  How do I install xubuntu on top of ubuntu without changing any of my settings/ keeping my documents.

---

### Post by hikujk123 on 2008-03-21
I have a swap of about 600 MB.  I am dual booting and have a 12 GB partition for ubuntu.  Please help!

---

### Post by hikujk123 on 2008-03-21
Well, the partition is really 17 GB after the install it reads 12 GB (I think this is because of swap and other linux stuff I am unaware of).

---

### Post by arochester on 2008-03-21
Connect to the Internet, open a terminal and input > sudo apt-get install xubuntu-desktop

You can then choose either Ubuntu or Xubuntu on the page where you sign in.

---

### Post by hikujk123 on 2008-03-21
Then how do I remove ubuntu?

---

### Post by Bruce M. on 2008-03-21
> **hikujk123 said:**
> Gnome is slowing down my computer, which is kind of funny because I have a 64-bit processor.  Anyway, I have heard that xubuntu is lightweight.  How do I install xubuntu on top of ubuntu without changing any of my settings/ keeping my documents.

With Synaptic Package Manager search for: Xubuntu Desktop

Install that and do a [Ctrl]+[Alt]+[Backspace] to restart your session.

At the Login select Sessions and select Xubuntu, Xfce I'm not sure what it will call itself.

This will allow you to use it and see if you like it.
I went from Gnome to Xfce and now I love it.
See my machine spec's in my sig and you'll know why.

Bruce

---

### Post by aysiu on 2008-03-21
You don't have to reset the X server (which is what Control-Alt-Backspace does). You can just log out and select your Xfce session.

---

### Post by arochester on 2008-03-21
Once you have installed xubuntu-desktop, open a terminal and input > sudo apt-get remove ubuntu-desktop

It will probably not take away all Gnomish apps but you can do that yourself...

---

### Post by hikujk123 on 2008-03-21
Thanks.

---

### Post by aysiu on 2008-03-21
> **arochester said:**
> Once you have installed xubuntu-desktop, open a terminal and input 

It will probably not take away all Gnomish apps but you can do that yourself...
I doubt that will work, actually, since *ubuntu-desktop* is just a metapackage (empty pointer) that depends on other packages. Removing *ubuntu-desktop* will not remove its dependencies.

That's why I created [a tutorial specifically for how to remove Gnome from Xfce](http://www.psychocats.net/ubuntu/purexfce).

---

### Post by hikujk123 on 2008-03-21
Is OpenOffice a Gnomish app?

---

### Post by hikujk123 on 2008-03-21
Also, will I be able to run such applications if I wanted to?

---

### Post by aysiu on 2008-03-21
> **hikujk123 said:**
> Is OpenOffice a Gnomish app?
It actually does not belong to any particular desktop environment. I believe Ubuntu, Xubuntu, and Kubuntu *all* come with OpenOffice.

---

### Post by aysiu on 2008-03-21
> **hikujk123 said:**
> Also, will I be able to run such applications if I wanted to?
Yes, you can run any application you want in any desktop environment you want. In fact, there's really no compelling reason to remove Gnome, unless you're hard up for disk space (i.e., your hard drive is only 5 GB).

---

### Post by hikujk123 on 2008-03-21
My hard drive isn't that small, but I am still pressed for space.  If it comes with OOo then great.  If not, I will just install it via synaptic.

---

### Post by hikujk123 on 2008-03-21
Now everything functions like xubuntu.  However, my log in screen still say ubuntu.  Will this be a problem when I update to Hardy?

---

### Post by aysiu on 2008-03-21
> **hikujk123 said:**
> Now everything functions like xubuntu.  However, my log in screen still say ubuntu.  Will this be a problem when I update to Hardy?
Xubuntu and Ubuntu actually share the same login screen manager (GDM). Kubuntu has its own login screen manager (KDM).

So you're fine.

If you're worried about the Hardy upgrade, just make sure you keep the *xubuntu-desktop* metapackage installed before you upgrade.

---

