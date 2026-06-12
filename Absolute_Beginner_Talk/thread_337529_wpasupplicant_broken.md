---
title: "wpasupplicant broken"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-01-13
```
Removing wpasupplicant ...
dpkg: error processing wpasupplicant (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 wpasupplicant
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I was supposed to update this according to the update manager. However, there is some error during upgrade. How can I resolve the problem?

Now the update manager is broken and I was asking sudo apt-get --install -f

Some prior info might help.
I tried to install vmware server but somehow it fails and prompt me to do the config.pl thing. Nevertheless, I can't get things work.

so how can i resolve the wpasupplicant thing and how can i remove vmware server and make a proper install?

---

### Post by jvc26 on 2007-01-13
Hi there - the repairing of the update you need to open a terminal window (applications->accessories->terminal and type:
```

sudo apt-get --install -f

```
I'm having problems with VMWare install at the moment too at what point does the installer crash?
Il

---

### Post by in_flu_ence on 2007-01-13
i tried the apt-get fix thingy but still can't get the wpasupplicant thing to be removed or upgraded.

For vmware, I have everything set but it just can't get vmware to run when i type it and keep asking me to do the config.pl thingy

probably i need to remove the whole vmware thingy somehow (every trace) and make a clean reinstall.

---

### Post by jvc26 on 2007-01-13
you have to run the vmware config script (the same way you ran the last script to install it) so that it configures to your kernel, otherwise it won't load - or have you already configured it and its still not working?
Il

---

### Post by in_flu_ence on 2007-01-13
i have run the config.pl and set the default options along the way.
still it doesn't work.
strange.

---

### Post by Copperteeth on 2007-01-13
can someone please fix the wpasupplicant problem, i cant get it working either, its bugging me how i cannot update!!!

---

### Post by in_flu_ence on 2007-01-13
While I don't exactly know the reason behind. I fix the wpasupplicant problem by first force downgrade in synaptic to 0.54 and then upgrade it to 0.57.

Some info that might help is that I believe the upgrade of this package is from download.tuxfamily.org. 

Some error message is shown [here](http://www.ubuntuforums.org/showthread.php?t=337669)

But of course if some expert that knows the exact reason behind the error, i would love to learn about it. So i will be more aware of similar problem in future.

---

### Post by smolko on 2007-01-16
This error was caused by the wpasupplicant package from Trevino's repository. I guess we are all using it :)  And the solution is simple.
```
sudo gedit /var/lib/dpkg/status
```
And remove the information which reference to wpasupplicant. Beginning with the "Package: wpasupplicant" line and ending with the "This package includes also wpa_gui, a qt front-end for wpa_cli" line.
Then simply install the wpasupplicant
```
sudo apt-get install wpasupplicant
```
It should result in the following change in the /var/lib/dpkg/status file
```
Package: wpasupplicant
Status: install ok installed
Priority: important
Section: net
Installed-Size: 1056
Maintainer: Trevi <trevi55@gmail.com>
Architecture: i386
Version: 0.5.7+3v1ubuntu3
Replaces: wpagui
Provides: wpagui
Depends: libc6 (>= 2.4-1), libdbus-1-3, libgcc1 (>= 1:4.1.1-12), libncurses5 (>= 5.4-5), libqt3-mt (>= 3:3.3.6), libreadline5 (>= 5.1), libssl0.9.8 (>= 0.9.8b-1), libstdc++6 (>= 4.1.1-12), libx11-6, libxext6
Suggests: kwlan
Conflicts: wpagui
Conffiles:
 /etc/default/wpasupplicant edd42614b0f4aed23dba9b17fdefa998
 /etc/wpa_supplicant.conf a3539c641835b2d2b59b399fc01ecba9
Description: Client support for WPA and WPA2 (IEEE 802.11i)
 WPA and WPA2 are methods for securing wireless networks, the former
 using IEEE 802.1X, and the latter using IEEE 802.11i. This software
 provides key negotiation with the WPA Authenticator, and controls
 association with IEEE 802.11i networks.
 This package includes also wpa_gui, a qt front-end for wpa_cli
```

---

### Post by tchoklat on 2007-01-17
great solution to a problem I had also - thanx!

---

### Post by in_flu_ence on 2007-01-18
great solution

---

### Post by giuliastro on 2007-01-19
Unfortunately this doesn't work. After a few upgrades the problem comes back again.

---

### Post by ubuntosh on 2007-01-19
Im having trouble with the sudo gedit/var/lib/dpkg/status
whenever I try this, I get:
sudo: gedit/var/lib/dpkg/status: command not found

please help I don't know what's wrong.](*,)

---

### Post by smolko on 2007-01-20
> **giuliastro said:**
> Unfortunately this doesn't work. After a few upgrades the problem comes back again.

If that problems still comes back, I'll suggest removing the trevino's repository completly from sources.list and installing the wpasupplicant from the ubuntu repository.
Remove the wpasupplicant lines from /var/lib/dpkg/status. And then remove the repository. Then run:
```
sudo apt-get update
sudo apt-get -f install
```
And the package manager will automaticaly install the wpasupplicant package from the ubuntu repository.

> **ubuntosh said:**
> Im having trouble with the sudo gedit/var/lib/dpkg/status
whenever I try this, I get:
sudo: gedit/var/lib/dpkg/status: command not found

please help I don't know what's wrong.](*,)

Have a better look at my first post and try to type exactly what's written there. Instead of
```
sudo gedit/var/lib/dpkg/status
```
write this
```
sudo gedit /var/lib/dpkg/status
```
there must be a space between gedit and /var/... (gedit is the editor, which edits the status file, therefor there must be space between the command and it's parameter)

---

### Post by in_flu_ence on 2007-01-20
I guess it will work by simply reinstalling the version (force version back to the lowest) at ubuntu repo and do a new upgrade. It works for me over the past few wpa.. upgrade at update manager.

---

### Post by ubuntosh on 2007-01-20
sudo gedit /var/lib/dpkg/status doesn't work either. I still get:
sudo: gedit: command not found. 
Is there any other way in which the wpasupplicant package can be removed?
thnx.
:confused:

---

### Post by smolko on 2007-01-21
Gedit is in the default Ubuntu installation. Are you using Kubuntu? If yes, then try kate instead of gedit. If that wouldn't work, you may try nano or vi, yet they can be a bit confusing if you are not used to them.

---

### Post by giruzz on 2007-01-22
thanks!

---

### Post by jvc26 on 2007-01-22
also use gksudo gedit /var/lib/dpkg/status rather than sudo gedit /var/lib/dpkg/status Use gksudo for graphical apps, sudo for terminal - for more info see: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
Il

---

### Post by thesandeep on 2007-01-22
Great solution, thanx to SMOLKO=D>

---

