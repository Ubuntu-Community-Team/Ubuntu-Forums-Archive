---
title: "Apple wireless keyboard ... and mouse"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by DeadSamurai on 2006-06-05
Hi,
I don't know if anybody else is using the Apple wireless keyboard but here goes.
Before I decided to install Ubuntu on my mac mini I tried the liveCD and the keyboard worked flawless. After installing the "real" distribution I can't use it anymore. It's a bluetooth keyboard which shouldn't be a problem since I can use it when choosing to boot Ubuntu or OSX. So I guess there is some kind of "ps2 equivalent" emulation within the system. But why does it stop working? Any clues? 
The mouse hasn't worked at all though and I realy don't care if it can't be made to work.
Thanks,
Per

---

### Post by entangled on 2006-06-05
I am using an Intel Mac Mini and have installed Ubuntu on it. I tried the BT keyboard with the installed Unbuntu but I only got connection for a few seconds, then nothing. I haven't tried BT with the Live CD. I use a small USB keyboard now.

Did you install Ubuntu like me, partitioning from OSX, putting a lilo file onto windows and using Boot Camp? 

I had some problems with user permissions and with unionfs.
I still have problems with wpa wireless.

---

### Post by DeadSamurai on 2006-06-05
It's a ppc G4 1,5Ghz
I backedup my stuff in OSX the splitt the disk in two first for OSX and second unallocated. I let Ubuntu partition the free space. It's using yaboot instead of lilo/elilo (not EFI based). I don't know what Boot camp is.

---

### Post by tactus on 2006-06-05
Bootcamp is a beta solution for installing Windows on Intel-based Macs.

I am more experienced with OS X than with Linux, but it appears to me that OS X makes the keyboard recognicable by the OpenFirmware. This enables you to utility hardware features during boot like disk-target mode holding down "t", resetting of PRAM by holding down option+command+r+p, choose startup partition while holding down the option/alt key, and so forth. It appears to me that this pairing done in OpenFirmware makes your software recognize your input devices as standard USB devices and thus makes it possible to use the keyboard to choose OS in the Lilo/yaboot (?) menu. I've seen my bluetooth keyboard being fully recognized in Linux desktop my self at one point, and I know it wasn't due to me pairing the hardware in the Linux software. Perhaps your Ubuntu installation tries to do the right thing and take controll over the bluetooth module?

Not sure if this was any help, but maybe it added some insight on the situation. :-\"

---

### Post by DeadSamurai on 2006-06-08
I was pretty sure that the I used the Apple wireless keyboard the first time I tried Ubuntu on the mac ... I was right. It works when booting with the 5.06 liveCD. From what I can see (didn't spend much time looking at it) it doesn't see the keyboard as a perticual bluethooth device which needs to be paired (as tactus mentioned). It shows up as a USB device doing an "lshw -v". It'd be realy cool if could be fixed in an "easy" way.

I'll continue my quest to get it working in U 6.xx but help is always welcomme.
D.S
Adding a couple of readouts from useful tools like: lshw, dmesg, lsusb, lspci and lsmod.

---

### Post by gu3st on 2006-06-11
I have a similar problem, recently I bought an Apple Wireless Keyboard and a DBL-120 (Works in Windows and OSX) for Bluetooth, and I was wondering if people have gotten it to work.

---

### Post by Xeon3D on 2006-06-12
This is defenitely a BUG.
I just updated from 5.10 to 6.06 and in the middle of the update my Apple Wireless Keyboard stopped working. After a reboot, it doesn't work, as it did on 5.10.

Will someone with a little more experience than me post a bug report on the Tracker? I'd sure love to see this particular bug fixed as it almost stops me from using Ubuntu (I still have a s***ty as hell USB Keyboard...).

There was a solution posted on the 5.10 forums, that said that if you remove bluez packages, it would fix it (note: it was written for 5.10). When I tried to do that (using just the mouse which was a PITA) it told me that it would also remove "ubuntu-desktop", so I stopped.

---

### Post by nkbj on 2006-06-13
This seems to be a known bug: [https://launchpad.net/distros/ubuntu/+source/bluez-utils/+bug/32415](https://launchpad.net/distros/ubuntu/+source/bluez-utils/+bug/32415)

---

### Post by Ptero-4 on 2006-06-13
Ubuntu-desktop is a meta-package. It doesn't contain the actual apps, it's just the info needed by apt-get to do the dist-updates. Ubuntu-desktop is safe to remove.

---

### Post by macattack on 2006-11-14
First off I am using a mac mini PPC G4 and V 6.10 of ubuntu. I got my bluetooth keyboard and mouse to function by removing the blueZ in synaptic package manager u(nder the System-administrator).  Then I rebooted the mac mini and both my mouse and key board are working perfectly.  Hope this helps

---

