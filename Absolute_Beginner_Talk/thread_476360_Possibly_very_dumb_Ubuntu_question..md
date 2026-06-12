---
title: "Possibly very dumb Ubuntu question."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Silent Knight on 2007-06-17
Hi,

This might sound like a completely stupid question but this is my first experience in a Linux environment and I desperately want to start learning/understanding Linux etc.

I've installed the Ubuntu Server O/S and I'm wondering it has a GUI at all?  If it does then how do you access it from the command prompt?

Thanks in advance,
Hanré

---

### Post by skymera on 2007-06-17
Ubuntu Server?

i have desktop edition and it is GUI :P

---

### Post by Silent Knight on 2007-06-17
Yea when I originally went to the Ubuntu site there was an option to download the Desktop or the Server edition and I opted for the latter.  Does it not have a GUI?

Does the Desktop addition has all the web hosting/DNS Server etc functionality built-in like the server does?

---

### Post by hyper_ch on 2007-06-17
Ubuntu Server does not install with a GUI... however you can add it later...
Ubuntu Desktop Edition does not come with server stuff... however you can install it later :)

If you want an ISP-style setup (having dns-server, email, webserver with the option of hosting multiple websites....) you can install the desktop edition and then follow this here:
[http://www.howtoforge.com/perfect_setup_ubuntu704_p3](http://www.howtoforge.com/perfect_setup_ubuntu704_p3)

---

### Post by Silent Knight on 2007-06-17
Wow, thanks for the quick reply guys.

I'll download the Desktop version and install it on a separate VM host.  Might as well have both and learn to work both the GUI and the command prompt, I'll probably gain a better understanding of everything if I do it that way!

---

### Post by Jimmyfj on 2007-06-17
> **Silent Knight said:**
> Yea when I originally went to the Ubuntu site there was an option to download the Desktop or the Server edition and I opted for the latter.  Does it not have a GUI?

Does the Desktop addition has all the web hosting/DNS Server etc functionality built-in like the server does?

Yup - Ubuntu server DOES have a GUI, you just have to install it yourself.

run this:

su
password

aptitude

In aptitude you can choose what ever programs you'd like to install including KDE-desktop or GNOME-desktop.

Just remember to install X11 Server and all associated with it before you install any GUI.

I have a Ubuntu 6.10 server running next to me with a GUI (GNOME or XF-something don't know for sure - I asked for GNOME though)

---

### Post by hyper_ch on 2007-06-17
If you want to run the server anyway in a VM, why bothering with a gui? That will only increase the load on your computer....

---

### Post by Silent Knight on 2007-06-17
Excellent, that's exactly what I needed to hear.

I was half under the impression that the GUI was incorporated in the default installation, this is just as easy though.

Thanks.

---

