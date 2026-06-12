---
title: "Synaptic Error: dpkg was interrupted"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Taters on 2007-09-22
I was trying to install Jokosher when I received this message:
[IMG]http://i204.photobucket.com/albums/bb211/tnemcod/Screenshot-3.png[/IMG]

I have put : sudo dpkg --configure -a into the command line, and now synaptic is won't allow me to select a program (I get the little spinner, the window doesn't freeze, but it ignores me).

Any ideas? I can re-install Ubuntu as there is nothing important on my machine yet.

---

### Post by alienexplorers on 2007-09-22
Try doing from terminal
> sudo aptitude update
sudo aptitude upgrade
then go back in to synaptic and reload repositories.

---

### Post by Taters on 2007-09-22
Uh... I am still getting the endless spinning... I'll try a reboot.
Edit:
That didn't work. I'll probably reinstall Linux then.

Thank you.

---

### Post by bodhi.zazen on 2007-09-22
LOL

close synatpic

Open a terminal and enter :

```
sudo dpkg --configure -a
```

oic you did that ...

How is it that installation was interrupted, what were you installing.

If you manually try to install a package with apt-get, do you get any error message ?

---

### Post by Taters on 2007-09-23
Before Synaptic crashed I tried installing some programs from their tar.gz files (SeaMonkey from Mozilla) and its said it couldn't find a file path.   

I just reinstalled Ubuntu.... Synaptic is fine now. But now I'm getting strange messages from the Update manager. Edit: Update manager is fine now...

Is there any specific computer language that would make me more Ubuntu savvy?

---

### Post by Kundalinux on 2007-09-25
> **bodhi.zazen said:**
> LOL

close synatpic

Open a terminal and enter :

```
sudo dpkg --configure -a
```

oic you did that ...

How is it that installation was interrupted, what were you installing.

If you manually try to install a package with apt-get, do you get any error message ?

I had the same problem and this worked for me. Thanks!

---

### Post by gasgasohlins on 2008-02-28
I too just had the same problem and it too worked for me (after a google search on the problem)...
:)

---

### Post by Tanno on 2008-03-01
I have the same issue and this DID NOT work for me.

```
tanno@Tanno-Linux:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1
tanno@Tanno-Linux:~$ 


```

Help.

---

