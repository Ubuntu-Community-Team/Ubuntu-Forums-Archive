---
title: "Remote Desktop Problem"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by doyler78 on 2007-06-18
I have connected to windows vista ultimate machine from my ubuntu 7.04 machine using terminal server client using rdp. I only have the one monitor and the two computers are beside eachother however I was getting bored with pulling the monitor cable in and out of the two machines so decided to use remote desktop.

No probs getting it going however when working in Photoshop CS3 I really need to view pictures with the monitor plugged directly into my Vista pc however when I do this the screen will not come on. The light on the monitor just flashes amber instead of going green. I decided that must be because my ubuntu machine has locked out the keyboard and mouse on the my vista pc and therefore I can't wake the screen up. I ran a command line shutdown /s on the command prompt and this shut the pc down however when it booted up normally it gets so far then the screen turns itself off again. After rebooting several times and getting no where with system restores and startup repairs I decided to go back into ubuntu and sure enough if I open a rdp session to my vista machine I can login again.

Any ideas whats happening here. It looks like somehow my screen is being locked out the previous ubuntu session.

Very new to linux therefore please offer any advice in an easy to understand format if possible.

Thanks

---

### Post by PgR on 2007-06-18
Sounds like a vista prob rather than ubuntu to me.

A simpler solution may be a KVM switch. You can pick one up very cheaply these days.

---

### Post by doyler78 on 2007-06-19
I managed to solve the problem. It was caused entirely by me.

When you bring up the terminal service client you have several protocols from which to choose. RDPv5 must be used for Vista and XP and not the plain RDP option. Once I logged in with RDPv5 and logged out of the remote session and plugged the monitor back into my pc the login screen was there waiting for me. I logged in again under RDP and tried that again and the problem returned therefore this is definitely what is causing the problem. Unfortuantely I am not very technical so cannot answer why it causes Vista not to boot to a login in screen from a cold boot as you would expect that any remote session lockouts would be cleared on reboot but obviously not.

---

