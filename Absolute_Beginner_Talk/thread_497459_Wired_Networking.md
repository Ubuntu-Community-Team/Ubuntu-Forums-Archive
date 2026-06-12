---
title: "Wired Networking"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by sgtbob on 2007-07-10
I want to connect two PC's in the same room via wire. Units are (1) Dell XPS 400, running Ubuntu 7.04 and Windows XP with a (2) Dell 8250, running Fedora 7 and Windows XP.

Knowing absolutely nothing about this process, could someone explain how to proceed or direct me to a site that explains in '**noobisms' **how to proceed?  I prefer to use cable/wire for the security that some articles indicate is desireable plus the <2 feet distance between the two.

From some preliminary data I have gleaned in reading forum postings, it appears that a connection via 'special' USB cables from a USB port on PC1 to a USB port on PC2 - is that feasible? What would I need? Is a simple USB cable useable or if not,  and if not, what is the 'special' cable I would need?

At present, I have both PC's connected to the internet through a D-link Ethernet Router and then to the cable modem, so how would this factor into the equation? Would one PC be the connection so that the other could also connect through it?

Advice and guidance solicited.

Numero uno noob!

Bob:confused:

---

### Post by Sparkster185 on 2007-07-10
I just bought a switch/hub for $20 and kept it in my room.  I have no problems with one desktop and two laptops accessing the network.

---

### Post by FleetAdmiral74 on 2007-07-10
I think Ubuntu needs a program called Samba to network with the XP installs. Not sure about Fedora to Xp though. And XP to XP should be as simple as using the network guide, its somewhere in their control panel :)

---

### Post by HereInOz on 2007-07-10
It appears that you already have an Ethernet switch to allow both computers to connect to the Internet, and I am guessing that the D-Link router is providing DHCP services - assigning a local IP address to each machine.

Therefore, if the IP addresses of both machines are in the same sub-net (like 10.1.1.3 and 10.1.1.4, or something like that) then they are already set up to be networked.

What you then need to do is to share some folders (directories) on each of the machines.  The techniques are different in Windows and Linux.

You also need to make sure that the usernames and passwords on both machines match.  This is not always completely necessary but it is a good idea.

You also need to ensure that the firewalls all allow access from the other machines on the network - again, different depending on what firewalls you are running.

Also if you want to share folders between Linux and Windows machines, you will need to install Samba on the linux machines, set up Samba shares, and create Samba users on those Linux machines.

I think that about covers it, but if there are any other things that people can think of, lets hope they add them here.

The absolute techniques to achieve all the above are well documented in various places which should be found using Google, for if I typed the full instructions, I would be here all night, and it is getting late.

Hope this helps.

---

### Post by chewearn on 2007-07-10
> **sgtbob said:**
> I want to connect two PC's in the same room via wire. Units are (1) Dell XPS 400, running Ubuntu 7.04 and Windows XP with a (2) Dell 8250, running Fedora 7 and Windows XP.

Knowing absolutely nothing about this process, could someone explain how to proceed or direct me to a site that explains in '**noobisms' **how to proceed?  I prefer to use cable/wire for the security that some articles indicate is desireable plus the <2 feet distance between the two.

From some preliminary data I have gleaned in reading forum postings, it appears that a connection via 'special' USB cables from a USB port on PC1 to a USB port on PC2 - is that feasible? What would I need? Is a simple USB cable useable or if not,  and if not, what is the 'special' cable I would need?

At present, I have both PC's connected to the internet through a D-link Ethernet Router and then to the cable modem, so how would this factor into the equation? Would one PC be the connection so that the other could also connect through it?

Advice and guidance solicited.

Numero uno noob!

Bob:confused:

Based on your description, it appears that both PCs are already in a network; i.e. they are already connected together via your D-link router.  What's next depends on what you want to do.

If it is file transfer, I suggest to use Samba server: enable Samba server on your ubuntu and/or Fedora.  I'm not sure about how to do this in Fedora, but in ubuntu, simple click the following menu on the gnome top panel (I assumed you are running gnome, instead of KDE or others):

System > Administration > Shared Folders

If Samba or NFS server is not already installed, ubuntu will prompt you to install either or both.  Choose Samba, because of compatibility to Windows.

Next, if you right-click on any folder (in Nautilus), you can enable sharing of the folder.  A minute or two later, the ubuntu computer and shared folder should appear automatically in your Windows Network Neighbourhood.

---

### Post by sgtbob on 2007-07-10
Well - I went to System --> Administration --> Shared Folders and I was not asked to install Samba, so presumed it was already installed (later verified via the synaptic suite).

So - I right clicked on several folders and each offered the 'shared option and now appear in a 'shared folder'.  Question is - how do I use them - nothing appeared and I did not see a 'Windows Network Neighborhood'.

I do have a 'disc' feature which allows me to access the Windows files on the same PC, but how to get to the second PC?

As I confessed - 'noobie-isms' must be employed since I really am new at this.

I do appreciate the replies and the suggestions, its helping me learn.

Bob

---

### Post by chewearn on 2007-07-13
> **sgtbob said:**
> 
So - I right clicked on several folders and each offered the 'shared option and now appear in a 'shared folder'.  Question is - how do I use them - nothing appeared and I did not see a 'Windows Network Neighborhood'.


Ok, sorry about that.  In Windows XP, it is now called "My Network Places".
If you don't see anything when you open My Network Places, click the link "View workgroup computers" on the left pane.

As for accessing the shared folders of other PC in Ubuntu, you click on: Top Menu > Places > Network

---

