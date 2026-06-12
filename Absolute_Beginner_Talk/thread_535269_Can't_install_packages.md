---
title: "Can't install packages"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by jambutties on 2007-08-26
Very new user and I have Ubuntu Fiesty Fawn on laptop but when trying to install Limewire, frostwire or anything else I get error message after error message.

Here's what I did when trying Limewire.
Went to Limewire page  left default "open with Gdebi package installer".On package installer window clicked "install package"
Put in password
Got "Only one software management tool allowed tom run at one time".
Checked System/Admin/Syst Monitor/Processes.
Only thing running was "Gnome system monitor", everything else was sleeping.
Went to terminal
Typed "dpkg --configure -a"
Got "requires superuser privilege"
Typed in "sudo dpkg --configure -a"
Put in password
Hit enter
Nothing happened.

Tried installing Frostwire
Got to "Installing dependancies
but in the download status bar where it says "Preparing sun-java5-bin" it freezes about 1/10th of the way across.

Any help greatly appreciated.

---

### Post by robenroute on 2007-08-26
> **jambutties said:**
> Very new user and I have Ubuntu Fiesty Fawn on laptop but when trying to install Limewire, frostwire or anything else I get error message after error message.

Here's what I did when trying Limewire.
Went to Limewire page  left default "open with Gdebi package installer".On package installer window clicked "install package"
Put in password
Got "Only one software management tool allowed tom run at one time".


When you tried installing the package, Synaptic Package Manager was probably up and running already. Just close Synaptic and double click the .deb file again.

---

### Post by Dark Star on 2007-08-26
Exactly ;) Close the process of update gng on and then type the command lines :)

---

### Post by jambutties on 2007-08-26
Can you tell me how to close synaptic because I can't see an obvious way of doing it.Thanks.

---

