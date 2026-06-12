---
title: "[SOLVED] Error installing limewire"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by mike868y on 2007-08-10
Hello, I'm trying install limewire. I downloaded the .deb to my desktop. WHen i try to install it i get an error message telling me that i can only have one software management tool running at once. I rebooted and i still get this error. what should i do? is their an alternate download to the .deb?

[img]http://mikemartinracing.com/images/Screenshot-gdebi-gtk.jpg[/img]

---

### Post by SOULRiDER on 2007-08-10
First of all, you need java installed:
```
sudo aptitude install sun-java6-jre
```

Also, i suggest you install Frostwire, its like Limewire but OpenSource.
[http://frostwire.com](http://frostwire.com)

If you still get that software management tool error, type this in a console:
```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

You will also want to remove Limewire if it was installed.

Good luck!

---

### Post by Hospadar on 2007-08-10
are you running synaptic at the same time?

what happens when you try it in a terminal, go to Applications->Accessories->Terminal and type

```
sudo dpkg -i ~/Desktop/*the_name_of_the_file*.deb
```
where *the_name_of_the_file *is the actual filename.

---

### Post by xopher on 2007-08-10
Well do as it says, make sure you don't have any update-manager running, eg. apt-get, aptitude, synaptic, update-manager etc.

Then, you can either double-click on the .deb to install it using the graphical tool, or open a terminal at the location and install it via dpkg:

```
sudo dpkg -i filename.deb
```

---

### Post by Ek0nomik on 2007-08-10
I don't think any of the solutions you guys have provided will fix his problem.  He is having problems with the package manager itself, even after a reboot.

Try to run this command:

```
sudo dpkg --configure -a
```

and hopefully you will be able to install anything whether it's via a *.deb file, using Synaptic, or apt-get.

---

### Post by mike868y on 2007-08-10
after typing countless commands into the terminal.. i reinstalled ubuntu.. it was just under wubi.. so its not that big of a deal.. tahnks for the help anyway tho

---

### Post by Billy_McBong on 2007-08-10
[COLOR="Blue"]i would suggest using frostwire, its is synaptic[/COLOR]

---

### Post by Ek0nomik on 2007-08-10
> **mike868y said:**
> after typing countless commands into the terminal.. i reinstalled ubuntu.. it was just under wubi.. so its not that big of a deal.. tahnks for the help anyway tho

I was waiting for a response from you based on what I said.  I had more suggestions for you...

Oh well, reinstall works I suppose...

---

### Post by SOULRiDER on 2007-08-10
> **Billy_McBong said:**
> [COLOR="Blue"]i would suggest using frostwire, its is synaptic[/COLOR]

Indeed, Frostwire is like Limewire Pro and open source!

---

