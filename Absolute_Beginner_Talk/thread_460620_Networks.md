---
title: "Networks"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Cerealbh on 2007-05-31
Roomate and i are trying to create a network to share music, just install linux on his and ive only done basic linux things but am "pro" at windows can't i just create a folder in network and ti will be shared or is there a method i have no idea about

---

### Post by dave-5B on 2007-05-31
one way would be to use samba which allows you to share folders like windows, they are readable by windows computers too, there are much faster and better ways out there but this will work

sudo aptitude install samba smbfs

Once installed , just go to:
System > Administration > shared folders

it is fairly obvious what to do next :)

if you want to share folders securely using a faster protocol that SMB (windows sharing protocol) this is probably your best bet:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29)

it will require some extra effort though

---

### Post by Cerealbh on 2007-05-31
ty very much for the help :)

---

### Post by Cerealbh on 2007-05-31
erm i feel like a retarted ive created the shared folder and targeted my computers but none of the 3 computers i have here 2 linux  7.04 and a windows XP can veiw the network, i can view the windows network but not either made on either linux box, im looking into the SSH now any advice on the other one? or was that program made for windows to linux only?

---

### Post by dave-5B on 2007-05-31
ok if you have a windows computer then samba is def the way to go (ms are way to cool to use ssh) it will do windows - linux & linux - linux

---

### Post by dave-5B on 2007-05-31
you might want to check that all teh computers are actually networked together properly (like ip addresses and everything)

if you can view a shared folder on the windows computer (from linux Places > Network) then this is the case, if not then you need to make sure they are getting Ip's from the DHCP or static ips are configured correctly, whatever
EDIT: this can be done similar to XP in System > Admin > Network

---

