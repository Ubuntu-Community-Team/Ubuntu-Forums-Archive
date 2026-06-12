---
title: "Minimal install Edgy on 450mhz iMac G3"
date: 2008-02-17
forum: Apple PPC Users
---

### Post by Ge64 on 2008-02-17
Hi,

I got an old iMac G3 and I want to install ubuntu on it,  preferably very minimal. I don't need a desktop environment so I'd rather not install gnome, or any of the stuff that needs it like offie suite, games, synaptic, etc. I have the 6.10 alternate ppc iso, is there an easy way to keep it from installing this stuff?

---

### Post by stream303 on 2008-02-17
There are some great docs on how to do exactly that here, even though it looks like it is for PC's:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

For some reason though, I found that on my ppc install disks, the instructions to just specify "Install a command-line system" didn't work for me at the boot prompt - it took me all the way to a full gnome install anyway.   Maybe I missed something.

The workaround for me was to download and install a server version, and when prompted later in the process if I wanted a DNS or LAMP server setup, I just opted not to install either one.  Result was a very nice cli-system.

Repositories and whatnot were all autoconfigured for me at install.  Nice.

I could now proceed with the directions above to install a minimal gui desktop system that consisted of only a window manager etc.  I thought about using a gdm on boot, but stuck to the startx cli method of bringing up X.  Neat.

I grabbed the Feisty 7.04 server image here:

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

.

---

