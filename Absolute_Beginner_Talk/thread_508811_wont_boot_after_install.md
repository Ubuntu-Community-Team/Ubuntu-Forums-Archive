---
title: "wont boot after install"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by burtyburr on 2007-07-24
God this is soo frustrating.I am trying to install ubuntu 6.06 onto a p3 IBM thinkpad 2647 with 128mb ram.No matter what i do I get the same error.I have tried both the live and alternate iso.I have tried the newer version of ubuntu but same problem.
     The computer sets up ubunto just fine.Then I reboot.As everything is loading I get an error about piix4_smbus on an ibm thinkpad  and something to do with the risk of a flash eeprom.Then i get the regular ubuntu splash with everything loading...ok.Then i just get a flashing curser and thats it.It just hangs there.Occasionally I also get the sound effect of 2 bongos being hit.I am unable to switch to a shell.
     Can anyone plase help as i don Not want to have to go back to Windows

---

### Post by FleetAdmiral74 on 2007-07-24
This is quite a pickle. 

128 megs is low for Ubuntu I believe. Possibly try out Xubuntu or Fluxbuntu, they are much lighter weight. 

Oh, and we don't want you to have to go back to Windows either :)

---

### Post by AceofSpades19 on 2007-07-24
I can barely run GNOME on 256 so ya go with Xubuntu or Fluxbuntu

---

### Post by benx009 on 2007-07-24
there is a fluxbuntu?  never knew about that...

---

### Post by w4ett on 2007-07-24
Here is the fluxbuntu page:

[http://fluxbuntu.org/en/node/3](http://fluxbuntu.org/en/node/3)

---

### Post by burtyburr on 2007-07-26
aaahhh.....well there is a bit of a problem. It HAS to run on 128mb of ram as this version of edubuntu is being supplied to schools as part of the camara.ie project in africa.They are able to get it to run on most of the desktop pc's out there but not the thinkpad.
I agree that Ubuntu is a bit of a resource hog in this regard, I use slackware myself. But they desperate for a fix for this bug.
Origionally the laptops came with win2k and they were dualbooting with linux. I have a fear that if this is not resolved then there first experience of both computers and linux will be a bad one. The error message that is seen is [ 193.873427] piix4_smbus 0000:00:07.3: IBM system detected; this module may corupt your serial eeprom! Refusing to load the module!
Is it possible that this an issue with the grub loader?
is it possible to enter a parameter at the boot that will by pass this problem?

---

### Post by burtyburr on 2007-08-01
Ok. I searched around a bit and found that the piix4 error message is standard for this type of laptop (IBM T-22). I ran
dmesg ¦ less
and narrowed the problem to a problem in the xserver.
I checked out
/etc/X11/xorg.conf
by booting into the recovery mode and logging in.
I saw nothing unusual there but i lowered the resolution to "800x600" by
sudo vim /etc/X11/xorg.conf
where vim is a text editor.I entered the edit mode by pressing i and changed the default settings.I then wrote to the file with :w and quit out with :q!
This did no good.
I also tried the following options by editing the kernel line in 
/boot/grub/menu.lst
as above.
acpi=off noacpi
pci=off
But this did not work.
Finaly what worked was
boot into recovery mode
login as root
edit the xorg.conf file by adding 
Option    "BusType" "PCI"
Option    "DmaNode" "None"
in the "Devices" field.
Seems to work ok for now
more inf here [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617)

---

