---
title: "wine"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-19
I followed this instructions to install wine [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
But console gave me this back at the end 

The following packages have unmet dependencies:
  wine: Depends: libgphoto2-2 (>= 2.3.0) but 2.2.1-2ubuntu4 is to be installed
        Depends: libgphoto2-port0 (>= 2.3.0) but 2.2.1-2ubuntu4 is to be installed
E: Broken packages
vandorius@vandorius-desktop:~$ 


Anyone got any clue?

---

### Post by jbayone on 2007-03-19
i think you can check what broken packages you have in Synaptec.  There is a filter for it.

---

### Post by AndyCooll on 2007-03-19
Are you particularly looking for the latest version of Wine? Otherwise it might be easier to install it using Synaptic since it's in the repositories.

:cool:

---

### Post by Vandorius on 2007-03-19
Yes i wanted to insatall the latest version. Now i cant install wine even from add remove.
Im new to linux so i dont know what to do especially what commands are needed :P

---

### Post by Fuzzban on 2007-03-19
Funny, I just had that same problem but luckily I fixed it. First off it gave me the same problems when I installed it though Synaptic ( System>Administration>Synaptic Package Manager). My solution was to go to Synaptic Package Manager and installed (if installed),  libgphoto2-port0 version 2.2.1, and then dl the updated one, 2.3.0, from:

[https://launchpad.net/ubuntu/edgy/i386/libgphoto2-port0/2.3.0-0ubuntu3~edgy2]("https://launchpad.net/ubuntu/edgy/i386/libgphoto2-port0/2.3.0-0ubuntu3~edgy2")

_Then libgphoto2-2 2.3.0 from:_ 

[https://launchpad.net/ubuntu/edgy/i386/libgphoto2-2/2.3.0-0ubuntu3~edgy2]("https://launchpad.net/ubuntu/edgy/i386/libgphoto2-2/2.3.0-0ubuntu3~edgy2")

Remember to download the .deb file, not source file unless you know what your doing. That should do it.

---

### Post by SwedishHatFaction on 2007-03-21
> **Fuzzban said:**
> Remember to download the .deb file, not source file unless you know what your doing. That should do it.

I downloaded both of the .deb files but when I attempted to install them with the GDebi Package Installer, I received the error message: "Error: Conflicts with the installed package 'libgphoto2-port0'". I was reluctant to remove libgphoto2-port0 from Synaptic and install the new package because it said it would also have to remove a heck of a lot of other things, ubuntu-desktop being one of them. Please help.

:confused:

---

### Post by steevz on 2007-03-21
I was having the exact same problem. I believe I fixed it by running update and upgrade.

In terminal type:

sudo atp-get update
sudo atp-get upgrade

After that try installing it again.
Hope that helps.

---

