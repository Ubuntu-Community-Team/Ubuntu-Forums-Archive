---
title: "how to network a pc &amp; ubuntu for A to Z"
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by TanKilleR on 2005-06-30
I dont know how. Lets pretend I am the most dumb pc noob their is. Please tell me how to network my pc and ubuntu in every step so that I can transfter files from my pc to my ubuntu, thanks.

---

### Post by Jussi Kukkonen on 2005-06-30
You should give us a little more information. Like: 
What operating system is the pc running?
Are the machines in the same network or both connected to the internet separately? 

The answer is quite probably Samba -- you can either 
[list]
[*]Share a folder in your windows machine and connect from Ubuntu (either mount the share so it looks like just another disk or use Nautilus with the syntax "smb://win_machine_name/share" if I recall correctly)
[*]Use sambaserver to share a directory from Ubuntu and "Map a network drive" (as they say in Win-land) on the other machine.
[/list]

But don't just rush into it. Describe your setup here, and someone will help you decide the right way to do it.

---

### Post by TanKilleR on 2005-06-30
PC: Windows XP SP1
Linux:Ubuntu Lastest Release

Home pc networked, so both are online, but not shairing files. Both run though a router.

---

### Post by Jussi Kukkonen on 2005-06-30
I'd probably share a directory on the winXP machine like this (I don't have a windows machine handy, so this is from memory):
Right-click on directory, select properties. 
Choose sharing-tab, set the directory as shared give the share a name.

Then make sure the share is accessible: you might need to fiddle with your software firewall, if you use one. Someone with more experience with winXP could maybe help here?

Your Ubuntu box should already have the necessary tools to connect to a smb-share. Like I mentioned there are multiple ways to do this. If your network setup is 'stable' (both machines are mostly online), you'll want to mount the share:

First, create the mount point:
```
sudo mkdir /media/winshare
```
Then mount:
```
sudo mount -t cifs -o username=*win-user-name* //*win-ip-address*/*win-share-name* /media/winshare/
```
(if you're still "sudoing"  you'll only be asked for the windows password, otherwise you'll first need to give ubuntu password (for sudo) and then windows password)
You should always umount the share before disconnecting or shutting down the winXP machine. For automatic mounting on boot you'll need to edit /etc/fstab.

For additional security you could create a specific low privilege user on the windows machine for this -- remember that you are sending the password over the network.

---

