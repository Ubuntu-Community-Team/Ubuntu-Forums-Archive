---
title: "[SOLVED] Parallels or VMWare"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by sanjinko on 2008-04-29
What are your experiences with using virtualization software?

Do you prefer more Parallels Desktop or VMWare Fusion? Or maybe VirtualBox?
:confused:
I'm thinking of installing one of them so I don't have to reboot between Leopard and Hardy Heron so often.

---

### Post by hajk on 2008-04-29
I'm a veteran of installing GNU/Linux on MacIntel hardware, starting in 2006 with Ubuntu Dapper on my just retired original MacBook: double-booting, single-booting (with OS X on an external HD), experimenting with Parallels for Mac. It was all great fun: how to make sound work, how to get the special keys to work, how to get the screen resolution right, how to get iSight going, and how to solve the temperature problems (boy, did that MB run hot in those early days!), etc. etc. *)

Now, recently I've upgraded my hardware to a 15" 2.4GHz MacBook Pro (the 4,1 model), ordered VMware Fusion with and -- for good measure -- maxed it out with 4GB of RAM. I've installed 64-bit Ubuntu Hardy and 64-bit mixed Debian testing/unstable VMs (giving them plenty of RAM) and I'm very pleased with how both of them perform. Actually, I'm amazed and feel no urge anymore to handle all the work-arounds of running GNU/Linux directly on the MacIntel hardware (there are still a few problems with the latest 4,1 models, like sound and wireless). 

Parallels for Mac is not really an option anymore, as it cannot handle 64-bit and/or multi-core hosts. The Debian install was absolutely without any problems whatsoever; the Ubuntu installer made a mess of the screen resolution (stuck in 800x600, both during installation and after a reboot), which I repaired by just copying the xorg.conf file from its Debian counterpart. Also, the open-vm-source and -tools package is only available in the Debian testing/unstable repositories, not in the Hardy repositories... a missed chance by the Hardy release team.

The above suits my needs, being a computing-oriented user, not a gamer. The VMware virtual graphics specification is SVGA, so don't expect fancy 3-D effects. 

*) I dropped out of these forums when MacIntel users were abandoned by the moderators late 2006, finding refuge in Debian. History is repeating itself right now, so this will be my last post in these forums, for a while at least. The mixed Debian testing/unstable I'm running right now is every bit as polished as Hardy, and will soon have more modern packages...

---

### Post by cyberdork33 on 2008-04-29
> **sanjinko said:**
> Do you prefer more Parallels Desktop or VMWare Fusion? Or maybe VirtualBox?I prefer VMware fusion myself, but either will work just fine.

> **hajk said:**
> *) I dropped out of these forums when MacIntel users were abandoned by the moderators late 2006, finding refuge in Debian. History is repeating itself right now, so this will be my last post in these forums, for a while at least. The mixed Debian testing/unstable I'm running right now is every bit as polished as Hardy, and will soon have more modern packages...
Care to elaborate via PM or other means? Please drop me a line.

---

### Post by mert on 2008-04-30
I have used both Parallels and Fusion and they both work pretty well.  I had trouble installing Breezy on Parallels so I ended up using a pre-installed disk image from the Parallels web site.  I don't know if Parallels has problems with Hardy but I just did an clean install of it on Fusion 1.1.1 and it worked fine.  As hajk says, Fusion supports 64 bit and dual CPUs so it is perhaps better.  Also, VMWare has an academic program, so if you are a student or staff, you might be able to get Fusion for free.

---

### Post by russo.mic on 2008-04-30
> **sanjinko said:**
> What are your experiences with using virtualization software?

Do you prefer more Parallels Desktop or VMWare Fusion? Or maybe VirtualBox?
:confused:
I'm thinking of installing one of them so I don't have to reboot between Leopard and Hardy Heron so often.

Screw'em both.  Virtualbox is awesome!  Easy to setup, and seems to me to be MUCH faster than VMWare and parallels.

Russo

---

### Post by larrinski on 2008-05-02
> **sanjinko said:**
> What are your experiences with using virtualization software?

Do you prefer more Parallels Desktop or VMWare Fusion? Or maybe VirtualBox?
:confused:
I'm thinking of installing one of them so I don't have to reboot between Leopard and Hardy Heron so often.

I had no problems installing Hardy 32 Bit on my Macbook via Parallels. The only issue I am having is that the wireless won't work. That is still a work in progress.

But the sound & trackpad works way better than when I had everything set up as a dual boot.

---

### Post by theltemes on 2008-05-02
I've never had much luck getting a good Ubuntu install in Parallels.

I just created a new Hardy VM with VMWare, everything worked out of the box except for the VMWare tools. There are instructions for re-compiling the openvm tools to fix that, and they worked flawlessly for me.

Due to other problems with Parallels and their lack of support, I ditched them for VMWare and have been really happy with my decision.

---

### Post by cybercookie72 on 2008-05-04
Parallels here ver 3 (5584) on a first gen macbook pro

As a matter o fact Im writing this on a fresh install....:)  I get to the internet with the "shared networking" ... in ubuntu it shows up as wired network.  

I use windowed mode while programing so I dont care about full screen...but if you want it...all you would need to do is add 1440x900 to the xorg.conf...not a big deal.

sound works just fine...although i dont use it..i use iTunes as i work in ubuntu.

I will downlad compiz and see if it works...i dont use it so dont know yet...ill edit this post with results..

well thats about it...have fun:popcorn:

------------compiz------------------
downloading the manager and with default settings could not start compiz WM
oh well..lol back to programing...good luck

---

### Post by Comhra on 2008-05-04
> **russo.mic said:**
> Screw'em both.  Virtualbox is awesome!  Easy to setup, and seems to me to be MUCH faster than VMWare and parallels.

Russo

Wish I could share your enthusiasm but 1.6 won't install on my Macbook.  The Beta version worked really well. 
I got the 1.6 from Version Tracker which redirected me to Sun Java.  I followed the installation instructions but did not work as advertised.
I'm still using Tiger (fully patched).  Maybe VirtualBox is just for Leopard?

---

### Post by davidj411 on 2008-05-20
i wish i were posting a solution and not another question, but hopefully this question gets answered and then the solution is available to all..

vmtools will not install on ubuntu (out of the box).
instead, i get two items dropped onto the desktop. one is an RPM package which i guess is only good on Red hat systems and the other is a file called vmwaretool-7.6.3.87978.tar.gz, which i extracted and could not find anything inside to work with UBUNTU. any ideas?

---

### Post by cyberdork33 on 2008-05-20
> **davidj411 said:**
> i wish i were posting a solution and not another question, but hopefully this question gets answered and then the solution is available to all..

vmtools will not install on ubuntu (out of the box).
instead, i get two items dropped onto the desktop. one is an RPM package which i guess is only good on Red hat systems and the other is a file called vmwaretool-7.6.3.87978.tar.gz, which i extracted and could not find anything inside to work with UBUNTU. any ideas?
extract the tarball and run the .pl script inside in the terminal.

---

