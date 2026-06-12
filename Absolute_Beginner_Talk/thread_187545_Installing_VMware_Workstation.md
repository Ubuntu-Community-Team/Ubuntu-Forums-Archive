---
title: "Installing VMware Workstation"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by ktvyeow on 2006-06-03
Hi guys, I'm an absolute noob with Linux.  JUst installed it last night on my laptop and I want to install VMware Workstation on it and put Win XP on it so that I don't have to dual boot.

I'm using Ubuntu 6.06 now and I've installed gcc.  I've ran ./vmware-install.pl and used default for all the options until I reached the part where it says this:

"Before running VMware Workstation for the first time, you need to configure it
by invoking the following command: "/usr/bin/vmware-config.pl". Do you want thisprogram to invoke the command for you now? [yes]"

Should I press yes as I've read somewhere that said I should press no when installing VMWare on Ubuntu.

---

### Post by Mordred on 2006-06-03
Hi,

I'm not using dapper but I'll try to help you anyway :D 

I think it's not necessary to compiler it yourself,
you can install it with apt:

sudo apt-get install vmware-player

perhaps you will first need to add extra repositories

run

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

and enable multiverse

---

### Post by Rackerz on 2006-06-03
[QUOTE=ktvyeow]Hi guys, I'm an absolute noob with Linux.  JUst installed it last night on my laptop and I want to install VMware Workstation on it and put Win XP on it so that I don't have to dual boot.

I'm using Ubuntu 6.06 now and I've installed gcc.  I've ran ./vmware-install.pl and used default for all the options until I reached the part where it says this:

"Before running VMware Workstation for the first time, you need to configure it
by invoking the following command: "/usr/bin/vmware-config.pl". Do you want thisprogram to invoke the command for you now? [yes]"

Should I press yes as I've read somewhere that said I should press no when installing VMWare on Ubuntu.[/QUOTE]

Do press yes, you will need to press yes. I installed VMware earlier and it does no harm.

---

