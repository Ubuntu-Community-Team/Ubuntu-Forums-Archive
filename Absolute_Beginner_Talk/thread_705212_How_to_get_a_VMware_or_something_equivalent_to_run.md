---
title: "How to get a VMware or something equivalent to run?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-02-23
Hi!

So I'm now ubuntu user. Two weeks ago i got really angry when i tried to lower the volume in Windows Vista and as a consequence of that i erased all on my hard disk. Then i installed Suse but i wasn't really pleased - it is almost as instable as windows. Then i went to centos then to debian and now i have ubuntu and I'm really happy with it.
But there are still some windows tools i want to use and i need to have on my mashine. First of all tools for my N95 8GB. I get it to run as a USB storage but i wonder if there is a possibility to use it with UMTS as a modem.
So I thought about installing a windows (not quiet sure witch) Maybe 2000 or XP or Vista ultimate on a virtual mashine. 
I've got a normal x86 architecture so no 64 bit. 

Is there any alternative to VMware that just works? I can't use the common installation method because it says VMware is not compatible to my architecture (i386).

Does someone now what i have to do?

Thanks in advance!

Thomas

---

### Post by .nedberg on 2008-02-23
You could try Virtualbox
```

sudo apt-get install virtualbox-ose

```

Or go to [http://virtualbox.org/]("http://virtualbox.org/") and download a .deb (or add a repository). This is the preferred way I believe...

---

### Post by anewguy on 2008-02-23
I have installed VMWare many times - try downloading VMWare Server directly from VMWare.  This works much better for me anyway.  Be sure to first remove all of the VMWare you have installed.  You will need a registration key, but it is all free, and you get the key at VMWare as well.  If you still have problems, copy and paste the session back here so we can take a more detailed look.

Thanks! :)

---

### Post by superprash2003 on 2008-02-23
yes, vmware server from vmware website should work!!!

---

### Post by glennric on 2008-02-23
The easiest way to install vmware server is to enable the canonical repository.  To do this add
```
deb http://archive.canonical.com/ubuntu gutsy partner

```
to the end of the file /etc/apt/sources.list
run
```
sudo apt-get update
sudo apt-get install vmware-server
```

---

### Post by thomas7.10 on 2008-02-24
Hi!

thanks for your reply i got to work both VMware and virtualbox. But i have the same problem with both of them. I can't get neither the ethernet nor the USB device to be recognized in the OS on the emulated computer. Is it just not possible or can I change something and then it works?

Thomas

---

