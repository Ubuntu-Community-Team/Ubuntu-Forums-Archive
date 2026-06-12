---
title: "Wireless Problem Unless Restarted After Login"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by canclan on 2007-03-10
Hello!
First, I would like to say that I love the support that Ubuntu has and the work that the community puts into helping those in need!  Also, I am very impressed with Ubuntu and its ease of use!  My only previous experience (minimal though it was) was with Mandrake and I ended up leaving it!

So now to my problem.  I have Edgy (dual boot with wnidoze) on a Dell C610 with a 2915abg mini-pci wireless card.  I have a Netgear FWAG114 router using WPA-PSK.  I am usingthe latest Network Manger, WPA Supplicant, and now even the Pam Keyring package.  After spending about 50 hours (!) on trying to get the dell to hookup to the router wirelessly ( and learning a great deal about ubuntu/debian in the process!),  I have finally managed to hook up - but *only if* I go to terminal, and type:

```
sudo /etc/init.d/networking restart
```

and then

```
sudo /etc/init.d/dbus restart
```

in that order.  If I do not type that, I will end up connecting to a wireless router near my house which has no security at all.  Furthermore, before I type the above,  the only router I can see in the list is the open one.  After I type it, I see all the neighbourhood routers (including my own).  More info/outputs are available upon request.

My question is:  does anyone know what the heck is going on?

Thank you in advance for any and all assistance!

PS  Has anyone successfully gotten a 2915abg to hook up to a 802.11a network?  I can not find any documentation on it.


Edit:  Sorry!  I meant to post in Networking!

---

### Post by SactoBob on 2007-03-14
Unless you are dedicated to setting things up from the command line, you could install the network-manager-gnome from the repository.  It is a painless way to set up your connections.  

Even if you fail with the n-m-g, you may get some valuable diagnostic info.  You can always remove it if you don't like it.

After you install it, you have an icon at the upper right of the screen.  Click on it, and select the connection you want.  It will store settings for a successful link.

---

