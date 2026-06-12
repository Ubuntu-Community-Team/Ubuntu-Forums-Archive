---
title: "Server and included software suitability."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by jimleg on 2007-04-26
Hi,
I&#8217;ve used (successfully) Ubuntu desktop&#8217;s (Dapper Drake & Breezy badger). Now I am looking at utilizing a basic set of server features, and am not sure if I need to go for the Server installation or not? I would appreciate some helpful advice for a basic user like myself (with limited terminal/command confidence), about which installation of Ubuntu and the included software packages are suitable for a small one-band man business. My main interests are having some centralised data and back-up options for data that has been stored on other systems. I would be prepared to purchase the Canonical  Server support on an annual basis as I need to be serious about  managing my data.

I do not need or want or need many of the full Server services that the Server edition offers. I will put this installation on dedicated server hardware, some basic features that I do want are:
1) A back-up utility that takes files/data from other networked windows machines, and saves these back up&#8217;s to various types of drive on the Ubuntu Server,
2) System management/support of local RAID 1 and SATA drives.
3) SAMBA File sharing to windows clients, I know this is not a problem.
4) I use an extensive collection of Windows Web links/URL&#8217;s which I want to share on the network, with both Internet Explorer & browsers like Firefox. I would need a management utility to convert the IE links and manage the URL/Bookmarks etc.
5) I also want to set-up and use an easy to use and configure LDAP database, I&#8217;ll be importing contact data in from MS Outlook PST files.

I really am a low level user with a very limited amount of time to learn new tricks. And would appreciate recommendations of (simple to use) software available within Ubuntu that might match my basic knowledge. 

Thanks

Jim.

---

### Post by KaeseEs on 2007-04-26
Some good news: your vanilla Ubuntu is capable of just about any server task you might throw at it, once you install the right software.  The Ubuntu server installation is identical to the desktop installation, except that it completely free of any graphical programs (X, Gnome/KDE, etc.).  

For your backup needs, probably the most elegant solution would be to mount the networked machines as SAMBA shares, and put a script to copy files on your cron tab (a daily/weekly/etc task scheduler).  However, you probably want something more point-and-click manageable, so I'll have to defer here to others.

For management of RAID and other drive setups, look into LVM (logical volume manager) and EVMS (Enterprise Volume Management System).

As you said, SAMBA, is not going to be a problem.  I'd recommend [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) for a guide to doing this.

I'd also like to note that google and the forums search bar are your friend here, and can often get you results much more quickly than anything else.

Best of luck with your computing and your business!

---

### Post by jimleg on 2007-04-26
My Thanks to KaeseEs for his input,

I’d like some further information please: If I were to use a current version of Ubuntu desktop instead of the Server installation would I have a less stable platform? i.e. is the server install more stable, with less graphical features and presumably more “test time” in place?

I need to learn cron, and have seen helpful little tutorials around and will investigate both of KaeseEs suggestions. I’ll go look at his other proposals too.

I’d still like to hear from those of you that can provide relevant information about suitable IE Favourite and BookMark URL management and suggestions for LDAP implementation (see above).
Would any of these questions be better suited in one of the other Ubuntu forums?

TIA.

Jim.

---

### Post by gh0st on 2007-04-26
I don't think the server version is any more stable than the desktop version. It's exactly the same with just the graphical components removed. The reason they are removed is not for stability as far as I know, it's just because the GUI parts of the system are an unnecessary overhead on a professional remote web server with lots of traffic. It doesn't sound like you are wanting to deploy in that kind of environment at all. I don't see a problem with using the normal desktop version, especially if you don't like using the terminal.

Using scripts and scheduling them in Cron is a good solution for backups but if you want something more GUI based there are a few backup applications out there that you might wanna check out. Here are some links:

[http://www.bacula.org/](http://www.bacula.org/)

You might wanna check this tutorial out - [http://www.ubuntux.org/detailed-bacula-network-backup-implementation-guide](http://www.ubuntux.org/detailed-bacula-network-backup-implementation-guide)

Good list of packages - [http://www.linuxlinks.com/Software/Backup/](http://www.linuxlinks.com/Software/Backup/)

For sharing your links between machines try this:
[http://paininthetech.com/synchronize_your_bookmarks_between_different_computers](http://paininthetech.com/synchronize_your_bookmarks_between_different_computers)

Hope that helps you out in some way. Good luck :)

---

