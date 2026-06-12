---
title: "Drive mounting shortcuts/launcher"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Bigbird999 on 2007-11-29
I have a home network with windows shares and a 3 drive -750 GB  NAS (Naslite) server which windows and Linux see as a windows share on the network.  I have created launchers on my desktop to mount various drives when I want to watch video or listen to music on my Ubuntu laptop.  .  

To connect to my windows machines, I created a launcher that executes
```
sudo mount //192.168.0.11/E /media/EonErniepc -o user=ernie,password=xxxx
```
I double click on the Laucher and my windows drive is mounted on the desktop.

If I type 
```
sudo mount smb://192.168.0.20/Disk-1 /media/BU -o user=admin,password=yyyy
```
in a terminal it mounts Disk-1 on the NAS server.  but the launcher I created with exactly the same code does not do anything.  Anybody have any idea why?  I want to be able to mount the NAS server disks the same way (ie from the launcher).

Why would the command work from the terminal but not the launcher?

BB

---

