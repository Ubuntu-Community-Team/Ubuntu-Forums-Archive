---
title: "Installing Thunderbird"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by wsun on 2006-08-27
Hi, I just downloaded the archive from the website, how do I install it? Thanks

---

### Post by kernelpanicked on 2006-08-27
Why not just use the thunderbird already packaged by Ubuntu?

```

sudo aptitude install mozilla-thunderbird

```

---

### Post by wsun on 2006-08-27
Thanks but I just want to know in general how to install stuff that are .bin files from the terminal. :D\

here is the error I got btw,

sudo aptitude install mozilla-thunderbird
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  mozilla-thunderbird
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.3MB of archives. After unpacking 29.3MB will be used.
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main mozilla-thunderbird 1.5.0.5-0ubuntu0.6.06 [10.3MB]
Fetched 10.3MB in 42s (241kB/s)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 1 during global destruction.
Preconfiguring packages ...
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 5.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 126337 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.5.0.5-0ubuntu0.6.06_i386.deb) ...
Setting up mozilla-thunderbird (1.5.0.5-0ubuntu0.6.06) ...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 5.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 1.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 1.

---

### Post by kernelpanicked on 2006-08-27
No worries. Been a while since I pulled it directly from mozilla but it should be something like this.

```


tar xzvf thunderbird-1.5.0.5.tar.gz

cd thunderbird

./mozilla-installer-bin


```

---

### Post by k94382 on 2006-08-27
are you sure? After typing ./mozilla-installer-bin, nothing happens even though it exists.

---

### Post by Bachstelze on 2006-08-27
[Here](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Thunderbird_1.5)'s a script that will do it all for you :)

---

