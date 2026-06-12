---
title: "PLEASE HELP im a newb and cant connect to the internet"
date: 2007-03-20
forum: Apple PPC Users
---

### Post by versatilehearts on 2007-03-20
hi again!


just installed edgy on an iMac G3 and i tried connecting my cable modem directly to the computer with an ethernet cable. my provided uses DHCP and that is whats enabled in settings. im a total newb with terminal so i havent tried anything in there. the modem is connecting properly to my iBook and PC directly just dosent seem to work with the iMac.


PLEASE HELP

---

### Post by Auria on 2007-03-20
Not too sure about DHCP, but i got my modem working with 'sudo pppoe-conf' on the terminal and entering the info it asked me

---

### Post by seatea on 2007-03-20
I have a DSL modem, but it uses DHCP. If I don't have my modem on when I start  Ubuntu, I have to either re-boot or go  to the networking sub-menu under System(I  am not using Ubuntu at the moment and  cannot  remember exactly where under System the Network menu is,) and select ethernet in order to get my connection working. Also, make  sure that you don't have a firewall interfering. I  had some how done this  once and had to reset  firestarter.

---

### Post by ppc_guy on 2007-03-21
Hey welcome to the world of macs and linux.

 A few things off the top of my head..

 1. When you did your install, did you have the cable modem plugged in?
 2. And/if when you plugged the modem in if it was after the install did you reboot? 

 I ask because the first time I did the install on my g3/300's and ibook g3/900 I did not have ethernet plugged in during the install and nothing was seen until I did a plug and reboot.
 On one of the g3's I had to manually get the ethernet port set to communicate w/ the cable modem.. Search the forums for that one.. There are a few good help links..

h-t-h
nathan

---

### Post by tomos on 2007-03-21
Hi,

I know I got this from someone on this list, and it sure did the trick with my DHCP.  Open a terminal and enter:

sudo ifdown eth0
sudo ifup eth0


Hope this helps
tomos

---

