---
title: "Problems with &quot;Run&quot; from CD and other files"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Trine on 2008-03-06
I have just bought a new laser printer, a Xerox that ought to work with Linux distributions, but the CD that came with it, won't run - or rather, the setup.sh executable does not start up, when I press "Run" in the dialog box appearing when activating the icon.

I have read the README.txt, but was not able to get any help from that. It says following:

_______________________________________
SUPPORTED CONFIGURATIONS
------------------------

- Linux distributions : Redhat 6.x, Mandrake 7.x, SuSE 6.x, Debian 2.2, 
  Caldera OpenLinux 3.x, TurboLinux, Slackware 7.x, Linux/PPC, Yellow Dog,
  and newer versions.
- Linux kernel 2.2 and up
- GNU Libc version 2.1 and up

Requirements :
- GTK+ 1.2 libraries ; these usually come with the GNOME desktop environment,
  but if your distribution didn't install those by default, you will need to
  install them before you can use the graphical tools from this package.
- A working Ghostscript installation
- CUPS 1.1.x is the preferred printing system for this package, but the
  Linux Package will accommodate any other printing system based on LPD.
  CUPS 1.1.14 packages are provided as a convenience with this program, and can
  be installed or upgraded from the installer. However, users of Debian and
  Slackware distributions should make sure they have an active printing system
  (such as LPD) before proceeding with the installation.

INSTALLATION
------------

- Run the 'setup.sh' script on the CDROM to launch the installation program, 
  if the installer didn't start automatically upon insertion of the CDROM in
  your drive.

- You may choose either the "Recommended" or "Expert" types of installation.
  "Recommended" is fully automated and won't require any interaction on your
  part. It will install the product under /usr/local/linuxprinter.
  The "Expert" installation allows you to fine-tune these settings and choose
  where the package will be installed.

- Once the installation is done, you will be offered the option to start the 
  Configuration Tool, which allows to install and configure new Linux printers
  into your Linux system.

- The configuration tool can later be launched by using the 'linux-config'
  command, or through the menu item that may have been added to your Gnome / KDE
  menus.

_____________________________________

I have checked that all the required programs listed, are all installed on my computer. Still, nothing happens when I try to run the executable, neither the "autorun" file on the cd.

Can anyone help? Please

Trine

---

### Post by taurus on 2008-03-06
I assume your CDROM is mount to /media/cdrom0.  Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la /media/cdrom0
```

---

### Post by hyper_ch on 2008-03-06
and you need to run the setup script as root/sudo

---

