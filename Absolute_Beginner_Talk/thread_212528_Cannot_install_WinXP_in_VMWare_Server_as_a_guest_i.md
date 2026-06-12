---
title: "Cannot install WinXP in VMWare Server as a guest in (K)ubuntu host."
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by gios on 2006-07-10
Morning folks.

I have just spent the weekend converting my work 'server' to Kubuntu; Ubuntu kept crashing with the Nvidia GF6600LE VGA card but all is good under K, which is what I am using.  At work we use Sage Line 50 and I cannot let go of this piece of software right now.  I need to run Win XP (as I do not own a  Server version) which is why I installed VMWare Server (after much pain).  However I absolutely cannot manage to make the OS get recognised by the VMW.  I have tried unzipping pre-made files, I have tried reading from ISO and a multitude of other half-understood attempts.  All walk-throughs, while very well done seem to skim over this part - probably because it is taken for granted that even a noob would manage it ! I did not and in conclusion, would very much like to know if a walk-through for dummy noobs exists which facilitates the insertion of the WinXP OS into VMWare server, hosted by Kubuntu.

Best rgds.

---

### Post by fluffington on 2006-07-10
I installed VMWare Server and several operating systems (Windows XP Pro included) on Kubuntu just last week, and found the entire process fairly painless. Here's a quick HOW-TO:

VMWware Server (I know you already got this far, but I'm going over what I did in case you missed something or want to do it again in the future):[list=1]
[*]Install xinetd, build-essential, and the appropriate linux-headers package ```
sudo apt-get install xinetd build-essential linux-headers-`uname -r`
```
[*]Download the tar.gz binary from VMWare's site and get your key via e-mail.
[*]Unpack, run vmware-install.pl (with sudo or as root), and use the default settings for everything (the only one I changed was the location of the virtual machines).```
tar xvzf VMWare-server-1.0.0-27828.tar.gz
cd vmware-server-distrib
./vmware-install-pl
```
[*]Run vmware from the console as root. Make note of any errors that show up (I didn't have any) and change the global settings to whatever you think is reasonable (I only had to decrease the amount of RAM used by Server).```
sudo vmare
```
[*]Change owner and group on ~/.vmware/preferences to your username (running as root changes the preferences to root, which makes it not work later)```
sudo chown `whoami`:`whoami` ~/.vmware/preferences
```
[*]Run vmware from the console (not as root) and make note of any errors that show up. If you don't get any errors at this point, you can probably safely use the entry in the menu from here on out.```
vmware
```
[/list]

Windows XP:[list=1]
[*]Click "Create a new virtual machine"
[*]Typical settings
[*]Select "Microsoft Windows" and whatever version you're using ("Windows XP Professional" for me)
[*]Fill in the name and location (I used the defaults)
[*]Pick a network type (I used NAT)
[*]Change the disk size (I used the defaults)
[*]Click Finish
[*]You should be back at the VMWare Server Console, with the new virtual machine selected. Click "Edit virtual machine settings".
[*]Change the amount of memory (default was 256M, which is fine, but I have 2G on this box, so I gave it 512M)
[*]Change the CD-ROM (It should default to using the host's CD drive) if you plan on installing from an ISO
[*]Click Add and select Sound Adapter if you want sound (the default settings should be fine)
[*]Press OK, and "Power on this virtual machine".
[*]If everything went well, the Windows installer should come up.
[*]Once Windows is installed, go to VM -> Install VMWare Tools to install the appropriate drivers.
[*]If you installed from an ISO, you'll want to power off the virtual machine and change the CD-ROM to point somewhere else.
[/list]

Hope that helps.

---

