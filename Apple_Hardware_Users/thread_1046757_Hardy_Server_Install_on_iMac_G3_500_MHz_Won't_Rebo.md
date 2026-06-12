---
title: "Hardy Server Install on iMac G3 500 MHz Won't Reboot After Upgrade"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by jrolland on 2009-01-21
Hello, all!

I have been trying for several days now to get Hardy installed on an iMac G3 500 MHz from the Hardy PPC Server install CD.

At first, I was trying to install ubuntu-desktop, and it wouldn't reboot after restarting.

But just now, I postponed installing ubuntu-desktop, and just installed the server and issued a "sudo apt-get update" followed by a "sudo apt-get upgrade", per the server instructions on <http://ubuntuforums.org/showthread.php?t=405934>. I tried restarting, and had the same problem I always had: goes through shutdown, chokes on something related to "ALSA", says something about improper memory, then the computer just goes blank - doesn't turn off or restart, just goes blank, have to manually turn off and turn back on, yaboot works fine, goes through the white screen, gets back to the black screen and a message "Loading [something] ...", and then the computer just goes blank - doesn't turn off, just goes blank

It is definitely not an X problem, because I hadn't installed X. If I had to hazard a guess, I'd say it's a kernel upgrade issue (but I'm not that familiar with the boot process).

Has anyone else had this problem? Can anyone help? I've looked through the forums extensively, but most of the issues were X issues. One was a kernel issue [<http://ubuntuforums.org/archive/index.php/t-972575.html>, user "palmdalian"] but I can't just reinstall from backup my previous /boot folder, as that would defeat the purpose of the upgrade.

Thanks in advance for any assistance you can provide.

---

