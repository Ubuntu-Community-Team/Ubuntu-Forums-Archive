---
title: "Boot failure:  How can I read boot messages (including errors) later?"
date: 2013-12-20
forum: Any Other OS
---

### Post by brian.joe.kelley on 2013-12-20
Hi, 

I am troubleshooting a boot failure with a Ubuntu installation on USB 3.0 drive,  trying to come up on a brand new Dell XPS 8700 Haswell 4th gen i7-4770 desktop.
There seems to be some sort of hardware conflict.  
How can I get the messages scrolling across my screen saved for inspection and analysis?

After a failed boot I had tried bringing the USB drive up on a virtual box vm  ( can boot either as a vm or physical from POST) and inspecting dmesg files in /var/log.
But it doesn't look like a failed boot from POST saves anything there.

Thanks for input,

B

---

### Post by oldfred on 2013-12-20
What version are you trying to install?

       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

Is this an Ultrabook with Intel SRT (and RAID)? And dual video issues?

Some with new Haswells have issues with an Intel setting in UEFI/BIOS.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

But turning off NIC turns off wired Ethernet.

---

### Post by Bashing-om on 2013-12-20
brian.joe.kelley; Hi !

See oldfred's last.

Depending on what Desktop Environment you have, might consider something along these lines:

I am using xfce4 for my DE, and to start xfce4 I use the control file ~/xinitrc and have made an entry in that file to redirect those errors to a text file:
```

 sysop@1304mini:~$ cat ~/.xinitrc
#!/usr/bin/env bash
#started creation of this file 23may2013
#
#
echo "starting the X session, Billy" >&2
export XAUTHORITY=/home/sysop/.Xauthority
exec startxfce4 --with-ck-launch [color=red]> /home/sysop/errors-boot.txt 2>&1[/color]
#end
sysop@1304mini:~$ 

```

Also on my box I can pause the boot process, and see the boot messages on screen with the key combo ctl+o;
and resume with key combo ctl+s.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by brian.joe.kelley on 2013-12-20
Hi,  it's a backtrack 5 R3 installation, and it's already installed on the usb flash drive which boots fine everywhere else in the world it seems except this new Dell desktop.

---

### Post by howefield on 2013-12-20
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by brian.joe.kelley on 2013-12-20
Thanks, Howefield.
That script looks interesting.
Hmmm. So you're pre-pending x server's init file with a little bash script that would redirect stdout and stderr to another file, and presumably x-server would start at that point in the boot process ( also possibly not), so that an output would start getting saved.
That looks pretty neat.  I'll try.

---

### Post by brian.joe.kelley on 2013-12-20
Howefield,

Where would xinitrc be placed?
In root's home directory (/root) or in /etc/X11/xinit?

Thanks- B

---

### Post by brian.joe.kelley on 2013-12-20
Nevermind.  Found out that with my startx, /etc/X11/xinit is the right place.

Well, this is very maddening.  But I did learn from a google search that hit an older thread here , that you may enable boot logging by changing a flag to yes in /etc/default/bootlogd.
However, here's what happened.
Both the bootlogd and the neat little xinitrc script did not produce anything when I tried booting the drive on the new Dell desktop.  I even cleared the /var/log directory of any log files (dmesg, syslog boot.log) to ensure that I not would cross the vm-booted versions with the physical (Dell XPS 8700).  That produced new files for the vm-booted and NOTHING for the Dell XPS booted.
This sucks.
Oh well.  I'll try looking more later to see if grub/grub2 can be configured to log all the garbage somewhere. 
This isn't huge, but it irks me with my new Dell desktop.   I had wanted to see the speed of crunching some password decryption testing on the new i7 cpu versus the other machines.
But it is primarily a Bacula backup server,  and I've installed CentOS 6.4 on it, and it seems to run fine so far.

---

