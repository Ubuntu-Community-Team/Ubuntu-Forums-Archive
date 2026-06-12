---
title: "Avahi primer"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by carpetn on 2007-06-21
Where can I find out in plain English what avahi is, what it does on my computer, and how one uses it? All the sites I look at simply make reference to other equally unfamiliar kinds of programs and don't give an answer to these basic questions.

There seem to be zillions of posts and articles about it not working right with Feisty Fawn, but nothing that answers my questions about what it is and how one uses it. 

All I can figure out is that it has something to do with making services available on a network. This sounds like it is opening up my computer to hacking. 

Thanks.

Carpetn

---

### Post by jfinkels on 2007-06-22
> **carpetn said:**
> Where can I find out in plain English what avahi is, what it does on my computer, and how one uses it? All the sites I look at simply make reference to other equally unfamiliar kinds of programs and don't give an answer to these basic questions.

There seem to be zillions of posts and articles about it not working right with Feisty Fawn, but nothing that answers my questions about what it is and how one uses it. 

All I can figure out is that it has something to do with making services available on a network. This sounds like it is opening up my computer to hacking. 

Thanks.

Carpetn

I'm no expert, but avahi is a system of programs which run as background processes ("daemons") and allow your computer to communicate with daemons running on other computers on your local network, if they are using the same protocol. Avahi is a "service discovery" (i.e. a daemon discovery) application, so it will be able to recognize services (aka daemons) running on other computers in your network. A program (like Pidgin or Rhythmbox) may be able to use information from Avahi to get information on services running on other computers so that you may communicate with them (i.e. chat with 'Bonjour', view Shared iTunes Libraries).

Try reading the man pages, type this in the terminal:```
man avahi-daemon
```

Or see here: [http://www.die.net/doc/linux/man/man8/avahi-daemon.8.html](http://www.die.net/doc/linux/man/man8/avahi-daemon.8.html)

---

### Post by carpetn on 2007-06-22
Thanks, jfinkels. Your answer helps a bit, but not enough. (I posted here because this program seems to be something new with Ubuntu--I've never seen it on any other Linux distro I've used.The avahi site is not helpful either as a primer for someone who doesn't know what it is or how it's used in the first place.) 

Maybe someone else can add more. For example, when I look at the man page, it's incomprehensible to me and I don't see anything that tells me how to USE avahi. How do I know if this daemon has recognized services somewhere?

The man avahi-daemon page starts out: 
"The Avahi mDNS/DNS-SD daemon implementing Apple's ZeroConf architecture (also known as "Rendezvous" or "Bonjour"). The daemon registers local IP addresses and static services using mDNS/DNS-SD and provides two IPC APIs for local programs to make use of the mDNS record cache the avahi-daemon maintains."

For example, the man page doesn't tell me what mDNS/DNS-SD is, etc. And, referring to jfinkel's reply, I don't know what Pidgin and Rhythmbox are, so why would I want something running that "helps" them?  My wife is using an iBook, but I don't see avahi telling me anything about what's on her machine (e.g., Bonjour). 

Basically, what I need to know is, why should I have this running on my computer? Is it just using up RAM and processor capacity? Is it a security risk? HOW DO I TURN IT OFF?

Thanks.

carpetn

---

### Post by jfinkels on 2007-06-22
> **carpetn said:**
> For example, the man page doesn't tell me what mDNS/DNS-SD is, etc.[http://en.wikipedia.org/wiki/MDNS](http://en.wikipedia.org/wiki/MDNS)> And, referring to jfinkel's reply, I don't know what Pidgin and Rhythmbox are, so why would I want something running that "helps" them?Pidgin is an instant messenger application which supports several instant messaging protocols, including AIM, Yahoo, MSN, and Jabber, and Rhythmbox is the GNOME default media library manager/audio player. They are both part of the basic install of Ubuntu, check in the menu under "Applications > Internet" and "Applications > Sound & Video", respectively. 

I think that the Avahi packages may be a requirement for viewing shared iTunes libraries and communicating via Bonjour, but I'm not certain. In any case, that's the reason you would want something running that "helps" them.

Avahi itself will not necessarily give you any messages about "Network service found" or something like that. It is a helper service (from what I understand). You need a different application (like Pidgin or whatever) to make use of its functionality.

I am not on Ubuntu right now, but there is a Panel Applet that you can add to your GNOME panel, it's called 'service-discovery-applet'. Install it like this:```
sudo aptitude install service-discovery-applet
``` and then right click on your panel and press "Add to panel..." and find it in the list. It will pop a little message when it (avahi) comes in contact with another service running on the local network.

If you want to turn on or off services, you can go to "System > Administration > Services". Or you can use ```
sudo /etc/init.d/servicename stop
``` for many of them. You can also replace 'stop' with 'start' or 'restart' if necessary.
> Basically, what I need to know is, why should I have this running on my computer? Is it just using up RAM and processor capacity? Is it a security risk? HOW DO I TURN IT OFF?If you don't need it and it bothers you, then uninstall it. You may find that certain packages are dependent upon it, however, as they may use its functionality. It is most likely using negligible amounts of processor power and RAM. You can check for yourself using ```
top
```

Any network service is potentially a security risk. Once you plug that CAT5 cable into your computer, you expose yourself to some risks, but most of the time, nothing bad will happen.

---

