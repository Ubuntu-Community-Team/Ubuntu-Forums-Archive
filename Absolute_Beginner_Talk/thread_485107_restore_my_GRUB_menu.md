---
title: "restore my GRUB menu"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-26
i seem to have loast my GRUB menu....
i somehow overwrote it during windows install...

how do i get it to show m ubuntu again??
it boots windows straught away

thanks guys,

---

### Post by bodhi.zazen on 2007-06-26
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by Yoooder on 2007-06-26
I haven't read the links provided above, but just fyi: When setting up a dual-boot system, it is a bit easier to install Windows first, then Linux afterwards.  Windows will always overwrite your mbr (master boot record) which is where GRUB and LILO live.  However, as I'm sure the above links indicate, repairing the overwritten mbr is a relatively easy task--just a pain in the neck

---

### Post by MikeSz on 2007-06-26
Can I nip in on this subject with a quick question??  My sister has XP and Dapper installed on a dual boot, for some strange reason, there is no grub menu anymore (think it got turned off rather abruptly during the thunderstorms last week).  Instead, it POSTs ok, BIOS seems fine (I took the CMOS battery out and reset it just to make sure) but wont get to a GRUB menu.  We now just get a little message saying "NVIDIA BOOT MANAGER........" (im assuming because its an Nvidia NForce 4 chipset its reverting to an imbuilt boot manager) and then I get a message about DCHP and then it just sits there.  If I disconnect the modem, I dont get the last bit, it just sits there on Nvidia Boot Manager.  So - Im guessing the MBR has been wiped!  

I can boot into 7.04 from the live CD as it picks up a bootable disc and I can see the hard drive and everything on it so I dont think there are any hardware problems.  

My question therefore is this - Can I use the above fix to restore the MBR and the Grub menu?  Will it fix both so I can dual boot again?  Will everything be the same?

Cheers in advance guys and girls!!

---

### Post by bodhi.zazen on 2007-06-26
Yes (I hope)

---

