---
title: "New monitor, no picture! samsung syncmaster 226bw"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by absalom on 2007-12-29
I have the following problem

- I bought a syncmaster 226bw, hooked up the cables and started ubuntu 7.10 (that had worked just fine with my old monitor).
- It started up this time as well, but on the wrong resolution. Ubuntu did not detect the monitor type, but assigned it as plug & play monitor. So i opened the wizard and specified it was a syncmaster 226bw, and that i wished it would use 1680x1050. I then hit reboot.
- When ubuntu starts there is no picture once i hit the login screen, but i can hear the drumroll. And restarting x gives me the same drumroll again ( of course) so it is just not showing anything else than a black screen to me.

Help is very much needed!






//Abe

---

### Post by taurus on 2007-12-29
Boot into recovery mode from GRUB menu and reconfigure your X server for the new monitor.

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, you can reboot with

```
shutdown -r now
```

---

### Post by Jerry N on 2007-12-29
Try selecting 'Recovery Mode' when the computer boots.  This should get you a display so you can start trying to fix the problem.  Neither Ubuntu nor LinuxMint recognize my Samsung SyncMaster 940t.  I am using the DVI interface - I don't know if it would be recognized if I were using the analog interface.  Do you have the appropriate drivers for your video card?

Jerry

---

### Post by absalom on 2008-01-03
Thanks guys! i resolved it partly with these tips. I had already tried the dpkg-reconfigure thing in recovery mode without success just after posting (when i googled it up on the web), but i had set the driver to "ati" when prompted, instead of flgrx or something like that, that i found to have been the one used previously in the xorg.conf file.

Now the screen identifies as plug&play screen, but works nicely. Odd that the gui-thing really didn't do it's job on my monitor models part.

---

