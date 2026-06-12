---
title: "dual booting ubuntu and xp.  Ubuntu not seeing wireless dongle help!!!"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by DraeLee on 2006-10-16
I neeed some help i am dual booting xp and ubuntu which so far is working correctly.  I got it partitioned correctly and all thanks to a guide i found here.  My problem is I am using a WG111T v1.3 wireless dongle.  Ndiswrapperv1.25 i hae installed and it does recognize both drivers and says the hardware is present.  Even has a pcid (i believe is what the number is next to present).  However for some reason ubuntu is not picking up my wireless dongle as part of the startup.  I did modprobe i added ndiswrapper in the /etc/ndiswrapper i did all of what i thought i could find.  I am writing now because i am truly at a brick wall.  Ive looked and read and did all that i thought i should do before i ask for help officially.  So now I am asking anyone if they can help me figure out why ubuntu does not recogize my dongle.  Sometimes it do sometimes it dont.  almost like its a gamble.  Thx in  advance to all that can help.  Ill chk back regulary so I will be prompt.

---

### Post by DraeLee on 2006-10-16
bump

---

### Post by DraeLee on 2006-10-16
please anyone help me lol im at a wall for this

---

### Post by DraeLee on 2006-10-16
someone ppppplllsss help me with this lol

---

### Post by DraeLee on 2006-10-16
ok is it me do i smell bad

---

### Post by blx_286 on 2006-10-16
I used to have that card and got it working with ndiswrapper and ndisgtk. I'll check my notes when I get home and see if I can find anything for you. While you're waiting, have you tried searching the forums?

Just an FYI, if you post several threads with the same question, you may be ignored.

---

### Post by DraeLee on 2006-10-17
yea i tried and i found a lot of useful information, and ndiswrapper does show that its present but the networking settings does not seem to load it up during boot.  ive even tried to unhook the dongle and rehook it and still under the network settings it doesnt find so im not sure what to do.  every now and then when i reload ubuntu it will pick it up but thats like 2 out of 10 reboots maybe

---

### Post by Fully216 on 2006-10-19
Now that I have found your post, I will see what I can dig up tonight, and I will try to post something tomorrow.  In the meantime, I would be more helpful if you posted specific details of the problem.  

For example, what driver are you using (32-bit/64-bit) and where did you get it from?  What specific version of ndiswrapper are you using?  What specific commands did you use and where did you get stuck (possibly modprobe)?  What other methods have you tired?

---

### Post by Fully216 on 2006-10-19
According to the ndiswraper website (I emailed to you), your netgear dongle should work fine with ndisrapper.  Specifically,

Card: NETGEAR WG111T

    * Chipset: Atheros USB
    * encryption: WPA-PSK (TKIP)
    * usbid: 1385:4250
    * Driver: Netgear windows driver Version: 21/06/2005, 1.2 from [http://www.netgear.de/download/WG111T/WG111T_GRV1.2.zip](http://www.netgear.de/download/WG111T/WG111T_GRV1.2.zip)
    * Other: This driver comes with two sets of .inf and .sys files: athfmwdl and wg111t. Both of these must be installed with their *.inf files. After that, with version 1.7rc1, ndiswrapper can be used as in the case of other drivers; earlier versions of ndiswrapper required load_fw_ar5523 program to be run, but it is not needed anymore. Suspend/resume also works now. 

As mentioned you could try version of ndiswrapper 1.7 or later.  Which version did you try?  Did you use the listed drivers and install both of them?

---

### Post by DraeLee on 2006-10-21
thank you i am using ubuntu 32bit i have an amd64 3200+ processor.  sorry i didnt get back sooner I had just gotten my land line (lol) so that i will have the internet on ubuntu and then i can solve the problem in ubuntu instead of going back and forth.  thank you again for the reply im gonna read the email now. oh i was using ndiswrapper 1.26 which i believe was the lastest but i did reinstall ubuntu and did ndiswrapper with automatix

oh also i at first used the drivers off of the disk then i went to the site and put the drivers (both of them) on the hd and the ndiswrapper found both of them and gave them both an hd id and at that point when i first install it will work fine but as soon as i restarted the pc it is not recognized in the network settings, but ndiswrapper does show that it is present.

---

### Post by Fully216 on 2006-10-23
That is strange that it would work once you installed ndiswrapper and not once you rebooted.  This might indicate you have multiple versions of ndiswrapper on your system.  One way to find out would be for you to post the output of dmesg.

There is a version of ndiswrapper available in the repos, which is older than the version you mentioned, since they use a stable version.  If you want to use the bleeding edge (v1.26), then this package in the repos should NOT be installed.  I would go to synaptic package manager and make sure that it is not selected, including ndis-utils.  I am also assuming you used automatix2 to install things on your system, since you have an amd64 system and regular autmatix would not work well.

According to the automatix wiki, [http://getautomatix.com/wiki/index.php](http://getautomatix.com/wiki/index.php), it also installs a gui for setting up your network called ndisgtk.  You might also try this to see if you can root out the conflict.

The ndiswrapper site explained that the drivers on the CD will not work, which is why I posted the above link.  I would uninstall them from your system and remove them so you won't get confused in the future (kernel upgrade that will require you to reinstall ndiswapper for example).

It also sounds like the best way to get it working is to walk through the install process step by step to make sure there are no problems.

---

