---
title: "Ethernet Card doesn't respond"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by cmbnd10 on 2008-01-17
I am a beginner running Fluxbuntu and I have just installed a Ethernet PCI Card and it will not respond. Everytime I think I get closer, it tells me i may not have the administrative ability to do anything. I just built the computer from  3 computers total and fluxbuntu has been okay other than this.

---

### Post by Hospadar on 2008-01-17
to get admin privileges, you need to preface your commands with "sudo" this will run commands as root (administrator).  Like let's say you wanted to edit your /etc/network/interfaces file, it's a text file that controls networks, and it's not editable by normal users.  first, bring up a terminal (Applications->Accessories in reg ubuntu, not sure where in fluxbuntu, but probably somewhere similar) and type "sudo <text editor of your choice, eg. gedit or nano> /etc/network/interfaces" or if you wanted to do an ifup to start a connection, it might go something like "sudo ifup eth0"

---

### Post by cmbnd10 on 2008-01-17
> **Hospadar said:**
> to get admin privileges, you need to preface your commands with "sudo" this will run commands as root (administrator).  Like let's say you wanted to edit your /etc/network/interfaces file, it's a text file that controls networks, and it's not editable by normal users.  first, bring up a terminal (Applications->Accessories in reg ubuntu, not sure where in fluxbuntu, but probably somewhere similar) and type "sudo <text editor of your choice, eg. gedit or nano> /etc/network/interfaces" or if you wanted to do an ifup to start a connection, it might go something like "sudo ifup eth0"

I have been usint sudo. I typed in the "sudo ifup eth0" and it says "Ignoring Unknown Interface eth0-eth0."

I have the windows drivers disk. Is there a way to use that? What else can I do to make it work? One light comes on and the other does not. I am assuming that means that there is no traffic going through, but it does read that something is in that slot.

---

### Post by cmbnd10 on 2008-01-17
bump

---

### Post by cmbnd10 on 2008-01-17
Okay, something that I think that was positive happened.

I typed in "sudo ifconfig" then I put in my password and this came up:

Link encap: Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:240 errors:0 dropped:0 overruns:0 frame:0
TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:18160 (17.7KB) TX bytes:18160 (17.7KB)

Then the next command line begins.


PLEASE HELP

---

