---
title: "Installing pptpconfig on Ubuntu"
date: 2005-05-03
forum: Apple PPC Users
---

### Post by grunk999 on 2005-05-03
Hi!

First of all: I'm a total noob at Linux - so please be gentle with me!

I've just installed Ubuntu 5.04 on my PowerBook. Everything works fine so far - but i can't seem to get a VPN connection to my workplace. I found out that a program called pptp (cleverly enough) exists - but since i couldn't figure out how to use the commandline version, i tried installing the GUI; pptpconfig.

I added [http://quozl.netrek.org/pptp/pptpconfig/](http://quozl.netrek.org/pptp/pptpconfig/) to my repositories - but when i try to install it via the Synaptic Package Manager, i'm told that some dependencies isn't met:

pptpconfig:
 Depends: php-pcntl (>=4.3.7) but it is not installable
 Depends: php-gtk-pcntl (>=1.0.0) but it is not installable

I'v tried figuring out how to get these packages installed, but with no luck! (Perhaps from source?)

Have anyone gotten pptpconfig to work on a PPC-based Ubuntu system? If you have, i would be extreemly grateful if u could drop me a hint on how!

Thanks,
/Joachim

BTW: I am VERY impressed with how integrated at smooth the installation progress was! Nice work!  :)

---

### Post by xristos on 2005-05-04
I have the exact same problem , but with no solution . sorry .
Waiting for a solution......

Try this [http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)

---

### Post by exile on 2005-05-13
[QUOTE=xristos]I have the exact same problem , but with no solution . sorry .
Waiting for a solution......

Try this [http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)[/QUOTE]
 add the following to your repository.

deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) pptpconfig/
deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) php-gtk/

sudo apt-get update
sudo apt-get install pptpconfig

For kubuntu users you might want to edit
/usr/share/applications/pptpconfig.desktop
and put the category in internet otherwise it will be in lost and found.

---

### Post by alistair77 on 2006-05-12
[QUOTE=exile]add the following to your repository.

deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) pptpconfig/
deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) php-gtk/

sudo apt-get update
sudo apt-get install pptpconfig

For kubuntu users you might want to edit
/usr/share/applications/pptpconfig.desktop
and put the category in internet otherwise it will be in lost and found.[/QUOTE]


DIdn't work for me.    libglade0 is required.

---

### Post by lichtgestalt on 2006-08-25
well first the page was reachable from time to time now it seems to be completly offline - took me one hour to find out the new changed site:
old:
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./
correct:
deb [http://quozl.linux.org.au/pptp/pptpconfig](http://quozl.linux.org.au/pptp/pptpconfig) ./

Hope i could help ya

---

### Post by Geoff2077 on 2006-08-26
I got around this by selecting the repository - Community maintained Universe (BIN) - this is not enabled by default.
System/Admin../Software Properties

Cheers

---

### Post by thushw on 2007-10-10
Yes - I got this to work by enabling universe and using this on my /etc/apt/sources.list:

deb [http://quozl.linux.org.au/pptp/pptpconfig](http://quozl.linux.org.au/pptp/pptpconfig) ./

i removed all others relating to [http://quozl.netrek.org](http://quozl.netrek.org)

with that, there were no errors shown on subsequent install steps, and pptpconfig was correctly installed.

I had to meddle a bit with the tunnel settings to get it to connect. Under 'Encryption' tab in pptpconfig, I enabled the following:

Require Microsoft Point-to-Point Encryption (MPPE)
Refuse 128-bit Encryption
Refuse Stateless Encryption
Refuse to Authenticate with EAP

On the 'Routing' tab, I had to add a route (using Edit Network Routes) to the office network. Since it has a 192.168.10.0 address, I used the following:

Network: 192.168.10.0/24
Name: whatever

I could then successfully start and access hosts within the office network.

I documented a bit more detail here: 

[http://paraviya.blogspot.com/2007/10/vpn-to-pptp-network-from-ubuntu-feisty.html]("http://paraviya.blogspot.com/2007/10/vpn-to-pptp-network-from-ubuntu-feisty.html")

---

