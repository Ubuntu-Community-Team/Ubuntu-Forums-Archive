---
title: "Installing Ubuntu in Dell Optiplex GX110"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Rannie on 2006-10-07
Hi there i'm new in this community.
right now i'm istalling ubuntu desktop in Dell optiplex GX110 but is not reach to the end of the installation. Is there anybody can advice what are the requirement of ubuntu for Dell Optiplex GX110?

---

### Post by wpshooter on 2006-10-07
How much memory does it have ?

How large is hard drive ?

What is the speed of the processor ?

Does it have any other current O/S on it ?

---

### Post by lapsey on 2006-10-07
what happens, exactly?

---

### Post by Dragineez on 2007-01-22
Another one.... These machines are giving the installer fits. What is happening (or **NOT** happening) is that it fails to mount the CD. If anyone can come up with a sure fire way around this, I'd love to know.
+-+-+-+Edit+-+-+-+
Used:```
boot: install ide=nodma pci=noacpi acpi=off aic7xxx=noprobe noapic nolapic hw-detect/start-pcmcia=false
```Worked on all 6 of these donated GX110's.

---

### Post by potah on 2007-01-30
I had some trouble with GX110 also.

Was wanting to install kubuntu - install cd would not mount.

I downloaded the server install - which booted fine.  Then did "sudo apt-get install kubuntu-desktop" (you should be able to do "sudo apt-get install ubuntu-desktop").

This downloaded all required packages but (I think) at the point where i should have had the login window it came up with weird flashing colours.

Thought it was some kind of refresh problem (was plugged into lcd) so plugged it into a high spec CRT with same result.  Tried all sorts of stuffing around with "sudo dpkg-reconfigure xserver-xorg" (logging into system recovery from server install disc) but nothing worked.  After searching i believe it's some kind of problem with the intel i810e integrated video.  (Tried the instructions listed here: [http://www.dilbeck.net/](http://www.dilbeck.net/) with no effect).  

I had an old nvidia tnt2 pci graphics card which i plugged in - after a bit of problems configuring the xorg.conf file it now works fine using the nv driver (except i can't eject the server install cd from the damn cd-drive ...).

---

### Post by potah on 2007-01-30
Just looking over my post - it should read:

I downloaded the server install - which booted fine.  I then installed the server (no lamp/dns) and then did the "sudo apt-get install kubuntu-desktop" ...

---

### Post by SlowYaRoll on 2007-02-05
Not sure what you guys are having problems with.  I have 3 of these machines.  They all had Windows 98SE on them.  I flashed teh BIOS and installed Dapper on two machines (one server, one desktop) and Edgy (desktop) on another.  Almost without error.  The only problem I had was that I have these LG DVD/CDRW drives that I got from ComputerGeeks.com.  Dapper recognizes this drive without any problems.  On the other hand, when I went to install Edgy. . .it'd get all the way up to the Partion setup and freeze.  I don't think Edgy recognizes the CD drive.  I took that drive out and put the original Dell cd-rom drive in, and the Edgy install went without error.

My DELL OptiPlex GX110 machines have either 512 (server) or 256 (desktops) megs of ram.
P3 866mhz
10 gig hard drive (desktops) 60 gig hard drive (server)
ATAPI ZIP100 drives.

I run VMware Server on my Dapper Server.  I actually use the ZIP drives.  When I installed Ubuntu, I made sure I already had a blank ZIP disk in the drive and proceeded thru the install.  I actually leave a blank disk in there and pop it out whenever I need to actually "use" the drive.

Everything works like a charm. . .except for syncying Dapper's version of Evolution with my Palm M100.  Edgy's version of Evolution works just fine.

P.S.
  IF IT'S OLD. . .I'LL USE IT!!!  
:lolflag:

---

### Post by Dragineez on 2007-02-06
> **potah said:**
> I I had an old nvidia tnt2 pci graphics card which i plugged in - after a bit of problems configuring the xorg.conf file it now works fine using the nv driver (except i can't eject the server install cd from the damn cd-drive ...).Could you please post your xorg.conf file. I'm about to pull out what little hair I have left trying to get an nVidia card to work in my GX110.

---

### Post by costonbw on 2007-02-07
I also have a edgy server that I tried adding the ubuntu-desktop to and now just get flashing colors.  I'm not very good with Linux yet (long time Windows SysAdmin).  Anyone have advice on getting this thing to stop booting Gnome at boot?  I've tried CTRL+ALT+1/2/3...6 to no avail.

---

### Post by potah on 2007-03-28
Bit of a delayed response to the xorg.conf query ...

Gave the machine away to a good home.

I see you got sorted on another thread.

Just thought i'd put a note in here to say that after installing with the server version, i tried to use automatix to install the proprietary nvidia driver but it was failing with some kernel package dependency not being found (forget exactly what it was now).  I needed to change over to using the normal desktop kernel package for the nvidia driver to install.  I think i ended up doing this from the gui package manager.

Hope this helps someone.

---

