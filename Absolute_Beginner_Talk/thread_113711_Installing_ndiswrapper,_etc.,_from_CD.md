---
title: "Installing ndiswrapper, etc., from CD"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by mohapi on 2006-01-07
Sorry if this is a question that has been answered. I've been through the wiki and tried searching the forum, but no luck.

I'm using UbuntuLite on an old machine, and while I had tremendous success installing it, I've hit a series of walls trying to get the PCMCIA wireless to work.

I don't think UbuntuLite comes with ndiswrapper, which I need (I think) to get my WPC54G working.

Naturally, without an Internet connection, I can't 'get' it straightaway. Bit of a conundrum. A catch-22, if you will. :confused: 

I can download the latest version -- ndiswrapper-1.7 -- and move it onto the machine via USB, but I can't seem to compile it because, again, I need more packages that weren't installed with UbuntuLite. A recursive catch-22. :cry: 

I have the standard 5.10 install CD (but I think UbuntuLite is built from 5.04). **Is it possible to install ndiswrapper off CD? **Can anyone describe how to do that?

Thanks again for your help. 

P.S.: As I mentioned, the wireless is a WPC54G. The machine is a CTX EzBook 700E ... K6-2 475Mhz/128MB/2GB.

---

### Post by racecat on 2006-01-07
A bit of an educated guess, but if you'll look at your sources.list:

```
sudo gedit /etc/apt/sources.list
```

the first line points to the cd. If you can edit that for the cd you have (including date/release code), you should be able to pull it off with Synaptic. I'm not really familiar with the lite version,  but I assume it has the same basic functions. Don't know what the implications are as to compatability between releases. Worth a try - worst case - you have to reload. But that's me.

You should first backup your sources.list:

```
cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Sorry I couldn't be more specific, but hopefully this will point you in the right direction.

Bill

---

### Post by bluefrog on 2006-01-07
ndiswrapper is on the install cd

james

---

### Post by mohapi on 2006-01-07
[QUOTE=bluefrog]ndiswrapper is on the install cd

james[/QUOTE]

Yes, I know it's there, but I want to find a way to point the "sudo apt-get" (or whatever) command at it, so I can install it under UbuntuLite. I thought perhaps there was a way to key the command to follow a route to the CD, rather than the Internet.

My other concern was compatibility between 5.04 and 5.10, which I don't think would be a problem.

---

