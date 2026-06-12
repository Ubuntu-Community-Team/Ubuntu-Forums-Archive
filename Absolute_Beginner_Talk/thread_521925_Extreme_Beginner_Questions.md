---
title: "Extreme Beginner Questions"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Bart_D on 2007-08-09
Hello, I tried the Live-CD to see how Ubuntu 7.04 desktop i386 would run on my system and am now considering installing it.  Before I do, I have some questions:

1.  I tried it out (CD-ROM in drive) with a USB keyboard and USB mouse and it worked fine with the OS running from the CD.  Both mouse and keyboard were connected to onboard USB 1.1 ports and worked fine.  Now, can I proceed with installation using the USB keyboard/mouse or should I use a PS2 mouse/keyboard instead?  I am not concerned with installing any software for the keyboard(as it requires some) but instead just want the basic functions especially NUM-LOCK to start off. 

2.  Are there any detailed step-by-step instructions as to how I could install Java, out there somewhere?

3.  Where would I get access to applications like anti-virus and anti-adware scanners and a firewall?

4.  The only piece of hardware I have added to my system is a USB 2.0 PCI Expansion Card.  I would like to use this with USB sticks.  Where would I get instructions to allow for this?

That&#8217;s all for now&#8230;your help would be greatly appreciated as I&#8217;d like to get most of it done this Saturday so I&#8217;m trying to prepare mentally and physically for the move.  I hope this is the right forum.

Please excuse the language.....I am not very familiar with computers but have had enough of slow Windows and would like to switch. :guitar:

Bart

---

### Post by vexorian on 2007-08-09
> 1. I tried it out (CD-ROM in drive) with a USB keyboard and USB mouse and it worked fine with the OS running from the CD. Both mouse and keyboard were connected to onboard USB 1.1 ports and worked fine. Now, can I proceed with installation using the USB keyboard/mouse or should I use a PS2 mouse/keyboard instead? I am not concerned with installing any software for the keyboard(as it requires some) but instead just want the basic functions especially NUM-LOCK to start off If they worked well with the live-cd they are good for the installation, regarding NUM-LOCK to start-off I am not sure about it.

2. Yes. It is very easy actually, you just have to get to the synaptic package manager and look for sun-java packages.

3. none of those is necessary on ubuntu! firewall might be needed if somewhen you open a port for an special task like ssh or sharing things, for that you can install firestarter, also from synaptic package manager.

4. Is it detected by the live-cd ?

---

### Post by userundefine on 2007-08-09
> **Bart_D said:**
> 1.  I tried it out (CD-ROM in drive) with a USB keyboard and USB mouse and it worked fine with the OS running from the CD.  Both mouse and keyboard were connected to onboard USB 1.1 ports and worked fine.  Now, can I proceed with installation using the USB keyboard/mouse or should I use a PS2 mouse/keyboard instead?  I am not concerned with installing any software for the keyboard(as it requires some) but instead just want the basic functions especially NUM-LOCK to start off.
Shouldn't be a problem.

> 2.  Are there any detailed step-by-step instructions as to how I could install Java, out there somewhere?
Yes, you'd simply search for these packages in Synaptic sun-java6-bin, sun-java6-jre and install them, as listed [here.]("https://help.ubuntu.com/community/Java#head-7852ba79216c811b4345924d824bf15489ce7164")

> 3.  Where would I get access to applications like anti-virus and anti-adware scanners and a firewall?
There are several firewalls and a few anti-virus programs in the repositories, easily installable from Synaptic.  However, if you're just using this for home use, anti-virus isn't necessary and Ubuntu ships without open ports by default so a firewall isn't required, unless you want one, of course.  Anti-adware software isn't needed on *nix.

> Please excuse the language.....I am not very familiar with computers but have had enough of slow Windows and would like to switch. :guitar:
Everyone starts somewhere.  Take your time and enjoy.

---

### Post by mybunche on 2007-08-09
Welcome. 
I had the same queries when I first started using 6.10. I have installed Ubuntu on a portable USB hard drive which is permanently attached to the PC (USB 2.0 port) so on boot up I select XP or Ubuntu. It defaults to XP because others use the PC as well. For me I find this more comfortable to have Ubuntu on a separate HD independent from my Windows HD. Works perfectly.

1. USB mouse/keyboard should be fine. NUM lock setup can be changed in the setup as the PC starts up . For me I press F12 to enter setup mode.

2. After install, go System>Administration>Synaptic Package Manager, enter password, click search, search for sun-java. Look for sun-java6-bin, sun-java6-jre, sun-java6-plugin, select these three, and apply.

3. I haven't installed any of these. Ubuntu is pretty locked down anyway. Anyway, after install you'll have time to do some research if you want these things.

4. I have USB 2.0 PCI card as well, it was just plug and play for me. No problem here.

Hope all goes well. I've been a very happy Ubuntu user for about 9 months.

---

### Post by Bart_D on 2007-08-10
Well, that was quick.  Thanks for the QUICK replies.  Two more questions:

5.  I forgot to mention that I want to install xubuntu.  Will I be able to do so by simply following these instructions:

LINK:  [http://www.xubuntu.org/get](http://www.xubuntu.org/get)
Install Xubuntu from Ubuntu
If you have an existing Ubuntu, Kubuntu, or Edubuntu installation, it is possible to install Xubuntu and retain your current installation. To do so, just go into Synaptic (or Adept if you use Kubuntu) and install the xubuntu-desktop package. There you are! Next time you login, you can choose Xubuntu from the Session menu on the login screen.

or will I need to carry out some prior steps?

6.  [https://help.ubuntu.com/7.04/installation-guide/i386/module-details.html](https://help.ubuntu.com/7.04/installation-guide/i386/module-details.html)  This link says something about encryption....is it possible to encrypt without partitioning as I do not intend on setting up a partition(s)?

Ok, welll, I've installed it and so far it seems good.  However, I have a real issue:

***FIXED***
7.  I had previously installed Windows on this PC with Thunderbird as the email client, so I am very familiar with Thunderbird.  Now, since my ISP does not provide IMAP support, in Thunderbird's Account Settings I had set a custom Message Store folder.  The folder was a shared folder on another PC.  Thunderbird was also installed on that PC.  So basically, the Email Store folder was being shared by two PCs and this way the same email account was being shared by the two different PCs.  This avoided causing the SAME messages to be downloaded into the mailbox on BOTH computers.

Now, I have Xubuntu Xfce running and I cannot find a Network Connections button somewhere to view my network connections.  This is a wired connection and the Internet works just fine.  When I click on Account Settings in Thunderbird and go to the Message Store Folder "Browse" option to set the store folder as the Shared Folder on the other PC - a Windows PC, I cannot view the second computer as I am not able to view Network Connections.

Could someone please assist me in locating the Network Connections.

***FIXED*** I went into the GNOME Session and adjusted the folder.. System>"Places" showed up in GNOME but not in XFCE, so this is fixed.

---

### Post by userundefine on 2007-08-10
5.  Xubuntu is simple to install from Ubuntu.  You just type "xubuntu-desktop" into Synaptic and click install.  No prior steps necessary as the installer takes care of everything.

6.  Don't know what you're trying to accomplish here.  Do you want to set up encryption or partitions?  You have to set up SOME partitions in order to install another operating system.

---

### Post by Bart_D on 2007-08-10
Two final questions:

8.  Is network printing allowed in XUbuntu?  I have a printer on the network and want to use it for the PC with Xubuntu as a network printer(if possible).  By the way, the printer is not a suported one but I'm wondering if it would still be possible to use the printer as just a network printer.

9.  How do I get XFCE to manage my desktop every time I log in.....right now, it is for some reason set to NOT manage upon log in and I would like to default option to allow for this, rather than have to do it manually.

Bart

EDIT:  Regarding printing, it is a HP PSC 750 Printer and I managed to make some progress from Applications>System>Printing but when I add a new Printer, I am asked for a driver.  What do I do at this this stage?

---

### Post by bapoumba on 2007-08-11
> **Bart_D said:**
> 
9.  How do I get XFCE to manage my desktop every time I log in.....right now, it is for some reason set to NOT manage upon log in and I would like to default option to allow for this, rather than have to do it manually.
Settings > Desktop settings > Tick the box "Allow Xfce to manage the desktop".

Moved the thread to "Absolute Beginner Talk" support forum, BTW.

---

