---
title: "Comments on dual boot idea please!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by MarkX on 2008-02-17
I am considering keeping XP and Linux on separate hard drives and avoiding selection via grub on boot altogether.

The idea is to mount a changeover switch on my PC which fits to the power cables to the separate  hard drives. That way I can choose which HD is powered up at boot.

Obviously the jumpers on both HDs would be set to master.
I know that obviously I wouldn't be able to transfer files between the two (but that's not an issue as a third slave drive could be employed) and that the switch must only be used while the computer is turned off (although a failsafe circuit could protect against that).


Can anyone think of any drawbacks to such a setup? I think it would be rather neat! It might even be possible to sell this as an accessory which mounts in a drive bay.

---

### Post by cookieforyou on 2008-02-17
My main setup consists of 2 harddrives which are both used for windows and Ubuntu (dual booting).  I have a third harddrive which contains Suse.  If I want to boot into suse I have to shut down the PC and disconnect the power supply (4-pin power leads) from the 2 drives and connect the third drive to the power.  I do not touch the IDE cables.  Its a bit of a pain :(

I think I need another computer !!!!!!! :(

---

### Post by jken146 on 2008-02-17
This would be much more difficult than just using GRUB.  It also creates the problem of copying between the two disks, as you point out.  I don't see any advantages.

---

### Post by jken146 on 2008-02-17
> **cookieforyou said:**
> My main setup consists of 2 harddrives which are both used for windows and Ubuntu (dual booting).  I have a third harddrive which contains Suse.  If I want to boot into suse I have to shut down the PC and disconnect the power supply (4-pin power leads) from the 2 drives and connect the third drive to the power.  I do not touch the IDE cables.  Its a bit of a pain :(

I think I need another computer !!!!!!! :(

Are you saying you don't have enough power leads?  Just get another power supply, not a whole new PC!

---

### Post by empthollow on 2008-02-17
I have to agree, i don't really see an advantage for the switch other than not having to learn the grub software especially since you could potentially damage your system.  If it is learning the software you are trying to avoid then here is everything you need to know about grub [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm).  However, if you wish to create a hardware solution to this problem that you would like to market, i would venture a guess that there are others that do not want to deal with the software either so don't let me stop your innovation.

---

### Post by rfurman24 on 2008-02-17
Grub can be set to chainload so that each drive can have its own boot loader. I always put a boot loader in the /boot partition of each drive rather than over writing the mbr everytime. I sounds like that may be the best for your situation.

---

### Post by MarkX on 2008-02-17
The point is that I have a pile of various old hard drives in the 3 to 10GB range and I just got a free DVD  with 11 different full Linux distros, and my XP. 
If I have a different HD  for each OS  I want to try, I don't forever have to fart about modifying grub or be worried about one messing up the other by accident. If I have a bigger data HD as slave I can potentially swap data between everything if I really want to (or use a USB stick).

---

### Post by MarkX on 2008-02-17
> **rfurman24 said:**
> Grub can be set to chainload so that each drive can have its own boot loader. I always put a boot loader in the /boot partition of each drive rather than over writing the mbr everytime. I sounds like that may be the best for your situation.

Can you elaborate a bit on that please? What's "chainload"?

---

### Post by Forrest Gumpp on 2008-02-18
> **MarkX said:**
> I am considering keeping XP and Linux on separate hard drives and avoiding selection via grub on boot altogether.


Can anyone think of any drawbacks to such a setup? I think it would be rather neat! It might even be possible to sell this as an accessory which mounts in a drive bay.

No, and it is.

These little after-market accessories are known as caddies.  The ones I use are supplied by ViPowER, see:  [www.vipower.com](www.vipower.com)

A caddy consists of two components, a rack that is designed to fit into a standard 5.25" optical drive bay, and a lidded drawer in which is mounted your 3.5" HDD.  ViPowER calls the drawer component a 'DataBridge', and the rack component a 'SuperRACK'.

These accessories can be purchased at computer fairs in Australia for around $15 each.

The model for my IDE drives is a VP-10LSFU-133.  You can get caddies for SATA HDDs for much the same cost.  IDE caddies are beige, SATA black.

There is a little power switch on the front which you must switch on before you attempt to boot up.  Forget to do this and your POST screen will tell you that you have no operating system or hard drive.  Instant heart failure follows until you realize what you have not done!

The caddy power switch is also a drawer lock, so you cannot remove a drive from the computer until power to the drive is switched off.  It goes without saying that you should have shut down first.

All in all, caddies would have to be one of the better kept after-market secrets of the computer industry.  See this post for how I have used them:  [http://ubuntuforums.org/showthread.php?t=691632](http://ubuntuforums.org/showthread.php?t=691632)

---

### Post by MarkX on 2008-02-19
Hehehe! Nice one, FG,  I forgot about caddies. I quite like the idea of it because it keeps the OSs completely separate. 
With the advent of cheap multi-Gig USB drives and the bios option of booting from them, they might be an even simpler solution. 
Just wondering now if XP is bootable  from a USB stick...

---

### Post by rfurman24 on 2008-02-21
> **MarkX said:**
> Can you elaborate a bit on that please? What's "chainload"?

[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

Try that. It was a great help for me.

---

