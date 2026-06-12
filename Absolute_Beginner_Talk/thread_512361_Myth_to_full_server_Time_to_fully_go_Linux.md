---
title: "Myth to full server? Time to fully go Linux"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by drifting on 2007-07-29
Need some advice.

I have been happily running Myth backend on a new dedicated machine, it's and AMD dual core and 4GB of memory, with shed loads of SATA disk space. OS is Ubuntu Feisty Workstation AMD 64bit.

Now I know this is hardly a beginners question, but I consider myself still very much a newbie, and spend hours trolling through docs to do the most basic things I do under windows server in seconds (Not a complaint)

I now want to retire my old Microsoft SBS server, which has been doing DNS, DHCP, email and proxy. What I want to know is if it's possible to install all the other services into Ubuntu? I know they can be installed, but what will they break in the process?

Am I just better re installing Ubuntu Server? as I assume these all come included preconfigured? I would like to keep the desktop if possible for those times that I cannot remember / find the right command line command.

Just a thought, i have already installed Apache for Mythweb and Webmin.

Any help or suggestions most welcome.

Paul.

---

### Post by cmnorton on 2007-07-29
I don't know about proxy, but you should have no trouble downloading and configuring DHCP, DNS, and sendmail. The only thing I had to go outside of Ubuntu's repositories was for the pptpconfig client, and I was easily able to add that repository in the Synaptic Package Manager.

We're in the process of spec'ing out new hardware for our Linux-based tax collection system, and I plan to rebuilt that as an Ubuntu server. It's currently running Red Hat 9. 

This is a big deal to us, because we have "forms" applications which rely on inside-firewall telnet clients and a customized termcap, and Informix SE. I was able to port this application in under a day over to Ubuntu on an old Acer desktop P IV and 512 MB ram. The db engine and tools installed fine with one small glitch on command line options for cpio. All in all, Ubuntu has been the easiest to configure of the rpm or debian flavours I have used.

---

### Post by drifting on 2007-08-02
Thanks Charles.

Taking a few days out of work to get this underway. thanks for the re assurance.

Paul.

---

