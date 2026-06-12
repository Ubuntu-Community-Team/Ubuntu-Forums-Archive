---
title: "k3b installs but does not run"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Jonam on 2007-01-31
Hello,

I am new to Ubuntu (Dapper) and relatively new to Linux. I need to produce a video and burn to VCD. I have Kino installed and running satisfactorily.

I used the Synaptic package manager to download the k3b application and it successfully installed all files. Unfortunately, after installation, I could not get k3b to run. I tried the following:

- using the k3b icon in the Applications/ Sound and Video/ menu did nothing
- typing k3b in a terminal window did nothing
- typing

```
gksudo k3b
```

did nothing.

Finally, typing

```
gksudo k3bsetup
```

produced:

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kcmshell (kdelibs): WARNING: Could not find module 'k3bsetup2'.

```

I could not find a k3bsetup2 file.

I have searched Google and these forums for a solution and what I found made no difference. I tried two solutions:

1. Linking device cdrom to sg0 as:

```
sudo ln -s cdrom sg0
```

2. Creating a root account and login and then running k3b as root.
 
This produced the same message as the gksudo k3bsetup command earlier.

I am at a complete loss as to what to do next. I would appreciate some guidance on what I need to do to install k3b and get it working.

Regards,

Jonam.

---

### Post by taurus on 2007-01-31
Maybe you just remove it and install it over again.

```
sudo aptitude --purge remove k3b
sudo aptitude update
sudo aptitude install k3b
k3b
```

---

### Post by Jonam on 2007-01-31
> Maybe you just remove it and install it over again.

Tried this and got the same results. No k3b startup.

Jonam

---

### Post by Jonam on 2007-02-01
I finally got k3b working as follows:

1. Found the man page for k3b on the web for command-line options and then opened a terminal window. Typed the following command:

```
k3b --copycd
```

many error messages later, k3b starts and asks me to set CD burner writing speed. After doing so, a CD copying window opens.

2. I burn a test CD and it works OK. I close k3b and it does not terminate cleanly. Terminal window hangs with the following error messages:

```
ICE default IO error handler doing an exit(), pid = 11328, errno = 0
ICE default IO error handler doing an exit(), pid = 11339, errno = 0

```

I have no idea what this means so I CTRL-C to terminate k3b.

3. I now click the Icon for k3B under Applications/Sound and Video and it starts OK.

Will try it out over the next day or so and post if any other errors found.

Regards,

Jonam

---

### Post by Jonam on 2007-02-02
Back to square one. k3b does not start.

After a re-boot, I clicked on the k3b icon and got nothing. Checking the system monitor, I found that the following processes were running:

k3b listed as Uninterruptible
kded Sleeping
kdeinit Sleeping
kdelauncher Sleeping

There is no k3b window and all other menu items work fine. Unsure as to what is going on. I will do some searching on the web to try and find and answer to this problem.

Jonam

---

### Post by Jonam on 2007-03-01
An update. I installed KDE to see if k3b would work under this environment. No luck.

However, I found that if I went back to Gnome and launched Konqueror, then using its applications menu, launched k3b, it would work fine. I now have to repeat this test under KDE. Seems that Konqueror must set up something that k3b needs to run which does not happen using the normal launch process.

Jonam

---

### Post by Jonam on 2007-04-15
Update - issue resolved. Searching the web linked Uniterruptible state of k3b with hardware fault on one of the drives. When I upgraded the machine to DVD-RW drive, I tested the system by disconnecting the remaining CDR drive and found k3b working properly. Replacing the CDR drive with the old CDRW also worked (though only with a 40-way cable). 

This also seems to indicate an issue placing CD and DVD drives on the same IDE bus as they tend to want to run in different UDMA modes. Currently system is working with 40 way cable, DVDRW drive on UDMA 2 and CDRW has UDMA disabled.

Jonam

---

### Post by dwblas on 2007-04-15
You might want to post this in a bug report, either to KDE/k3b or KUbuntu.

---

### Post by Jonam on 2007-04-15
> **dwblas said:**
> You might want to post this in a bug report, either to KDE/k3b or KUbuntu.

Yes, thanks for the suggestion. I will do that shortly. Interestingly, the little information I could find on Uniterruptible state said that it occurs when some software sends commands to hardware (say k3b requesting something from the CDR drive) and the hardware does not respond. The software then ends up waiting forever doing nothing (in Uniterruptible state) rather than resume with an error message.

Jonam

---

### Post by Jonam on 2007-04-20
Update - submitted bug report to k3b developers and bug was found in k3b related to how the CD/ DVD drives were being accessed. This has now been fixed.

Jonam

---

