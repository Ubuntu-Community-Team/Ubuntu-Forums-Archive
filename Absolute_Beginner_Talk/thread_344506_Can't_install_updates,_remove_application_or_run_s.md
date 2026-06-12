---
title: "Can't install updates, remove application or run sudo"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by fnacer on 2007-01-23
Hi,

I installed Ubuntu over the weekend and proceeded to add VMWare using instructions found in a recent Digg article. Everything worked fine for a couple of days. Today, I tried to install software updates but clicking "Install Updates" only gets me a "Checking for Updates" dialog before I'm returned to the update list.  I tried to install a new application and remove an already installed one but the same thing happens. I select or unselect the app, click whatever button I'm supposed to click and a couple of seconds later I'm back to the same dialog with the application intact.

I perused the forums and tried some of the suggestions that involved using sudo. But sudo following by anything returns the following:

>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
...
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 8

I tried looking at sudoers but the admin account I'm logging in with doesn't seem to have the appropriate privileges.

Can anyone help me understand what is going on? Please be gentle with your explanation. I've spent way too much time in the Windows world. Thanks.

Farid

---

### Post by tonyr1988 on 2007-01-23
You may wanna try the suggestion in this thread:

[http://www.ubuntuforums.org/showthread.php?p=1985060](http://www.ubuntuforums.org/showthread.php?p=1985060)

---

### Post by fnacer on 2007-01-23
Thanks for the link. I restarted in recovery mode (took awhile to figure out I needed to hit ESC to get to the boot loader), ran visudo and found the following message twice at the top of the file:

X Error: BadDevice, invalide or uninitialized input device 166
  Major opcode: 144
  Minor opcode: 3
  Resource id: 0x0
Failed to open device

I deleted the lines, saved the file (without the tmp extension) and restarted the system. Everything seems to be working fine now.

Any idea what may have caused the error messages? Thanks.

Farid

---

