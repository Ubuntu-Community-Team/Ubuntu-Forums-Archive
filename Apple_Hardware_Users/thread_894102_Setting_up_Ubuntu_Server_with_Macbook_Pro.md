---
title: "Setting up Ubuntu Server with Macbook Pro"
date: 2008-08-18
forum: Apple Hardware Users
---

### Post by devinloretz on 2008-08-18
I have a windows PC and my HD failed just the other day. No worries I didn't need anything there. So I just bought a new HD and someone told me I could set up a server for my photos. I am a photographer.

I am such a noob with Ubuntu or Linux is general. I downloaded the Ubuntu Server Edition ISO image and burned it to a CD and now I am running through the installation process......


I have no clue what I am doing.

I want to use this as just a local server for photo storage and also music storage. I don't need to have anything web based and pretty much just something that will be sitting right next to my laptop. I wont always be connected to it though since I travel with my MBP alot for work. 

I temporarily skipped the network configuration because I am not sure what I am doing. And I am sitting at the Software selection screen. DNS server, LAMP server, Mail server, OpenSSH server, PostgreSQL database, Print server, Samba file server. I don't know what I need. 


Please please please I am hoping someone can help me with this setup and get everything working =]

---

### Post by arranmc182 on 2008-08-18
use Samba file server i tend to use the standard Linux distro and setup samba from there via the GUI if u google about Samba file server or Samba Ubuntu u should find what u are looking for and u will find it nice to have a small file server because when its fully setup up u dont need a monitor mouse or keybaord plunged in as it will be remotely controlled over the network only thing about Samba is that Vista is a ******* bitch with it and does not work out of the box with Samba as XP did

---

### Post by devinloretz on 2008-08-18
how wil it work with Mac OSX? 

what do you mean by you use the standard Linux distro? Just the Ubuntu desktop version or something else?

---

### Post by cyberdork33 on 2008-08-19
Ok. First, this is a bit out of place, as it really doesn't matter that you are trying to share with Macs... you need support for installing on a normal PC.

If you ONLY want to make a fileserver from the PC and not use it for anything else, I suggest something like FreeNAS. This is a distribution that is made specifically for creating a fileserver. It is a bit more cumbersome, but you can find tutorials on setting up shares that make it pretty easy. Installing the server edition of ubuntu will leave you with a sommandline-only linux system, and if you are new with linux that can be very daunting. FreeNAS will do the same, but you access the configuration and such via webbrowser over the network.
[http://www.google.com/search?q=freenas+install+video](http://www.google.com/search?q=freenas+install+video)

If you want to continue with Ubuntu, that is fine, but since you are quite new to linux, I would not use the server install unless you are willing to jump into the commandline, and instead opt for the normal desktop installation, and setup your shares from a normal windowing system (Gnome). (This is what he meant by the "standard" version, I think)

Next you will want to determine what filesharing method you want to setup on your fileserver. Windows sharing is samba, Unix sharing is NFS (This is supported by OSX too, since OSX is UNIX), and you can also try netatalk which is similar to Appletalk. I would research these things a bit and see what is right for you. Samba will probably be the easiest of these to setup and use.
[http://us3.samba.org/samba/](http://us3.samba.org/samba/)
[http://en.wikipedia.org/wiki/Network_File_System_(protocol]("http://en.wikipedia.org/wiki/Network_File_System_%28protocol"))
[http://netatalk.sourceforge.net/](http://netatalk.sourceforge.net/)

Additionally, if you would just like to play with / test some linux distros, you can use a VM on your Mac that will run quite well. VirtualBox is free, and should allow you to run Ubuntu as well as other distros in a Virtual machine on your Mac. Once you have confidence with what you want, you can install on your main machine.

---

### Post by billmunson1 on 2008-09-22
> **cyberdork33 said:**
> Ok. First, this is a bit out of place, as it really doesn't matter that you are trying to share with Macs... you need support for installing on a normal PC.

If you ONLY want to make a fileserver from the PC and not use it for anything else, I suggest something like FreeNAS. This is a distribution that is made specifically for creating a fileserver. It is a bit more cumbersome, but you can find tutorials on setting up shares that make it pretty easy. Installing the server edition of ubuntu will leave you with a sommandline-only linux system, and if you are new with linux that can be very daunting. FreeNAS will do the same, but you access the configuration and such via webbrowser over the network.
[http://www.google.com/search?q=freenas+install+video](http://www.google.com/search?q=freenas+install+video)

If you want to continue with Ubuntu, that is fine, but since you are quite new to linux, I would not use the server install unless you are willing to jump into the commandline, and instead opt for the normal desktop installation, and setup your shares from a normal windowing system (Gnome). (This is what he meant by the "standard" version, I think)

Next you will want to determine what filesharing method you want to setup on your fileserver. Windows sharing is samba, Unix sharing is NFS (This is supported by OSX too, since OSX is UNIX), and you can also try netatalk which is similar to Appletalk. I would research these things a bit and see what is right for you. Samba will probably be the easiest of these to setup and use.
[http://us3.samba.org/samba/](http://us3.samba.org/samba/)
[http://en.wikipedia.org/wiki/Network_File_System_(protocol]("http://en.wikipedia.org/wiki/Network_File_System_%28protocol"))
[http://netatalk.sourceforge.net/](http://netatalk.sourceforge.net/)

Additionally, if you would just like to play with / test some linux distros, you can use a VM on your Mac that will run quite well. VirtualBox is free, and should allow you to run Ubuntu as well as other distros in a Virtual machine on your Mac. Once you have confidence with what you want, you can install on your main machine.
Hello.  I'm also new.  I'm running a macbook 2.2 ghz on 10.5 and I installed virtualbox fine.  I downloaded ubuntu 8.04 and am only able to boot from the live cd after I burned it.  Is there a way that I don't have to boot from the cd everytime?  From my hard drive would be great.

Thanks in advance, Bill.

---

### Post by cyberdork33 on 2008-09-22
> **billmunson1 said:**
> Hello.  I'm also new.  I'm running a macbook 2.2 ghz on 10.5 and I installed virtualbox fine.  I downloaded ubuntu 8.04 and am only able to boot from the live cd after I burned it.  Is there a way that I don't have to boot from the cd everytime?  From my hard drive would be great.

Thanks in advance, Bill.
If you are planning to setup Ubuntu in VirtualBox, you need to boot the iso / CD in the Virtual Machine. You can set the VM to boot from an iso in the VM configuration. If you are trying to dual-boot your Mac with Ubuntu, VirtualBox is not needed. See the "Before You Post" link in my signature to find instructions for doing a dual-boot install.

P.S. If you need more help, please make a new thread as your issue is not really related to this persons issue.

---

