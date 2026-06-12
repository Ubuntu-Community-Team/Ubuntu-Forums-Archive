---
title: "[SOLVED] Lightscribe in Ubuntu 64 not detecting hardware"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2007-08-04
Alright, First I'm running Ubuntu 64bit. I got Lightscribe installed. The way I did that, I downloaded some .deb files I found on this forum that are converted using alien of the rpm files for Lightscribe. I forced the .deb install. 4L-gui works but it does not detect my writer what so ever. I know my drive works because I've burned discs on it in Ubuntu. Any ideas?

---

### Post by apswartz on 2007-08-05
Do you have ia32-libs installed? If not...
```
sudo aptitude install ia32-libs
```
reboot
try again

---

### Post by apswartz on 2007-08-05
If that doesn't work, here is someone who seems to be willing and able to help with 64bit system problems  involving the Lightscribe.

---

### Post by AegisTalons on 2007-08-06
so i have ia32-libs installed. Any other ideas?

<<Edit>>
So after I couldn't get Lightscribe in Ubuntu working, I went into XP and got it working there, and burned the dvd and the label there.

I just went into the software and now it recognizes my drive. I don't know what it is. I believe it might have been due to the reboot, but I tried that.

Either way, it works. Horrary.

---

### Post by apswartz on 2007-08-06
hmmmm...
maybe this guy can help.
[http://k3b.plainblack.com/message-board/lightscribe-testing](http://k3b.plainblack.com/message-board/lightscribe-testing)

---

### Post by apswartz on 2007-08-06
> **AegisTalons said:**
> Either way, it works. Horrary.

Fantastic!

---

### Post by spaztick1 on 2007-08-12
I am having this same problem but rebooting did not help.  I can burn cds with K3b but the Lightscribe software doesn't recognize my drive.  Has anybody else soved this problem?

---

### Post by AegisTalons on 2007-08-12
Do you also have Windows install? In Windows, do you have Lightscribe working? Try to get Lightscribe working in Windows and then see if it helps in Linux. I know it's suppose to be independant but that was one thing that I did and it works now. Go figure.

---

### Post by spaztick1 on 2007-08-13
Thank you for responding.  I just realized that it does work.  The reason I thought it didn't was because when I run the gui from the console I get a

X Error: BadDevice, invalid or uninitialized input device 167
  Extension:    144 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device


But when I try to print it works fine  

Thank you

---

### Post by AegisTalons on 2007-08-14
Glad to hear it works. If you want to get Lightscribe working from menu, I wrote a little howto including a script to get it working. Lightscribe needs root access to print so this script will let you run it from menu and also asks you for your password.

[HOWTO: Lightscribe work from Menu (SCRIPT)]("http://ubuntuforums.org/showthread.php?t=520317")

Let me know how the howto works for you.

---

### Post by GoCool on 2008-02-29
I am a newbie..even I have the same issue, I am using UBUNTU Gutsy Gibbon. I installed both the packages as mentioned in Lacie website and couldnt make it to work. Then I came across this thread and tried to give the command as suggested by you...but its giving me the below error

Couldn't find any package whose name or description matched "ia32-libs"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Am I doing anything wrong?

> **apswartz said:**
> Do you have ia32-libs installed? If not...
```
sudo aptitude install ia32-libs
```
reboot
try again

---

