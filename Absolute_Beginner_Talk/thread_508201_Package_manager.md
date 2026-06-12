---
title: "Package manager"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by maestro234 on 2007-07-23
When opening packagae manager I am getting the following message:

E: sub-process gpgv returned an error code (2)

W: signature verificateion failed for : /media/cdrom0/dists/feisty

it then brings me into package manager, but I am unable to install anything.

What may be causing this?

---

### Post by p_quarles on 2007-07-23
Both of those errors have to do (I'm fairly certain) with securely connecting to the repositories.

I've never run into this problem, so I'm not sure I can help, but here's how I would start the debugging process. First, edit the sources list:
```
gksudo gedit /etc/apt/sources.list
```Then, put a pound symbol (#) in front of the line that starts with "deb cdrom:[Ubuntu. . ."

Next, use the command line to install a small package, e.g.
```
sudo apt-get install vim-full
```If that gives you an error, come back and post the text of the error message.

If that installation is successful, try this [edited for correct syntax]
```
gksudo synaptic
```Again, post any error messages you get with that.

---

### Post by Frak on 2007-07-23
Correction
```
gksudo synaptic
```
GKSudo is used for graphical applications.

---

### Post by p_quarles on 2007-07-23
> GKSudo is used for graphical applications.
That's true. All the same, I did test my instructions before posting them, and "sudo synaptic" ran the graphical package manager (for me, at least). All the same, I'll edit my post.

---

### Post by maestro234 on 2007-07-24
There is no line that starts with  "deb cdrom:[Ubuntu. . ." in the file that opens.

I was trying to install the package from the cdrom because I am unable to connect to the internet.  I believe it is because my wireless card is not recognized.  

I am using a linksys wireless card model wmp54g.  I thought that if I installed the ndiswrapper package I could get the card to work.

I am very new to this and am not really sure what to do.

---

### Post by Frak on 2007-07-24
See if this works for you, as I have the same card, and this seemed to work for me.
[http://ubuntuforums.org/showthread.php?t=419709&highlight=ralink+feisty](http://ubuntuforums.org/showthread.php?t=419709&highlight=ralink+feisty)

---

