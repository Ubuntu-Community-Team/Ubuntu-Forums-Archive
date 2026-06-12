---
title: "please help with install on older computer"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Adam590 on 2007-11-15
As my newer, primary computer is experiencing some extreme hardware issues, I'm stuck with having to make a serviceable work/browsing machine out of my wife's older PC.

basic specs:

333 Mhz Pentium II
6.4 GB hard drive
128 MB ram (I've been told this type is too expensive/rare to upgrade easily)

This computer ran Win98 fairly well, IIRC, but I've no need to keep that, so I'm going for a full wipe/install.

I have a standard Ubuntu 7.04 cd and an alternate install cd of the same. I also have internet access through a second machine with a cd burner, so I can opt for other distros if advised (though DSL didn't work, for some reason - it kept hanging on a step having to do with determining a network something-or-other).


What I'd like, if at all possible:

-decent GUI desktop
-Firefox
-OpenOffice
-some image editor (I'm used to GIMP) 
-use of PPPoE - this older computer does have an ethernet port and could connect to our ADSL via Win98

Any advice, especially including recommended partitioning?

TIA

---

### Post by CatKiller on 2007-11-15
[Xubuntu]("http://xubuntu.org/") is fine. You might still struggle to get the live cd working though with that little RAM- I'd try to install from the Alternate cd instead. 

OpenOffice.org is a bit heavy for that machine - Xubuntu comes with Abiword, which is lighter. OpenOffice.org can still be installed in the usual way through Synaptic though, as can the GIMP.

If there's an ethernet port then connecting it to the Internet really shouldn't be a problem. Possibly a router would be a good investment if you've more than one computer there?

Otherwise, for an even lighter environment, some people recommend [Fluxbuntu]("http://fluxbuntu.org/"), which uses FluxBox. I've never used it though, so I couldn't say.

My 70-year-old technophobe mother managed to install Xubuntu on her ancient laptop though.

---

### Post by Adam590 on 2007-11-15
Thanks for the tip on Xubuntu.

On my newer (out-of-order) machine, I was using a [/, /home, swap] configuration. Is that appropriate in this case, too? If so, how should I allot the 6.4 GB of space?

Also, in my attempts to install the command line version of the Ubuntu 7.04 alternate install cd I already have, I kept wondering about the "boot flag" option I get during the partitioning process. Is one of the partitions supposed to have "yes" entered here? (the default is "no")

---

### Post by bulldog on 2007-11-15
I should let xubuntu take care of partitioning,let it use the whole hdd,a separate /home is not usefull on such small hdd.
The bootflag should be set enable on the / partition,if you choose to let xubuntu do the install,it will take care of that.

---

### Post by glotz on 2007-11-15
open office will be very slow, try abiword
also gimp could be slow

If I was you, I'd download the old Dapper server install and then install xcfe or fluxbox on it.

---

### Post by Adam590 on 2007-11-15
glotz - what would be the benefits of using an Ubuntu Dapper server install vs. Xubuntu's (Dapper) alternate install cd?


(to all) - Also, in trying to install anything, I keep getting this message: 

"Network autoconfiguration failed. Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly."

As mentioned above, we connect via PPPoE to our ADSL service. Is that something I can configure afterwards, skipping the DHCP stuff during the install? I tried that a previous time, but even though PPPoE loaded, seemed to run correctly, and listed eth0 as available hardware, it wasn't able to "find" anything in order to proceed to the next step. Are there settings/configurations I'll need to modify?

---

### Post by mike555 on 2007-11-15
If you can't get anything installed and need to use it , you might get " Puppy " Linux , it is very small and will run off the CD to get you online , at least till you get going with another OS ........

---

### Post by glotz on 2007-11-15
The server install contains least bloat to remove after installation. You'll have to install a window manager on the other hand. Basically it's all the same chassis with custom packages, so it's really what you prefer. Just be sure to rip off anything you don't need on such an old box. Don't really know too much about the networking setup.

---

### Post by Inxsible on 2007-11-15
Fluxbuntu is also something that you might wanna try out. Its very lightweight

---

### Post by Adam590 on 2007-11-15
Thanks for the advice. I've installed Xubuntu Dapper as a server, and I let the installation take care of the partitioning process. Everything seems to load fine, but I'm having trouble with using pppoeconfig to get online. The installation part worked, though, so I posted about it [[COLOR="Blue"]**_here_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=613814") in the Networking forum. Thanks again.

---

