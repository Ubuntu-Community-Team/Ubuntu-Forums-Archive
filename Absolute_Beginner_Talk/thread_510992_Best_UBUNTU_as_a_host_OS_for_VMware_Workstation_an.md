---
title: "Best UBUNTU as a host OS for VMware Workstation and VMware Server?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by marmaj on 2007-07-27
Hello all!

I am in the process of researching the following concept (it will turn into a build when I have all of  my questions answered) :)

 Hardware:  HP Pavilion dv8000 laptop with AMD Turion64 2.4 GHz CPU, 2 GB RAM, ATI MOBILITY RADEON XPRESS 200M Series with 128 MB RAM, two 100 GB drives

OS / Software environment:

- UBUNTU 64 as the only boot - I would like this to be static as I will use it only to boot up the laptop

A) VMware Workstation with two "guest” virtual machines:
1.  UBUNTU 64 desktop as one of the virtual machines (in VMware terms this is a guest OS for the VMware Workstation)
2.  WIN XP Pro (32) as one of the virtual machines (in VMware terms this is a guest OS for the VMware Workstation)

B) VMware Server with three "guest" virtual machines:
1. Solaris x86 10 in a 64 bit mode as one of the virtual machines (in VMware terms this is a guest OS for the VMware Server)
2. UBUNTU Server 64 (in VMware terms this is a guest OS for the VMware Server)
3. Windows 2003 server 64 (in VMware terms this is a guest OS for the VMware Server)

**My question is this:**

Which of the UBUNTU builds should I use for the main boot OS?

1.  UBUNTU workstation?
2.  UBUNTU server?
3.  or, perhaps, XUBUNTU?

Please keep in mind that I do not intend to us the main boot OS for anything other that booting the laptop and loading VMware Workstation and VMware Server.  All of user work will be performed within the virtual machines.

I keep on reading that XUBUNTU is the least hardware resources hungry, so it seems that it is the best choice, but before I devote a week or so of my time to pursue this route, I would like to hear what you have to say.

I appreciate your time and welcome all comments!

Best regards,

-mm-

---

### Post by dca on 2007-07-27
I use 6.06LTS Server Ed.  Then I install 'ubuntu-desktop' (sudo apt-get install ubuntu-desktop) and then I install either VMWare or Virtual Box.  I've found both to be about equal...  I think there's still a good how-to on newsforge.net...

---

### Post by yota on 2007-07-27
Hi,

just one question: are you going to use the virtualmachines locally or remotely?

If you plan to use them remotely you can run vmware server without X, to save some ram, and then the difference between ubuntu server, desktop or xubuntu is not relevant.
Instead, if you plan to use them locally... why wmware server?

In general my pick would go to xubuntu, since it's more lightweight.

Hope this helps!

---

### Post by marmaj on 2007-07-27
> **yota said:**
> Hi,

just one question: are you going to use the virtualmachines locally or remotely?

If you plan to use them remotely you can run vmware server without X, to save some ram, and then the difference between ubuntu server, desktop or xubuntu is not relevant.
Instead, if you plan to use them locally... why wmware server?

In general my pick would go to xubuntu, since it's more lightweight.

Hope this helps!

Thanks for your reply!

1.  I will use the VMs off of VMWorkstation locally, and the VMs off of VMServer remotely.

2.  VMware Server without X?  Are you referring to VMWare ESX?

3.  VMware Server because my understanding is that you can not run guest OS which are server OS (i.e. Windows 2003) off of VMware Workstation.

-mm-

---

### Post by yota on 2007-07-27
> **marmaj said:**
> Thanks for your reply!

3.  VMware Server because my understanding is that you can not run guest OS which are server OS (i.e. Windows 2003) off of VMware Workstation.

-mm-

Mhh... not exactly: wmware workstation is meant to host virtual machines on a workstation (the display is hooked to the real display with better performance), while vmware server is meant to serve machines to used remotely (the display is virtualized and can be seen remotely using the vmware server console; more flexibility, less performance); the distinction does not refer to the operating systems you are going to install inside the VMs.

Since vmware server has no local display (although one can run the console locally too), it can be installed in a command line environment:
> 
Well - in fact one doesn't need full x-window-system at all (!!!!). Only needed packages are:

    * linux-kernel-headers-`uname -r`
    * libc6-dev
    * gcc
    * make
    * psmisc
    * x11-common
    * libxau6
    * libxdmcp6
    * libx11-data
    * libx11-6
    * libxrender1
    * libice6
    * libxext6
    * libxtst6
    * libsm6
    * libxt6
    * libxi6

These are small X-related libs - no full X environment is needed. Last lib - libxi6 is only needed to install MUI - pure VMware Server works without it. Of course I only listed packages not present in "default" task-sel. One also need perl, binutils...

List of libriares may be obtained by typing `sudo ./vmware-install.pl` in vmware-server-distrib directory. Installer looks for specific libs and shows info which are not found. Just apt-get install them. The only one not listed is libxi6 - needed only in order to get MUI working. 

(from [http://www.howtoforge.com/debian_etch_vmware_server_howto](http://www.howtoforge.com/debian_etch_vmware_server_howto) )

As a bottom line, what about xubuntu + vmware workstation for all your virtual machines (both servers and desktops)? Maybe vmware server totally is uneeded here.

---

### Post by nickburns on 2007-07-27
Just add (to sources.list)

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

and sudo apt-get install vmware-server 

Then the dependency on X packages is taken care of.


I have several MS server 2003 versions running on the same box. So it is possible.

---

### Post by marmaj on 2007-07-27
> **yota said:**
> Mhh... not exactly: wmware workstation is meant to host virtual machines on a workstation (the display is hooked to the real display with better performance), while vmware server is meant to serve machines to used remotely (the display is virtualized and can be seen remotely using the vmware server console; more flexibility, less performance); the distinction does not refer to the operating systems you are going to install inside the VMs.

As a bottom line, what about xubuntu + vmware workstation for all your virtual machines (both servers and desktops)? Maybe vmware server totally is uneeded here.

Excellent point - thanks a lot.

If I can simplify the environment and NOT run VMware Server but have all FIVE host OS under VMware Workstation - the better!

Thanks again!

-mm-

---

