---
title: "DapperDrake-iso-cd not booting in refurb Laptop w/no OS"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by 3katie3 on 2007-03-16
Hello All, 

i just bought a refurb HP zv6000  laptop with no OS to use for Linux OS.

but it is not booting a cd burned with ubuntu-6.06.1-desktop-amd64.iso  (i burned it with [http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/) and checked hash)

i disabled ethernet in bios, and made cdrom #1 boot order,
 now the cd spins and spins, but screen is black, black as a bootblack.

i'd like to make a haiku about this, but i'm completely out of ideas.

----
and to compound my confusion, the same .iso cd (with correct hash) when opened in myother XP laptop of nearly same config. (another amd64 zv6000)---it opens the Sonic DVD/cd ripper software, and Sonic lists only the one file:  ubuntu-6.06.1-desktop-amd64.iso instead of opening into the graphical install program shown in ubuntu install screenshots, [ [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) ].  

And the Sonic software does not display the list of included files as shown here [ [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) ]  and neither does WinXp explorer.

i've looked over at [http://filext.com/detaillist.php?extdetail=iso&Search=Search](http://filext.com/detaillist.php?extdetail=iso&Search=Search)
to find the correct executable to open the .iso cd at boot on the WinXP system, but dont see any help there. 

yikes.

---

### Post by Scunizi on 2007-03-16
Sounds like you created a data cd and burned the entire ISO image as a file.  You need to burn it as an image.

---

### Post by 3katie3 on 2007-03-17
Thanks very much, scunizi.

the disc image cd loaded and opened up the graphical interface.

a very good start.

---

