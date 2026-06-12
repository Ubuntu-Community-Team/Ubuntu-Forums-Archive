---
title: "Printer share"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by bartbes on 2006-01-20
I have a desktop computer and a laptop on the desktop im using Ubuntu, on the laptop Win XP. I need to print from my laptop on the printer attached to the desktop (network) but how do I share it. I have read of mounting a printer, but how to do that?

---

### Post by AndyCooll on 2006-01-20
Allow sharing of the printer on your XP computer.

You will then need to install Samba (including smbfs IIRC) on your Linux box. Samba is software that enables Linux and XP pc's to communicate with each other.

:cool:

---

### Post by bartbes on 2006-01-20
I already had samba and smbfs but how to share my printer with them??

---

### Post by AndyCooll on 2006-01-20
Unfortunately I'm at work at the moment (so I apologise if my help seems a bit vague). IIRC you'll need to edit your Samba settings

```
sudo gedit /etc/samba/smb.conf
```

Change settings to allow your Linux pc to be viewable by a Windows pc (there are some HOWTOs on these forums which explain how to do this).

Then towards the bottom half of that document are some settings regarding sharing of printers. You'll need to allow your printer to be shared and enable it to be browseable on the network. Log out, log back in.

Now you go to your XP machine and add a printer the same way you would for a printer on a XP machine (i.e. browse the network and you should see the Linux box with printer shared).

Have a look at these threads, they might be of help:

[http://www.ubuntuforums.org/showthread.php?t=108211]("http://www.ubuntuforums.org/showthread.php?t=108211")

[http://www.ubuntuforums.org/showthread.php?t=106990]("http://www.ubuntuforums.org/showthread.php?t=106990&highlight=sharing+printer+windows")

---

### Post by d1337 on 2006-01-20
Windows supports ipp out of the box.  With a few tweaks to your cupsd.conf file  (on Ubuntu) as well as the hosts files (on Windows) you can share printing without using Samba.  See #5 in t[his thread]("http://www.ubuntuforums.org/showthread.php?t=43956") for how I did it.  While this was on a server install, things should be more or less the same.  Sorry if it's wordy, I was 6 months newer then than I am now.

d1337

---

### Post by bartbes on 2006-01-20
thx all but I finally did it with a link in the 2nd link of AndyCooll :p :D

---

