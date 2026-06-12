---
title: "PoweBook G4 - Video problem"
date: 2008-01-15
forum: Apple PPC Users
---

### Post by slum on 2008-01-15
I am new to the Ubuntu system but not to computers.  I decided I would try to install Ubuntu onto an old PowerBook G4 laptop that has been laying around with OS X 10.2.  I was able to install Ubuntu with no problem and everything seemed to work fine, but after I restarted the machine I started to see problems.

As soon as I turn on the computer and boot to Linux my screen turns an almost metallic silver with several horizontal lines.  I cannot do anything from this screen and when I try to reboot the machine it does the same exact thing.

Has anyone else had this problem and might know a fix.  Thanks again.

Edit: 
Update 1: On the last boot up attempt I came to a screen where it froze with a _ in the top left hand corner of the screen. Also when choosing a bootable kernel I selected 'live-nosplash-powerpc video=ofonly break=top' if that helps anyone one. 

Update 2: If I boot off the Live CD and do the install everything goes through fine.  It asks me to re-start and remove the disk.  It pops out the disk and I restart the machine.  When it comes back up it asks me how to boot and I select l and then type in Linux to boot.  It looks like it is going to start to load... it flashes to a white screen then says Loading, Please wait.  after that it flashes to a solid _ and will not move past that point.  I can run Ubuntu when running of the CD but as soon as I remove it... it will not load.  Any help would be greatly appreciated!!

---

### Post by slum on 2008-01-15
I think I am giving up on this.  I tried everything I could think of and even did some searching on the internet.  All I could find is this:

Once you have installed add the line
ide-core
to /etc/initramfs-tools/modules and run
sudo update-initramfs -u

When I tried to run this fix it tells me that I don't have the proper permissions to do that.  I guess it is because I am running the Live CD version at that time and it won't let me edit the modules file.  Regardless I cannot get it to normally to make those changes.  I just get stuck at the _ in the top left hand corner of the screen and the machine is useless. ](*,)

---

### Post by stmiller on 2008-01-16
What version of Ubuntu? What specific powerbook? 

Check out the PowerPCFAQs (from link at top of forum) which has some Gutsy issue workarounds.

---

