---
title: "Buildin' My First Ubuntu Machine"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by maheanuu on 2006-12-19
I am in the process of putting together a new 'puter consisting of a MSI K9N SLI with AMD Dual Core Proc and 2 Gigs of Memory along with  the NVidia Geoforce 7900 GS Graphics Card and 5 Maxtor SATA 300 gig hard discs that I want to run raid 5...

This is my first linux project, and perhaps I'm biting off more than I can chew, but have downloaded Dapper Drake and will install the alternate as I am hoping that I may struggle through the set up of everything..  Sorta like I used to do with DOS way back when...

Are any of you long time users in the Portland Oregon or surrounding area?  Just in case I run into probs...  (Which I am very prone to do).

Any suggestions or ideas would be greatly appreciated....

---

### Post by jvc26 on 2006-12-19
Well go for the install, and if you run into probs the best solution is to come a-looking on the forums - everyone is very helpful round here :) Enjoy.
Il

---

### Post by Circus-Killer on 2006-12-19
to be honest, the altenate cd isnt hard at all. its basically the installer ubuntu used to use before switching to a gui. but the steps of the installation are pretty much the same for the most part.

i doubt you will run into any troubles, but if you do, just post your question in these forums, they usually get answered within minutes. if you want a real challenge that will teach you a lot about linux, you can always try gentoo (but make sure you have plenty of documentation ready, i usually print the docs).

but, anyways, i hope you enjoy ubuntu.
i'm sure you will.

---

### Post by schwascore on 2006-12-19
Good Luck! I have a bad case of machine-envy now...

---

### Post by earobinson on 2006-12-19
good luck!

---

### Post by blackened on 2006-12-19
Just a tip:
When presented with multiple checkable options (such as choosing resolutions for the x-server), make sure you use the spacebar to select/deselect the options and not enter.  If you use enter it will accept what you already have, or have not, selected and move to the next page of the installer.  Some new users find this confusing, as do I.

---

### Post by maheanuu on 2006-12-21
Ok......  I have now spent a full two days doing all the puttin together, and loading and setting the raid drives and trying to find out all the errors I have been receiving trying to get the OS (6.06.1) installed and running...  Found that grub was corrupted on the download, and also found that if I tried to skip the Networking.. install that I would hang in limbo.

After doing a dozen Raid5 installs and running around in circles, I believe that I am ok in that dept. but am finding that the NVIDA Boot Agent is giving me 2 error messages when it tries to load...   I get the following message at the beginning Looking for: Client MAC ADDR:00 16 17 45 DD 86  GUID: 00020003-0004-0005-0006-000700080009DHCP......
After several minutes of searching I get the following two Error Messages 
PXE-E53: No Boot Filename Received

PXE-MOF: Exiting NVIDIA Boot Agent

Then it retries and comes up with the following error message

PXE-E61: Media Test Failure, check cable

PXE-MOF: Exiting NVIDIA Boot Agent

Reboot And Select Proper Boot Device
or Insert Boot Media in selected Boot device and press any key...

I am so new that I am totally dangerous...  I have rebooted from both the alternate and the live discs and still no joy...  My drives (in the bios) are shown as setup Raid5 and Ubuntu is showing them all, but I am not sure if I am pointing to the mount point for the boot, or if they are truly striped Raid5...

Any help would be greatly appreciated!!

---

