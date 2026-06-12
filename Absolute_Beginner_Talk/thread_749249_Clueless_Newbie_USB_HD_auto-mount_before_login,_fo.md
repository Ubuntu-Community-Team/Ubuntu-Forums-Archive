---
title: "Clueless Newbie: USB HD auto-mount before login, for Samba?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Delta5 on 2008-04-08
Hello to all.  

First of all, let me say that I have been a long-time Windows user.   I've tinkered with a couple of Linux distros before; Ubuntu, Suse, and Redhat, but have always treated them more as a curiosity than an actual tool.  Being a somewhat entrenched Windows guy, I never really had a reason to keep them around.  Recently, however, I have a need for a simple file & print server at home.  I could install Win2K or XP Pro on a spare desktop, and I know that it would work and work easily, because that's what I'm used to both at work and at home. 

But I decided to go back to Linux, specifically Ubuntu, to give it another go.  I had been impressed with Ubuntu when I had tinkered with it a few months back.  I'm a computer guy (C#/VB.Net/VB6 software developer & MSSQL DBA at my company) who is somewhat embarrassed to admit that I don't know much about Linux.  \\:D/  So I'm trying to learn.  I want to learn because I'm growing a bit tired of my Micro-centric world, and variety is the spice of life, right?  

I have a 250GB Seagate FreeAgent USB drive that I want to use as shared hard drive space on my home network.  A place for my wife and I to backup documents, photos, etc.  Nothing fancy.  I also have an HP printer I'd like to share too.  To make a long story short, after a couple of hours of tinkering, I got all of that working exactly as I want, **except** that I have to log in to the Ubuntu machine to force the Seagate shares to come online.  **Samba, or Ubuntu in general does not seem to be auto-mounting that USB drive on boot, and I don't know how to tell it to do so.  It seems to unmount the USB drive whenever no one is logged in.  That's not what I want, and that's my problem.**

I don't know what will be helpful, so here's what I've done...

I downloaded the 7.10 ISO Desktop version and installed it on a spare desktop.  It's a few-years-old Shuttle mini-PC with an AMD 2800+ , 1GB ram, 80GB ATA hard drive.  If that matters.  Easy as could be.  Immediately downloaded a couple hundred megs of updates, also easy.  I am very impressed at the ease of the setup.  

[LIST=1]
[*]Winbind.  I wanted Ubuntu to be able to 'see' my windows PC's by name.  Installed & configured this, as outlined [http://ubuntuforums.org/showthread.php?t=405662]("http://ubuntuforums.org/showthread.php?t=405662").  Seems to work great, as I can ping & 'see' windows PC' (XP & Vista) by name now.
[*]Samba.  I knew I'd need Samba to do what I wanted to do.  Followed big chunks of this tutorial. [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba").  One big change is that since this server was on a private, local, home network with only two users, I don't care about needing a username/password to get to the shares, so I followed the advice here [http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/]("http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/").  I then set up the shares using the Shared Folders GUI.  Quite easy.  The folders show up & are R/W accessible from Vista & XP machines on my network without prompting from a user/pass.  Looking great!

[*]Seagate USB drive fix.  I'm using a 250GB Seagate USB FreeAgent drive as a file backup.  Music & photos.  I discovered that after a few minutes the USB drive would disappear and wouldn't re-mount.  A few minutes later, with the help of Google, I discovered that there is a bug/design flaw with the drive and/or Ubuntu that prevents the drive from coming out of 'sleep mode'.   It was affecting my setup, so I found & applied the fix from here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/193154]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/193154").  I created /etc/udev/rules.d/98-local.rules and added 

# Set the allow_restart flag for all SCSI disks.
ACTION=="add", \
SUBSYSTEM=="scsi_disk", \
ATTR{allow_restart}="1"

to the file.  That seems to have fixed the problem, as the drive now spools back up from sleep mode.  Granted, I have no idea what I really did in that file, but I can follow directions.

[*]Printer.  I have an HP All-In-One printer.  Hooked it up, auto-installed, works.  Easier than windows.  :)  Configured it to be sharable via the GUI, and it works perfectly from Ubuntu & Windows machines.  Really neat.

[/LIST]

For good measure, I then rebooted the Ubuntu machine.  Once rebooted, I could still see the shares from a Windows machine, but I'd get a 'share not available' error message when I tried to open it.  I quickly discovered that if I was logged in to Ubuntu (with any account), that the shares would then work.  I could then log back out, and the shares would cease working.

So that's where I am.  I don't know how to fix it as I haven't had much success finding a solution online.  How do I tell Ubuntu/Samba to keep that USB drive mounted at all times?  It seems that once that's working, my little Ubuntu server will be fully operational.

Do I need to do something like this? Specifically, adding it to the fstab?
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Thanks for your time, and I look forward to learning as much as I can so I can help someone else down the line!  :)

---

### Post by Delta5 on 2008-04-08
Ignore this post. I hit reply by accident...

---

### Post by Delta5 on 2008-04-08
Anyone? :redface:

---

