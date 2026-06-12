---
title: "fresh install rebooting"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by mijutras on 2007-09-03
Hi,
I did a fresh install of 7.04 server. Installation was successful except that it could not find the NIC but I guess I can worry about this later.
During boot from HDD I get:
GRUB Loading stage1.5
ESC for menu
Startup
And the server reboots.

Based on other posts I've seen, I tried booting in recovery mode with the CD and when at the prompt did apt-get remove linux-server and apt-get install linux-386.
On apt-get install linux-386 it could not find the package.
I tried linux-image-386 (same problem)
I tried linux-image-generic and this installed something.
However, I still have the same reboot problem.

I have an old Pentium 233MMX with 15Gb HDD and 128Mb RAM

Thanks for your help

Mike

---

### Post by ddrichardson on 2007-09-03
I can't be sure but that's a very small memory footprint for an Ubuntu server.  You may have to consider a distribution designed for a smaller footprint.

That said, I don't know if the server version uses the same repos but its linux-image-386. If you have no network connection how are you getting on line to do apt-get?

---

### Post by mijutras on 2007-09-03
This is obviously a starting point for me and this server, I am new to Linux and I was told that Linux is efficient with little ressources.
I will upgrade the RAM to the max once I get going.

Based on your last coment, I thaught apt-get was to install from CD only so I guess if I make it a priority to have my NIC going, I suppose when I do apt-get install linux-image-386 it will find it and my problem will be resolved...
My fingers are crossed and I'm working on it.

Thanks

---

### Post by ddrichardson on 2007-09-03
I can't be sure of this but don't think the install CD has the full repo, although you can install from a cd using apt-get.

Linux is much less bloated for server use, but its a very small footprint and depends on what you want it to do. As a rule of thumb, more memory in servers generally improves response more than other factors.

Try looking a round for lightweight distros like DSL, which I have on a 200 MHz machine with 32 Mb and runs fine. Like I say it depends on the requirements for your server.

---

### Post by mijutras on 2007-09-03
I want to install Spamassassin on this server, this will be its only role as I am running Web and Mail servers on Windows 2K3.

Based on what I have read, although they offer a Windows version of Spamassassin, it runs better on Linux and at the same time its a good reason for me to enter the Linux world.
Only problem I have is... sooo many versions, sooo many ways to proceed and it looks like there is not one version better than the other!

---

### Post by ddrichardson on 2007-09-03
You could do that with damn small linux.

---

