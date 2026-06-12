---
title: "Grub doesn't list o/s boot options"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by WaddlzInMN on 2008-02-09
I have (finally) successfully installed 7.04 on old IBM ThinkPad 390x. I have booted Ubuntu and looked around and did some work to try and get my Linksys wireless adapter card to work. I have been unsuccessful so far. But, I digress. 

Since I couldn't get to the internet in Ubuntu, I shut-down, booted up Win98 (I told you it was an old machine). The GRUB listed Ubuntu and Win98 as boot options just fine. I finished up in Windows and shut-down. 

Now when I start the laptop, I get "GRUB Loading stage1.5" and nothing, it just hangs.

How do I get the boot options back?

---

### Post by buntu_Geek on 2008-02-09
GRUB will display some error numbers....

Try rebooting.... (Ctrl+Alt+Del)

Else...

Try installing the Grub boot loader by booting using any ubuntu live CD....

---

### Post by WaddlzInMN on 2008-02-09
I've tried rebooting (multiple times). I can't use a live CD because of low memory on this system. I had to install using an alternate cd.

I rebooted from alternate cd, and looked through the options. I tried the "recover" option which goes through a lot of install questions, and then asked if I want to reboot, which I tried. But it brought me back to the same "GRUB Loading stage1.5". There is no error number listed, just a blinking cursor.

---

### Post by buntu_Geek on 2008-02-09
I Havnt heard such a problem.... Generally Grub leaves an error message ... (if any).... which might be used to troubleshoot the problem...

But reinstalling grub might surely solve the problem....

Check these out,,,
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

HOWTO for reinstalling GRUB:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Pelham123 on 2008-02-09
Try SuperGrub Disk, the download is only a few MBs so i'm sure it'll run on your great-grandma's PC ;)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Good luck

---

### Post by WaddlzInMN on 2008-02-09
Thanks for the links. I looked them and found out how to rescue GRUB from the alternate CD. Unfortunately, I was unable to follow all directions. What happened on my system is not what the directions said would happen. I tried to make some good guesses, but to no avail. I'm guessing I will re-install. What a bummer. It takes this system hours.

---

### Post by buntu_Geek on 2008-02-10
You could tell where you found the difference from the directions....
We might help...

---

