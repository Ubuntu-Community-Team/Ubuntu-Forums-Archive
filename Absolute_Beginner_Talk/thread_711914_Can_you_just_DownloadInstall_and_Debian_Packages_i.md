---
title: "Can you just Download/Install and Debian Packages into ubuntu?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-03-01
A very basic question:

If you go to a site such as this (as an example, but could be any other one)

[http://www.kompozer.net/](http://www.kompozer.net/)

And see it has a Debian Package (installer) to download.

Can you just use it in ubuntu knowing it will work?

I've read that there is some connection between Debian and ubuntu, but I'm not sure (no one has explained) how this all works/is put together.

Thanks.

---

### Post by imT on 2008-03-01
yes, you can install deb packages in ubuntu but be careful where you get them.

---

### Post by p_quarles on 2008-03-01
Ubuntu uses the same package management system as Debian, so many packages made for one will work with the other. In this particular case, it specifically says the package was tested on current versions of both Debian and Ubuntu, so that one should work.

---

### Post by Malta paul on 2008-03-01
I would first check if the package is in the synaptic package manager by doing a search for it.
If the file is a .deb you can down load and then install it with your Package Installer.
If the package is an .rpm it might ( not guaranteed ) be possible to converted it to a .deb package using 'Ailen'
Have fun :)

---

### Post by PiggiePaul on 2008-03-01
> **imT said:**
> yes, you can install deb packages in ubuntu but be careful where you get them.

Thanks for the reply.

Well, yes, I'm only really thinking of "Big Name" software places (well known software titles)

Could anyone (in plain English) simply explain what Debian is, and how it related to ubuntu?

Had a look around...........

So is this right:

Debian is the actual name of the operating system.

But, it runs on the Linux Kernel.

(not quite sure I know the difference between a Operating system and a Kernel!)

On top of this Debian operating system (which is sitting on top of Linux) we have Gnome, which is handling the Graphical Interface, and the way it LOOKS basically.

Then, on top of Gnome we have Nautilus which is the file manager, and does the file manipulation.

I'm not quite clear where Gnome ends and Nautilus starts when it comes to displaying icons, folders etc in the windows on your screen.

Any of this right?

---

### Post by p_quarles on 2008-03-01
> **PiggiePaul said:**
>  Could anyone (in plain English) simply explain what Debian is, and how it related to ubuntu?
Debian is a much older Linux distribution, and Ubuntu is a derivative of it.

> Debian is the actual name of the operating system.
Well, the full name of the OS is Debian GNU/Linux. It's one of many Linux distributions. 

> But, it runs on the Linux Kernel.
Yes. The Linux kernel by itself would not be an operating system.

> (not quite sure I know the difference between a Operating system and a Kernel!)
The kernel interacts with the hardware at a low level. It's part of the OS, but not the whole thing. Think of it as the lowest layer in a complex system. 

> On top of this Debian operating system (which is sitting on top of Linux) we have Gnome, which is handling the Graphical Interface, and the way it LOOKS basically.
Linux is, again, part of the operating system. Gnome is one of several options for a graphical interface. 

> Then, on top of Gnome we have Nautilus which is the file manager, and does the file manipulation.
Nautilus is part of Gnome, it's not a separate thing. It acts as a file manager and it draws the desktop. Apart from this, you also have a window manager (for Gnome, usually either Metacity or Compiz) that handles the way open applications are displayed and manipulated. 

> I'm not quite clear where Gnome ends and Nautilus starts when it comes to displaying icons, folders etc in the windows on your screen.
Gnome is basically a suite of applications that are bundled together to create an integrated environment. Nautilus is one of those applications, along with Metacity, Gnome-panel, Gnome-settings-manager, the Synaptic Package Manager, and so forth. Together, these things all make up Gnome itself.

---

### Post by ellalan on 2008-03-08
Hi guys
I wonder whether one of you might help me.
I have downloaded cnijfilter-common_2.80.1_i386.deb and cnijfilter-mp210series_2.80-1_i386.deb  to my Desktop, then I installed them using Synaptic Package Manager.
I obtained the drivers from Canon Australia and these drivers are released for Linux systems.
But unfortunately when I connect my printer and tried to get a test page it came up with an error message "CUPS Server error"
There was an error during the cups operation
Could you please help me to fix this. Thank you.

---

### Post by ellalan on 2008-03-08
Hi
I just want to update my previous post,
I have found a solution and got my printer working, Thank you.

---

