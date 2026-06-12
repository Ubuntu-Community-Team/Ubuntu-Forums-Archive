---
title: "update manager hangs"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by mcspl on 2008-01-21
hi,

i have installed the following files from the Brothers Solution website and it resides in the File System. [COLOR="DarkSlateBlue"] /cupswrapperMFC4800-1.0.2-1.i386.rpm[/COLOR]

somehow this file will cause the update manager/synaptic manager/add&remove to hang. message as follows
.[COLOR="DarkSlateBlue"] E: The package mfc4800lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/COLOR]

so i reported in the launch-pad.  i've tried the forum on the same topic and get the same error message.

can anybody help? thank you in advance.

---

### Post by stump138 on 2008-01-21
do a search in synaptic for that package and lock the version if you can.  That should stop your update manager from looking to update it.  Since it is an .rpm did you install it with alien?  If so, you might want to rebuild the package with the -c option enabled.

---

### Post by mcspl on 2008-01-22
hi, thank you for your response. my synpatic manager cannot be activated as the error window will appear and when clicked acknowledged, the synaptic manager closes automatically. likewise for update manager.

i was thinking, can i just delete the file? unfortunately it resides in the File Systems directory and it says i do not have the permission.  any advise?

---

### Post by mikeyphi on 2008-01-22
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Look at the above guide for installing RPM packages - see item 3

You will need to open a terminal and use text commands - navigate to wherever the cupswrapperMFC4800-1.0.2-1.i386.rpm file is located - instead of the desktop as in the guide.

If you can't do that you can try to delete but you will still have to do that via a terminal and text commands!

If your (normal) system refuses to cooperate - reboot into the recovery mode - that sets you up as root by default and should give you access to the command line.
Good luck!!

---

### Post by mcspl on 2008-01-23
hi, thank you for your advise. i've visited your site. very informative indeed.

i've managed to delete the problematic file, but unfortunately it seems that the error persist. 

i'll see what i can pick up from the forumers and resolve.  other than not being able to install new packages & performing updates, my system is working fine. so am still able to bear w it.

rgds

---

### Post by mikeyphi on 2008-01-24
Open a terminal and enter:
sudo dpkg --configure -a

post any further error messages!

---

### Post by mcspl on 2008-01-30
hi,

i key in as per your message.  there are no further error messages.

however, i noticed that the update managers icon changes from orange to grey and now goes back to orange again.

understand the orange icon means there are updates available. when i clicked on it, the error message as earlier posted remains.

so looks like the error is still there, i can;t do any updates or installation of applications. :confused:

rgds

---

### Post by oedha on 2008-01-30
have you check /etc/apt/source.list

~E~

---

### Post by oedha on 2008-01-30
uppss...sorry......
it supposed to be /etc/apt/sources.list

~E~

---

### Post by mcspl on 2008-02-02
hi,

[permission denied] is what i get. 

[COLOR="DarkSlateBlue"]mcspl@mcspl-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
mcspl@mcspl-desktop:~$ 
[/COLOR]

:confused:

---

