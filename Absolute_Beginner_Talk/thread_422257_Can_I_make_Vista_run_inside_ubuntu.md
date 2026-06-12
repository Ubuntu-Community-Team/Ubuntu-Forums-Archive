---
title: "Can I make Vista run inside ubuntu?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-04-25
Hi! I wonder if it's possible to make vista run instide ubuntu?
Anyone got a good guide they could share?

Regards
James

---

### Post by lotacus on 2007-04-25
You'll have to have vmware or linux's conterpart and install Vista as a VM. However, you will not get all the prettiness and features because of hardware limitation of Vmwareplayer. Not to mention the hefty requirements of Vista all together.

---

### Post by the_axiom on 2007-04-25
Naah no problems with my hardware.
2gb ram, x1950xt and e6300 dual core  :) 
Is there any guide out there?

---

### Post by jdonat on 2007-04-25
> **the_axiom said:**
> Naah no problems with my hardware.
2gb ram, x1950xt and e6300 dual core  :) 
Is there any guide out there?

just get virtualbox ( [www.virtualbox.org](www.virtualbox.org) ) , install it , make sure to add yourself to the vboxusers group so you can start it up,  and then install Vista as usual, to get networking working, follow the guide here : [http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/](http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/)

---

### Post by the_axiom on 2007-04-25
Do I have to install vista **_after?_**, I have vista installed allready...

---

### Post by the_axiom on 2007-04-25
When i type this command:
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
Virtual Personal Use and Evolutions License (PUEL) and loads of text under it.
What do than? How do I press "ok"?

---

### Post by ofek on 2007-04-25
Yes u have to install vista after ... this is a virtual machine and as one it can't use ur normal vista installation which is probably on another partition. Theres a guide somewhere in this forums about installing virtualbox just run a search and follow the guide.

---

### Post by the_axiom on 2007-04-25
Ok, how do I uninstall?
I get this error when trying to open synaptic.
The package virtualbox needs reinstalling, but I'cant find any archive for it (translated).

---

### Post by AlexenderReez on 2007-04-25
> **the_axiom said:**
> When i type this command:
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
Virtual Personal Use and Evolutions License (PUEL) and loads of text under it.
What do than? How do I press "ok"?

it is better for next time to use deb installer rather than use dpkg command because deb installer will find dependency for a particular software but if you use that command...it will install and ignore your package without dependency...it it will break your system....remove and install it again using deb installer...how?find broken software in synaptic...remove...install it all over again....

---

### Post by the_axiom on 2007-04-25
I'm sorry but I didn't understand your post to well.
I have to add that I'm a noob and I didn't really understand everything.

I cannot use synaptic until I've uninstalled the software, could anyone please tell me how to do this in "noob" way.

Thank you for your answers btw.

---

### Post by the_axiom on 2007-04-25
Can anyone help me by MSN? (PM me)
I need quite fast help...

---

