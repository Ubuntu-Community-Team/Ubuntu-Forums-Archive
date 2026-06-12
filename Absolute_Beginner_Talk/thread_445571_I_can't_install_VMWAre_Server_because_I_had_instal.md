---
title: "I can't install VMWAre Server because I had installed VM Player before"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-05-16
Even though I deleted it, it still says it recognizes the other program.

Here is my code
```
andre@andre-desktop:~$ cd /tmp
andre@andre-desktop:/tmp$ cd vmware-server-distrib
andre@andre-desktop:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

andre@andre-desktop:/tmp/vmware-server-distrib$ 
andre@andre-desktop:/tmp/vmware-server-distrib$ 



```

---

### Post by Kobalt on 2007-05-16
How did you uninstall your previous VMWare install ? Did you use : ```
sudo apt-get remove --purge vmware-player
```

---

### Post by diargasm on 2007-05-16
> **Kobalt said:**
> How did you uninstall your previous VMWare install ? Did you use : ```
sudo apt-get remove --purge vmware-player
```

no, i did it with automatix.  I just tried what you suggested and that did not work either.  I got the same error.

---

### Post by diargasm on 2007-05-16
actually, i get this:

```
andre@andre-desktop:~$ sudo apt-get remove --purge vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vmware-player is not installed, so not removed
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.20-15 vmware-player-kernel-modules
  libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andre@andre-desktop:~$ cd /tmp
andre@andre-desktop:/tmp$ cd vmware-server-distrib
andre@andre-desktop:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure


```

---

### Post by Kobalt on 2007-05-16
I don't know much about VMWare-player, but do you have a ./vmware-plaer folder in your /home directory when you press Ctrl+H ? If so, you can try removing it...

---

### Post by Kobalt on 2007-05-16
> **diargasm said:**
> actually, i get this:

```
andre@andre-desktop:~$ sudo apt-get remove --purge vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vmware-player is not installed, so not removed
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.20-15 vmware-player-kernel-modules
  libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andre@andre-desktop:~$ cd /tmp
andre@andre-desktop:/tmp$ cd vmware-server-distrib
andre@andre-desktop:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure


```
Ah, ok now I see.
You should run (as apt advise you) to run : ```
sudo apt-get autoremove
```

---

### Post by diargasm on 2007-05-16
> **Kobalt said:**
> Ah, ok now I see.
You should run (as apt advise you) to run : ```
sudo apt-get autoremove
```

I hate to bug you, but it still didn't fix it.  It is giving the original error message. I also deleted the folders in the home directory like you suggested - even the hidden ones.

---

### Post by Jose Catre-Vandis on 2007-05-16
do a search on your file system for "vmware"

You will need to do this as root so you can delete from the search dialog:
```
sudo gnome-search-tool
```

Delete all the files found except those that relate to xorg (I say this without reason other than I didn't want to mess with my xorg config!)

vmware server should then install. You will need to install build essential and update your kernel headers. Search forum for howto on installation

---

### Post by veloce on 2007-05-16
> **Jose Catre-Vandis said:**
> 
vmware server should then install. You will need to install build essential and update your kernel headers. Search forum for howto on installation

vmware-server is now in the Feisty repositories - the commercial one.  Easiest way to install - sorts the kernel modules for you.

---

### Post by zvacet on 2007-05-16
Find vmplayer folder in** etc** and delete it.You should be fine.

---

### Post by holotone on 2007-07-01
Deleting /etc/vmware/ seemed to work perfectly for me. Thanks!

---

