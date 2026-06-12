---
title: "problem printing hp laserjet 6l"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by u0392185 on 2007-02-05
I am new to Ubuntu and have spent the last two days trying to set up my HP Laserjet 6L.  I am using Ubuntu 6.10 on a AMD 64 system.  I followed the advide on all the tutorials but was unable to get the printer to work.  I have intalled all the cups pachages, and foomatic packages.  I have installed the printer about ten times and uninstalled it.  I have been mostly using the default driver , ljet5.ppd, which is supposed to work perfectly.  When i go to print test pages nothing happens.  Somebody please help me diagnose this.

Brian

---

### Post by Sef on 2007-02-05
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_6L").

From LinuxPrinting:  >  Remember that the 6L is more like the LaserJet 4 family than the LaserJet 6 family (as with most "L" printers from HP). For example it does not work with the "lj5gray"/"lj5mono" drivers but only with the "ljet4" or "lj4dith" drivers (and also Gimp-Print and HPIJS).

---

### Post by u0392185 on 2007-02-05
> **Sef said:**
> Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_6L").

From LinuxPrinting:

I have been through all of that.  I am pretty confident that the problem is not with the driver, but with the parallel port.  For instance the printer is not recognised and I have to intall it as Hp_no_device_found.   I used the CUPS online printer setup, and the printer was supposedly set up correctly, yet the test page would not print.  Please help.

---

### Post by Xappe on 2007-02-05
I have the same printer as you (LaserJet 6L), and I got it working with the ljet4 driver. Don't think I did anything else to get it running but to add it through the Printing tool in gnome...

---

### Post by u0392185 on 2007-02-05
Thats depressing.  You mean administration, printing? I wonder if maybe I have inadvertanly installed extra packages that are preventing it from work.  I have tried everything on the tutorials.   I really would like to know some terminal commands that will help me with that, and maybe someone who knows what they are looking at can tell me how I messed things up.

---

### Post by u0392185 on 2007-02-05
I am pretty sure that the drivers are correctly configured, but I don't think my parallel port is showing up.  I found a thread that said there was possibly a bug in the amd64 ubuntu 6.10.  I really need a way to diagnose the parallel port, I think.  [http://www.ubuntuforums.org/showthread.php?t=316233&highlight=parallel+port+bug]("http://www.ubuntuforums.org/showthread.php?t=316233&highlight=parallel+port+bug")

---

### Post by u0392185 on 2007-02-06
I figured it out.  Had to enable my Parallel Port in BIOS.  Stupid of me I know.

---

