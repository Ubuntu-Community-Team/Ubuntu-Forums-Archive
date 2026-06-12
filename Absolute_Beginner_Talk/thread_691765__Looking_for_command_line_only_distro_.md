---
title: "_Looking for command line only distro_"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by HautingLu on 2008-02-08
Are there any Linux distros out there that are only command line? Reason I ask is I'd like to dual boot it with Ubuntu or Windows. Hoping to slow down prying eyes (think TSA). (I already use TC)


With the new Truecrypt (5) release, I'm interested in the new whole drive encryption. Do you think it would be possible to encrypt a whole drive, but put a second OS into a hidden volume? Just thinking out loud, thanks for listening :biggrin:

---

### Post by amingv on 2008-02-08
You can always install your favourite distro and uninstall X.

---

### Post by kevdog on 2008-02-08
TrueCrypt 5 is got some issues with the CL -- they removed some options -- Im not sure if they are going to be adding back in the options that are included in the GUI to the CL.

---

### Post by HautingLu on 2008-02-08
amingv - Are there any write-ups? Is it possible to default to one OS, and only boot the other when a key (F1 or Esc) are pressed?

kevdog - Good to know. I'm using the GUI version right now, but the older CL version would do.


Guess it's time to play and find out....

---

### Post by amingv on 2008-02-09
> **HautingLu said:**
> amingv - Are there any write-ups? Is it possible to default to one OS, and only boot the other when a key (F1 or Esc) are pressed?

kevdog - Good to know. I'm using the GUI version right now, but the older CL version would do.


Guess it's time to play and find out....

Well, you can set GRUB to boot your command line linux as default. If you press ESC at boottime you can choose what else to run... Not that I think it would make a security advantage, but then again some people may feel "intimidated" if they fall into a CLI.

---

### Post by Rocket2DMn on 2008-02-09
Any linux distro can be set to not load the GUI at start, either through disabling X or GDM or by setting the startup init level to "3" (multi-user terminal).  However, that means if somebody knows linux, they could just "init 5" to get to the GUI; or enable X and GDM if they gain root privileges - this is easy if they are at your computer, they would just boot into recovery mode.  Also, Ubuntu server does not come with a GUI at all (you have to install it separately if you want it).
You could just get a standard Ubuntu install, then stop gdm and uninstall "ubuntu-desktop".

---

### Post by dreadlord_chris on 2008-02-09
The Ubuntu **server** ISO's don't install a desktop environment

---

### Post by santiagoward2000 on 2008-02-09
You could use an Ubuntu AlternateCD to install a command line system.

---

### Post by nikoPSK on 2008-02-09
> **amingv said:**
> You can always install your favourite distro and uninstall X.

Thats what I was going to say :lol:

---

### Post by scorp123 on 2008-02-09
> **HautingLu said:**
> Are there any Linux distros out there that are only command line? Ubuntu Server Edition
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

---

### Post by lswest on 2008-02-09
also, Debian installs are just CLI. [www.debian.org/]("www.debian.org/")

---

### Post by nikoPSK on 2008-02-09
> **scorp123 said:**
> Ubuntu Server Edition
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

and theres fedora for servers as well, it's nice. (Just my opinion)

---

### Post by Mary.Riley on 2008-02-09
Well, there's always Gentoo if you want to have some REAL fun...

---

### Post by nikoPSK on 2008-02-09
> **Mary.Riley said:**
> Well, there's always Gentoo if you want to have some REAL fun...

Hehe, yup. :lol:

---

### Post by woedend on 2008-02-09
arch linux install only base linux utilities by default and is command line from there....

---

### Post by jvc26 on 2008-02-09
Any linux server edition is highly unlikely to include a GUI - one less step than uninstalling X, and gets you a clean CLI linux.

Il

---

### Post by nikoPSK on 2008-02-09
> **Illuvator said:**
> Any linux server edition is highly unlikely to include a GUI - one less step than uninstalling X, and gets you a clean CLI linux.

Il

Exactly.:)

---

### Post by amingv on 2008-02-09
> **Illuvator said:**
> Any linux server edition is highly unlikely to include a GUI - one less step than uninstalling X, and gets you a clean CLI linux.

Il

In case you want to install the server edition, just remember not to choose LAMP or DNS when installing.
Also stop any server daemon that might be running...

---

### Post by scorp123 on 2008-02-09
> **nikoPSK said:**
> and theres fedora for servers as well, it's nice. (Just my opinion) I personally find Fedora way too buggy, e.g. I can't install Fedora 8 on most of my machines without having to mess with boot parameters to get the thing even started in the first place (nonsense such as "floppy.allowed_drive_mask=0 clocksource=acpi_pm" .... WTH? :confused: ) ... And "Fedora for Servers" ... There is no dedicated server edition, or at least I seem unable to find it. Red Hat's "Enterprise Linux" (RHEL) is a commercial distro and plays in an entirely different league than Fedora.

---

### Post by scorp123 on 2008-02-09
> **Illuvator said:**
> Any linux server edition is highly unlikely to include a GUI  Not true. Both RHEL and SLES ship with GUI's and they'd install GNOME or KDE per default unless you tell them not to. From that POV Ubuntu's Server Edition is my favourite: It really just installs the absolute minimum you need for a server (exactly what you want on a server anyway) and thus avoids any bloat.

---

### Post by Nythain on 2008-02-09
unless you want a bunch of pre-installed server stuff, i would suggest teh ubuntu alternate install disc (with command line system) or arch

---

### Post by scorp123 on 2008-02-09
> **Nythain said:**
> unless you want a bunch of pre-installed server stuff ...  You can have that with the "Ubuntu Server" edition, just don't select any of the "Installation Tasks" it suggests, e.g. "LAMP server", "bind (DNS)", and so on (I'd recommend installing the SSH server though for remote access!). Then you'd get a very minimal CLI-only system.

If you want to try such a total minimum CLI-only system e.g. within VMware I'd recommend "Ubuntu JeOS":  JeOS = Just enough OS. It's sooooo totally minimal and it is CLI only. A few infos are here:
[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

A small tutorial can be found here:
[http://www.linux-mag.com/id/4829](http://www.linux-mag.com/id/4829)

The ISO image of "Ubuntu JeOS" is only 150 MB in size ... so yes, it is totally stripped down as far as this is possible with Ubuntu. Ideal if you want to try this out first e.g. in VMware or VirtualBox before installing "Ubuntu Server" for real somewhere.

---

### Post by p_quarles on 2008-02-09
JeOS is a specialized version of Ubuntu meant primarily to run virtual machines, so I don't think that's the best option here. 

The best choice for a completely customized installation is the Ubuntu Minimal CD:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's all of ~10 MB, installs just enough to get the system working, and allows you to install exactly the packages you want afterward.

---

### Post by scorp123 on 2008-02-09
> **p_quarles said:**
>  JeOS is a specialized version of Ubuntu meant primarily to run virtual machines, so I don't think that's the best option here.  It's OK for trying it out in a virtual machine, e.g. see what Ubuntu "CLI only" would look like before installing e.g. Ubuntu Server for real on a real PC.

> **p_quarles said:**
>  The best choice for a completely customized installation is the Ubuntu Minimal CD:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)  Nice! Thanks for the link. :)

---

### Post by p_quarles on 2008-02-09
> **scorp123 said:**
> It's OK for trying it out in a virtual machine, e.g. see what Ubuntu "CLI only" would look like before installing e.g. Ubuntu Server for real on a real PC.
Oops, I don't think my last post was very clear. JeOS isn't meant to run *in* a virtual machine, it's meant to be a minimal operating system that runs the VMs -- in other words, it comes with the tools to install something like VMWare Server or Xen, but isn't very functional beyond that. It's missing a lot of the tools you would want in a normal CLI setup. 

> Nice! Thanks for the link. :)
No problem. That's a fantastic little disk, and really is ideal for getting a streamlined setup.

---

### Post by scorp123 on 2008-02-09
> **p_quarles said:**
>  Oops, I don't think my last post was very clear. You were clear. You are misunderstanding me. :)

Let's suppose someone wants to test-ride a "CLI only" system .... so what is he supposed to do? Install *something* on a PC and then find out it was the wrong thing? JeOS is perfect for this: It's only 150 MB in size, so you won't have to download too much and it pretty much gives you the "look & feel" (or lack thereof :) ) of "Ubuntu Server", so you can find out if this stuff is for you or not before you install this thing for real anywhere.

That's what I meant.

> **p_quarles said:**
>   Ubuntu "Mini" ISO: No problem. That's a fantastic little disk, and really is ideal for getting a streamlined setup.  I was kind of surprised to see that after all there indeed is a Ubuntu 7.10 version for the PowerPC ... and even Cell?? Wow. I guess not all packages from the i386/x64 branches are available? Do you have any feedback somewhere somehow or sources how good (or bad?) Ubuntu for the PPC is?

---

### Post by scorp123 on 2008-02-09
> **p_quarles said:**
> JeOS isn't meant to run *in* a virtual machine, it's meant to be a minimal operating system that runs the VMs. Not true BTW. Please read this article I linked to earlier: [http://www.linux-mag.com/id/4829](http://www.linux-mag.com/id/4829)

Quotes from there (emphasis added by me): 

"JeOS is a specialized installation of Ubuntu Server Edition with a tuned kernel that only contains the base elements **needed to run within a virtualized environment** ..."

"Ubuntu JeOS has been tuned to take advantage of key performance technologies in the latest virtualization products from VMware. The combination of reduced size and optimized performance ensures that Ubuntu JeOS Edition delivers a highly efficient use of server resources in large virtual deployments."

and so on.

JeOS was clearly designed to run inside of a VM. But again: It's perfect for doing a test-ride of Ubuntu Server before installing that one for real on a real PC :)

---

### Post by p_quarles on 2008-02-09
Oops, you're right. Looks like I had it backwards. ;)

---

### Post by nikoPSK on 2008-02-10
Lots of nice server editions out there. :D My friend uses fedora for his server, and he likes it, so I'd recommend that.

---

### Post by Rocket2DMn on 2008-02-10
> **nikoPSK said:**
> Lots of nice server editions out there. :D My friend uses fedora for his server, and he likes it, so I'd recommend that.

I use Fedora on a game server, and it's not bad.  It's sort of like the Ubuntu for Red Hat.  For a red hat based server, I have heard that CentOS is good too.  For both of these you would probably just have to disable the GUI to you can CLI only.  I did that on my Fedora server by setting the bootup init level to 3.

---

### Post by nikoPSK on 2008-02-10
> **Rocket2DMn said:**
> I use Fedora on a game server, and it's not bad.  It's sort of like the Ubuntu for Red Hat.  For a red hat based server, I have heard that CentOS is good too.  For both of these you would probably just have to disable the GUI to you can CLI only.  I did that on my Fedora server by setting the bootup init level to 3.

So it's nice then. :D

---

### Post by p_quarles on 2008-02-10
> **Rocket2DMn said:**
> For a red hat based server, I have heard that CentOS is good too.
CentOS actually *is* Red Hat, but a community maintained version. The source code is the same.

---

### Post by scorp123 on 2008-02-11
> **Rocket2DMn said:**
>  For both of these you would probably just have to disable the GUI to you can CLI only.  I did that on my Fedora server by setting the bootup init level to 3. Yes, but why even have a GUI installed in the first place? That's bloat on a server, IMHO. That's what I like about Ubuntu Server: it doesn't even ship with a GUI to begin with and doesn't install one and thus not waste diskspace and not drive you crazy with some weird dependency issues  ... exactly what one would want for a server.

---

### Post by Rocket2DMn on 2008-02-11
> **scorp123 said:**
> Yes, but why even have a GUI installed in the first place? That's bloat on a server, IMHO. That's what I like about Ubuntu Server: it doesn't even ship with a GUI to begin with and doesn't install one and thus not waste diskspace and not drive you crazy with some weird dependency issues  ... exactly what one would want for a server.

I understand that and agree that most servers don't need GUIs, the problem is a lot of good server distros come with a GUI pre-installed.  If you do a custom install though, you could probably tell it not to install any GUI.  The amount of space that a GUI takes isn't really a lot compared to the size of hard drives nowadays anyway, and in fact most servers have far more drive space than they ever need.  I actually just ran across this recently: [http://ask.slashdot.org/askslashdot/08/02/09/1319258.shtml](http://ask.slashdot.org/askslashdot/08/02/09/1319258.shtml)
I run a game server with an 80GB hard drive and only use about 10GB of it! (you get the point).  You're right about dependencies though, no use in upgrading/maintaining garbage you don't use.

---

### Post by scorp123 on 2008-02-11
> **Rocket2DMn said:**
>   You're right about dependencies though, no use in upgrading/maintaining garbage you don't use. Exactly. I just took a look at SUSE again the other day and it will drive you bananas with installing stuff you don't want ... but it insists for some odd reasons that all the BS packages it wants to keep are "needed".

---

