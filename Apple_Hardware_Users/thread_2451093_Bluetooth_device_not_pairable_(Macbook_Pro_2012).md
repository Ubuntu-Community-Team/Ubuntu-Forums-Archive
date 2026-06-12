---
title: "Bluetooth device not pairable (Macbook Pro 2012)"
date: 2020-09-26
forum: Apple Hardware Users
---

### Post by Leilani on 2020-09-26
Hi,

a while ago I installed Ubuntu on my Macbook Pro (2012), and after initial problems with setting up the WiFi drivers everything has been working flawlessly. Unfortunatly Im now struggeling with connecting my Bluetooth speakers (Philips SB5200, 2015).
Whenever i go into the bluetooth settings the system does detect the box and lists it as "not set up". I guess the way it should be working is that I click on the device and it then should start to connect, unfortunatly this is not the case. I click on it and after a short period of loading it still sais "not set up". 


first thing i tried was:

    sudo apt-get update

which didnt solve the problem


I then tried purging and reinstalling the bluetooth drivers with

sudo apt-get purge blueman bluez-utils bluez bluetooth
sudo apt-get install blueman bluez-utils bluez bluetooth


unfortunatly the last command throws the following error:

Package bluez-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  bluez:i386 bluez


E: Package 'bluez-utils' has no installation candidate




I then tried (out of despair): 

 sudo apt-get install blueman bluez:i386 bluez bluetooth




which trhows the following error: 

The following packages have unmet dependencies:
 bluez : Conflicts: bluez:i386
 bluez:i386 : Conflicts: bluez
E: Unable to correct problems, you have held broken packages.




as a result i now cant even activate bluetooth anymore haha

any suggestions?

---

