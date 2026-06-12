---
title: "Installing HPLIP"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by notoriousjosh on 2007-02-14
I'm running a manual install of HPLIP 1.7.1 to get familiar with Terminal commands (I'm pretty new to this whole thing) but at the configure step I keep getting: 

                     configure: error: cannot find libusb support

lil help?

---

### Post by Maestro23 on 2007-02-14
It's looking for that dependency. You need to install the package via Synaptic(GUI) or apt-get(command line).  If you don't find it on first search, you need to enable extra repositories.

Extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

More links to help/bookmark:

Installing anything in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good for learning commads/linux file structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Good luck.

---

### Post by notoriousjosh on 2007-02-14
Thanks, couldn't find it with Terminal but used the package manager to get that and all the others I needed.

EDIT: Alright ran into another problem, I got:

                    configure: error: cannot find net-snmp support

And no packages that I could find fixed it. Any suggestions?

---

### Post by notoriousjosh on 2007-02-14
So no new ideas then?

---

