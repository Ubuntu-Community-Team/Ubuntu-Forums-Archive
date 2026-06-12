---
title: "How to re-install the bootloader"
date: 2014-08-25
forum: Any Other OS
---

### Post by project722 on 2014-08-25
I accidently altered my partition table. Somehow I wiped it out completely and changed the disk label. Before I rebooted I managed to rebuild it the way it originally was using the original structure and label however I need to re-install a new bootloader for the new MBR. I have Ubuntu 14.04TLS running inside VirtualBox on a Windows 7 machine. Is there a way to do this without rebooting?

---

### Post by slickymaster on 2014-08-25
Moved to the **Other Operating Systems and Projects** sub-forum.

---

### Post by Mike_Walsh on 2014-08-25
Hi.

Have you tried 'Boot-Repair'?

[http://ubuntuportal.com/2014/02/boot-repair-tool-will-added-on-ubuntu-14-04-trusty-tahr-by-default.html](http://ubuntuportal.com/2014/02/boot-repair-tool-will-added-on-ubuntu-14-04-trusty-tahr-by-default.html)

[https://launchpad.net/boot-repair/+download](https://launchpad.net/boot-repair/+download)

Regards,

Mike.

---

### Post by project722 on 2014-08-25
I ran those commands but get a 404 not found when apt-get tries to access those repositories. Anyway I just re-installed Grub. I think this may have worked. I'll reboot and see. On a side note - I noticed that my system has both Grub and Grub2 installed. How can I tell which bootloader the OS is using?

---

### Post by oldfred on 2014-08-25
Boot-Repairs report shows all the details of your install.
There is not a trusty version and you have to edit the sources to use the saucy version. Instructions in link.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The Boot-Repair report actually uses this for about the first third of its report. It will also show most of your install details.

 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by project722 on 2014-08-25
oldfred - followed the instructions in the first link in your post. Everything seemed to install ok - till I tried to run "boot-repair" in terminal then I got this:

[EMAIL="brian@$"]$[/EMAIL] boot-repair(gksudo:9573): Gtk-WARNING **: cannot open display:
[EMAIL="brian@$"]$[/EMAIL] sudo boot-repair
error: XDG_RUNTIME_DIR not set in the environment.
error: XDG_RUNTIME_DIR not set in the environment.

Then a bunch of rolling failure lines with GTK critical. I suppose its telling me it cant run from terminal and wants the GUI. Anyway, I ran env to see if I have a the XDG_RUNTIME_DIR set and it does have a path set. How do you make this work from the shell?

---

### Post by project722 on 2014-08-25
Well it ran fine from the GUI - said "Boot Successfully Repaired". Would still like to know how to make this work from the shell if that's possible and if there is a way to tell of the systems using Grub or Grub2. They are both installed.

---

### Post by oldfred on 2014-08-25
It should give you a link to a pastebin. Post that.
Or if you did not save it just rerun report only and post link.

---

### Post by project722 on 2014-08-25
[http://paste.ubuntu.com/8142980/](http://paste.ubuntu.com/8142980/) - I see a few errors not sure if they would be fatal on a reboot or not.

---

### Post by oldfred on 2014-08-25
Grub install had an exit code of 0 or no errors, so it says it reinstalled correctly.

With one install, you do not get grub menu unless you hold shift key from BIOS until menu appears.
Not sure if with virtualbox that is the same or not.

But if video is not correct you may get past boot issues and into video or other driver issues and not really know it.
Sometimes boot parameters are required for video or other hardware settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by project722 on 2014-08-25
So this boot-repair you don't think there is a way to run it from terminal?

---

### Post by oldfred on 2014-08-25
I thought you could be in anther thread it required a gui.

But you can run the bootinfoscript which is the first third of the BootInfo report. I run script as part of my rsync backup so I always have a current report of how system is configured.

---

### Post by project722 on 2014-08-25
Ok thanks oldfred - you have been a great help.

---

