---
title: "Installing ndiswrapper-1.35"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by noob@linux on 2007-01-30
Hi,

im trying to install ndiswrapper-1.35 so i can get my ethernet driver on but having trouble.

here are the install instructions 

Go to the source-directory and run 'make distclean' and 'make'. As root, run 'make install'. This should compile and install both the kernel module and the userspace utilities. If you don't need USB support in ndiswrapper, with recent versions, you can compile with 'make DISABLE_USB=1' and install with 'make DISABLE_USB=1 install'. 

Edit: Need to go to main directory (top of the source-directory mentioned above) and then do a make install. Without this, it does not work.

Everytime i do this it gives me

bash: make: command not found.

can anyone help

---

### Post by PartisanEntity on 2007-01-30
I think there is a newer version of ndiswrapper, namely 1.8?

Someone correct me if I am wrong, but it is easier to install ndiswrapper and its utilities from the repository, either through Synpatic or through the terminal.

If you want to try Synaptic go to: System->Administration->Synaptic, then click on Search and type ndiswrapper, this will bring up all related entries. Click on the one you want and mark it for install. Then click apply.

---

### Post by phansiizwe on 2007-01-30
> **PartisanEntity said:**
> I think there is a newer version of ndiswrapper, namely 1.8?

Someone correct me if I am wrong, but it is easier to install ndiswrapper and its utilities from the repository, either through Synpatic or through the terminal.

If you want to try Synaptic go to: System->Administration->Synaptic, then click on Search and type ndiswrapper, this will bring up all related entries. Click on the one you want and mark it for install. Then click apply.

The one in Synaptic would be ndiswrapper 1.18, 1.35 is the latest stable version (installed it yesterday). Installing (and updating/uninstalling!) is definitely easier from Synaptic,

but noob@linux,

if you really want to build from source, try to install the package build-essential first.
This will provide all tools needed to build programs from source and I'm fairly sure that 'make' is one of them.

To install, use Synaptic or in a terminal, type:

```
sudo apt-get install build-essential
```

Then try building ndiswrapper again, running

```
make
sudo make install
```

---

