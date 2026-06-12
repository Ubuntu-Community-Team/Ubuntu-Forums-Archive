---
title: "Fun with VMware?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by firestorm_v1 on 2007-12-12
It's time for more FUN with VMWARE.. puke.

Ok, here's the deal.  I have two VM machines set up with VMware on my laptop which is an Intel Pentium 4.  I migrated one image to my server which is an Athlon system.  The odd thing is that when I fired up VMware server on the athlon, it properly booted and initialized the vm and everything *appeared* to load without issue.  When I fired up my network manager, it could not see the VM that was now running on the Athlon.  Thinking I had screwed up the bridging, I started poking around until I found out that Ubuntu post-migration did not recognize the ethernet network adapter.  The modules for the vm network card (pc net32 and mii) were loaded and when rmmod'ed and modprobe'd  /var/log/messages indicated that it had found the network card, but any attempt to configure eth0 in the VM resulted in a "eth0 :error fetching interface information: Device not found."

Thinking that maybe when ubuntu did the original install on the laptop's Pentium4 chip VMware passed the processor info into the installer and the setup was tailored around the P-4.  I was able to manually install the linux-i386 package (god, what a nightmare apt-get becomes when you don't have internet connectivity) and rebooted the VM praying that the NIC would come up.   It didn't.

I'm at my wits end and I would prefer not to have to reinstall and recreate the VM from scratch as I *just* got it configured and then an early x-mas present arrived which prompted the migration. (new motherboard and RAM)

Anyone have any ideas or am I off my rocker?

---

### Post by Threbus5 on 2007-12-12
Hi,

This may help provide potential direction.
Maybe.

When I configured a VMserver I had problems with NIC conflicts. In other words the laptop had more than one ethernet card and depending upon the startup timing one or the other automatically became the master. At that point, the other card would not connect.

So, bottom line, check the (I believe) Ifconfig and see if all the ethernet cards are set to auto. If so, choose one as default by removing the "auto" from the others. Then bridge the VM connection to the default card.

Of course, if your laptop has only a single ethernet card, disregard all of the above.

Lastly, exercise plan "B" and reinstall. Urk.

Good luck..

---

### Post by firestorm_v1 on 2007-12-12
I just might have to.

On a wing and a prayer, I grabbed some pegasus based USB thingy and plugged it in.  My XP host recognized it then promptly complained that Local Area Connection 15 had no connection.  I added it to the VMware session under test and I saw the same thing happen.  Ubuntu identified it correctly as a Pegasus device and loaded the proper modules, but again trying to ifconfig eth0 resulted in no interface.  I think (and pray) that I am going to blow away all the configuration data from the migrated vmware disk except the disk files and see if I can create a new install and specify the old disk images.

Well, hold on to your butts......  (from Jurassic Park)

---

### Post by firestorm_v1 on 2008-01-10
Well, I thought I had a fix..

After fumbling around with VMware configuration scripts and whatnot I was never able to get the ethernet NICs working in Ubuntu.

Thankfully I didn't have much working on those ubuntu images so I said eff it and blew them away and did new installs (thank god for PXE boots).  I have migrated other images that I had as well and didn't even have a problem with a Windows XP guest.  (HA! Take that WGA!!!).

Oddly enough, I migrated a couple of RedHat images and they worked well too.  I'm really confused now... 

:confused:


Is there a way that I can move this topic into the Virtualization category of the forums or is that something that the Mods can do?

---

