---
title: "powerbook G4 trobble big trobble"
date: 2008-04-15
forum: Apple PPC Users
---

### Post by ryrules1 on 2008-04-15
ok, so I have a powerbook g4 1.6 ghz and i want to install Ubuntu 7.10 on it. So last night I put in the Mac leopard install disk from my new macbook pro so i could partition the hard drive. Of course it said you can install looped (because it didn't come with the powerbook) so i reformatted the hard drive as a ms dos fat hdd and then tired booting from the ubuntu live cd using Control-Command-Shift- delete and nothing happens it just spins the disk for a while and has a mac folder with a question mark on the screen the hole time. a little help??? please and I dont have the install disk that came with my powerbook just the install disk that dosnt work except for formatting htat came with my macbook pro last night. and from some reason holding "C"while booting has never worked for me i dk its weird. HELP.

---

### Post by ditsch on 2008-04-15
You mean Command-Option-Shift-Delete, don't you?

---

### Post by ryrules1 on 2008-04-15
yes, command-option-shift-delete.

---

### Post by swash_buckle on 2008-04-15
Do you have a binary version of Leopard?  I know when I tried to install Tiger on my iBook a while back I got the same result, the problem being that I had an Intel install disk for my iMac, but a PPC iBook.

I had to find the install disk for my iBook to get it running again, and it now runs very happily with Leopard and Kubuntu now that I've got a binary copy of Leopard.

---

### Post by stream303 on 2008-04-15
> **ryrules1 said:**
> ok, so I have a powerbook g4 1.6 ghz and i want to install Ubuntu 7.10 on it. So last night I put in the Mac leopard install disk from my new macbook pro so i could partition the hard drive.

Are you trying to dual-boot or just dedicate the whole G4 powerbook to Ubuntu?  If you are going to dedicate the whole thing, no need to partition first - just boot with the Ubuntu ppc image, and let it "use the whole disk".  It will destroy any existing partitions and proceed to partition the whole disk on it's own.  Get your data off of it first!

> Of course it said you can install looped (because it didn't come with the powerbook) so i reformatted the hard drive as a ms dos fat hdd and then tired booting from the ubuntu live cd

Ok, sounds like the whole drive is gone now. :)  Are you sure you are using the PPC-specific Ubuntu installer, and not one made for Intel's?  Here's the link for Gutsy 7.10 ppc.  I recommend the "alternate" image and not the live-cd desktop:

[http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/)
as a first install, it might be better to go with Feisty 7.04 to get your feet wet:
[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

Be sure to burn it as an iso, and not just copy it over to the cd.  I would burn it at a low-speed, somewhere around 4x to 8x perhaps and then see if you can boot holding down "C".

---

### Post by ryrules1 on 2008-04-16
> Ok, sounds like the whole drive is gone now. Are you sure you are using the PPC-specific Ubuntu installer, and not one made for Intel's? Here's the link for Gutsy 7.10 ppc. I recommend the "alternate" image and not the live-cd desktop:


haha i am an idiot. I just couldnt find this link anywhere on the ubuntu page, thank you. It is up and working after some boot problems, however I am still suck on how to disable tap using the trackpad command I keep getting no device. Also my airport exteme isnt working even after installing rectred drivers if anyone cant help it would be greatly appricated. I am also reilizing now that my spell cheak isnt working as well because I am sure I spelt "reilizing" wrong. hahaha if you know anything about these problems please help.

---

### Post by zeus123 on 2008-04-17
check the hardy success topic. I got my airport extreme card woerking.
There are lots of bits which dont work though. I might just install debian or dapper.

---

### Post by ryrules1 on 2008-04-17
yea, i am having a pretty rough go with ubuntu and this Powerbook but ubuntu diffidently has the best support out of any linux distro.

---

