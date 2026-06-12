---
title: "Dual boot w/ XP BSOD"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by DogsOfWar on 2007-07-19
Today I got a second HD for my dell desktop and tried to install the latest ubuntu on it as a dual boot with XP Home.  I formatted the new drive manually, with separate partitions for /boot and others.  I restarted the computer and the grub screen loaded, with options for ubuntu and XP.  Ubuntu worked fine, but when I tried XP it immediately crashed to a BSOD which said something about a 0x0000007b stop error (I think... that was many hours and BSODs ago :???:).  

Thinking that I could just fix the MBR and get ubuntu working again later, I tried the fixmbr and fixboot commands from the windows recovery center.  When those didn't work, I tried chkdsk which said there were errors on my HD, but it didn't accept /f so I couldn't fix them.  Then I fiddled with the bootcfg command, but nothing changed.

Now when I try to boot up, windows starts to load (the windows loading screen comes up and the blue bar runs for a while), then goes to a screen that looks like the normal chkdsk screen (blue, but not the BSOD) and says that autochk.exe was not found so it's skipping the Autocheck.  Then it crashes to the BSOD with a "STOP: c000021a" error and I have to shut it down.

As a last resort I tried to reinstall windows, but it wouldn't let me do that without reformatting my windows HD.  I'll do that if absolutely necessary, but first I'll need to find a way to boot back into my ubuntu instillation to save my files.  

Please tell me there's a way to fix this mess without drastic measures!

- D.O.W.

---

### Post by mikewhatever on 2007-07-19
Try the Super Grub Disk. It can boot both Ubuntu and Windows, restore Grub boot loader *** well as that of Windows.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by splintercellguy on 2007-07-19
MSDN has some suggestions for your STOP 0xc000021a error:

[http://support.microsoft.com/kb/156669](http://support.microsoft.com/kb/156669)

---

### Post by DogsOfWar on 2007-07-19
Thanks for the replies :)  I did some more research on the stop error, and it looks like I'll have to reformat and reinstall windows to fix it.  *sigh*  I'll use super grub disk to get at my ubuntu installation so I can back up my files.

- D.O.W.

---

