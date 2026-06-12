---
title: "Help creating warning banner at *console* login screen?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by scottsre on 2008-03-22
I need help creating a warning banner of custom text when someone is about to log into the console, ideally before they enter their user/pass, but, if needed, it could be after.

This is NOT for a remote login, but the graphical console screen.

I happen to be using 64-bit Gutsy.

I tried gdmsetup, and selecting Custom under its Local tab, then typed in some random text, but saw nothing even on reboot.

Funny thing is, an out-of-box install permitted gdmsetup to work fine.  But after an apt-get update/apt-get upgrade, gdmsetup core dumped after attempting the custom option.

So what do I need to change, and where?

Under CentOS/Fedora, I can easily place /etc/gdm/kdialog --yesno "This is my custom banner" as the first uncommented line in /etc/X11/xinit/Xsession, but that doesn't seem to work in Ubuntu.

Thanks for any leads.

Scott

---

### Post by Oldsoldier2003 on 2008-03-24
The MOTD is traditionally displayed after you enter your username and password, not during boot. If you would like to have a mesage displayed above the "login" prompt at the console, edit /etc/issue. to verify this just cat /etc/issue, then hit ctrl+alt +f1 for  tty1 you'll see that /etc/issue is printed before tty1

---

### Post by gwolfman on 2008-04-28
Were you able to figure this out?  I'm having the same issue!

---

