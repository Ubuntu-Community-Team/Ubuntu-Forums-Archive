---
title: "How's Ubuntu All Hang Together"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Frogbarf on 2007-10-04
Will some kind soul please explain, or point me to a good explanation of, the interrelationships between Linux in the strictest sense, the Gnome desktop, and Nautilus (whatever that is!)

Further, whether it's possible to run KDE *and* Gnome at the same time, and the relationship of these to X servers (is that the right lingo?)

And finally, is there a good list somewhere of basic keyboard shortcuts so I can navigate at the system level?

Very basic questions, but I'm trying to get my head around the Linux and Ubuntu view of the world and I've never used a Unix-like system before. 

I'm motivated because I'm having trouble with a Win program under Wine and want to try running it as "unmanaged.  When I try that, it fires up but never gets focus so you can't do anything with it except click the cancel button. This is a reported bug with some applications, btw. I have an idea it might be because the program is in effect running parallel to Gnome and I don't know how to get from Gnome to another program. I hope I'm making sense.

I labor under a great difficulty: I've been involved with computers for nearly 50 years and simply have to have a mental model of how any given system hangs together to be comfortable. We're talking conceptual stuff here for the most part.

---

### Post by bodhi.zazen on 2007-10-04
Linux is "modular". Each piece is maintained by a different group and distros, like Ubuntu, put it all together for you.

You can do it yourself, see LFS : [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Linux = the kernel [http://www.kernel.org/](http://www.kernel.org/) = the basic core to initialize your hardware

GNU = c compiler + additional stuff [http://www.gnu.org/](http://www.gnu.org/)

Distro = Ubuntu = Kernel + gnu + additional applications

X = the foundation of a GUI, where the hardware meets the graphical interface ie configuration of monitor, mouse, and keyboard + basic grapical interface

gnome = a desktop environment 

Window managers : [http://xwinman.org/](http://xwinman.org/) These are basic graphical intervaces, a text box, mouse movement, tool bars to minimize windows, widgets.

Desktop environment = window manager + additional applications (file manager, editor, spread sheet, CD burner, etc)

Gnome = the default DE in ubuntu. KDE = Kubuntu. XFCE= Xubuntu

nautilus = file manager in gnome
knoquorer = file manager in KDE
thunar = file manager in XFCE

File managers show the file system copy, paste, etc graphically. In windows this is Explorer.

You can run gnome apps in KDE and visa versa ... but there will be some redundancy 

HTH

---

### Post by Dr Small on 2007-10-04
> **How's Ubuntu All Hang Together**
[http://www.ushistory.org/franklin/quotable/quote71.htm](http://www.ushistory.org/franklin/quotable/quote71.htm) :D

---

### Post by elvis on 2007-10-04
> **Frogbarf said:**
> Will some kind soul please explain, or point me to a good explanation of, the interrelationships between Linux in the strictest sense, the Gnome desktop, and Nautilus (whatever that is!)

Further, whether it's possible to run KDE *and* Gnome at the same time, and the relationship of these to X servers (is that the right lingo?)

Linux is a kernel.  It's the "brains" of the system.  It talks to the hardware on behalf of the shell (see below) via drivers.  The kernel does not communicate in a human-understandable language.  A shell needs to sit beween the human using the system and the kernel to be human-friendly.

Shells are human-friendly interface that talk to the kernel.  Shells come in many shapes and sizes.  Ubuntu (and most GNU/Linux distributions in fact) come with BASH (Bourne Again SHell) as their default shell.  BASH is a "command line" interface (a plain-text non-graphical system that takes written commands in from the keyboard, and prints plain-text output back to the user via the screen).

Additionally, there is a variety of GUI (Graphical User Interface) systems that can talk to the kernel on your behalf too.  Most Linux distros go about this as such:

Firstly there is a graphical "server".  This is a piece of software lives on the physical  machine in question.  Unlike some other Operating Systems where the GUI is entirely on one machine, Xorg (the graphical server typically used on Linux systems) is split in half - client and server.  This means that a user can choose where their client lives.  It can live on the same machine as the server (such as a typical Ubuntu desktop), or the client can live on another machine somewhere else, enabling the user to connect back to the X server over a network.  This can be very useful for Point of Sale, Educational and other systems where cheap client hardware can be easily utiliised to connect back to a more powerful server, and multiple users can log into a single server, using the server's resources.  This is called a "thin client" (as opposed to a "fat client", where all the software and services run locally and share resources via centralised file servers).

X clients can employ various window managers and desktop environments to provide a complete graphical system for the user to use.  One thing that needs to be stressed about GNU/Linux is that it is free (as in freedom) and open.  Anyone is free to develop software for it, and choice is plentiful.  As such, many desktop environments exist for Xorg on Linux.  GNOME and KDE are just two.  There are literally dozens of others that are available should you choose.  (Choice is a wonderful thing!).

GNOME and KDE are by far the two most popular.  They are developed by completely independent teams and follow their own design goals and schedules.  Despite what some might argue, there is no one "superior" system.  They are very different, and people certainly have their preferences.  But they are both entirely competant, and fantastic examples of free software working well,

The beauty of either is that their libraries are freely available to the other.  For example, I use GNOME by choice.  However I think GNOME is lacking a good CD/DVD burning application.  My preferred burning app is K3B, which is a KDE application.  Not a problem however, as when I install K3B on my system via Ubuntu's APT packaging system, KDE libraries (Qt and others) needed by K3B are installed also.  Now I can easily fire up K3B and it will load and run from within GNOME!  Likewise, KDE users can easily run GNOME-based (GTK - GNOME Tool Kit) programs very easily.

You can load GNOME and KDE in their entirety on a single system.  There's no problems there.  As a single user you can only use one at a time (they come with their own unique desktop management systems, application menus, system tools, etc).  They also use their own file managers - GNOME uses Nautilus, KDE uses Konqueror (and in Kubuntu 8.10, Dolphin).  However from the logon menu the user can easily change their selection at logon time.  

If you run a system where multiple users log in at the same time (see the "thin client" example above), each user can choose a desktop independently.  It's a per-user setting, not a system-wide setting.

> **Frogbarf said:**
> And finally, is there a good list somewhere of basic keyboard shortcuts so I can navigate at the system level?

Very basic questions, but I'm trying to get my head around the Linux and Ubuntu view of the world and I've never used a Unix-like system before. 

I'm motivated because I'm having trouble with a Win program under Wine and want to try running it as "unmanaged.  When I try that, it fires up but never gets focus so you can't do anything with it except click the cancel button. This is a reported bug with some applications, btw. I have an idea it might be because the program is in effect running parallel to Gnome and I don't know how to get from Gnome to another program. I hope I'm making sense.

I labor under a great difficulty: I've been involved with computers for nearly 50 years and simply have to have a mental model of how any given system hangs together to be comfortable. We're talking conceptual stuff here for the most part.

Keyboard shortcuts are documented by the individual desktop authors.  [www.gnome.org](www.gnome.org) and [www.kde.org](www.kde.org) are your first points of call to visit, and read the documentation.

WINE problems are not related to either GNOME or KDE.  WINE is a totally separate application.  Head over to [www.winehq.org](www.winehq.org) and post your problems there to get prompt support.  

50 years computer experience!  Wow, you must have seen quite a bit in your time.  I'm amazed that you haven't come across a Linux/UNIX/BSD system in that time.  UNIX was the first "portable" operating system for computers (long before Microsoft was even a thought in Mr Gates' mind).  Linux is a completely different design philosophy from other proprietary systems.  What you need to remember always is that it's community driven, and open.  No single entity is responsible for the entire system head to toe, but at the same time everyone makes their systems open so others can leverage their systems and build from there.  In computing it doesn't make sense to constantly re-invent the wheel.  If your specialty is in graphical user interfaces, there's no point in you writing a whole operating system from scratch - kernels, drivers, networking.  If these things already exist and are free to use and extend, it makes sense just to code the software you are good at and use other people's code as a base.  

And that's precisely where Linux is today.  Originally the GCC development environment (made by the GNU and Free Software Foundation) was used to make the Linux kernel.  From there, others made all the parts of the puzzle that make up what you now see as a modern day Linux.  True international, community-driven software at it's best! Software written by a small group of individuals from one single country (or even city) will never succeed en mass, because it can never appeal to everyone all the time.  Free software makes software design an international event, meaning that everyone can have their say in what they want to see included.

---

### Post by Anzan on 2007-10-04
elvis, that was a great post.

---

