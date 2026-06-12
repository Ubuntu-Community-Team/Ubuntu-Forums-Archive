---
title: "Getting at folder on Desktop"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by soho2014 on 2007-05-06
I have a problem in that I have no internet access.  I know that it is because I'm using a broadcom 4303 PCI wireless card, and I need to tell Ubuntu about it.

I wanted to use something called fwcutter to suck the firmware out of the card for ubuntu.  I downloaded this using my mac.  Using my USB memory stick, I was able to transfer it and unpack it onto my desktop.

There is sits in a folder on my desktop, but I don't know how to tell the command line interface to install it.  When I type: ls to see the folder, it doesn't show that folder.  Can anyone tell me the secret to install this from here.  Remember I have no internet access on this linux machine until I can get this card working.

I'd be willing to buy another card of there is one that works right out of the box.

---

### Post by aysiu on 2007-05-06
Well, assuming it's a .deb file you downloaded, you'd type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sudo dpkg -i *fwcutter*.deb
``` Otherwise, just look at your desktop (Control-Alt-D) and double-click the .deb file sitting there.

Was it here you go the *fwcutter* file from?
[http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter)

---

