---
title: "Install problem - 7.04"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Metal Mick on 2007-10-05
Hi everyone,

after giving heavy thought to the situation I found myself in yesterday ([http://ubuntuforums.org/showthread.php?t=566957](http://ubuntuforums.org/showthread.php?t=566957)), with an install that had several broken bits, I decided to reformat the HD and do a complete reinstall of 7.04

I did a straight reformat of the HD and got rid of Grub by using FIXMBR in the Windows XP recovery console. then found the "live" CD just took me into a text-based menu. I followed the install prompts, and then found I was getting Grub errors - specifically "Loading stage 1.5... loading..please wait ....ERROR 2" message. I've had a good time since then, trying to be self-sufficient and failing miserably - I tried using the supergrub utilities (recommended elsewhere in these forums) but was unable to elicit any repair or reinstall of Grub.

My machine has Windows XP on HD-0, which has 3 partitions: one as drive C for Windows; one for applications as drive D; and one for data as drive E. There are two CD/DVD burners on the one cable as well. I want to install Ubuntu on HD-1, which is a 250GB drive, though I'd like to keep an NTFS partition on there for future use.

I've tried a couple of installs since then and repeatedly get the same Grub "Error 2" and the system just hangs.

How can I fix Grub (and the install)? I am sure this question has arisen before, and a link to a successful fix (with clear and complete instructions) would suffice.

Or, since there is no urgency, should I wait for 7.1 in a couple of weeks, and take things from there?

Regards,

Michael

---

### Post by candtalan on 2007-10-05
Fixmbr will revert the boot sector to windows norm, and the reformat of the installed partition should wipe any grub files.
grub error 2 may very well be
=================
2 : "Selected disk doesn't exist"
This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.
=================
see
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

if this is a correct guess, is it possible that the hard drive is somehow not being recognised by the bios correctly? maybe a hard drive jumper setting wrong, a HD too large for the bios to 'see' at boot time, or some other unusual thing etc?

btw I do not believe version 7.10 will address such install issues, at least I have not heard such.

good luck

---

### Post by Metal Mick on 2007-10-06
Hi,

thanks for the reply.

In an earlier post, I had an install of 7.04 that booted from Grub, but this install had several broken parts - "Add/Remove" programs for example, didn't work.

Clearly, Grub was able to cope. I did research the error message, and found somebody fiddled with the BIOS setting and found one that worked. (He couldn't be specific, unfortunately.)

However, on boot, the disks appear to both be recognized by the BIOS. I have rechecked the jumpers on the disks, and they are correct.

Please pardon the apparent foolishness of the question, but is Grub having a difficulty with the Master or the Slave drive? Ubuntu is being installed on the slave, and Windows is on the master.

Regards,

Michael P

---

### Post by candtalan on 2007-10-06
The installer and grub afaik does not care whether it is used for the master or slave drive, as long as it is visible to the bios at boot time and can be pointed to from the boot sector (MBR). The only problem I ever had was when I had a PC with a bios which could only recognise HD of up to 8GB size, and I had installed into a second added HD  of 250 GB size. I had to install grub onto a (very small) partition on the 8GB HD and put the main linux system install onto the new 250GB drive. 

I am not clear about which live CD you are using. Are you using the live CD to first run the OS live, then choosing the Install Prompt from the Desktop display? Or are you using the alternate CD which boots and only offers a text based installer?

It is also worth checking exactly what partitions you now have every where, just to confirm things are as you expect.  Gparted live CD is an excellent way of examining this, you do not have to change anything of course, just look.

(I have poor internet access from now on for a while so I may not be able to continue here, if so, apologies)

---

### Post by Metal Mick on 2007-10-07
Hi,

thanks again for persisting with me! AFAIK the HD is being correctly recognized by the BIOS - at least Windows XP has no trouble recognizing it, partitioning it and formatting it.

I was using the live CD for 7.04, and also tried the current (live) 7.10 DVD to try to get Ubuntu to install. For some reason, without changing the machine in any way, I got an error 17 from Grub, rather than 2. For both CDs, the install would hang form time to time at different stages.

I'm pretty good at following written instructions, and after searching the web for causes tried one suggestion that involved using SuperGrub (recommended elsewhere on this site) to edit files for Grub. I even tried using SG to boot into an  OS which SG was supposed to accomplish. Nothing worked.

For now, I'll depart this forum and this OS, as Ubuntu is just more trouble to me than it's worth - I've spent days trying to get it to install again, after a first attempt that was so broken it seemed to me it wasn't worth keeping.

Cheers,

Michael P

---

