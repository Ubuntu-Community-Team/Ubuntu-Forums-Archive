---
title: "Linux Noob Setting Up UbuntuStudio HELP!"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by badbrainz75 on 2008-01-28
I'm an utter noob with Linux in any form, but I'm very computer savvy.  With that out of the way, here's my situation:

I'm a musician trying to setup a dedicated PC to serve as a DAW (digital audio workstation) using UbuntuStudio.  Namely, I am intrigued with using Ardour to do multitrack recordings as it comes highly recommended and saves me around $1000 for software.

I have gotten UbuntuStudio 7.10 installed on a PC I cobbled together from older parts.  7.10 seems to work fine as I can browse the web with Firefox, etc.  If Ardour shows promise, I'll certainly upgrade the parts appropriately, but for now I just want to see if this will even work.  Currently the machine is a Celeron 850 with 512MB RAM and onboard video.  I would like to use my Presonus Firepod recording interface with the machine, and I've installed a PCI firewire card to accommodate this.  

Here's where things get tricky (for me). From what I read, it looks like I need to install a driver package called FreeBob for firewire to even function on the machine.  Is this correct? And if so, can someone point me to a noob-friendly guide to installing it?  From there, it appears that the JACK application will use the FreeBob driver to communicate with my Firepod, but I can't even get to that point at the moment because i can't figure out how to install FreeBob.

Thanks for any help you guys can offer, and for your infinite patience in dealing with us recent Linux converts.

W.

---

### Post by emarkd on 2008-01-28
I know nothing of what you're talking about, but FreeBob has these instructions on its page:

[http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux](http://freebob.sourceforge.net/index.php/FreeBoB_on_Debian_GNU/Linux)

Tow small changes.  Ubuntu doesn't have a root login, so everywhere that those instructions tell you to use root, you'll have to preface the command with sudo.  Like this:

```
sudo apt-get install ....
```

Also, Ubuntu supports firewire out of the box, so you can skip the first section and start at the "Installing" heading.

---

### Post by badbrainz75 on 2008-01-28
Thanks.  I assume these commands are typed in the Terminal window?

W.

---

### Post by emarkd on 2008-01-28
yup.  Applications > Accessories > Terminal

---

