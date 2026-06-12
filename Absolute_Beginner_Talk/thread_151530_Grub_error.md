---
title: "Grub error"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by master5o1 on 2006-03-28
hi we have been using linspire for a while and decided to try ubuntu. i have just finished installing ubuntu on one of our computers, it has 3 hard drives in it one with linspire, one iwth xp and a new one with ubuntu and then a cdrom... grub worked perfectly on linspire... but now (after stupidly re-writing the master boot record) i cant get in and it says error 25.  on the debian site this says it is a "boo boo" under bugs or something and basically i have to re-install... funny cos i've just intalled! now maybe this the extra hard drive (the ubuntu one) i dont know... in the bios i tried changing which disk is booted first and stuff like that... i even changed the ubuntu drive to cable select just incase blaah blaah blaah. im very lost... any suggestions on how to fix this and make my machine accessable...if i cant fix the MBR grub i will have to reinstall linpsire too no?

something about menu.lst i have seen mentioned before? hda/boot? /grub?  i cant remember thank god we have more than one computer and thank god for live cd's :D

note:
linspire hda1 is 80gb and master
winxp is hdb1 80gb and slave

ubuntu is hdc1 and cabel select (was master a moment ago)
dvd drive is slave.

thanks :D

---

### Post by IDipSkoalMint on 2006-03-28
[QUOTE=master5o1]hi we have been using linspire for a while and decided to try ubuntu. i have just finished installing ubuntu on one of our computers, it has 3 hard drives in it one with linspire, one iwth xp and a new one with ubuntu and then a cdrom... grub worked perfectly on linspire... but now (after stupidly re-writing the master boot record) i cant get in and it says error 25.  on the debian site this says it is a "boo boo" under bugs or something and basically i have to re-install... funny cos i've just intalled! now maybe this the extra hard drive (the ubuntu one) i dont know... in the bios i tried changing which disk is booted first and stuff like that... i even changed the ubuntu drive to cable select just incase blaah blaah blaah. im very lost... any suggestions on how to fix this and make my machine accessable...if i cant fix the MBR grub i will have to reinstall linpsire too no?

something about menu.lst i have seen mentioned before? hda/boot? /grub?  i cant remember thank god we have more than one computer and thank god for live cd's :D

note:
linspire hda1 is 80gb and master
winxp is hdb1 80gb and slave

ubuntu is hdc1 and cabel select (was master a moment ago)
dvd drive is slave.

thanks :D[/QUOTE]


I was experimenting with trying to install the MacOSXx86 (by installing SUSE and then re-writing it, as I heard that was a possible solution) on my machine that has WinXP and Ubuntu and ended up messing up my GRUB. I got Error 17 though. I just reinstalled Ubuntu and everything worked fine for me. I believe there's actually an option to simply reinstall the GRUB, but don't quote me. Try a reinstall of Ubuntu or your other Linux distro.

---

### Post by mrbiscuit on 2006-03-28
If you try reinstalling Ubuntu with GRUB, then get into the installer menu by keep pressing the back button on the installed until it pops up a menu (after it loads the modules from the cd-rom) or however you get into the installer menu and go down to Install LILO and see if that helps any.

---

### Post by Mustard on 2006-03-28
I don't think you need necessarily reinstall linspire or ubuntu.  I would think you need to reinstall grub though.  How did you write over the MBR?  Do you have a live CD?  Are you able to boot into XP?

---

### Post by belikralj on 2006-03-28
I'm sorry but I'm not understanding the situation fully. Can you boot into either of your linux distros? Sorry if I'm making you repeat your self.

---

### Post by belikralj on 2006-03-28
After more carefully examining your post I think I sort of understand the situation now. I don't exactly know if there is a grub substitute, but on most Windows boot disks you have the "fdisk" option which can reset the MBR "fdisk /mbr" or "fdisk \mbr" something like that.

UBUNTU fix. Try running Ubuntu in rescue mode. I believe it was designed exactly for situations like this. Though I'm not sure how to do it exactly I believe rescue mode is the key.

put your instalation cd in and type in: "linux rescue" at the boot: prompt.
(ps. You might want to read information on rescue mode by pressing F5 before typing in any commands at the boot: prompt)

hope this helps, good luck!

---

### Post by IDipSkoalMint on 2006-03-28
[QUOTE=belikralj]After more carefully examining your post I think I sort of understand the situation now. I don't exactly know if there is a grub substitute, but on most Windows boot disks you have the "fdisk" option which can reset the MBR "fdisk /mbr" or "fdisk \mbr" something like that.

UBUNTU fix. Try running Ubuntu in rescue mode. I believe it was designed exactly for situations like this. Though I'm not sure how to do it exactly I believe rescue mode is the key.

put your instalation cd in and type in: "linux rescue" at the boot: prompt.
(ps. You might want to read information on rescue mode by pressing F5 before typing in any commands at the boot: prompt)

hope this helps, good luck![/QUOTE]

I believe the windows command you're referring to is "fix mbr" (if you're talking about the command you enter in the "repair mode" of the windows installation) ;)

---

### Post by Ferri on 2006-04-07
I've had also this error 25. Reinstalling grub with kubuntu install disk has restored everything back to normal.

---

