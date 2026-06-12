---
title: "reinstall windows, not reinstall ubuntu?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by tocleora on 2007-04-10
Ok, I'm sure this has been asked before in here but not exactly sure how to search for it so hopefully someone can either point me to the right thread or maybe I'm unique enough it won't matter. ;)

I want to reinstall Windows. I have a 80 GB Hard Drive and (I think) 40 GB is available to Windows, and yet only like 1 GB is free. In addition it seems to take forever to boot.  I don't use Windows for anything other than games, photoshop and flash anymore so I'd like to wipe that partition clean, reinstall windows, and then reinstall grub if that's necessary (I'm guessing it is) without touching my Ubuntu installation.  My questions:

1. I'm running XP Media Edition on my laptop. I bought a copy of XP Home for my home computer.  The CD for my laptop is one of those factory CD's that I'm guessing would completely overwrite the hard drive when it pus XP back on it.  Is there a way around this, or can I use the XP Media Edition Key with my Home CD's?

2. I'm currently running Symantec something with Antivirus, Antispyware and such, It may be Systemworks or it may just be Antivirus.  My friends tell me this is part of the reason my Windows partition boots slow.  If I just run Windows Firewall, Windows Antispyware and say AVG Free for Antivirus, will this be faster and will this be enough? Remember, all I'm doing is playing games, Photoshop and Flash.

3. How easy is grub to put back when/if I do this?  Anything to take into consideration?

4. I'm sure I'll be quick to install Fiesty when it comes out.  Is it smarter to wait until then and start from scratch?  I'm ok with doing this if it will be cleaner than upgrading.

5. What can you recommend doing (or not doing) to make the reboot from ubuntu to windows in order to get in the game as quick as possible?  My friends all use Windows and just start the game. It seems to take me 10 minutes to get in and they're already ahead of me.  I want to cut that time as much as possible.

Even if you have only part of 1 answer, all responses that move me forward are greatly appreciated!

---

### Post by rai4shu2 on 2007-04-10
This is something that can help you out:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you don't use Windows for networking, you might consider simply disabling the network in Windows.

---

### Post by ComplexNumber on 2007-04-10
if you already have ubuntu installed on the first part of the hard drive, my reaction to that is "oh dear :(".
when i reinstalled windows sometime ago, i made the mistake of putting linux on the first part of the hard disk. windows XP didn't like that at all. in fact, i couldn't find any way to reinstall it on the partition after where linux is installed. it kept on complaining and saying that something else appears to be there. it would make no attempt whatsoever to install at any other place other than the first part of the hard drive. i had to wipe out linux first, then reinstall windows on the first part of the hard drive, then reinstall windows.

if anyone knows a solution, i'm not aware of it. i'm not saying there isn't one, though. maybe some enlightened person will be able to say.

---

### Post by tocleora on 2007-04-10
> **ComplexNumber said:**
> if you already have ubuntu installed on the first part of the hard drive, my reaction to that is "oh dear :(".

No, it's on the second part of the partition. :)  But I'm sure windows will write over the boot sector.

---

### Post by tocleora on 2007-04-10
> **rai4shu2 said:**
> This is something that can help you out:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you don't use Windows for networking, you might consider simply disabling the network in Windows.

Thanks, I think that link answers #3, and I'm that much closer! :)  No, I'll be playing multiplayer games so disabling the network won't help.  Plus I'm sure at times I'll need to browse for something as well. Oh and I *love* xfire so I can't go without it! :D

---

### Post by garrido on 2007-04-10
All you have to do is reinstall grub.  Boot with a live CD after installing Windows and run:

```
grub
```

Then find which partition holds your /boot directory:

```
grub> find /boot/grub/stage1
```

Then set the root to that partition, and setup grub:

```

grub> root (hd0,0)

grub> setup (hd0)

```

Note that you might need different values other than (hd0,0) and (hd0), depending on your setup.

---

