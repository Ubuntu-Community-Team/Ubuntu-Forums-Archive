---
title: "Can't access my samba share from my osx terminalwindow"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2008-03-25
Hello.

I have problems with accessing my Ubuntu 7.10 samba share from
my terminalwindow in osx 10.4.9. I can access the share from Finder in
OSX, but not from terminalwindow.

Iv made a shell script that uses rsync to backup data from my mac to my
ubuntu 7.10 server.

When I map the share from finder on osx it appers ok in finder.
But when I enter terminal window on my osx I cant access the share.
It is shown as :

/Volumes/WORKGROUP;T10

Does anybody have tips what im doing wrong ?
(My Ubuntu 7.10 server is running dns, http, samba, ssh og mail server)

---

### Post by chrisdee on 2008-03-25
Would really apreciate some tips.

---

### Post by Squish on 2008-03-25
This isnt really advice, but just reassurement that sharing is indeed possible. My computer running ubuntuu had a ton of extra harddrive space that my video editor friend needed to utilize. Although it took quite awhile of learning how to open ports, and create permissions (His useless trialware mac software didnt help much) we did end up getting it to work.

Although I dont have any tips, I would like to see what people say, because I am interested in this as well.

---

### Post by chrisdee on 2008-03-25
When I run a smbtree on my Ubuntu 7.10 server i get the following
output :

WORKGROUP
        \\T10                           Samba 3.0.26a
                \\T10\PDF               PDF
                \\T10\IPC$              IPC Service (Samba 3.0.26a)
                \\T10\www               Web Files
                \\T10\backup            Backup Files
                \\T10\print$            Printer Drivers


Should I mount one of the above shares manually from osx terminal
window ? How do I do this ?

Before I upgraded to Ubuntu 7.10, when I mounted the share from
Finder on OSX it came up under the /Volumes/ drive on my OSX.
It still does, but now as WORKGROUP;T10, with I cant access.
If i try to write : cd /Volumes/WORKGROUP;T10 I get a message that this is no folder/directory.

---

### Post by chrisdee on 2008-03-25
Maby if someone could tell me how to map share
from osx terminal window I could try that ?

---

### Post by chrisdee on 2008-03-25
Again, would greatly apreciate some tips on this:)

---

### Post by chrisdee on 2008-03-25
Anybody ?

---

### Post by Squish on 2008-03-25
*Bump*

---

### Post by surfer63 on 2008-06-12
from the terminal create a directory with sudo:
sudo mkdir /Volumes/NewShare

Then issue the command:
sudo mount_smbfs -W myworkgroup //username@netbiosname/share /Volumes/NewShare


Then your share is mounted and will also "pop up" in Finder.

---

