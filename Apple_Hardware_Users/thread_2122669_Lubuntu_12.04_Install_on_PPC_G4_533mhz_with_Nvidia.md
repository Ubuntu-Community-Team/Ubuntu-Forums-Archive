---
title: "Lubuntu 12.04 Install on PPC G4 533mhz with Nvidia Geoforce Graphics Card"
date: 2013-03-05
forum: Apple Hardware Users
---

### Post by FilmMusicGuy on 2013-03-05
Hi,

I'm new to Ubuntu but have successfully installed 12.04 on PC VAIO Laptop and PowerMac3,4 G4 PPC Dual 533mhz.  It's worth noting that I had no issues with the PC install but the G4 has been very problematic.

For those who have similar G4 PPC machine with bootup issues, the issue is the Nvidia Geoforce graphics card.  My research and experimenting came up with the following as the only surefire method to get the OS up and running.  However, this is not a convenient fix as it requires some code to be inputed into the Command Line everytime the machine boots up.

Also, please note, I'm first and foremost a user not a programmer, so if there is anyone out there who reads this and can suggest a mod so that the following happens automatically, or an even more elegant permanent fix then please chime in!

The following instructions come from [http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462), every credit goes to abtabt for coming up with this workaround!

**THE PROCESS:**

Using the PPC Lubuntu 12.04 Desktop (LiveCD), after starting up the PPC and holding down C to boot from CD, at the Boot: prompt I manually entered:

live video=offb:off nouveau.modeset=0 single [return]

Some text soon followed with a white screen, I waited a few minutes until the CD had stopped working and then while I couldn't see what I was typing I entered (blind):

modprobe nvidiafb mode_option=1024x768-16  [return]

Much to my surprise the Command Line (CLI) appeared with the text I had entered, I then entered in:

start lightdm [return]

The Lubuntu GUI then started up and I was able to use the OS as well as the install Lubuntu shortcut found on the desktop.

So far so good.  Once the install was complete and the machine rebooted itself, it once again hung on the white screen.  I then restarted the machine and at the Boot: prompt I entered a slightly altered command line to startup from the internal harddrive:

***Booting 12.04 from internal HD***

Linux video=offb:off nouveau.modeset=0 single [return]

Wait 5mins and enter blind:

modprobe nvidiafb mode_option=1024x768-16  [return]

start lightdm [return]

Lubuntu 12.04 then loads up from the internal Harddrive.
[B]
END OF THE PROCESS![/B]

**THE PROBLEMS:**

1. Its evident that the screen resolution and colour is not so good, however the OS seems fully functional, able to install apps, update the OS, surf the net etc.

2. The above command line process, booting from the internal HD, has to be followed each time the machine is started, it would be great if this could be automated, or some sort of mod done to achieve the same result.  Better still, a fix for the nvidia graphics cards on this OS which seems to have plagued it for quite some time... but that may be wishful thinking.

3. On shutdown I receive an error message, telling I'm in Low Graphics Mode and I'll have to fix this manually, I'm yet to know how to do this... sigh.

Thanks for reading and I hope that this helps someone in the same way abtabt's thread helped me.

Cheers.

---

### Post by danield on 2013-03-06
For your boot prompt, add the parameters to your /etc/yaboot.conf, under the "image=/boot/vmlinux" section so the "append" line looks like this:

append="nosplash video=offb:off nouveau.modeset=0"

Assuming you already had nosplash in there (or maybe it's quiet splash--just keep all the parameters inside the quotes).  I don't know if the "single" parameter is necessary.  Then run sudo ybin -v to write changes to the bootloader.

To automate the modprobe step, add nvidiafb mode_option=1024x768-16 to /etc/modules.  Other documentation also says you may need to add nvidiafb mode_option=1024x768-16 to the end of your /etc/initramfs-tools/modules file.

---

### Post by str8bs on 2013-03-06
+1 danield comments
More information in the PPC FAQ on yaboot and configuring graphics. 

You may also want to check out the xubuntu test iso in post #226 [here.]("http://ubuntuforums.org/showthread.php?t=1918246&page=23") Your geforce mx is a good candidate for this test. Specific to that iso, boot: live nomodeset xforcenv

---

### Post by abtabt on 2013-03-06
FilmMusicGuy

i will recommend you to install the nv driver read FAQ 
and make a xorg.conf

or danield suggest 

if you get lost in space let us now

have a nice day

---

