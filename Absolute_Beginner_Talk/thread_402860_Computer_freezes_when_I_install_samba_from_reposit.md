---
title: "Computer freezes when I install samba from repositories"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by rjfioravanti on 2007-04-06
Hi everyone

I am working with a fresh install of ubuntu edgy 6.10

What I did so far
- install from cd
- do all upgrade and dist-upgrade
- restart
- install samba
- freeze!

This is the second time I have tried installing samba on this computer and it has frozen up. I have reinstalled because I thought it was another problem at first, but now I know it is something to do with samba because I have done nothing else except for updates

I can still boot up in recovery mode.. and my syslog has the two following lines leading up to the crash

ISO 9660 Extensions: Microsoft Joliet Level 3
ISOFS: changing to secondary root

Can anybody help me??

---

### Post by wpshooter on 2007-04-06
How are you installing SAMBA ?  Are you doing this thru System/Admin./Folder Sharing ?

Before you attempt to install SAMBA and before you attempt to update the initial O/S installation, are you making sure ALL of the repositories are marked ?

Here's what I do.  Initial O/S installation.  Wait for updates to become available in panel.  Install those updates.  Reboot whether it prompts me or not.  Then make sure ALL repositories are marked.  The go to update manager and poll for any further updates.  Install them if any found.  Reboot if prompted.  Then install SAMBA thru System/Admin menu.

Good luck.

---

### Post by mikeyphi on 2007-04-06
Please say exactly how you tried to install samba

---

### Post by rjfioravanti on 2007-04-06
sudo apt-get install samba

as soon as the download and install finished it was frozen

---

### Post by wpshooter on 2007-04-06
Like I said before, I would NOT do it that way.  I would install using the program as listed on the system/admin menu.

---

### Post by rjfioravanti on 2007-04-06
> **wpshooter said:**
> How are you installing SAMBA ?  Are you doing this thru System/Admin./Folder Sharing ?

Before you attempt to install SAMBA and before you attempt to update the initial O/S installation, are you making sure ALL of the repositories are marked ?

Here's what I do.  Initial O/S installation.  Wait for updates to become available in panel.  Install those updates.  Reboot whether it prompts me or not.  Then make sure ALL repositories are marked.  The go to update manager and poll for any further updates.  Install them if any found.  Reboot if prompted.  Then install SAMBA thru System/Admin menu.

Good luck.

Please read my post again. I did update my entire OS, and I did restart. I did not mention this, but I uncommented all repositories in sources.list before doing my update. 

I will try removing samba with apt-get remove, and then looking for some way to install through system admin, but i dont see why that should start a difference

It freezes after saying..

..starting samba daemons

---

### Post by mikeyphi on 2007-04-06
It's probably a question of 'dependencies' - if you use the GUI 'Synaptic' it will make sure that all the packages you need are installed - not just the one you ask for!

---

### Post by rjfioravanti on 2007-04-06
using apt-get install resolves dependencies

---

### Post by wpshooter on 2007-04-06
When the developers of the O/S give you a nice GUI tool to use, why would you not want to use it ???

---

### Post by rjfioravanti on 2007-04-06
> **wpshooter said:**
> When the developers of the O/S give you a nice GUI tool to use, why would you not want to use it ???


Why not use a perfectly good terminal

Using GUI's exposes me to another layer of possible bugs

---

### Post by rjfioravanti on 2007-04-06
So I didn't resolve that problem but turns out I don't need the samba package installed for what I want to do. I just wanted to be able to access a printer that is on the network attached to a windows computer. I thought I had to install samba to do that, but I removed it (allowing me to run my computer again not in recovery mode) and then I went to system - admin - printers and added a windows smb network printer. Then I could print fine with whatever samba client is already on my computer

Does installing the samba package put a samba server on your computer allowing windows computers to connect to the linux computer?

---

### Post by wpshooter on 2007-04-06
> **rjfioravanti said:**
> Why not use a perfectly good terminal

Using GUI's exposes me to another layer of possible bugs

Since your terminal method does not seem to be getting the job done (and if I were a betting man, I would almost be willing to bet you that the GUI method will work properly, as mentioned by an earlier poster), it would seem to me that the bug lays in the terminal method !!!

---

### Post by rjfioravanti on 2007-04-06
clearly, the terminal is always the most stable thing in any distribution

every gui tool just fires commands to the OS the same way I can with the terminal

---

### Post by wpshooter on 2007-04-06
> **rjfioravanti said:**
> clearly, the terminal is always the most stable thing in any distribution

every gui tool just fires commands to the OS the same way I can with the terminal

Yes, but the GUI was written by the developers who know EXACTLY what commands are necessary to PROPERLY accomplish the task.

---

### Post by rjfioravanti on 2007-04-06
Well ok, you didn't even tell me what to do, you just said go to System -> Administration

What was I supposed to do in there, they didn't program it to know what I was thinking as soon as I select the administration drop-down menu

---

### Post by wpshooter on 2007-04-06
I believe I said system/admin/folder sharing.  If you pick folder sharing, it gives you the option of installing either SAMBA or NFS or both.

---

### Post by rjfioravanti on 2007-04-08
The problem was my wireless card.

It was very deceptive because it seemed to be supported out of the box since I got internet right away.

Using Netgear wg111v2 wireless usb card. 

I noticed one time on boot that it was using an experimental driver, and success/ failures should be reported to whoever. So after getting the windows driver and compiling ndiswrapper, no more freezing

---

