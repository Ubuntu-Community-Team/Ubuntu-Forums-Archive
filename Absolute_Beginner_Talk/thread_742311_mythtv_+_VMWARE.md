---
title: "mythtv + VMWARE"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by guilly on 2008-04-01
Just out of curiosity has anyone been successful in running mythbuntu on virtual box or vmware. I'm thinking of building a mythubuntu box but if i can manage getting it to work on my current desktop with just a few simple upgrades instead of building an entire different box that woudl be great!!

Thanks

---

### Post by foxbuntu on 2008-04-01
Successful for Dev, absolutly, watching TV on it..not going to happen, sorry. VMWare Server has too slow of a Video Driver to make this work in an acceptable manner for watching TV.

---

### Post by Slushdoot on 2008-04-01
I tried to set my mother up with a Mythbuntu VM with Virtualbox on Windows.  It works OK but the CPU useage is silly high on her new, fast machine.  Without hardware graphics acceleration it makes for a less rosy user experience.  This was only as a frontend.  I don't know how it would deal with accessing a PCI capture card but I imagine it'd be able to do it sufficiently well.

I assume your current OS is a variant of Windows.  If so, why not dual boot?

---

### Post by guilly on 2008-04-01
I'm currently running Gutsy 64bit and Vista, I'm really unfamiliar with all of this Mythtv but I'm thinking of installing it as a back-end for pvr purposes. However I would like to still be able to use Gutsy while having Mythbuntu running on a VM for all of my pvr needs, does this make sense or am I way out to lunch? or would I be better off installing mythtv onto my gutsy install?

Thanks

---

### Post by Calash on 2008-04-01
I wonder if a MythTV backend would run well as a VM.  The only issue would be the capture cards...

---

### Post by warp99 on 2008-04-01
If you have a single machine as a backend you can reduce you requirements to run HDTV, then have a frontend on your windows box.

[http://www.mythbuntu.org/requirements](http://www.mythbuntu.org/requirements)

If you don't need HDTV then any cheap box will do. I build mine for about $175.00 complete including a used IBM Netvista box. The only real problem was that the $15.00 MSI TV@nywhere card was not well supported and after some extensive searching I had to re-compile some modules with patch code for the cx88-tvtuner and cx88-alsa modules.

It would have been much easier to buy another cheap tuner card, but dagnabit I wasn't going let that card beat the best of me.

---

### Post by Slushdoot on 2008-04-01
> **guilly said:**
> I'm currently running Gutsy 64bit and Vista, I'm really unfamiliar with all of this Mythtv but I'm thinking of installing it as a back-end for pvr purposes. However I would like to still be able to use Gutsy while having Mythbuntu running on a VM for all of my pvr needs, does this make sense or am I way out to lunch? or would I be better off installing mythtv onto my gutsy install?

ThanksNo need to do a fresh install of Mythbuntu then since you already have a working Ubuntu system.  Install the Mythbuntu control center and go through it to have it do 90% of the MythTV setup.
sudo apt-get install mythbuntu-control-centre

With it, you specify the machine's role, primary backend and frontend. It helps you configure capture cards, IR remotes, install restricted media codecs, connect to the database, install different desktop packages, install MythTV plugins, install and use system services like VNC, ssh, Samba, and NFS, and further configure your hardware.> **Calash said:**
> I wonder if a MythTV backend would run well as a VM.  The only issue would be the capture cards...I bet it would work well since so many enterprises use MySQL, Apache2, and PCI devices in virtual machines.  A VM in this case  is unnecessary IMO.

---

### Post by guilly on 2008-04-01
Alright so just so I'm clear the backend would be "the database" and the front end is my gui interface? if that is the case. if I were thinking of configuring my desktop as the "backend" how is ps3 support for the front end? and should the "backend" be configured by installing mythbuntu through VM or the other approach that was mentioned by slushdoot which is just installing mythtv onto my already gutsy install? And I thik it is worth noting that I would be looking for HDTV support....

Thanks for the advice once again!!

---

### Post by Slushdoot on 2008-04-01
Read up on Myth at the MythTV wiki.  The backend is the program (group of programs, actually) that does all the recording work.  It stores its data in a MySQL database.  The frontend is the part you use to view content.  YOu can have both of these on one machine, or you can split the two.  You could definitely run the backend on your machine in either a VM or natively on your Gutsy install (this would be vastly superior).

[http://www.mythtv.org/wiki/index.php/MythTV_on_Playstation3](http://www.mythtv.org/wiki/index.php/MythTV_on_Playstation3)
Seems to suggest that some people are playing with a PS3 as a frontend but it's not done yet.  It's complicated becasue Sony's hypervisor doens't allow Linux to access the graphics hardware.

The whole thing can go on your existing Gutsy install, there's no reason to bring VMs into teh equation if you don't *need* to do so. :)

---

### Post by guilly on 2008-04-01
Awsome....

Thanks

---

### Post by Slushdoot on 2008-04-01
If^H^HWhen you run into trouble when installing Myth create a new thread in the appropriate forum.  I'd be glad to help you along there.

...PM me if I don't see it. :p

---

