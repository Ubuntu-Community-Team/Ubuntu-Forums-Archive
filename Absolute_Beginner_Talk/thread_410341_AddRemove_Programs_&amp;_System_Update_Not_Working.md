---
title: "Add/Remove Programs &amp; System Update Not Working"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by rudelerius on 2007-04-15
I am very new to Linux.  The command line/terminal is a mystery to me. I am absolutely overwhelmed by the amount of information required to use this system.  Add/Remove on the Applications menu and System Updates just stopped working.  Also, the Networking application under System->Administration no longer works (I get the "hourglass", then nothing). I really need help.  Please have pity on me.

---

### Post by Happy_Man on 2007-04-15
Any by "just stopped working" you mean "won't start?"

---

### Post by zvacet on 2007-04-15
What version do you use and how did you set up network.More information you give to us better help we can give to you.

---

### Post by lamalex on 2007-04-15
open a terminal, and try typing
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install-package-that-you-want

```
and see if it gives any information.

---

### Post by rudelerius on 2007-04-15
sudo keeps saying "sudoers file: syntax error, line *n*" and then returns "sudo: parse error in etc/sudoers near line 0." With Add/Remove..., when I check an item and click Apply, the system checks for "installed and available applications", then all action terminates and the application is either not added or not removed from the system.  The same thing with the system updates, it runs through the same checks, then terminates.  The system update icon still shows in the task bar and the same 6 items show up in the list of available updates each time.  I don't know what version I am using, other than Edgy 6.10.  I downloaded the desktop edition and installed from the live CD.  I have added and removed applications in the past.  The last that I remember was VMPlayer.

---

### Post by rudelerius on 2007-04-16
The problem seemed to start after I installed SMB4K and tried to configure SAMBA using the GUI.

---

### Post by kvonb on 2007-04-16
Eeek!  Sounds like your /etc/sudoers file is corrupted!

That is NOT nice, it means that you will not be able to administer the system, which is probably why it won't let you add or remove anything.

A quick search of the forums revealed that it was the SMB4K that damaged it!

Have a read of this thread here:

[http://ubuntuforums.org/showthread.php?t=293454&highlight=sudoers+corrupted](http://ubuntuforums.org/showthread.php?t=293454&highlight=sudoers+corrupted)

it seems that you will have to boot in "safe mode" and edit the /etc/sudoers file to remove the smb4k stuff.  That thread has all the instructions.

Good luck, Kev :)

---

### Post by rudelerius on 2007-05-02
Thank you kvonb.  Your post was most helpful.  I was at work and did not have a link to this post, and I recalled that you sent me to a thread called "i hosed my sudoers file" so I did a search, and while looking through the results, I found a post from aysiu that referenced an external website that had a hepful guide to correcting problems with sudoers.  I think it could help anyone else with the same problem and little knowledge of Linux/Ubuntu: [http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

---

