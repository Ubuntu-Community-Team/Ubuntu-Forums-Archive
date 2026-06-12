---
title: "Updating Ubuntu with CDs?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by vees on 2006-05-20
Hi,

I am thinking of giving Ubuntu a try, but I wonder about one thing.  If I make a hard disk install of Ubunutu, will I be able to *update* (rather than reinstall) form the next CD shipped to me?

I only have a dial-up connection so updating via the Internet is not an option.

Another Debian derived distro, Kanotix, offers the possibility to update all the applications installed on the hard disk rather than re-install the new version instead of the old one.  Can Ubuntu do that?

Many thanks for any info!

VS

---

### Post by dmizer on 2006-05-20
two questions

what version of ubuntu do you currently have installed?
what version of ubuntu did you have shipped?

---

### Post by aysiu on 2006-05-20
If you use the *text-mode installer* CD instead of the *live/installer* CD, then you will be able to update with CDs, yes.

---

### Post by vees on 2006-05-20
Hi,

Thanks for your answers.  I have not installed Ubuntu yet, but I requested the shipping of the free CDs which, I believe, will be shipped in June with the version 6 of Ubuntu.  So my question was dealing with the future, not with an issue I have now.

How do I pick the text based installer?  Do I get a choice on boot up?

Kind regards,

VS

---

### Post by aysiu on 2006-05-20
[QUOTE=vees]
How do I pick the text based installer?  Do I get a choice on boot up?[/QUOTE] It's not a choice when you boot up the CD--it's an entirely different CD. There are two Dapper CDs:

Live/Installer CD and Text-Mode Installer CD.

The live one boots up into a live session that doesn't affect your hard drive. Once you boot up to that, you can click the **Install** icon on your desktop and install Ubuntu on to your computer. This CD contains no .deb files, so it cannot be used to update Ubuntu, only install over it.

The text-mode installer CD has no live session--it just installs, and it does have .deb files on it, so you can use it as an upgrade source disk.

---

### Post by PhilOSparta on 2006-05-20
Speaking of the future, each time there is an update on any package, Ubuntu will notify you.  If you agree to an update, the system will go out over your dial-up line and start the download.  Some of the updates are quite large.  I don't know if there is an option to get "upgrade" versions of the CDs. 

It would be nice if there was an upgrade version of the CDs issued every month or so, but I believe the way it works is that you install the June version and all upgrades must be done via the internet.

---

### Post by aysiu on 2006-05-20
[QUOTE=PhilOSparta]Speaking of the future, each time there is an update on any package, Ubuntu will notify you.  If you agree to an update, the system will go out over your dial-up line and start the download.  Some of the updates are quite large.  I don't know if there is an option to get "upgrade" versions of the CDs. 

It would be nice if there was an upgrade version of the CDs issued every month or so, but I believe the way it works is that you install the June version and all upgrades must be done via the internet.[/QUOTE] Upgrades can be done from the installer (not the live) CDs. What you have to do is use either the *apt-cdrom add* command from the command-line or Edit > Add CD-ROM from Synaptic Package Manager to add the CD-ROM source. 

Then you need to disable or "comment out" (which, again, can be done from the terminal or through Synaptic) the online repositories to force *dpkg* to look for the CD-ROM only as a source.

---

### Post by vees on 2006-05-20
Hi friends,

Thanks for all the info.  I am looking forward to trying out Ubuntu both as a live-CD and on a HD.

I ran the live-CD of the previous version (5.04) and I was rather impressed.  One strange thing happened though, Ubunutu did not see my hard disks or, should I say, I did not find out whether Ubuntu did see them.  They were not on the desktop, so I opened a console and tried 'mount' and 'cat /etc/fstab' but they were nowhere to be seen.  I did not have to time to investigate further (I was in a rush to get some work done) but this strikes me as strange.  In particular since a friend of mine had exactlyt  the same thing happening to him on some Apple hardware.  I asked him to send me his dmesg and, sure enough, his hard disk were there.  How can they be on a dmesg but not on his fstab?!

I wish I had taken the time to check my own dmesg but as I said - I was in a hurry.

Anyway am I missing something really obvious (like a exotic mount point or renamed file table) or should I look into this deeper before posting unresearched questions here :confused: ;) 

Kind regards,

VS

---

### Post by mister_p_1998 on 2006-05-20
Im  running the latest Dapper Beta, by doing all the online updates, (theres a lot isnt there? sometimes 70 a day!) will my system be exactly the same as if Id installed the Dapper final? (when its released of course)

---

### Post by aysiu on 2006-05-20
[QUOTE=vees]
One strange thing happened though, Ubunutu did not see my hard disks or, should I say, I did not find out whether Ubuntu did see them.  They were not on the desktop, so I opened a console and tried 'mount' and 'cat /etc/fstab' but they were nowhere to be seen.  I did not have to time to investigate further (I was in a rush to get some work done) but this strikes me as strange.  In particular since a friend of mine had exactlyt  the same thing happening to him on some Apple hardware.[/QUOTE] This behavior is strange only insofar as the technology is available to have partitions automount (just look at Knoppix).

The Ubuntu live CDs, however, are meant to be a preview and not to be recovery (they can be *used* for recovery, but--unlike Knoppix--they're not *designed* for recovery).

---

### Post by vees on 2006-05-20
[QUOTE=aysiu]
The Ubuntu live CDs, however, are meant to be a preview and not to be recovery (they can be *used* for recovery, but--unlike Knoppix--they're not *designed* for recovery).[/QUOTE]

well no - you don't need to mount anything to have the disks at least show up on /etc/fstab.

also, last time I tried Knoppix, the drives were detected but not automounted.

either way - how do I

1) see the drives missing form /etc/fstab
2) mount them

---

### Post by aysiu on 2006-05-20
[QUOTE=vees]well no - you don't need to mount anything to have the disks at least show up on /etc/fstab.

also, last time I tried Knoppix, the drives were detected but not automounted.[/quote] Yes, but they showed up on the desktop. If you click a partition's icon in Knoppix, it'll automount and open. There's no such option in Ubuntu.

> 
either way - how do I

1) see the drives missing form /etc/fstab
2) mount them If they're Windows drives, go here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If they're not, let me know and I'll walk you through it.

---

### Post by vees on 2006-05-20
[QUOTE=aysiu]Yes, but they showed up on the desktop. If you click a partition's icon in Knoppix, it'll automount and open. There's no such option in Ubuntu.

 If they're Windows drives, go here:[/QUOTE]

God no!  I have not used Windoze since 2000:D 

[QUOTE=aysiu]If they're not, let me know and I'll walk you through it.[/QUOTE]

they are reiserFS made by and running under Debian-Sarge.

Speaking of Debian, under Debian I would do 'cat /etc/fstab' and then 'mount /dev/XXX /media/XXX' (assuming the mountpoint exists, of course.  But with Ubuntu my fstab did not show the disks...:-k 

Cheers & thanks,

VS

---

### Post by aysiu on 2006-05-20
[QUOTE=vees]
they are reiserFS made by and running under Debian-Sarge.

Speaking of Debian, under Debian I would do 'cat /etc/fstab' and then 'mount /dev/XXX /media/XXX' (assuming the mountpoint exists, of course.  But with Ubuntu my fstab did not show the disks...:-k 

Cheers & thanks,

VS[/QUOTE] The command you want is ```
sudo fdisk -l
``` which will tell you the location off your ReiserFS partitions. Create mount points for them ```
sudo mkdir /*directoryname*
``` Edit the /etc/fstab ```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Add in a line for each partition ```
/dev/*xxx* /*directoryname* reiserfs defaults 0 0
``` Then save (Control-X), confirm (Y), and exit (Enter). ```
sudo mount -a
```

---

### Post by vees on 2006-05-21
Thanks,

That makes perfectly good sense (I should have thought of that myself).  I just did not think that this rather long way would be the only one in Ubunutu.  But - no problem, I can happily live with that.

Thanks for the walkthrough!

Kind regards,

VS

---

### Post by PriceChild on 2006-05-26
I remember playing about with my ubuntu cds, at one point i had 5.04 installed on my pc. When i inserted the 5.10 cd, it recognised it automatically as being the new version, and asked me whether i would like to upgrade.

I clicked "yes" and about 10 minutes later, all was good! (except i didn't get the tinkling sound when ubuntu logs on but that's not the most pressing issue)

Any reason why this won't work this time?

Personally i'm just going to save all my work, music and whatever else i want to keep, then completely reinstall Dapper on a clean drive. Many will say otherwise and say it shouldn't make a difference, but i think its better :)

Pricey

---

### Post by Jose Catre-Vandis on 2006-05-27
[QUOTE=PriceChild]I remember playing about with my ubuntu cds, at one point i had 5.04 installed on my pc. When i inserted the 5.10 cd, it recognised it automatically as being the new version, and asked me whether i would like to upgrade.

I clicked "yes" and about 10 minutes later, all was good! (except i didn't get the tinkling sound when ubuntu logs on but that's not the most pressing issue)

Any reason why this won't work this time?

Personally i'm just going to save all my work, music and whatever else i want to keep, then completely reinstall Dapper on a clean drive. Many will say otherwise and say it shouldn't make a difference, but i think its better :)

Pricey[/QUOTE]

This worked for me too. Easy peasy !

---

