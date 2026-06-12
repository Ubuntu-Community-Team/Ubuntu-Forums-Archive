---
title: "Getting 5.10 to be a SOCKS proxy"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by lovingboth on 2005-10-22
**What I have:** PC A is connected directly to the internet via DSL, PC B is connected directly via ethernet to PC A. Each sometimes runs Windows and sometimes Ubuntu 5.10. In any case, for the internal networking, PC A is 192.168.0.1 and PC B is 192.168.0.10

When A is using Windows, a small http and SOCKS proxy (AnalogX's *Proxy*) works wonderfully well for letting PC B access the internet via PC A.

**What I want:** PC B to access the internet via PC A when PC A is using Ubuntu.

Because it is working so well when PC A is on Windows, I want to keep using SOCKS. I am aware that there are other methods. I don't want to use them, OK?

**Where I am now:** Synaptic got but failed to install dante-server due to the following error:

[INDENT]Setting up dante-server (1.1.14-2) ...
Starting Dante SOCKS daemon: {time} danted[11443]: fixsettings(): no internal address given[/INDENT]

I have successfully used synaptic to get and install socks4-server 4.3.beta2-14ubuntu1 ... now what? 

/etc has socks.conf sockd.conf and sockd.route .. but no obvious documentation.

How do I set it up? TIA.

---

