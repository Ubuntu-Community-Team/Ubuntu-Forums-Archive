---
title: "Enabling Xfwm4 compiling"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-02-07
Hi, 

I only have an 8mb video card, and its not even an nvidia one. I'm using Xfce as DE.  

There is no compositing tab in the window tweaking pane in settings, which is where it is on the Xfce website screenshots. Can I enable this on my computer?

---

### Post by mcduck on 2007-02-07
I suppose the screenshots on the XFCE page are from the latest version.. I've seen somebody lposting a link to repository with latest XFCE4 packages for Edgy, so you could searching for that if you want.

---

### Post by Brendantb on 2007-02-07
How long is it generally until the Xubuntu distribution is updated to the latest Xfce version?

---

### Post by mcduck on 2007-02-07
> **Brendantb said:**
> How long is it generally until the Xubuntu distribution is updated to the latest Xfce version?

As update? Most likely never. But I suppose it will be in 7.04.

---

### Post by Brendantb on 2007-02-07
Okay, I have downloaded the Xfce 4.4.0 to my Xubuntu desktop, as a .tar.bz2 archive. I used Xarchiver to Open it, but it appears to be a collection of further .tar.bz2 archives. 

How best do I install this release? Do I have to open all the archives manually? Can synaptic handle this?

---

### Post by mcduck on 2007-02-07
No, Synaptic only installs from repositories, not anything you download yourself.

But, like I said, there should be a Ubuntu repository for XFCE 4.4, search the forum and you should find more info about that.

---

### Post by kerry_s on 2007-02-07
Here's the 4.4.0 repo-> deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0  

You also have to add->

```
Section "Extensions"
    Option         "Composite" "True"
EndSection
```

To your xorg.conf for the composite tab to show up. I got poor performance with it on, so i turned mine off. It's just not worth it to me.

---

### Post by Brendantb on 2007-02-20
I have done a minimal install from the command line. 

Now, how do I use the command line to down load this version of Xfce-4-4-0 from that location?

---

### Post by Maestro23 on 2007-02-20
> **Brendantb said:**
> I have done a minimal install from the command line. 

Now, how do I use the command line to down load this version of Xfce-4-4-0 from that location?

Add what Kerry_S posted to your /etc/apt/sources.list  You will need to do this thru an editor(nano, vi, gedit, mousepad, kate,etc..) Pick one you are comfortable with.  I use nano a  lot, so for me:

Open a terminal and type:

> sudo -B nano /etc/apt/sources.list

Add the line that he posted above, save the file and exit.

Then still in terminal:

> sudo aptitude update

sudo aptitude install <programname>


---

### Post by Brendantb on 2007-02-20
Hi, 

Thanks for the reply, that is definitely one for the notebook. 

However, my minimal install wasn't as minimal as I thought, and I have the whole desktop, with all the apps. This was after choosing option four on the alternative CD, "Install an LTSP server." During the install, a message said that the chroot couldn't detect  a network, and then the computer sat for a while, and then installed a whole lot of stuff I didn't want, like OOo files. 

Of the four Options in Xubuntu Alternative install, 

Text mode,
OEM mode, 
A command line system, 
An LTSP server, 

which will give me the most minimal installation?

---

### Post by Brendantb on 2007-02-20
When I type in

sudo aptitude install xfce4, 

I am prompted to put in the CDrom again. Is this right?

---

### Post by kerry_s on 2007-02-20
You want the command line system for minimal install. Are you connected to the net? You have to be connected.

command line install
login
sudo su
nano /etc/apt/sources.list
comment(#) out the cdrom and all the deb-src, then uncomment the deb
add> deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0 
ctrl and x and y and enter to save
apt-get update
apt-get dist-upgrade
apt-get install x-window-system-core gdm xfce4 leafpad synaptic
reboot
choose xfce4 from the session menu and login
open synaptic and get what ever applications you want.

---

