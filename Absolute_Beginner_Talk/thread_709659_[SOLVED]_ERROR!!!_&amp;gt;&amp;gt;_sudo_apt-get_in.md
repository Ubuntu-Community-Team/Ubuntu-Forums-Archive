---
title: "[SOLVED] ERROR!!! &amp;gt;&amp;gt; sudo apt-get install -f"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by sevenearths on 2008-02-27
I've got a problem with

```
sudo apt-get install -f
```

which I presume fixes all your installs/updates

Little background > I was trying to replace the AWN Mac type launcher that I installed from this page

[http://www.ubuntugeek.com/howto-install-avant-window-navgator-in-ubuntu-gutsy-gibbon.html]("http://www.ubuntugeek.com/howto-install-avant-window-navgator-in-ubuntu-gutsy-gibbon.html")

with the one you get in the 'Synaptic Package Manager' called 'awn-manager'. At this point it fliped out. The AWN bar at the bottom of the screen still works, and I can still use the manager

This is what I get when I type 'sudo apt-get install -f'

```

arthur@laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libawn0
The following NEW packages will be installed
  libawn0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/63.9kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 129123 files and directories currently installed.)
Unpacking libawn0 (from .../libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
Errors were encountered while processing:
 /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any ideas how I can fix these broken packages?

(sorry I just have to mention that did try 'sudo apt-get install -f' after disabling awn. It had no effect)

---

### Post by christina_svats on 2008-02-27
Does synaptic say that you have broken packages?

---

### Post by sevenearths on 2008-02-27
Yeah! I booted up synaptic

it said I have 1 broken package

I set the filter to broken

I selected it for re-installation, clicked apply and got the following error

```
E: /var/cache/apt/archives/libawn0_0.2.1-0ubuntu1~gutsy1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
```

AH HA!

Then I uninstalled... and all is well

Solid!

(Plus I still have my awn manager :)

---

### Post by christina_svats on 2008-02-27
Good job! Please mark as solved...
Goodnight!

---

