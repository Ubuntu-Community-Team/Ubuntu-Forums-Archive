---
title: "Can't Cofigure Xorg With Live CD"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by EdInHouston on 2006-11-06
I am a newbee concerning linux.  I have been fighting this problem for two days now.  I've read at least 200 post.

I can't get the prompt that I believe is the xterminal to do anything after x server disables GDM do to a problem that 'seems' to be my ATI VisionTec 7000 Card.  I want to reconfigure xorg to use the VESA driver to see if Umbuntu is compatable with my 3D graphics card.

Here are the details:

System information:
ATI VisionTec Radeon 7000 64MB Dual Monitor 3D graphics card
Windows XP Home Edition Service Pack 2 (build 2600)
ST380012A [Hard drive] (80.03 GB)c: (NTFS on drive 0) 74.05 GB 55.64 GB free d: (FAT32 on drive 0) 5.96 GB 1.05 GB free
Hp Pavilion A310N PC with 768MB DDR SDRAM, 2.7 GHz Celeron.
Board: TriGem Computer Inc. Glendale motherboard 
BIOS: Phoenix Technologies 3.21 07/16/2003
Note:
I haven't tried going back to my optional Intel Extreme shared video 82845G/GL/GE/PE/GV Graphics Controller [Display adapter] disabled in Xp and BIOS because I need 3D.

Leadup to problem:

I install Live version 6.10 i386 standard DVD and reboot to test on my system before installing.
I rum memory test and double check the DVD.  I also checked the MD5 checksum before burning at 4x using a Sony DVD on a Sony burner.

Start screen appears.
(Note:   The problem occurrs under "Start or Install Ubunbu", Start in Safe mode", and the "boot: live noapic nolapic", others"
The Ubuntu progress bar goes back and forth for a minute as the DVD spins and the kernel loads 100 percent with vmlinuz and initrd.gz.

This error occurs:
"Failed to start the x server.  It is likely it isn't configured correctly.  Would you like to view the x server output to diagnose the problem?"
Yes
..."Module loader present"...
(==) Log file: "/var/log/xorg.o.log"...
(==) Using config file:"/etc/X11/Xorg.config"
I press Esc and it says:
"Would you like to view the detailed x server output as well?"  Yes.
It is the same exactly.
I press Esc
It then says
"The x server is now disabled.Restart GDM when it is configured correctly"
OK
Now a black screen appears that I 'think' is a xterminal that says:
"*Activating swap...[ok]"
"mount: function not implemented"
"*Checking file systems..."
"fsck 1.39 (29-MAY-2006)  [ok]'
Then the flashing prompt is below that.

I try typing at this prompt:
"Sudo dpkg-reconfigure xserver-xorg" and then press enter.
The prompt moves down and nothing happens.
I type ctrl+alt+f1 and get this:  [[[A
I try ctrl+alt+f2 and get [[[B, and then I try f3 through f6 and try to run commands, nothing.
I then push ctrl+alt+backspace to get out, nothing.
I then type "sudo /etc/init.d.gdm restart" and press enter, nothing
I had to do a hard reboot.

What Am I missing?
Was that prompt the terminal?
I'm on a 56K modem so testing the alt cd is not an option.

---

### Post by chuckyp on 2006-11-06
Did you try selecting safe graphics mode on the live cd menu?

If not sudo nano /etc/X11/xorg.conf you should be able to switch Driver to "vesa"  and just restart X with sudo /etc/init.d/gdm restart

---

### Post by EdInHouston on 2006-11-06
"Did you try selecting safe graphics mode on the live cd menu?"

Yes

"If not sudo nano /etc/X11/xorg.conf you should be able to switch Driver to "vesa" and just restart X with sudo /etc/init.d/gdm restart"

I tried that command too.  the prompt wont carry out commands.  When I press enter it just moves down one space and blinks.

I'm linux stupid.  Do you think I was typing in the xterminal as described in the above post; the prompt after pushing esc  after the xorg error message which is the blinking prompt with the black screen.

It must be something really simple because I'm a linux novice and the prompt wont do a thing.  Is there some precursor involved before typing a command that isn't discused here because a blind person would see it?  Should I be pressing enter after typing a command?  What about logging on?  I don't think I should type anything to log on trying to get a live dvd to boot but I just don't understand.

3:30AM here and this is driving me nuts.  I think I'll bump this in a few hours when I wake up.

Thanks
Ed](*,)

---

### Post by chrisblue on 2006-11-06
I am new to Ubuntu as well so this maybe the blind leading the blind but I am haveing a similar problem where I tried to install xgl and stuffed up somewhere, now xserver is borked and I get basically the same problem as you.

What you need to do to access a command line is press esc when you see the grub loader timer counting down during the boot process, you only have a few seconds on my system so be prepared. From there you can select recovery mode. That should boot to a command line.

Quite what the hell you do then I don't know but it may help to get that far.

Tell you what if you find out some answers let me know in this thread ([http://www.ubuntuforums.org/showthread.php?t=293356](http://www.ubuntuforums.org/showthread.php?t=293356)) so far I haven't got much help :(

---

### Post by Dr. Nick on 2006-11-06
Looking at your first post it would appear that it is not finishing booting, you will have a prompt similar to this (~) when you can enter commands, not sure if the live cd makes you login first or not, once installed you will need to logon before entering commands
 
I havent used the live cd in a while, forget what all boot options it has.
 
I can tell you a few things though, With the vesa drivers you will not have 3d acceleration, vesa is a standard driver that attempts to work on any configuration as a failsafe of sorts, it will not 3d accelerate. I would hook up the integrated intel card and see if the live cd will boot, Want to try and determine exactly what is going wrong, If it boots on the intel then I would fault the card, if no boot on intel gfx then it may be a different problem to diagnose

---

### Post by EdInHouston on 2006-11-06
The driver in the Ubunbu 6.10 386 Live DVD for ATI graphics cards will not work with the Radeon 7000 3D card in my computer.

I went back to on board shared memory and Umbutu booted the live DVD.

I found out I like Puppy much more than Umbutu.  I was disappointed because I have a 56K modem and Umbutu doesn't have basic drivers for linmodems or a dial up screen that I could find.  Puppy has a few easy dialers and it is about 65MBs.  I can run it as a live multi session CD, it loads completely in RAM and is fast.

On the positive side I found Umbutu to be a clean, stable OS on my machine.  I think it is a fine OS for broadband users, it's just not for me.:)

---

