---
title: "NOOB start-up questions"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by mstone on 2008-02-18
I recently decided to investigate the viability of switching from a WAMP (Win2K) web server to LAMP, and came across Ubuntu.  After trying the LiveCD and liking it, I downloaded Ubuntu 7.10 Server Edition, burned it to a CD, and ran the installer.  I selected the LAMP, mail server, and Samba programs.

Everything seemed to install fine.  But I was quite surprised (and somewhat befuddled) when it booted to a command-line prompt, and not a GUI desktop.  I logged in with the non-root account as requested, but still no desktop.  I'm familiar with Unix systems (HP-UX), but not enough to know why the desktop didn't start.  Is this by default on the server edition?  How do I start the desktop?

Also, once I get the server and desktop parts configured, I will install a second harddrive that will be completely devoted to the web content (i.e. the Apache document root = D:/).  Can Ubuntu handle a 250G drive?  In anticipation of complications, is there anything specific I should do when setting up such a drive (e.g. format options, partitioning, etc), keeping in mind that I will be copying data back and forth between this server and a Windows2K computer (development machine)?

Thanks in advance,
Mitch

P.S. FYI, I'm not a noobie to computers - I've been a software engineer for 20 years and have maintained my own web/mail server for about 6 yrs.  So, yes, I did search the forums already, with various different search parameters and did not find an answer.

---

### Post by Scheater5 on 2008-02-18
Yes, CLI is the default on the server edition.  To install a GUI from this point, connected to the internet, run the command 
> sudo aptitude update
sudo aptitude install ubuntu-desktop
You may also substitute apt-get instead of aptitude, and kubuntu-desktop or kde-base instead of ubuntu-desktop.  I think there's a way to install gnome-base, too, but I don't think it's "install gnome-base."  Gnome user wanna take that one?
The repositories also include fluxbox, blackbox, matchbox, and I think e16 that can be installed with the same process.  So take your pick.

---

### Post by mstone on 2008-02-18
Thanks!  I now have a desktop!  Time to play!!!  :)

Where is this documented?  I looked at the help pages under the "New To Ubuntu" and it starts off explaining how to use the desktop.  And the Server homepage doesn't mention anything about having to load a desktop, and even implies the gnome desktop as being part of the installer (at least that's my recollection from a couple of weeks ago).

--Mitch

---

### Post by theRightNee on 2008-02-18
hey mstone,
i have not had much experience with the server edition (none at all really), but I am pretty sure it can handle a 250 GB harddrive. Only complication that may arise is having to change a few things to autoboot the second HDD (it does not automatically mount) I forget where this tutorial is...my apologies

---

### Post by ice60 on 2008-02-18
you can install a much lighter desktop if you're using it as a server, there's fluxbox. ubuntu-desktop installs loads of stuff doesn't it :confused: i just always thought the whole point of a server was to have only the minium amount of things running and installed as possible, that way there's less to exploit and hack in to! 

OT, i once saw someone who'd only used MS servers review an ubuntu server install, he said there was no desktop and no software and it was rubbish! i wish i'd kept the link :D

---

### Post by mstone on 2008-02-18
theRightNee - I found this page on mounting drives: [https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29%7C%28auto%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29%7C%28auto%29), but it seems to be assuming I'm taking a drive from a Windows machine and moving it to my Linux box.
Question to the community: is it better to simply take the data drive from my out-going Windows server and plop it into my Linux server and mount that puppy as specified on the above link (keeping the NTFS type); or should I start with a fresh drive, format it using a Linux format, and copy the data over (via Samba)?

ice60 - Yeah, I was a bit surprised when it took an hour to download the desktop, then another hour to unpack the whole thing?!?!  Whathappened to "lightweight"?!?  Is there a utility out there to streamline the desktop, sorta like the Windows optimizers that delete what's not used from your system?

Thanks for y'all's help & comments!  Greatly appreciated!
--Mitch

---

### Post by ejay563 on 2008-02-19
As for putting in the second hard drive, I would format it as ext3, and then mount it in fstab so it will mount on startup. 

#ls /dev

this lists all devices. Find the second hard drive (probably hdb or sdb)

Once you have determined whihc is the second hard drive

#sudo gedit /etc/fstab

and add an entry like this to it (subsittuting drive and parition letters/numbers)

# /dev/sdxY
/dev/sdxY /media/sdxY     ext3    defaults      0         0

save the file, and the second hard drive will now mount automatically on startup. 

I don't know of any utility that will automatically go through and delete what is not used, but if you open up the package manager, (the Add/Remove item at the bottom of the Applications menu) and select "Installed Packages" from the drop down list at the top right, you can go through and de-select what you don't want. Good luck!

---

### Post by hyper_ch on 2008-02-19
mstone:

What do you need a gui for on a dedicated server? It would be a waste of system resources.

Au contraire to windows, you don't have a central registry but you have config files for each application. You alter the way an application is setup by editing their configs. So there is no need for a gui on a true dedicated server and that's why you don't get a GUI by installing a server version.

---

### Post by ice60 on 2008-02-19
if i were you i'd just spend a few weeks working with what you've got and learning a bit about using a terminal, then do a reinstall and not install a desktop.

there's a subforum for servers and security here, well there used to be, i can't find it now!

once you have the server setup you can run something like Aide, an intrution detection, or apparmor which will help lockdown the server.

for Aide you just run this (it will tell you if anything has changed on the system when you re-run it) -

in a root shell run this -
# aide --init

that will create the databse.

then move that new database and make it the default database -
cd /var/lib/aide/
mv aide.db.new aide.db

the rules governing what and how things are checked are kept here -
/etc/aide.conf

to re-run and check for any changes run this from a root shell -
# aide --check -V2 

you can keep the database on a CD, or off the HDD so it can't be altered by anyone else. i'd don't use servers so i'm not an expert, you're better off asking at the appropriate subforum (if you can find it lol)

you can lookup things like 'locking down a server install' 'harding linux' 'securing linux' etc

---

