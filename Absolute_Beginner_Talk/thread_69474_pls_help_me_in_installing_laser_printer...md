---
title: "pls help me in installing laser printer.."
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Lancelot on 2005-09-27
hello guys,

can you help me pls, after installing my printer Kyocera in ubuntu in usb even in tcp..i have a problem in print out..in a piece of paper..


%!
 % %  % %
                 % !PS-Adobe-3.0
                                        %RBINumCopies: 1
                                                                  %%Pages: (atend)
                                                                                            %%Title:

                                                                                                etc..
I can print in winxp2..
my problem is can print in network using samba, but the result is above mentioned..

I am using samba, smbfs,
my printer server (kyocera) is in winxpsp2..
my workstation is ubuntu..

Thanks in advance,

- Lancelot

---

### Post by nocturn on 2005-09-27
[QUOTE=Lancelot]hello guys,

can you help me pls, after installing my printer Kyocera in ubuntu in usb even in tcp..i have a problem in print out..in a piece of paper..


%!
 % %  % %
                 % !PS-Adobe-3.0
                                        %RBINumCopies: 1
                                                                  %%Pages: (atend)
                                                                                            %%Title:

                                                                                                etc..
[/QUOTE]


Hello Lancelot

I can at least tell you the cause of the problem.  The printer gets the information from your Linux box, but prints out the postscript commands it received instead of interpreting them.

How did you set it up in Ubuntu?  Did you use the printer control panel, and what options/drivers did you set?

---

### Post by Lancelot on 2005-09-27
This is the setup...

Winxp - SErver (Winxp sp2 Norton 2005)
Shared printer name:
Kyocera
Ip add: 10.0.0.5


Ubuntu - Workstation
System>Administration>Printing>Add Printers
Network Printer - Windows Printer (SMB)
Host - 10.0.0.5
Printer - Kyocera
UserName:    Password:

that's it..
i have a driver of kyocera in linux - and i thought that the ppd only the driver that he got..

in HP no problem..but in Kyocera..
I tried in in detecting and direct printing with my workstation using CUPS nothing works..
the output is still the same..i think i need to update the postscript?
what do you advice..?

---

### Post by nocturn on 2005-09-27
[QUOTE=Lancelot]
in HP no problem..but in Kyocera..
I tried in in detecting and direct printing with my workstation using CUPS nothing works..
the output is still the same..i think i need to update the postscript?
what do you advice..?[/QUOTE]

Do you have a HP that is working? (also connected to the Win2000 machine).
In the driver selection box, did you select the exact model?
Also there, do you see the gimp-print driver?

---

### Post by Lancelot on 2005-09-27
ya..i have an hp that is working..
and i choose the exact model..
no gimp-print driver..coz it came from a cd..just ppd drivers..
kyocera1815.ppd

is there a problem if not gimp-print driver?

---

### Post by nocturn on 2005-09-27
[QUOTE=Lancelot]
is there a problem if not gimp-print driver?[/QUOTE]

Not really, but I found the gimp-print drivers of better quality then the others.
What is the exact model of printer you have?

Also one more thing to check, does the resolution set on the Ubuntu panel match the one set in Windows?

From what program did you try to print?  Maybe try something easy like gedit first.

---

### Post by Lancelot on 2005-09-27
[QUOTE=nocturn]
Also one more thing to check, does the resolution set on the Ubuntu panel match the one set in Windows?

From what program did you try to print?  Maybe try something easy like gedit first.[/QUOTE]

am complete noobs on this stuff..they have the same resolution..
i try to print test..but the output is the same..

i only install the KYOCERA MITA 1815.ppd

but there is available file in cd>linux>kmpdq>
km-install-rpm
km-install-tar
km-update-printc
pdq-2.4.4.1.386.rpm
pdq-kyo-km-2.4.4.tgz

is this files be installed? or not?
i read it from from the read me ...

Installation Note
Kyocera Mita Linux Support using PDQ
Installation Components
Kyocera Mita devices are supported on Linux (and other UNIXs) through the PDQ print system. The installer places the pdq and xpdq applications in the /usr/local/bin directory. It also installs .drv files for each supported Kyocera Mita device. Xpdq is a graphical print tool designed for printing and monitoring print jobs. Within an X Window session, you can control the driver settings and manage print jobs.

Installation of the Kyocera Mita Linux support can be accomplished in two ways: the RedHat Package Manager (rpm) installs the compiled object files to the proper directories, or for users familiar with installing software via compilation, select the tar file provided.

The Kyocera Mita models are supported through the following .drv files:
kcfs0600.drv, kcfs0680.drv, kcfs0800.drv, kcfs1000.drv, kcfs1200.drv, kcfs1700.drv, kcfs1700p.drv, kcfs1750.drv, kcfs3700.drv, kcfs3700p.drv, kcfs3750.drv, kcfs5800c.drv, kcfs5900c.drv, kcfs6900.drv, kcfs7000.drv, kcfs7000p.drv, kcfs9000.drv, kmci1100.drv, kmfs1000p.drv, kmfs1010.drv, kmfs1050.drv, kmfs1800.drv, kmfs1800p.drv, kmfs1900.drv, kmfs3800.drv, kmfs6020.drv, kmfs6026.drv, kmfs8000c.drv, kmfs9100dn.drv, kmfs9500dn.drv, kmfsc5016n.drv, kmkm1510.drv, kmkm1530.drv, kmkm1810.drv, kmkm2030.drv, kmkm2530.drv, kmkm3530.drv, kmkm4030.drv, kmkm4230_5230.drv, kmkm4530.drv, kmkm5530.drv, kmkm6230.drv, kmkm6330.drv, kmkm7530.drv, kmkmc830.drv

This package has been developed and tested primarily on Linux systems, although it should be suitable for any form of UNIX. If your system supports PDQ, this installer will successfully add Kyocera Mita device support. For non-Linux platforms, compiling from the source is the preferred method.

For more information about pdq, visit [http://pdq.sourceforge.net/](http://pdq.sourceforge.net/)
Xpdq requires the Gnome Gtk/Glib libraries to be installed on the system. This may present a problem for earlier Linux versions or another flavor of UNIX. RedHat 6.0, SUSE 6.3 and Caldera OpenLinux 2.4 already have these libraries. To verify the presence of the required libraries, type the following command:

    gtk-config --version
    glib-config --version

If both of these commands return a version of 1.2.0 or higher, the libraries are installed. If not, download the latest Gtk/Glib libraries and instructions at [www.gtk.org](www.gtk.org) and install them.


Additional Information:
GhostScript 5.50 and above must be installed in the system.

Fonts used for printing must be installed and configured for GhostScript.

Perl 5.6.0 and above must be installed in the system.
 

Installing from the RPM Package (Recommended)

1)  Insert and mount the CD.

On some Linux distributions, the CD is automatically mounted.

The following command is an example of how to mount a CD, assuming the mount point is ‘/mnt/cdrom’. (The mount point varies depending on the Linux distribution.)

mount /mnt/cdrom

2)  Open a terminal such as xterm, then run the following command from a shell. (It does not matter whether the Kyocera PDQ has already been installed.)

You do not have to become a super user at this time.

It does not matter whether a pre-existing PDQ was installed from RPM or tar.

/mnt/cdrom/Linux/KMPDQ/km-install-rpm

On some Linux distributions like SuSE, the script ‘km-install-rpm’ cannot be launched directly from the CD due to security reasons.

In this case, it is necessary to type the following at the command line instead:

bash /mnt/cdrom/Linux/KMPDQ/km-install-rpm

3) Follow the instructions displayed on the screen to finish the installation process.

Installing from the tar file

1)  Insert and mount the CD.

On some Linux distributions, the CD is automatically mounted.

The following command is an example of how to mount a CD, assuming the mount point is ‘/mnt/cdrom’. (The mount point varies depending on the Linux distribution.)

mount /mnt/cdrom
2)       Open a terminal such as xterm, then run the following command from a shell. (It does not matter whether the Kyocera PDQ has already been installed.)

You do not have to become a super user at this time.

It does not matter whether a pre-existing PDQ was installed from RPM or tar.

/mnt/cdrom/Linux/KMPDQ/km-install-tar

On some Linux distributions like SuSE, the script ‘km-install-tar‘ cannot be launched directly from the CD due to security reasons.

In this case, it is necessary to type the following at the command line instead:

bash /mnt/cdrom/Linux/KMPDQ/km-install-tar

3)     Follow the instructions displayed on the screen to finish the installation process.


how can do this..if this files were to be installed?
i know a few command in terminal..but i just keep in learning..

thanks a lot,,

---

### Post by nocturn on 2005-09-27
[QUOTE=Lancelot]am complete noobs on this stuff..they have the same resolution..
i try to print test..but the output is the same..


how can do this..if this files were to be installed?
i know a few command in terminal..but i just keep in learning..

thanks a lot,,[/QUOTE]

Ok, let's disregard the installation CD for the moment as I do not know how well it works.

Can you see if gimp-print is installed?
If so, try the HP Laserjet 4 series driver, the gimp-print site lists this as working for your type of printer.

If this has the same result, maybe you can try it first with the printer connected locally (to the Ubuntu machine).

---

### Post by Lancelot on 2005-09-27
[QUOTE=nocturn]Ok, let's disregard the installation CD for the moment as I do not know how well it works.

Can you see if gimp-print is installed?
If so, try the HP Laserjet 4 series driver, the gimp-print site lists this as working for your type of printer.

If this has the same result, maybe you can try it first with the printer connected locally (to the Ubuntu machine).[/QUOTE]

Gotcha! Thanks nocturn... Thanks for the advice..
i try HP Laserjet 4 series drivers...
But why is that machine(kyocera) is good for HP Laserjet 4? how can i explain it to myself?

anyway thanks a lot,

-Lancelot

---

### Post by nocturn on 2005-09-29
[QUOTE=Lancelot]Gotcha! Thanks nocturn... Thanks for the advice..
i try HP Laserjet 4 series drivers...
But why is that machine(kyocera) is good for HP Laserjet 4? how can i explain it to myself?
anyway thanks a lot,
-Lancelot[/QUOTE]

The control language used by both models is the same, that is why it works.

---

