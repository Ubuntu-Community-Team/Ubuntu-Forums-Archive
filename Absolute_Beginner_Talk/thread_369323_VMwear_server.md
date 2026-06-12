---
title: "VMwear server"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-02-24
I've been reading a little about VMwear but remain a little confused by what I can do with it. Can someone give me a simple explanation please.  Should I choose server as opposed to the player version?  My attempts at downloading from the VMWear home page have failed so far.  Is there another way of getting it?

---

### Post by irish_flu on 2007-02-24
VMWare enables you to run what's called a "virtual machine".

A "Virtual Machine" is just what it sounds like.  It's an operating system that runs separately from (in this case, alongside) your "host" operating system (in your case, Ubuntu).  VMWare makes the "guest" OS believe that it's running on a machine of its own.

As an example, I run VMWare so that I can test some web stuff I'm doing without messing around with my "real" OS.  I keep a backup copy of the Virtual Machine, and if I screw it up I can easily revert to that.  It's also a fun way to "try out" operating systems, if you're into that sort of thing.

What it does is make a file on your hard drive.  The "Guest" OS believes that this file is a disk partition, and lives there just like it's running on "bare metal".

As for whether you should run "Player" or "Server", that's up to you.  "Player" allows you to run pre-built virtual machines which you can easily download from a number of locations.  They download as one big file and are already set up.  "Server" allows you to build your own virtual machines (for instance, you can stick your Windows XP CD into the drive and "install" it to a virtual machine).

I'd start off using "Player", mess with it, and if you start wanting to make your own stuff then you can always get server later.

You can download a bunch of pre-built Virtual Machines for the player here:
[http://www.vmware.com/vmtn/](http://www.vmware.com/vmtn/)

As for how to get VMWare player installed, the easiest way in Ubuntu is to enable the "Multiverse Repository" (do a search on this forum if unsure how to do this).  Then you can open Synaptic Package Manager, do a search for "vmware", and install the package.  Download yourself a VM and you're ready to go!

---

### Post by irish_flu on 2007-02-24
Oops, I linked to the wrong page for the Virtual Machines.  Here ya go:
[http://www.vmware.com/vmtn/appliances/directory/](http://www.vmware.com/vmtn/appliances/directory/)

---

### Post by a.v.l on 2007-02-24
> **irish_flu said:**
> Oops, I linked to the wrong page for the Virtual Machines.  Here ya go:
[http://www.vmware.com/vmtn/appliances/directory/](http://www.vmware.com/vmtn/appliances/directory/)

Thanks very much, I have a better understanding now. I'm told the VMWear software in the Ubuntu repository is broken at present, can anyone confirm this?

---

### Post by zvacet on 2007-02-24
I think vmware server is better choice,but that is only my opinion.It had bed habbit to install in var by default,but you can change it.Read this if you are interested
[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware")

---

### Post by hyper_ch on 2007-02-24
Get vmware directly from their website:

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

See that register link--> use that to get free vmware server serials...

Once you've registered and got some serials and have the package downloaded, you need to extract it....

but before you can install it a few dependencies must be met.

Open a command line interface and execute the following things:

```

sudo apt-get install linux-headers-`uname -r` build-essential xinetd gcc-3.4

```

Once that is downloaded and installed, go in the terminal to the extracted vmware server folder and execute this command:
```

perl vmware-install.pl

```

That will start installing it... the rest should be evident... well, if you encounter problems, jsut ask :)

---

