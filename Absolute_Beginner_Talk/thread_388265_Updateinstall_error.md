---
title: "Update/install error"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-03-19
Not sure what to do with this output
> Setting up clamav-base (0.88.4-1ubuntu2.1) ...
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base


---

### Post by eljalill on 2007-03-19
Which command were you running: what triggered this error message?

---

### Post by Icemanyurt on 2007-03-19
Pretty much any sort of install script (Easy Ubuntu, Automatix...) will trigger it
> Unable to determine desktop environment, falling back to gksudo
/usr/lib/easyubuntu
When you get a 'Password: ' prompt, type in your user password.
System sanity check: Failed!
Errors: 
--------
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors: 
--------
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base

EasyUbuntu will not run before these errors are fixed. Please fix them and try again


Easy Ubuntu's full output

The one I posted first was from 'dpkg --configure -a'

---

### Post by eljalill on 2007-03-19
This thread 
[http://ubuntuforums.org/showthread.php?p=2109957](http://ubuntuforums.org/showthread.php?p=2109957)
is about the same error code..
Maybe it helps?
Else people have been suggesting, that this error comes up, when the file system was not cleanly mounted/unmounted. then fsck might help.

Let know how it goes!

---

### Post by Icemanyurt on 2007-03-19
I tried running fsck,but the warning kinda scared me off....

---

### Post by eljalill on 2007-03-19
What warning did fsck give?

---

### Post by Icemanyurt on 2007-03-19
It said something about running fsck on a mounted file system can cause major errors...

---

