---
title: "Networking problems- Help setup 7.10"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Stjames on 2008-03-23
I am sure there is a million post out there about this but i cant seem to find just the right place.  I have an HP Pavilion DV5000 with a BCM 43xx wireless card i cant seem to figure how to get wireless working. I am new to Ubuntu from Windows.  

when i run iwconfig 
  lo     no wireless extensions
  eth0       no wirless extensions

I have updated Ubuntu but that is about it.

So any help on this would be great, thanks.

---

### Post by ghost_ryder35 on 2008-03-23
> **Stjames said:**
> I am sure there is a million post out there about this but i cant seem to find just the right place.  I have an HP Pavilion DV5000 with a BCM 43xx wireless card i cant seem to figure how to get wireless working. I am new to Ubuntu from Windows.  

when i run iwconfig 
  lo     no wireless extensions
  eth0       no wirless extensions

I have updated Ubuntu but that is about it.

So any help on this would be great, thanks.
Before anything:
1.make sure universal repositories is checked (if your using wired internet connection)
2.sudo apt-get update

Wireless card using BCM43XX-FWCUTTER (requires wired internet connection, or a cd with the package on it)
```
sudo apt-get install bcm43xx-fwcutter
sudo modprobe bcm43xx
```
then restart computer and all is good
```
sudo iwconfig 
```to check

---

