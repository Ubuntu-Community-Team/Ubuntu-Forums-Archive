---
title: "apt-get not installed"
date: 2007-05-04
forum: Apple Intel Users
---

### Post by bcr88 on 2007-05-04
I was trying to install Feisty to my external HD, but I gave up on that and installed it on my internal with the Alternate CD. When I went to boot into my newly installed system, it said apt-get was not installed and to type apt-get install apt to install it. Well, obviously, I get do that, so I tried aptitude, but it wasn't installed either. so, neither of the programs for installing other programs are installed, so I can't install them, and I can't boot into Ubuntu.

Any ideas?

---

### Post by 5-HT on 2007-05-04
What about installing apt from the .deb on the alternate CD using dpkg?
Navigate to the directory containing the apt .deb and install with;
```
sudo dpkg -i apt* 
```

---

### Post by Neil H. on 2007-05-05
I'm having this same issue, "apt-get not installed" coming up at boot and halting the boot process. 

I'm a complete Linux noob, so I bought a new hard drive, partitioned it up several ways, and am experimenting with Ubuntu, Kubuntu, Fedora, and Mepis. Anyway, this "apt-get" issue didn't show up immediately, but it is now happening on my installs of Ubuntu and Kubuntu.

One thing that seems to restart the booting sequence for me is the old "three fingered salute": alt + ctrl + delete.

I have no idea what I'm doing, so don't take this information as anything other than "this is what I'm seeing on my machine".

System is Dell XPS M140 laptop. 

Cheers,

n

---

### Post by bobpress on 2007-05-13
I had the same problem after I changed the size and type of partitions on my hard drive to add Vista as a third boot to my dual boot of Kubuntu and Win XP.  'fschk', file system check, died, because the partition types did not match what it expected.  'apt-get not installed' was just the last in a list of messages.  I was able to access the graphical mode by using Ctrl-Alt-Del also.  After using the System Settings/Advanced/Disk & File Systems (Administrator Mode) to remove the partitions which I had changed (it does NOT actually remove the partitions), the PC booted into graphical mode automatically again.  Your 'apt-get not installed' message may be the result of some other process dying.  If you review all the boot messages, you may find some other process caused the problem.  I am not an expert, but someone may have an idea about what is causing your problem and suggest a fix if you can list all the messages.

---

### Post by muhamad on 2008-06-13
Hello guys!
I'm new in Linux, I have been install Redhat Enterprise "server" and i'm trying to install some additional programs as Dansguardian, Squid and so on...
 The problem comes when i write apt-get install ..., the system doesn't recognize this command "apt" 
there is a command to install?
Please can you help me.

Muhamad


:guitar:

---

### Post by Barrucadu on 2008-06-13
Redhat does not use the Debian package management system, and so apt won't work.

---

### Post by jjgomera on 2008-06-13
the redhat equivalente to apt-get is yum, so is you want to install squid:
yum install squid

---

