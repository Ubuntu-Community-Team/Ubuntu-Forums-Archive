---
title: "madwifi drivers"
date: 2007-03-31
forum: Apple Intel Users
---

### Post by fumanchu on 2007-03-31
I am trying to install the madwifi drivers in ubuntu 6.10 on my core duo macbook pro, but whenever I try to compile I got this long list of errors.  I followed the installation instructions on the madwifi website and I just can't seem to find what the problem is.  Does anybody know what to do with this?

---

### Post by cyberdork33 on 2007-03-31
get the build-essential package from apt first

---

### Post by ronocdh on 2007-03-31
Cyberdork's right, try that first. And although I think you were very careful, I just have to point out that while Core Duo Macs can use the madwifi drivers Core2 Duo users have to use ndiswrapper. Sorry if I'm being pedantic. ;)

---

### Post by fumanchu on 2007-03-31
The problem is that my wired connection isn't working either, so I have no way of getting the build-essentials package.  Would it be possible to download it from OSX and install it on ubuntu?

---

### Post by thonuz on 2007-03-31
latest madwifi is working here on intel duo core 2 as of Yesterdays build for me. 
Works great. If you use an external infrared mouse it helps concerning touchpad issues.
Other than that my macbook intel is lots faster in ubuntu. Open office opens very fast and better after the second time. I am not sure if this has to do with ram, but I upgraded to 2G from 512 and have yet to see any difference on the mac side. Everything else is better. osx is interesting for a while but it seems to take longer to do some things. If it get a little better I will ditch osx partition. I've had a few crashes on osx side. Before this I hade Feisty Herd 5 running and wrapper worked fine with simple if up command.
I don't care about the isite stuff, just use it in mac for a while and you will get bored with it quickly. It is good as maybe a mediocre scanner.

---

### Post by fumanchu on 2007-04-01
does anyone know how i can install the build-essentials package without a working internet connection on ubuntu?

---

### Post by DaniT on 2007-04-01
> **fumanchu said:**
> does anyone know how i can install the build-essentials package without a working internet connection on ubuntu?

Here [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") you can download the .deb packages from another computer.
The madwifi drivers are only way I've been able to use the wireless, ndiswrapper didn't worked for me even though I'm using the 32-bit versionof ubuntu.

---

### Post by fumanchu on 2007-04-01
Many of the .deb packages require the use of other packages, and the installer will try to download the missing packages before installation.  How can I manually install all the needed packages in order to avoid this?

---

### Post by cyberdork33 on 2007-04-01
you are just going to have to determine the dependencies and download all the needed packages... This why everything is done via downloads.

---

### Post by fumanchu on 2007-04-02
The problem is that the g++-4.1 package is dependent on the libstdc++6-4.1-dev package and vice versa, so i'm stuck.  The g++-4.1 package also claims to be dependent on itself.  Is there no way around this?

---

### Post by Co.Sinecure on 2007-04-02
> **fumanchu said:**
> Many of the .deb packages require the use of other packages, and the installer will try to download the missing packages before installation.  How can I manually install all the needed packages in order to avoid this?

You can use Synaptic to generate a download script:
File > Generate Package download script
Select the packages you want, then use this command to generate the script (it'll work out all the dependancies), and if you have access to another linux computer you can just run this script to download everything (using wget). If not, you at least have the URLs of all the packages you need.
Then use
File > Add downloaded packages 
to install them!

Much easier than trying to work it out yourself... :)

---

### Post by Chrisj303 on 2007-04-02
Right, i'm giving up - can't get the Madwifi drivers to work, neither can i get the NET5416 drivers to work (says there installed but 'ndiswrapper -l gives "invalid drivers")

Until a future ubuntu release has this working out of the box, i'm not going to able to use my airport card with ubuntu.
I'm more than happy to shell out a few quid for a USB wireless adapter though, is this possible?
Can somebody please confirm if this can be done, and even better specify a brand/model of USB adapter that they know to work? This would be GREATLY appreiciated BIG TIME!

A friend of mine has a USB adapter working with ubuntu on his PC laptop. If i were to use the same model/same driver i *should* get the same results?? Or does the fact that it's running on a mac make a huge difference?

Thanks,
chrisj303

---

### Post by Meck1982 on 2007-04-02
I am using Feisty Beta on my C2D-Macbook. Just installed the ndiswrapper 1.9 and loaded the driver from my Macintosh-Windows-Drivers. At first it gave me invalid driver, but then I assured, that not only the inf.-File but also the two other files were in the same directory before doing the sudo ndiswrapper -i ...
Then - at first everything went fine and I saw a new device, even in network manager! Now after a reboot, everything is ****** up. Does not boot any more... I guess it's the ndiswrapper ;-)
I never tried the Madwifi option, but I heard it would work without Encryption. Just see [**here**]("http://madwifi.org/ticket/1001")

EDIT: Now after a few trials the system boots correctly. I cannot tell why. At least I have to say that ndiswrapper MIGHT cause problems/unstabilities.

---

### Post by DaniT on 2007-04-03
> **Meck1982 said:**
> 
EDIT: Now after a few trials the system boots correctly. I cannot tell why. At least I have to say that ndiswrapper MIGHT cause problems/unstabilities.

Yeah, something similar happened to me. If I added ndiswrapper to /etc/modules It would crash during boot. With madwifi it works fine, although I have to reinstall it when the modules or the kernel  are updated. My wifi network is not encrypted so I don't know if it works with encrypted networks.

---

### Post by dr. zoidberg on 2007-04-29
> **DaniT said:**
> Yeah, something similar happened to me. If I added ndiswrapper to /etc/modules It would crash during boot. With madwifi it works fine, although I have to reinstall it when the modules or the kernel  are updated. My wifi network is not encrypted so I don't know if it works with encrypted networks.

Same thing happened to me.  What I did was remove ndiwrapper from /etc/modules and have it start up via modprobe ndiswrapper with a script placed in /etc/rc2.d.  Its a patchwork solution but it worked for me (i'm running feisty btw).  I also blacklisted the madwifi driver (ath_pci)

---

