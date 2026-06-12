---
title: "Anti-virus"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by whodat on 2005-07-24
Sup everyone,

The unofficial guide to Ubuntu has been great as well as this forum.  I need help, where do I get clamAV or any other anti-virus package.

Once I get it, how do I install it with the terminal or Synaptic.

Thanks in advance people.

---

### Post by Omnios on 2005-07-24
Basicly open menue/ system tools, Add remove programs click on advanced advanced and search for clam in search. Most stuff in Synaptic is ready to go after downloading and install wich it does. Might have to use freshclam command in terminal to update the virus data base. It kind of runs in the background with terminal commands to scan etc and has email demons etc. Type "man clam"  and "man freshcalm" and also "clam --help" and "freshclam --help" to read up on it.
 
 I also had the backport version wich is a bit newer but got rid of it because I found it to be a bit heavy on ram usage wich affected gamming as I only have 128megs ram but other than that its greate.

---

### Post by Firetech on 2005-07-24
You don't really need antivirus on a Linux computer, as there aren't very many viruses for Linux... (And as long as you're careful with root or sudo access, there's almost no virus threat at all... Nothing to worry about at least.) 
ClamAV is intended for mail servers to remove viruses from mails that probably will end up on Windows computers (It only scans for Windows viruses).
There is a small (very small if you are sure about which files you are playing with) chance that Windows viruses can sneak it's way though a local network to Windows computers, but as long as all the Windows computers on the network have antivirus, there's no need for antivirus on the Linux computer(s).

The short version: You don't need antivirus in Linux, except in some very rare cases.

---

### Post by UbuWu on 2005-07-24
[QUOTE=Firetech]
The short version: You don't need antivirus in Linux, except in some very rare cases.[/QUOTE]

But some people use it to scan their windows drives  ;-)

---

### Post by Firetech on 2005-07-24
[QUOTE=UbuWu]But some people use it to scan their windows drives  ;-)[/QUOTE]
 That's what I would call a rare case... Most people have antivirus in their Windows installations (if they have any)...

---

### Post by UbuWu on 2005-07-24
[QUOTE=Firetech]That's what I would call a rare case... Most people have antivirus in their Windows installations (if they have any)...[/QUOTE]

It is always better to clean the infected system from a clean system, so you can clean your infected windows drive from Ubuntu. Although a complete reinstall would be even better...

And it can be useful to scan your own email inbox. Although the viruses will be no treat to you, they will be to other if you forward an email. And you can notify the sender.

---

### Post by whodat on 2005-07-24
Cool thanks for the info.

---

### Post by stig on 2005-07-25
[QUOTE=Firetech]...as long as all the Windows computers on the network have antivirus, there's no need for antivirus on the Linux computer(s).
The short version: You don't need antivirus in Linux, except in some very rare cases.[/QUOTE]

But be careful you don't receive a Windows virus on your Linux PC and then inadvertenlty pass it on  (e.g. via email) to a friend/colleague/customer elswehere who uses Windows. The virus may not affect your Linux PC but it is still dangerous to a Windows user.

---

### Post by Perfect Storm on 2005-07-25
Try to check out a howto I made for anti-virus: [http://www.ubuntuforums.org/showthread.php?t=25421](http://www.ubuntuforums.org/showthread.php?t=25421)

---

