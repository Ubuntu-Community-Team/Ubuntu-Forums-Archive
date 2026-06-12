---
title: "Ubuntu in MS Virtua lPC 2007"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by mynogan on 2007-12-20
Hi!

A completely Ubuntu/Linux noob here. I am running Ubuntu 7.10 in MS Virtual PC on WinXP Pro SP 2.
I was able to install it thanks to help from [http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/](http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/)
However, there are a couple of problems for which I have yet to get a fix.

First, Ubuntu would hang/freeze after some time. I can still move the mouse about, in and out of the Virtual PC, but the mouse clicks won't do anything. Short-cut keys don't work either. (I have assigned 512 MB  RAM to Ubuntu; total Available RAM is 2 GB).

Second, I can't seem to get Windows Network to work properly. I have installed Samba and configured it. I can access the Ubuntu shared folders from Windows, though sometimes the network path seems to be lost. Restarting Samba would fix that. However, I can't access the Windows shared folders from within Ubuntu.

Can anyone help?

---

### Post by mynogan on 2007-12-20
Lest this gets buried in the rapid flow of requests for help, I'm replying to my own post in hope that some good samaritan comes along to help. :)

p.s. please excuse the typo in the subject heading ... obviously, it's supposed to read "Virtual PC."


p.p.s. The physical video card on the host pc is nVidia GeForce 7600 GT, if that means anything.

---

### Post by SunnyRabbiera on 2007-12-20
hmm well I am not surprised if it hangs, even with a heavy amount of memory using virtual software can be a killer...
But maybe you can try another virual machine software, there are a few good free ones out there for windows.
by the way why are you trying ubuntu out in a virtual machine, it certainly wont give you a look over like the live CD that allows you to run your linux system without installing it.

---

### Post by mynogan on 2007-12-20
I was hoping for a fix before I decide to ditch this microsoft thingy and maybe try Virtualbox or VMWare.
Reason why I'm running Ubuntu in a virtual machine is that I still need the WinXP as certain stuff I am using for my work is available only in Windows. Someone suggested the dualboot option, but the process felt kinda intimidating; besides, I figured it might be easier to switch to and from Windows and Ubuntu without the need of rebooting constantly.

---

### Post by candtalan on 2007-12-20
> **mynogan said:**
> I was hoping for a fix before I decide to ditch this microsoft thingy and maybe try Virtualbox or VMWare.
Reason why I'm running Ubuntu in a virtual machine is that I still need the WinXP as certain stuff I am using for my work is available only in Windows. Someone suggested the dualboot option, but the process felt kinda intimidating; besides, I figured it might be easier to switch to and from Windows and Ubuntu without the need of rebooting constantly.
Welcome!
I have installed many dual boot systems (ubuntu particularly) for myself and friends, and it has been reliable - I do however take backups of data before installing just in case. I have never got round to using a virtual machine though, it has always been a bit of a stretch for my experience! 

For a PC with single windows OS existing, chkdisk checked and defragged well, installing is easy. Do *read* the install process options carefully and choose to avoid wiping your windows if that is not what you want!
hth

---

### Post by kestrel1 on 2007-12-20
I have tried Virtual machines, but not been that keen. You don't get the best out of the OS, but if you want to use a Virtual environment try Virtual Box. This is totally free & there are versions for Windows, MAC OS X & Linux.
I have dual & multi-booted many a PC. I think the most OS'es I had installed at any one time was 6 (Win XP, Win 2K, Win ME, Win 98, Mandrake Linux & Fedora core) Took a bit of setting up, but was a good learning curve.
I normally use Partition Magic to re-size my hard drives before a new install of an OS, I just found it easier.
I am currently running Ubuntu 7.10 & Windows XP Pro, both on my personal home machine & my works desktop (being a Network Manager has it's advantages) Just thinking about putting Ubuntu on my laptop as well, mainly cos Windows has slowed to a crawl (as usual)
Only just got back into the Linux scene though. Ubuntu is the best I have seen.

---

### Post by mynogan on 2007-12-20
Thank you for all the advice. I think I will try Virtual Box after all. It appears from the comments made so far that the problem lies with the virtual environment specifically Virtual PC and not with any settings within Ubuntu itself.
I am aware that I will not get optimal experience running Ubuntu in a virtual environment: things will be slower, a crash every now and then but not this frequent hanging/freezing.
A couple of observations though: last night I experimented a bit, keeping the Terminal window open while running Deluge Bittorrent client all through the night. The blinking cursor would help me know that the desktop is still alive and not dead. Well, it has not hanged yet. I will let it continue to run and see if it survives the day too.
My daughter who introduced me to the Virtual environment runs WindowXP on a host Windows Vista because certain of the programming tools that she uses for her work are much more stable in XP than in Vista. She has never encountered his hang/freeze problem. Perhaps, it is just that MS Virtual PC does not work well with non Microsoft OSes. A pity!
I wonder anyone else who has run Ubuntu in a virtual environment cares to share their experience.

---

