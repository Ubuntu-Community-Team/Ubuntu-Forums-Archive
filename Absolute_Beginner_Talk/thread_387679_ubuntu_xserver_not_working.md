---
title: "ubuntu xserver not working"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by ravis_31 on 2007-03-18
hi there,
      This is gonna be long.Sorry for being a noob :(...I have an ati x700 on my acer ferrari laptop and had faced initial xserver startup issues during live cd sessions,so i used the alternate cd to install.Faced a few partitioning issues while installation but got those resolved somehow an successfully installed ubuntu.After going through the forums i already knew that there was an ongoing issue with the ubuntu not working with ati cards and had to be manually reconfigured.
When i booted into recovery mode i ran **sudo-dpkg repackage xserver-xorg** as instructed and went through most of the settings.my card was detected correctly but gave me an error on PCI:1:0:0 initially but when i retried it went fine.After going through all the boxes.i ran **startx**.
I can hear the startup sound but still could not see anything on the screen
I tried manually editing the xorg.conf file in vi and changed it to vesa and radeon but still no luck.
Could someone please let me know what needs to be done now.

i heard that linux installation is gonna be a pain in the a** but not such a sore.Atleast i have it installed and its only the xserver which is problematic.

EDIT:How do i find out whether PCI:1:0:0 is correct or not?
EDIT2:when i access system>administration>networking it says "Configurations could not be loaded,you do not have access to this blah blah"
How do i login as root and not as user?

---

### Post by sad_iq on 2007-03-18
Try looking at this page about installing the drivers for your card: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) 
 Also there are many pages about installing linux (not just ubuntu) on acer laptops:
  [INDENT][http://tuxmobil.org/acer.html](http://tuxmobil.org/acer.html)[/INDENT]
[INDENT][http://www.linux-on-laptops.com/acer.html](http://www.linux-on-laptops.com/acer.html)[/INDENT]
 Google some more if needed!!!

---

### Post by annda on 2007-03-18
can you post the output of the following command (errors in your xorg log)

grep 'EE' /var/log/Xorg.0.log

---

### Post by ravis_31 on 2007-03-18
thank you very much guys,really appreciate it
but i was just going through the troubleshooting documentation and got [this]("https://wiki.ubuntu.com/EdgyKnownIssues/22985")
and you know what it worked!!!yay
now i have the gui
thanx to the all those who patiently replied to my questions.I can now go about configuring my network.If possible could someone direct me as to how to do it?

travis

---

### Post by ravis_31 on 2007-03-18
i'm currently referring to [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_activate.2Fdeactivate_network_connections") guide to configure my network but when i select system>administration>networking, a message box says "The configurations could not be loaded,You are not allowed to access the system configiruration" i thought i was logged in as root?How do i log into root now?

travis

---

### Post by annda on 2007-03-18
this is strange - it should ask you for your password.

as an alternative, use the terminal or ALT+F2 and type:
gksudo network-admin

---

### Post by ravis_31 on 2007-03-18
thanx for the help..it worked :),now how do i configure my network?
i have a netgear DG834G router with ethernet access point and i have attached the cable from the router to the laptop.Now how do i go about configuring my network?

travis

---

### Post by annda on 2007-03-18
a couple of quick ideas:

1) set your wired/eth0 connection to DHCP and activate the changes. reboot if necessary (sometimes it is, i don't know why)

2) ifconfig (in the terminal) to check if you get an IP address from your router (inet addr)

3) if you still have no internet access, post a new thread with the output of ifconfig - some people know a lot about and have experience with networking, but not much with xorg, so they will not be reading this thread.

---

### Post by ravis_31 on 2007-03-18
thanx very much annda,a few more q's
how do i set wired/etho connection to DHCP?
is it from System > Administration > Networking?

i will post the output for ifconfig if it gives me a prob again.
thanx again
travis

---

### Post by zvacet on 2007-03-18
system>administration>network setting>highlight your modem>properties>select type of connection you want>chek upper left box>close
Click on DNS and you will see one address and replace it with your nameservers>close
```
pppoeconf
```
I hope it helped

---

