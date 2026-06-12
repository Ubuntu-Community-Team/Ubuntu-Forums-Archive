---
title: "Launching XP inside of Gutsy"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by teddybairs1 on 2007-12-17
OK, Does anyone know if you can launch a bootable XP partition inside of QEMU or KVM if it's not an actual image? I'm trying to activate a Civ 4 game I downloaded from Dell. I loaded it on my windows partition, and it says that in order to run it, I have to be connected to the internet. The problem is that my windows partition's networking abilities are hosed, so it's dial up only for it. Now the problem is that I don't have a working landline in my house. I use either Skype or cell phones. See my problem. I've tried installing it under Wine, and it's a no go. It gives me an error message. So I got the idea of trying to mount the XP partition in a virtual machine under Linux, which is fully functional, but Qemu keeps telling me I can't do that. any ideas?

---

### Post by Yellowdog428 on 2007-12-17
I don't know if this is what you are looking for but here are some instructions that describe running a virtual machine in VMware on a partition.

[http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu)

I cannot say if it works or not, cause I have my windows on another drive and I cannot get VMware to look at both drives at the same time, but It seems it should work OK.

I have heard that running a 3d accelerated game in a  virtual machine wont work very well.

Good luck!
Cheers

---

### Post by teddybairs1 on 2007-12-17
Thanks, I don't know if vmware will run on my system but I'll give it a go.

---

### Post by KhaaL on 2007-12-17
There's no point to install QEMU, VMware or VirtualBox if you want to run Civilization 4 since it requires hardware acceleration. I guess you've bought it from a direct2drive store? in that case see if you can exchange it for a retail disc instead.

What's the error message you're recieving? Let me know since I've managed to get Civ4 working with all expansions. see my guide at [appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9501")

---

### Post by teddybairs1 on 2007-12-17
Yeah, I bought it from dell's direct to drive. I did the download using Ubuntu.

I found an activation crack which solves my problem on running it on the XP partition. I hadn't intended on using the virtual machine to play the game, I only wanted to use it to see if I couldn't activate it by running the XP partition on top of the Linux host.

Thanks anyway.

---

### Post by KhaaL on 2007-12-17
You could just copy over Civ4 folder, the required DLL's to wines system32 folder, and do a pair of tweaks on wine, and It'll work :)

---

### Post by teddybairs1 on 2007-12-18
I'll keep that in mind. Right now it's working. The folder itself is over a gig and right now I'd rather have it sit on my nearly empty windows partition rather than take up space in the .wine folder. Beyond that, I've got read/write enabled anyway for ntfs partitions from Ubuntu, so theoretically all I should have to do is get the native dlls.

Thanks though.

---

