---
title: "Ewmote Desktop"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-22
Hi

I am trying to use remote desktop, i have just install a fresh copy of kubuntu and it seems that the terminal server client is mising. Any ideas anyone what the app is called? I have tried running krdc but this does not allow me to establish a connection but only configure the settings.

I am wondering do i need samba installed for it to run? I know it was there on my last install of kubuntu cos i used it !!! going everso slightly mad so any help would be appreciated.

Vheers
niteblind

---

### Post by Zikes on 2006-06-22
I've not messed with remote desktops on Linux, but I keep hearing that SSH and PuTTY are a good combination to use.

---

### Post by niteblind on 2006-06-22
not really what i am after ssh and putty only give command line access AFAIK. I need to be able to access my sisters XP machine running winvnc/remote desktop.

The option was in the start up list the last time I installed but i amd wondering if i added somehting in from the repositories but if so i cannot remember what it was!!!

---

### Post by Zikes on 2006-06-22
Hmm, I'm not at a Linux machine right now so I can't check, but you might try opening Synaptic and doing a search for "remote desktop."  Hopefully that'll pull up what you're looking for :)

---

### Post by mlind on 2006-06-22
You probably want vnc or ssh with X11 forwarding.
freenx and tightvnc are both good, and ultravnc is nice for windows

---

### Post by niteblind on 2006-06-22
daft question what is x11 forwarding? also would vnc be able to access a windows remote desktop session using RDP?

---

### Post by tronica on 2006-06-22
i use terminal server client (TSC), and its allready installed. it handles vnc and RDP.

---

### Post by mlind on 2006-06-22
[QUOTE=niteblind]daft question what is x11 forwarding? also would vnc be able to access a windows remote desktop session using RDP?[/QUOTE]

ssh's X11 forwarding allows you to connect remote x-server through secure ssh tunnel.
Quick google lookup found a gentoo article which should help you get the picture 
[http://gentoo-wiki.com/HOWTO_X-forwarding](http://gentoo-wiki.com/HOWTO_X-forwarding).

I dunno know about RDP stuff, but what freenx doesn't support, it's not necessary ;)
I guess you should check out their faq or manual about that.

You can run tightvnc or ultranvc server on windows machine and connect from Ubuntu
using vlc client. It just works! :)

At least tightvnc -server be run locally without running any installers on windows.
Ultravnc performs much better and faster though.

---

### Post by niteblind on 2006-06-22
thanks for all the help mlind.

As it turns out i must have installed tsclient which although states is a GNOME frontend loads fine in KDE.

I will admit as a new ubuntu user i am findinng this whole applications lark a little perpexing nevermind tho the important thing is i can fix my sisters pc without having to leave the house again!!!!! :P

niteblind

---

