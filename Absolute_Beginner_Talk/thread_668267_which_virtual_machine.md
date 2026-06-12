---
title: "which virtual machine?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-15
I will need to install a virtual machine onto my linux box to run windows.  What is my best choice, this wont be for gaming.  I am a systems admin at a company and some things aren't available to me without it.

Whats my best choice, for simple and fast.

---

### Post by Mithrilhall on 2008-01-15
I went with VMWare but I'm sure others will recommend something different.

---

### Post by angryfirelord on 2008-01-15
I would go with VirtualBox. I've used it for a while and never had any problems with it. (It has handled Windows 2000, Windows XP, and Windows Server 2003 without problems) You can use VMWare as well, but it's a more of a pain-in-the-butt to set up.

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

Just remember to add yourself to vboxusers when it's done installing
```
sudo adduser *your_name* vboxusers
```

---

### Post by hyper_ch on 2008-01-15
I chose VmWare over VBox because:

(1) I could not get networking done properly in VBox between guest and host
(2) I think external USB devices are much better handled in VmWare

However VBox has the seamless mode which VmWare lacks so far...

My recommendation:

Install both, test them both out, then decide for one.

P.S.: VmWare Server is no pain to setup. Add the Canoncial Partner repos and install it through synaptic / aptitude / adept / apt-get... then go to vmware's site and get your serial number:  [http://register.vmware.com/content/registration.html](http://register.vmware.com/content/registration.html)

---

### Post by KezzerDrix on 2008-01-15
Okay, I am used to VMware so I will probably choose that, but I could not find it in the repo, I added the canocial repo and tried searching for vmware and just vm, I found some tools but no main program.  What am I looking for? and how do I get it?

Thanks

---

### Post by KezzerDrix on 2008-01-15
which virtual box do I use, I have ubuntu 8.04 installed


Sorry about the double post, I don't use forums much and forgot to edit

---

### Post by CCBalla10 on 2008-01-15
Ahh i dunno about 8.04  but i am runnin Gusty and have VirtualBox....its sooo easy to use

---

### Post by SOULRiDER on 2008-01-15
If you dont needs USB use the OSE of Virtualbox.
I'd too use virtualbox, IMO its faster than VMWare but it seems to be slighly less stable.

---

### Post by SOULRiDER on 2008-01-15
> **KezzerDrix said:**
> which virtual box do I use, I have ubuntu 8.04 installed


You probably have already been told this.. but expect breakage.. lots of breakage :P
Hardy is still alpha, not even beta, if you need to work with your computer use 7.10 or your computer will crash when you need it the most :P

---

### Post by KezzerDrix on 2008-01-15
yea, I just updated this morning and have just realized that my sound quit working.  I probably will revert to 7.10, I was happy with it.

The biggest thing for me is getting used to gnome.  I switched from PCLOS to ubuntu, and to be honest am very green in the linux scene :) 

I actually like gnomes appearance better but I keep getting told that I am missing out on all of KDE's massive improvements

Well, I have realized that I can still use all the kde programs I am used to but have a cleaner, faster desktop.  IMHO

---

### Post by hyper_ch on 2008-01-15
Here's the repo for Gutsy:
```

# Canonical Commercial
deb http://archive.canonical.com/ubuntu gutsy partner

```

and then it will be in your repos:

```

hyper@xubi:~$ apt-cache search vmware
mdetect - mouse device autodetection tool
xserver-xorg-video-vmware - X.Org X server -- VMware display driver
libview-dev - VMware's Incredibly Exciting Widgets
libview2 - VMware's Incredibly Exciting Widgets
libview2-dbg - VMware's Incredibly Exciting Widgets
**vmware-server - Free virtual machine server from VMware**
vmware-server-kernel-modules - vmware-server kernel module dependency package
vmware-server-kernel-modules-2.6.22-14 - vmware-server modules for Linux (kernel 2.6.22)
vmware-server-kernel-source - Kernel modules for VMware Server.
hyper@xubi:~$

```

Just don't forget to update first ;)

Btw, you could also try to add the repos to hardy. Just exchange "gutsy" to "hardy". That might work.

---

### Post by KezzerDrix on 2008-01-15
thank you all for the tips

Kezz

---

### Post by ignorance on 2008-01-15
If i may suggest but take a look at Xen. Now i'm not completly sure but as far as i know it only work for 64-bit cpu's.

---

### Post by KezzerDrix on 2008-01-16
> **SOULRiDER said:**
> If you dont needs USB use the OSE of Virtualbox.
I'd too use virtualbox, IMO its faster than VMWare but it seems to be slighly less stable.

I reverted to 7.10ubuntu, 8.04 was more than a noob could handle :)

I need USB but only found virtualbox ose in the repo, Is there a different version, am I missing something?

Does vbox take advantage of VT processors?



Thanks

---

### Post by angryfirelord on 2008-01-16
> **KezzerDrix said:**
> I reverted to 7.10ubuntu, 8.04 was more than a noob could handle :)

I need USB but only found virtualbox ose in the repo, Is there a different version, am I missing something?

Does vbox take advantage of VT processors?



Thanks

-Yes, there's a VirtualBox repo you can add to your sources.list.
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")
(Remember to import the key as well)
-Yes, the latest version (or one of the recent versions) added support for hardware VT. I'm not sure if its enabled by default, so check your settings first. However, even with hardware VT off, I still found Vbox ran quite fast.

---

