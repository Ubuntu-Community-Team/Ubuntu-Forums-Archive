---
title: "Kranky Jack"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by johnstod on 2008-01-16
I installed Linux 7.10  3 days ago as a dual boot with XP  I have Linux on a second hard drive. The problem I have is that although I managed to copy my music, images and office files to be available as root , I can't access these when I log on as  other users. I have tried to change permissions on folders but that doesn't work for me. Help would be appreciated. I am just testing at this stage and although I can run command line in DOS, I haven't yet got around to it in Linux and I won't get involved with a whole lot of jargon unless Ubuntu can do basically what I want. This is to play and rip music, edit photos and videos and create documents.  I don't want to spend my time doing administration. Stopping MS from it's predilections was bad enough.

---

### Post by angelsguitar on 2008-01-16
In which folder do you have the docs you need to access?  Keep in mind that, normally, you can't access the docs on another user's home folder, unless they are on a public folder.  The best and safest way is to copy all your docs into your home folder and log in to your account (not as root).

Also, the root account is disabled by default in Ubuntu.  Did you enable it manually?  I'm asking because it catches my attention that you said you can access the docs as root.  Usually to do admin stuff we use the sudo command to avoid having to enable and/or login as root.

---

### Post by johnstod on 2008-01-16
Thanks  angelsguitar
I had all my data  about 100Gb  in different partitions on the original hard drive
I went to the nautilus file manager and clicked on Computer and saw my logical partitions from that drive above the dotted line. I originally tried to just drag and drop but couldn't do that so I created the same name folders that I had for partitions on  the Windows disk below the line. 
I then copied the files across to the new folders with Ctrl+ C and Ctrl+ V in blocks of 500 or so files.
I then removed the mount points and the files were then available to me without mounting and I had access as root.
However I am reluctant to make another copy of 100Gb as this would be a huge waste of space. I have 100Gb of data and a 400Gb drive available foe Linux, but using this just to make data availabe to another user on the same machine is not sensible in my case.

---

### Post by johnstod on 2008-01-16
PS   how do I make  these folders public?  Thanks for your interest.

---

### Post by angelsguitar on 2008-01-16
> **johnstod said:**
> PS   how do I make  these folders public?  Thanks for your interest.

To change the access rights, just right click on a folder and go to the permissions tab.  There are three sets of access rights: one for the owner, one for the group and one for everyone else.  You should set them according to your needs.  If you are looking to grant access to every user in your computer without letting them make changes or erase something, set them to "access files".

---

