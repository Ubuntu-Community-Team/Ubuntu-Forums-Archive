---
title: "Problem with kdevelop installation"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by LinuxVictim on 2007-05-09
Hi,
I installed "kdevelop" via Synaptic.
So far it went fine,

1. But it didn't create a link in the application menu. (not a real problem)

2. When I try to start it from the console with "kdevelop" it complains about insufficient
    permissions. But within my home directory!

When I try this as root, it works.

Do I have to develop as root??

Thanx for any advice.

Greetz,
Andreas T.

---

### Post by mejy on 2007-05-09
Can you post the exact error message?  It may be that some other app restricted permissions somewhere in your home directory.

---

### Post by LinuxVictim on 2007-05-10
the .kde folder has root as its owner, and only he has rights on it.
I don't know if the .kde folder was previously created by any other app which
required this to be owned by root.
(would still be strange to place it in my home directory)

How do I change the rights?
chmod, tells me no permission.
ok
then I do sudo chmod u+rwx .kde but this only changes the rights for the current user,
unfortunately that's root again.
I dont want to give everyone permissions.


This is the complete output:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/socket-r116168: Permission denied
trying to create local folder /home/andy/.kde/socket-r116168: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/andy/.kde/socket-r116168/kdeinit__0'
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/socket-r116168: Permission denied
trying to create local folder /home/andy/.kde/socket-r116168: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/andy/.kde/socket-r116168/kdeinit__0'
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/cache-r116168: Permission denied
trying to create local folder /home/andy/.kde/cache-r116168: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/socket-r116168: Permission denied
trying to create local folder /home/andy/.kde/socket-r116168: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/andy/.kde/socket-r116168/kdeinit__0'
trying to create local folder /home/andy/.kde/cache-r116168: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDevelop/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDevelop/Plugin not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KDevelop/Plugin not found
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied
trying to create local folder /home/andy/.kde/share: Permission denied

---

### Post by LinuxVictim on 2007-05-10
Ah, chown did the thing.

sudo chown -R myusername .kde

gave me the ownership, and

sudo chmod -R u+rwx .kde

ensured full permissions.

After killing everything that was left from my previous tries to start kdevelop,
(like the klauncher process for instance)
it now started up with barely a warning.

But those strange messages about a "bad device" are strange.
Does anyone know what those mean?
(they're the same as in the post above!)

Greetings,
LinuxFriend ;-)

---

