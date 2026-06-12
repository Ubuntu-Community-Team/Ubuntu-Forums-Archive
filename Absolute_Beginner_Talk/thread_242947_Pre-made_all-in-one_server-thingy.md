---
title: "Pre-made all-in-one server-thingy"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by nollkoll on 2006-08-24
I ahve this school project, we have to do something computer-related...
Anyways, i figuerd, why not make a pre-made email/web-hoten with pre-conigured FTP-server to it.
Plus some other nifty thingys added to it. 

And now to the question, im wondering if there's possible to "save" an allready installed Ubuntu and eg call it server-thingy, and make a Install-CD that installs everything you had on the server-thingy OS i saved, thus making a cd that you only need to insert and press OK or install.

P.s, i can't check synapics for such app because i have a Dlink G604T(It's broken somehow).

---

### Post by tribaal on 2006-08-24
I'm not really sure if we both think of the same thing, but I think this would be a pretty nifty feature to have (the "safe to install disk" thing).

I vote for that, if it doens't already exists. :)

If it doesn't, would it be enough to safe the installed packages to a script (that would reinstall all the same packages), and the to sort of "overwrite" the /etc folder (so that the config if the same as on the master system?).

Am I being naive? :)

- trib'

---

### Post by petersjm on 2006-08-24
I'm *pretty* sure there's a way to burn your existing Ubuntu install as an ISO file to disk, but I don't have a clue how.

Other than that, what about doing a kind of Automatix thing, whereby you install one program which then fetches and installs all the other programs? Would that not be easier? Would save on file size of your script, too.

---

### Post by nollkoll on 2006-08-24
hehe, that's exacly how i wanted it to be :P but, the script thingy might be a bad thing if someone has a not-supported network card, or wait. im just talking nonsense :P well, i like the install-then-use :P kinda like "plug in screen and all that, install, unplugg everytign exept power supply and network-thingy and let the machine stand and slowly turn into rust :P

Woops, there's the mindless typing again XD

---

### Post by nollkoll on 2006-08-24
Well, i'll have ot look into that, still rather new to linux

---

### Post by David Corrales on 2006-08-24
Another way would be to add a meta package which install other packages you might need. But that would need an extra repository...

---

### Post by tribaal on 2006-08-24
Yes, that's correct.

Yet I don't think a huge aptitude script would really adress the concern here, because we'd need to "clone" not only the programs themselves (that's the packages part), but also the configuration and settings... For example, I want to "preseed" Apache, MySQL, a CMS and an IMAP server to work together (an all-in-one ready to use CMS server).

Reading this last paragraph, I'm not sure i'm making sense (English is not my mothertongue). Am I?

- trib'

---

### Post by bluenova on 2006-08-24
You might want to have a look at the OEM option:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

Not sure if it's what you are looking for.

---

### Post by sbassett on 2006-08-24
Well -

I suppose there are a few different ways to do this:

[http://wiki.oss-watch.ac.uk/UbuntuDapper/Remaster]("http://wiki.oss-watch.ac.uk/UbuntuDapper/Remaster")
This goes through the process of remastering a live Ubuntu CD.

Also, is VMWare an option? That would give you total control as to what you can place on the system, and then take a snapshot and open said snapshot once it is time to demonstrate.

---

### Post by nollkoll on 2006-08-25
does it work to use a mounted ISO as a CD ? or wait, lol, then i'dd ahve to partition the hhd whule using windows, and that can't be anything but bad...

---

### Post by nollkoll on 2006-08-25
or maby i can "fake" a partition, or wait, lol, that's what vMware deos?

Heh, i feel like the worst beginer ever =/

---

### Post by nollkoll on 2006-08-25
im trying to install Ubuntu 6.06 using vMware, but it stops at "Loading essential drivers"..

---

### Post by dca on 2006-08-25
I don't know if this helps (you'll notice all of my replies start with this) but as an example:
 
[http://linux.softpedia.com/progDownload/Ghost-for-Linux-Download-53.html](http://linux.softpedia.com/progDownload/Ghost-for-Linux-Download-53.html)
 
 
On a roll-out of multiple workstations that have the same guts, ie:  Intel mobo w/ PIV 2.8 or 3.0 GHz CPU, 512 MB RAM, and so-on....  Let's say ten workstations at a law firm.  We'd load the LiveCD on one of the workstations (purchased bare-bones, w/o OS & downgraded from 80GB HDD to 40GB) and install it.  Tweak the heck out of it, install some POS (point of sales, not piece of s**t) software and other db utilities for keeping track of clients.  Once the PC is set-up how we like it, we use a utility similar to the one in the link above.  Ghost the HDD and Ghost it back, keep the spare made and as other PC(s) arrive just re-image the un-formatted HDD, put it back in the box, and place it at the user's desk.
 
This probably has nothing to do w/ orig thread, just throwing it out there...

---

### Post by sbassett on 2006-09-08
> **nollkoll said:**
> im trying to install Ubuntu 6.06 using vMware, but it stops at "Loading essential drivers"..

Is this still an issue? I have installed Dapper several times within VMware and never had issues.

---

### Post by tribaal on 2006-09-08
Well it's sort of an issue still, yeah.

The HDD cloning idea is likely to work, but only on clone systems.
My point was to have a way to take a "snapshot" of an installed system, and to make an install .iso from that snapshot.

VMware would be the best option to do this *if* you have ESX (non-free) version that you can deploy on the new machine in the first place... ESX installs a VMware kernel and low-level virtualisation machine, so that you don't have a "host OS" anymore. But this is a non free solution (as in beer and as in speech).

We need a way to customize the install CD. A way to "push" some packages, like what the LAMP install does, along with the configuration files and all the setup.
If you will, something like the LiveCD customiser, but for the "Alternate" CD. :)

I hope you guys understand what I mean, I feel like I'm loosing my English... :(

- trib'

---

### Post by lapsey on 2006-09-08
its really really easy.

all you need to do is have a location where all the correct config files are stored.

then, using a bash script you can 
- install the software
- wget the config files
- move them into the correct location
- change permissions, set up user accounts etc
- remove the script file that is running
- restart the machine.

the only places where you need user input in this process are things like entering a sudo password, or a password for a new user account, or installing things that reguire you to view the EULA (like Java)

It also takes a bit of trial and error - to avoid a lot of guess work, set it up manually but keep track of all the things you do in terminal so you can put them into the script later.

---

