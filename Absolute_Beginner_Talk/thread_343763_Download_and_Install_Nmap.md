---
title: "Download and Install Nmap"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by ggj13557 on 2007-01-21
I am trying to download and install nmap from:

[http://packages.debian.org/stable/net/nmap.html](http://packages.debian.org/stable/net/nmap.html)

However,I'm not sure what to download from the above link.  I tried downloading several of the packages under "Download NMAP" but I haven't had any success.  What Architecture should I download.  I've tried "alpha", "i386", etc and try to "Open with" the GDebi Package Installer.  The file downloads fine but the package installer window gives "Error: Wrong Architecture 'i386'".

I'm using ubuntu 6.06 on a dell laptop...what is the correct Architecture to download?

As you can tell, I'm very new to ubuntu and would appreciat any help available.  Thanks in advance!

---

### Post by OMRebel on 2007-01-21
You should just Synaptic to download it.  Go to System -> Administration -> Synaptic Package Manager.  Do a search for NMAP, and you should see it listed there.  Just check it to install and then select Apply.

---

### Post by CroEragon on 2007-01-21
nmap is installed by default in ubuntu. I dont know about dapper but on edgy it is. To check type "nmap" in terminal.
You should get some sort of help output

---

### Post by Mba7eth on 2007-01-22
> nmap is installed by default in ubuntu. I dont know about dapper but on edgy it is. To check type "nmap" in terminal.
You should get some sort of help output
I don't agree with you on that :) . I have reinstall my ubntu a week ago and no sign for nmap. 
Anyhow, ggj13557 :
 just enter the following command 
     $sudo apt-get install nmap
if you have problems you have to update source.list by 
$sudo gedit /etc/apt/source.list 
remove every # from a non comment line 

Cheers, 
       Mba7eth

---

