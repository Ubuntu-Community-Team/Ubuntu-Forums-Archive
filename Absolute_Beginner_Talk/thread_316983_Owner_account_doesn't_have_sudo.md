---
title: "Owner account doesn't have sudo"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by phazonmutant on 2006-12-11
Hi, I'm a new Ubuntu user, and I've been having an incredible amount of difficulty with permissions.  For general background info, I use a Gateway laptop with an Intel Core Duo processor, 2 GB of RAM, a 100 GB hard drive, and an ATI Mobility Radeon X1400.  Peripherals include: a Logitech Bluetooth mouse, a HP psc950 Multifunction printer (attached via USB), and a USB flash drive

(Major) Problem 1:  Sudo permissions
I downloaded and installed the LiveCD.  In Windows, I used PartitionMagic 8.0 to resize my Windows XP partition (not touching my vendor-installed recovery partition), and left free disk space for Linux.  I then booted the CD and installed Linux (manually editing the MBR--about 15GB for Linux, and 1.5GB for swap).
After trying it out, I got REALLY pissed off with GRUB's 10 second timeout and default to Ubuntu, so I tried to edit GRUB's menu.lst (a read-only system file).  This is where my problems start.  I realized after trying a few commands that I (the owner account) don't have sudo privileges.  So I checked User Administration, and discovered that I have a check by "Administer the System" (allowing me to use sudo, right?), and my group is my username.
Obviously, without sudo I can't install anything or change the file I need to, and I can't log on to root because 1) it's disabled and 2) sudo is needed to enable it.
I've formated the partition (using gparted on the LiveCD) and reinstalled Linux, same problem.
Now, I acknowledge that my experience with Terminal (or any command-prompt based system) and Linux is extremely limited, so I may be mistaken.  But sudo returns the error message "You don't have permission" and gksudo (graphical sudo?) returns a pretty box saying the same thing.

Problem 2:  In the first install of Ubuntu I did, it didn't seem to want to load certain web pages.  Notably, any page that wasn't Google or Wikipedia.  Very odd.  This became very problematic with problem 3

Problem 3: Drivers.  Ubuntu displays in low resolution and the GUI is laggy, is that because I need to install graphics drivers?
Also, where could I find drivers for my mouse?

I apologize for such a long post, but I've always thought it's better to be overly verbose than under-explained.

---

### Post by Iowan on 2006-12-11
Part of your details probably covered this, but...
What happens when you type (in a terminal):
```
sudo nano /boot/grub/menu.lst
```

I suspect that's similar to what you typed to get the aforementioned "You don't have permission" message.  But, if your user doesn't have **sudo** privileges, I don't understand how you could check (or edit) user privileges.

---

### Post by rccharles on 2006-12-11
> **phazonmutant said:**
> 

(Major) Problem 1:  Sudo permissions
I downloaded and installed the LiveCD.  In Windows, I used PartitionMagic 8.0 to resize my Windows XP partition (not touching my vendor-installed recovery partition), and left free disk space for Linux.  I then booted the CD and installed Linux (manually editing the MBR--about 15GB for Linux, and 1.5GB for

Maybe you entered the wrong password.

To get a continuous root command line, enter:

sudo bash

when done, enter exit

You may select single user mode at boot time.  I believe pressing, esc when grub is waiting will put you into the edit mode.  Select single user mode.

to edit the user ids which can use sudo edit:

visudo /etc/sudoers

add a line like:

robert ALL=(ALL) ALL

Substituting your userid for robert

From another angle...
Are you in the admin group?

cat /etc/group



Robert

---

### Post by phazonmutant on 2006-12-18
Thank you for you assistance, but I spontaneously seem to have sudoer permission.  Either (1) I was doing something wrong in both of my installs or (2) There really was something wrong with my first installation.  In any case, that problem is resolved.  Now to move on to the others...

I can't install the drivers for my ATI Mobility Radeon X1400.  Their official distribution is a .run, but that doesn't appear to be a valid installation executable.  I've searched for help, and a lot of times it has directed me to the Add/Remove Programs utility.  For some reason, it won't download and update repositories, it just hangs at 0%.  Also, one guide I saw told me I needed to enable the *restricted* repository, which one is this?

Possibly related to this problem is another one that has been really hindering.  I think my installation is occasionally unable to get IP addresses from a DNS server.  I've used the internet before on Ubuntu, but a few times before, it won't load a page that's not google.  I've pinged the DNS servers in my DNS server list, and they respond with a time of around 38 ms, but when I try to use Whois, it just hangs.  Again, I've used the internet on Ubuntu before, so I find this very odd.
I'm on a wireless network behind a Gateway 802.11G router (I don't know the model number, but I can find it).

---

### Post by jvc26 on 2006-12-18
The restricted repo is in your /etc/apt/sources.list

How to sort this one is as follows:
First backup your sources.list then open it for editing
```

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

```

This will bring up a sources.list like this one:
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```

Those lines with the # in front of them in yours are not available. To enable the restricted ones remove the # from infront of them (the bold lines above)

The sources.list above is taken from 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
which is probably worth a look as is the psychocats one
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
take a peek at these and that'll help.

Il

---

### Post by phazonmutant on 2006-12-19
I had the same problem connecting to the internet today.  I can search google fine, and today I can use wikipedia, but it hangs at "connecting to *x*".  For example, I couldn't get onto this site not five minutes earlier (I'm using Windows XP now).

---

