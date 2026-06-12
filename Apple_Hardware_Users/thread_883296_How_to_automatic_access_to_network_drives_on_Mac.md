---
title: "How to: automatic access to network drives on Mac"
date: 2008-08-07
forum: Apple Hardware Users
---

### Post by xp2mac on 2008-08-07
I am running Ubuntu in VMWare on an Intel Mac OSX 10.5.4.

I believe that the folders on the Mac, from the perspective of Ubuntu, are called Windows shares.

Each time I run Ubuntu, in order to access a Windows share I have to go to Places, then Network, then click on my Mac, then double-click on one of the folders that I want to access.

Wouldn't it be nice to have those folders automatically show up in a File Browser?

The other part of this problem is that those Mac folders do not show up when I want to open a file in one of those folders from an application, specifically, gnucash. I have to copy that file using a File Browser from the Mac folder to some place in the Ubuntu file system that I can access with gnucash.

Now I know about adding objects to a panel, such as to connect to a network. Adding a Network launcher still means I have to go through the process of entering the Share information.

The Help document talks about Applets, but I'm sorry, I haven't ever learned about Applets and I don't know how to create an Applet in Ubuntu. I think having an Applet that executed when I log into Ubuntu would be really great.

I fancy myself to be a decent C/Unix programmer and I know Perl and Bash quite well. That should be a start.

Any help here? Thanks.

---

### Post by Sammi on 2008-08-07
Did some friendly searching for you and found these treads that I think solve the same issue you have:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
[http://ubuntuforums.org/showthread.php?t=146456](http://ubuntuforums.org/showthread.php?t=146456)
[http://ubuntuforums.org/showthread.php?t=282008](http://ubuntuforums.org/showthread.php?t=282008)

On a general note:
Linux uses an open source framework named samba to connect to windows shares (believe OS X does the same), and you need to make samba mount the shared folders by putting some lines of config in the fstab file, which is used to configure how and what filesystems are mounted on boot.

---

### Post by cyberdork33 on 2008-08-08
additionally, your Mac is capable of sharing folders in various formats, Samba only being one of them. You can also checkout appletalk/netatalk and NFS shares.

My personal favorite for automounting Samba shares is the first one in the list.

---

### Post by Sonicreindeer on 2008-08-09
I have a WD My Book Premium 320 GB external dual-port USB/ Firewire 400 drive. I was able to transfer files using Xubuntu 7.04 on my G4/ 400 Mhz box with 1GB RAM w/out a hitch until I discovered a 501 dialout in my Properties box. What are the list of terminal commands to elevate my sudo permissions and execute the removal of the " 501 dialout "  error message which prevents the transfer of my files from any drive, including USB thumb drives, into the external device? Still have 175 GB of unused storage I'd love to access.:(

   Thank you, in advance, for helping me out.

---

### Post by cyberdork33 on 2008-08-10
> **Sonicreindeer said:**
> I have a WD My Book Premium 320 GB external dual-port USB/ Firewire 400 drive. I was able to transfer files using Xubuntu 7.04 on my G4/ 400 Mhz box with 1GB RAM w/out a hitch until I discovered a 501 dialout in my Properties box. What are the list of terminal commands to elevate my sudo permissions and execute the removal of the " 501 dialout "  error message which prevents the transfer of my files from any drive, including USB thumb drives, into the external device? Still have 175 GB of unused storage I'd love to access.:(

   Thank you, in advance, for helping me out.

Please start a new thread as this is completely unrelated to this one...

Also it is unlikely that this problem is Mac specific, so try the more general forums.

That said, you might need to give a little more information about the problem. I am not even sure what a "501 dialout" is...

---

