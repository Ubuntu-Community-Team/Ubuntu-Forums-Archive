---
title: "Powerbook G4 - Booting Issue"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by slum on 2008-01-15
I posted this on the PPC forum but it doesn't seem to be as active as this forum... I will try here.

I am new to the Ubuntu system but not to computers. I decided I would try to install Ubuntu onto an old PowerBook G4 laptop that has been laying around with OS X 10.2. I was able to install Ubuntu with no problem and everything seemed to work fine, but after I restarted the machine I started to see problems.

As soon as I turn on the computer and boot to Linux my screen turns an almost metallic silver with several horizontal lines. I cannot do anything from this screen and when I try to reboot the machine it does the same exact thing.

Edit:
Update 1: On the last boot up attempt I came to a screen where it froze with a _ in the top left hand corner of the screen. Also when choosing a bootable kernel I selected 'live-nosplash-powerpc video=ofonly break=top' if that helps anyone one. When I get stuck at the busybox... I type "modprobe ide-core" then 'exit'.  This allows the installation to continue and I am fine till I have to restart. If I boot off the Live CD and do the install everything goes through fine. It asks me to re-start and remove the disk. It pops out the disk and I restart the machine. When it comes back up it asks me how to boot and I select l and then type in Linux to boot. It looks like it is going to start to load... it flashes to a white screen then says Loading, Please wait. after that it flashes to a solid _ and will not move past that point. I can run Ubuntu when running of the CD but as soon as I remove it... it will not load.

I tried everything I could think of and even did some searching on the internet to find a fix. All I could find is this:

Once you have installed add the line
ide-core
to /etc/initramfs-tools/modules and run
sudo update-initramfs -u

When I tried to run this fix it tells me that I don't have the proper permissions to do that. I guess it is because I am running the Live CD version at that time and it won't let me edit the modules file. Regardless I cannot get it to normally to make those changes. I just get stuck at the _ in the top left hand corner of the screen and the machine is useless. ](*,)

Any help would be GREATLY appreciated!!

---

### Post by SunnyRabbiera on 2008-01-15
I am afraid powerpc support is practically dead... for your old apple you may need another distribution, personally I suggest debian, its not an easy set up but it will work.

---

### Post by slum on 2008-01-15
That is a bummer... I really like ubuntu from what I saw running the live CD.  It seems as tho everything installs correctly and I only experience issues when I pop out the live CD and it reboots it just sits at the _.

---

### Post by SunnyRabbiera on 2008-01-15
well a lot of distro's are dropping support for it as it was a rough archetype to deal with anyway.
But Debian should do you nicely, after all ubuntu is based on debian after all.
your biggest hurdle will be the installer, its rather old fashioned and rough to deal with.

---

### Post by tgalati4 on 2008-01-15
Can you boot to a rescue shell from the Boot menu?  Once there you can look in /var/log for errors (specifically xorg errors to see what is hanging).  It looks like a display/resolution issue.

---

### Post by dstew on 2008-01-15
> When I tried to run this fix it tells me that I don't have the proper permissions to do that.How did you try to edit the file? If you try a graphical editor, like gedit from the desktop, it might not let you because you need admin privleges. To get priveleges, use **gksudo gedit** from the command line.

Also, the blank screen may be only a problem with the graphical interface. Try ctrl-alt-F1 to see if you can get a command line.

---

### Post by slum on 2008-01-15
> **tgalati4 said:**
> Can you boot to a rescue shell from the Boot menu?  Once there you can look in /var/log for errors (specifically xorg errors to see what is hanging).  It looks like a display/resolution issue.

I'm not sure how to access the rescue shell?

> **dstew said:**
> How did you try to edit the file? If you try a graphical editor, like gedit from the desktop, it might not let you because you need admin privleges. To get priveleges, use **gksudo gedit** from the command line.

Also, the blank screen may be only a problem with the graphical interface. Try ctrl-alt-F1 to see if you can get a command line.

I am only able to access Ubuntu via the live CD. **Edit:** Left this part out... I tried to edit the file after the Live CD was done with the install while still using the live CD.

 And the only command lines I get are when I bootup at the beginning and they ask me if I want to boot 'Linux' or 'old' - although booting to 'old' does nothing.


I appreciate the help!

---

### Post by Joe R on 2008-01-15
I have got the same problem. I put the disk in and click install. Eventually I get to a milky silvery screen and ctrl alt F1 does get to the command line. Now what do I do?

---

### Post by dstew on 2008-01-15
> Eventually I get to a milky silvery screen and ctrl alt F1 does get to the command line.Check if the system is functional. Enter **pwd**, and it should give you back your username. List your home directory with **ls**. If things are OK, I suggest reconfiguring your X-window server. The command is```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Joe R on 2008-01-15
Thanks for the info. The cd is starting to read the stops then starts to read still. so perhaps the installation has stalled. At first I typed pwl but nothing happened on the screen pressed a couple of other keys then hit enter and it appeared so I typed pwl enter then ls and nothing happened

---

### Post by dstew on 2008-01-15
The command is pwd, and not pwl. Anyway, it looks like your LiveCD is not working. You could try kernel parameters, but if you know you want to install, use the Alternate Install CD. It installs the same Ubuntu system using a text-based interface that avoids graphics difficulties. You get is from the same Ubuntu Download page, just click the box beneath the Start Download button.

---

