---
title: "Ubuntu in VMWare Fusion under Snow Leopard"
date: 2011-06-24
forum: Apple Hardware Users
---

### Post by lowell.dennis on 2011-06-24
I currently have a full install of Ubuntu 10.4 64-Bit running under VMWare Fusion on my MacBookPro.  I works fine but I am looking to streamline things a bit.  All I actually need is to be able run commands from the command line.

---

### Post by lowell.dennis on 2011-06-25
Sorry for being so terse with the first post ... my wife called me and I had to cut it short.

Anyway, I am working with a build system that only works with Linux distros and is only certified on Ubuntu 10.04 64-bit.  There are a few native commands that will not run from Apple_Terminal command prompt.  At present I am running a full Ubuntu 10.04 64-bit install under VMWare Fusion.  I do notice performance some degradation when the VM is  running.  All I really need is to be able to open a terminal window that will run native Ubuntu 10.04 64-bit executables.  I am hoping that someone here will know how I can streamline th VM needs or another method of running the Ubuntu exes on a Mac.

---

### Post by Untitled_No4 on 2011-06-25
Will SSH help you?

On the Ubuntu VM run
```
sudo apt-get install openssh-server
```

Once installed, you can then run on Mac's terminal
```
ssh username@ipaddress
```
(you don't need the username if it's the same on both machines)

Obviously, the commands are executed by the virtual machine.

---

### Post by lowell.dennis on 2011-06-27
> **Untitled_No4 said:**
> Will SSH help you?
Yes, I can use SSH.  I have installed open SSH on the VM but that stull involves launching the entire VM (graphics and all) to use.  I was hoping that there was a way to set up the VM such that it it can handle the SSH but does not have all of the other unneeded stuff.  I just need to run a few executables from the command line.

---

