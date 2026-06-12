---
title: "Help with Samba P2P network?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by bigkahuna on 2006-05-28
Background:
I've got two computers: 
1) desktop running Windows XP Pro 
2) notebook running Ubuntu 5.10
The notebook has 2 nic adapters, one is connected to a router/modem and my ADSL service, the other nic is a PCMCIA card and connects me to my Windows machine.  My internet connection is working on the Ubuntu machine and the network connection seems to be working (the nic lights are on and the Windows machine says that there's a connection).

I installed and configured Samba following these instructions:

[http://help.ubuntu.com/starterguide/C/ch07.html#sect-samba-server](http://help.ubuntu.com/starterguide/C/ch07.html#sect-samba-server)

and opted for #5, which would allow read/write sharing of my Home folder (seems like the simplest to set up).  I also used "security=share" to skip authentication (I hope that's OK,  both computers are on my desk).

Now I'm not sure what to do next.  I tried setting up the Windows side, but it's not seeing my Ubuntu home folder.

What should I do now?  Thanks!

---

### Post by bigkahuna on 2006-05-28
Argh... this is getting frustrating...

I think I've got the Linux side setup properly, when I restart Samba it dumps this info:
```

# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

```

So the "MSHOME" group I'm guessing means that it's talking to my Windows machine, but when I go to the Windows machine it doesn't see anything ? argh...

---

### Post by christhemonkey on 2006-05-28
Do the machines have static IP addresses?

If so can they ping each other?

```
ping ip.add.ress.of.other.pc 
```
Press Ctrl+C to stop it.

---

### Post by bigkahuna on 2006-05-28
Ok, I'm getting closer.  I had to give the Ubuntu system a static address (I had picked DHCP earlier) and I can ping both ways now.

Now when I try to setup a "Network Place" on the Windows machine, it lets me set up "\\vaio\share" but when I try to access it I get this error:  "\\vaio\share is not accessable.  You might not have permission to use this network resource... The network path was not found".  So I'm guessing that I haven't setup my shared directory properly?

I went to System>Administration>Shared Folders and selected my "/home" folder to share.  It want's me to enter "Share Properties" "Name", but what name do I enter?

---

### Post by christhemonkey on 2006-05-28
Call it what you like!

But on the windows machine, you have to type:
```
\\ip.adress\whatyoucalledtheshare
```
In a internet explorer address bar.

---

### Post by bigkahuna on 2006-05-28
OOOH...  THAT WORKED!  I'm getting closer!  Ok, I can access the shared file in IE, now I've got to setup a "network place"...

---

### Post by bigkahuna on 2006-05-28
GOT IT!!!  I want to tweak things a bit.  Maybe create a "SHARE" folder since I don't want to accidently mess up my home folder...

---

### Post by christhemonkey on 2006-05-28
Fair does!

The joys of Samba!


Hahaha, glad you got it sorted.

---

### Post by bigkahuna on 2006-05-28
Ok, one -last- issue...

I created a new folder "SHARE" in my "Home Folder".  I set it up to share, but the only way that the Windows machine sees it is if I use the IP address, ie:  \\192.168.0.1\share\SHARE .  If I try to use the machine's name (VAIO) it doesn't work (?), it tells me it's not found.  The only problem is that Windows thinks this is an internet connection (?).  What have I done wrong?

---

### Post by christhemonkey on 2006-05-28
On windows you need to find the file called hosts (located in windows/system32/drivers/etc/hosts) and add the line:
```
ipaddress     Vaio
```
to the end.

---

### Post by bigkahuna on 2006-05-28
OOH YEAH...  that did it!  Thanks a bunch!!!  This Ubuntu community is sooo great, thanks again for your help!

---

