---
title: "Need Network Manager to be active even if i don't login!"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by James79 on 2006-09-17
Using Ubuntu 6.06... my first linux install.

This is a frustratingly simple problem...

I finally got Network Manager to establish a connection to my AP using WPA... not using a static IP like I wanted; but its a start.

I rebooted the server, and to my horror realized that its network wasn't up while sitting at the login screen! I need this computer to be accessible without login in, as I intend to use it as a server in my closet, and hence will have no screen/keyboard/etc.

I hesitate to use automatic login as I find that's a rather crummy way to solve what I think should be a simple problem...

Another problem is that I get the famous "keyring" password prompt, which obviously for my needs is unacceptable. I've read that v0.6.3 fixes this problem (I currently use 0.6.2). I've tried:

apt-get install network-manager-gnome

but it claims I already have the latest version installed. I've thus far been unable to compile it manually :(

Being a newb is difficult sometimes ](*,)

Thanks for any insight people! 
~ James

---

### Post by jlsheehan on 2006-09-21
The Network Manager might not be the right tool for you to use.

If you turn it off or uninstall it and then manually put in your settings using the System > Administration > Networking tool then you can set it up with a static address etc, and it should come up during bootup.

It sounds like you are using a Ubuntu desktop version where you would noramally use the server version, but since you are new to it all you may as well stick with it since the GUI tools will probably be helpful.

Jeff

---

