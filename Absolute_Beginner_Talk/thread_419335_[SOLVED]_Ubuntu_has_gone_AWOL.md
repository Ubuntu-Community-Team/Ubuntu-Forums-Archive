---
title: "[SOLVED] Ubuntu has gone AWOL"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-04-22
I'm having a big problem. I cannot access Ubuntu anymore. After I enter my username and password, a popup window comes up:

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

[OK]

After I hit ok, nothing happens and the computer just hangs on an empty screen. How can I save my system?

PS: I tried some mojo with the terminal system restore, but I'm experiencing the same problem.

---

### Post by SonicSteve on 2007-04-22
The same message appears on server of mine. It logs in though and other than seeing the message I haven't noticed any ill effects. 
I'll be interested to see why this is happening.

---

### Post by the8thstar on 2007-04-22
You're luckier than I am. It won't let me go through at all.

---

### Post by lamalex on 2007-04-22
this usually occurs from graphical root stuff, like gksudo nautilus. it messes stuff up. [http://ubuntuforums.org/archive/index.php/t-91455.html](http://ubuntuforums.org/archive/index.php/t-91455.html) should help you out. btw AWOL means absent without leave.

---

### Post by the8thstar on 2007-04-22
Thanks for the link** Iamalex**, I'll check it out. I knew what AWOL meant, don't worry :)

---

### Post by lamalex on 2007-04-22
haha sorry if I sounded rude, people misusing awol is a pet peeve of mine :) hope that link helps you out

---

### Post by the8thstar on 2007-04-23
The link helped and confused me altogether.

I noticed a second popup telling me that the computer can't lock in ICEauthority blah,blah... in my user directory. I guess I'll burn the Feisty CD and zap the hell out of my partition... it's so frustrating. All these hours of work for nothing. :( 

Where's my old c:\config.sys? :mad:

---

### Post by igknighted on 2007-04-23
> **the8thstar said:**
> The link helped and confused me altogether.

I noticed a second popup telling me that the computer can't lock in ICEauthority blah,blah... in my user directory. I guess I'll burn the Feisty CD and zap the hell out of my partition... it's so frustrating. All these hours of work for nothing. :( 

Where's my old c:\config.sys? :mad:

No need to zap it, just look what it asked you to do... it said the folder needed 644 permissions for that one file (owner can read/write, others only read), so do a "chown username /home/username/.dmrc" and "chmod 644 /home/username/.dmrc".  Then "chown username /home/username".  Then reboot and see what it does.  Failing that, deleting the offending files should make the system rebuild them properly (although to the stock state) on boot.

This is quite like config.sys issues... except there is a whole directory of them for system files (/etc) and many many more in you home file (.dmrc being one of them).  If it was one file, it would way too long to be useful :)

---

### Post by the8thstar on 2007-04-24
Nevermind... I tried your idea but it failed.

I terminated the partition and reinstalled everything from scratch. NO MORE PROBLEMS... for now. Thanks for the help, **Igknighted**.

---

