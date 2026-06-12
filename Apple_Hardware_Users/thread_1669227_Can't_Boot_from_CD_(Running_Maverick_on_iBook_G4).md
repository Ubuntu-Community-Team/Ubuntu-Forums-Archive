---
title: "Can't Boot from CD (Running Maverick on iBook G4)"
date: 2011-01-17
forum: Apple Hardware Users
---

### Post by Dan Lucier on 2011-01-17
I installed a PPC version of Ubuntu 10.10 on my iBook last night. It's really slow and buggy. I'm trying to find a good Linux distro that can be EASILY installed on an iBook so I can recommend it to a friend who has never used Linux and has an iBook she wants to convert. I came across an LXDE edition of Linux Mint 9. I thought I would try that next, but ever since I installed Ubuntu 10.10 on my iBook, I can't get it to boot from a CD. I also tried a bootable CD of DSL that I know works, because I just used it two days ago on a different computer, so I don't think it's the disk that is causing the problem. I'm guessing the answer is in understanding this message from yaboot (please explain):

To boot a kernel image which is not defined in the yaboot configuration file, enter the kernel image as [[device:][partno],]/path, where "device:" is the OpenFirmware device path to the disk the image resides on, and "partno" is the partition number the image resides on. Note that the comma (,) is only required if you specify an OpenFirmware device, if you only specify a filename you should not start it with a ","

What should I enter at the boot prompt?

Thanks in advance.

---

### Post by linuxopjemac on 2011-01-17
Boot a CD with the "C" key hold down at boot. To boot from USB, see the installation instructions for MintPPC.

---

### Post by linuxopjemac on 2011-01-17
To boot from CD hold down the "c" key during boot. To boot from USB, see the MintPPC installation instructions.

---

### Post by Dan Lucier on 2011-01-17
I should have specified. I was already booting while holding down "C". That brings me to:

[INDENT]Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot:[/INDENT]

When I enter "help", I get:

[INDENT]Press the tab key for a list of defined images.
The label marked with a "*" is the default image. press <return> to boot it.[/INDENT]

[INDENT]To boot any other label simply type its name and press <return>.[/INDENT]

[INDENT]To boot a kernel image which is not defined in the yaboot configuration file, enter the kernel image as [[device:][partno],]/path, where "device:" is the OpenFirmware device path to the disk the image resides on, and "partno" is the partition number the image resides on. Note that the comma (,) is only required if you specify an OpenFirmware device, if you only specify a filename you should not start it with a ","[/INDENT]

[INDENT]If you omit "device:" and "partno" yaboot will use the values of "device-/pci@f4000000/ata-6@d/disk@0:[/INDENT]

[INDENT]boot:[/INDENT]

Any suggestions?

In the meantime, I will try the USB installation. I didn't think that was an option on an iBook. The instructions say it works on some and not on others so we'll see.

Thanks.

---

### Post by Dan Lucier on 2011-01-17
No luck with the USB installation.

---

### Post by linuxopjemac on 2011-01-18
at boot:
just enter, it will run the installer.

---

### Post by Dan Lucier on 2011-01-18
Still no luck. Pressing enter at the boot prompt just boots from the hard drive.

---

### Post by este.el.paz on 2011-01-26
Folks:

Similar issues as Dan has described with Mav 10.10 burned to DVD since CD is not large enough to hold Desktop edition--when booting from DVD I get the black screen with the Terminal type white letters.  When I hit "enter" or "help" or "live" I get a sound of busy-ness from the iMac G4 as it seems to be loading the DVD??  But then the screen just stays black.  I'm trying to just boot from DVD so that I can see how the system works, but it's just giving me blackness.  Any ideas?  It seems like I'm getting to the same place as Dan, but when it tries to move beyond the command line??  it doesn't get there.

Thanks
e.e.p.

---

### Post by Dan Lucier on 2011-01-26
I ended up booting from USB, but you could also try holding down the "option" key after your computer chimes when turning it on. This should bring you to a graphical interface where you can boot from a CD.

Where did you get the DVD of Ubuntu 10.10? You shouldn't need a DVD, and if you're trying to install on an iBook you definitely need a PowerPC version on Ubuntu 10.10. This may be your problem. You can download a PowerPC version [here]("http://cdimage.ubuntu.com/ports/releases/10.10/release/"). Make sure you select the Mac (PowerPC) version. I used this iso for my iBook G4. It worked just fine except I was not satisfied with the speed. I only have 256K of RAM and I think it's a 2.0 GHz processor (don't have it with me). If Maverick is too slow on your machine consider [Linux Mint PPC]("http://mintppc.org/") or [Lubuntu]("http://lubuntu.net/").

---

### Post by Dan Lucier on 2011-01-26
Correction:

The live CD iso for 10.10 PPC is 710 MB; I guess you do need a DVD. I had used the Alternate CD because I knew I wanted to install to the hard drive anyway. Sorry.

---

### Post by este.el.paz on 2011-01-27
Dan:

Thanks for the quick follow up, I'm winding up the day here, but I'll try the option key idea in the morning--I've already got a fair bit of time spent to get the .iso disk image burned to DVD as my iMac didn't seem like it was interested in the job.  I think I've got the correct PPC version as I spent a few days reading through articles on how to do it and how to get the PPC version and was hoping it would be a GUI experience to boot the DVD and just test drive the OS . . . as advertised on the Ubuntu home page, etc.  Not ready to do an install or partition my drive to get it full time just yet.  Tiger is doing most everything I need at this point, but I'm thinking ahead to when it won't check my emails or be able to get to web sites, then I'll need something in Linux that will work with PPC iMac.

I'll look at the other suggestions you made . . . in the near future.  Thanks again.

e.e.p.

---

### Post by este.el.paz on 2011-01-27
Dan, et al.,

Didn't wait to try the boot using option key--did that last night--and something changed, but still not getting passed the single color screen issue.  With the option key boot the screen went to white with the Terminal window and when I hit the return key it says something like "booting ELf32"  ??? and then the sounds of the optical drive . . . driving?? as the screen stayed white.  At least it showed more clearly that the display was being powered???

Today I'm going to try to get it working in my newer iBook G4 to see if the problem's related to the older G4 iMac.  But, question(s):  I downloaded the .iso using Camino, my usual browser, but sometimes I've found while downloading chess PGN's that they don't open as GUI games when using Camino--that might be part of the problem or no?  

And, then the iMac w/Superdrive was not recognizing blank DVD's so I couldn't burn the .iso in the iMac.  I transferred it to an Ext HD and then into my Intel MBP which had no problem recognizing the .iso in DU and burning it there--and then the iMac recognized the DVD.  Would there be some formatting in the Intel unit that would make the disc not work in the PPC unit?  I checked the "Get info" of the disc in the iMac and there was around 715 MB of data or so so it appears that it's physically all there--but permissions were set at "read only" since I burned it on another computer--would that matter?  Seems like that shouldn't be a factor, well, so far we still can't get passed the ".iso won't load the desktop edition"  onto the computer.  Thanks for any further thoughts.

e.e.p.

---

### Post by este.el.paz on 2011-01-27
Folks:

OK, I'm typing this running Ubuntu from my iBook booted up in the DVD, so at least I can play around with it on the iBook, and go back and try to figure out why it's not working in the iMac later.  So far it seems fine, it doesn't wake from sleep or when I close the the computer, had to re-boot, and then a couple of programs crashed while I was checking stuff.  But anyway, the sample program is working from DVD as advertised--in the iBook.

e.e.p.

---

