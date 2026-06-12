---
title: "Dapper and hardware upgrades"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by j0eb0b on 2006-07-19
I have a solid working implementation running with most issues reolved.  I am now considering upgrading some of the hardware on the machine.  Current hardware configuration:

Antec Tru-Power 430W PSW
DFI NFII Ultra MB (runs Nvidia NF II chipset)
AMD 1700 Thoughbred at 1.8 Mghz
2X512 twinMOS PC 3200 memory
Maxtor 160MB ATA 133 HD
Nvidia 5500 graphics 256 meg
liteon CD burner
Sony DVD player
MB onboard sound based on AC 97
Floppy drive and plenty of fans

New configuration;


As above with:
AMD 64 FX 55 CPU (939)
Asrock MB (ULI chipset)
Sapphire Radeon 9800 Pro 128 graphics card.

I've done lots of hardware upgrades on MS and have experienced the normal driver install and removal issues as well the call to Microsoft Tech Support to affirm I'm not a pirate (I'm not) and activate my system.

Questions:

how will my existing Dapper installation react when it see a new MB with a different chipset?

What do I need to do to remove the Nvidia graphics card and driver and then reinstall the ATI Radeon card.

I plan on staying with the current 32 bit version of Dapper in the near term.  Will I have problems with the AMD 64 CPU and 32 bit Dapper?

Is the consequence of what I am considering a reinstall from scratch Dapper?

All school of hard knocks comments appreciated.

Joe

---

### Post by moshuptrail on 2006-07-19
Since you are writing in the Beginner forum I'm assuming you're not an experienced Linux wizard.  I'm no wizard, but I'm fairly sure that Ubuntu (or any Linux) won't react well at all to the processor change.  There are diffedrent distributions depending on what processor you have. Add to that all the complexities for the other changes, and I'm thinking re-install.  If you have followed the recommendations and created /home in a separate partition your work will be limited to installing and configuring Linux and any special apps you had.

---

### Post by j0eb0b on 2006-07-19
You are right to assume i am no Linux expert.  When I put this machine together I accepted the install defaults and don't remember creating a seperate partition for /home.  Is the recommendation you refer to a default at install time?

Do you know if there is a wiki or other reference regarding hardware and ubuntu?

Thanks,
Joe

---

### Post by jimrz on 2006-07-19
> **j0eb0b said:**
> You are right to assume i am no Linux expert.  When I put this machine together I accepted the install defaults and don't remember creating a seperate partition for /home.  Is the recommendation you refer to a default at install time?

Do you know if there is a wiki or other reference regarding hardware and ubuntu?

Thanks,
Joe

you can look in /etc/fstab to check and see if one of your mount points is lableled "/home". if not, then your /home is included in your / directory. i have not yet used the gui installer from the "live" cd (always have used the alternate) so am not sure but do not thnk that it makes a separate /home by default. should you do a re-install making a separate /home during the partitioning stage is a good idea, as i takes some of the pain out of future re-installs and dist-upgrades

---

### Post by moshuptrail on 2006-07-19
You've got 160Gb.  That's plenty of space.  You may be able to use a utility like Gparted to shrink the partition and make room on your hard drive for another partition or two without destroying your saved files.  When you re-install, I suggest the following partitions:

/home = shrink your present space, keep whatever files you want, and mount the partition as /home
/ = create a 10Gb partition for installing Ubuntu
swap = create a 1Gb swap partition
/usr = usually application software is installed under /usr

Divide the space between /home and /usr partitions as appropriate for the applications you use.  Personally, I don't have any special applications like games, so I don't even have a partition for /usr.

---

