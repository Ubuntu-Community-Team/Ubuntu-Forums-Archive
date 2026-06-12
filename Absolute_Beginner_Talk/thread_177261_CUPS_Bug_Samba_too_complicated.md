---
title: "CUPS Bug? Samba too complicated?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-16
There is a thread here somewhere saying that there is a bug so CUPS won't share a printer in Dapper to a Win box.  I don't have Dapper.  I have Breezy.  Does Breezy have this bug?  

If I can't share my printer in Breezy then I need to allow a winXP computer to send Ubuntu files so Ubuntu can print them. I have searched for Samba related threads and I have gotten nothing but a headache.  Seems way too complicated to set up.  Do you have a quick way to set it up?  Security might not be much of an issue, but prefered.

I guess an ftp session would work, but I feel cheated out of the best way to do it.  I have enough usernames and passwords.  I don't want to get another one; assuming Samba doesn't require one.

Thanks

---

### Post by Nikusan on 2006-05-16
To work out how to share your printer, you'll have to tell us what model it is.
To set up a shared folder use System > Administration > Shared Folders. If you haven't installed samba yet this will prompt you to do that. Make sure read only is unticked so you can write to the folder from windows.

Alternatively, you could just set up a shared folder on the windows machine and put the file you want to print in there before accessing it from the ubuntu machine.

---

### Post by morequarky on 2006-05-16
[COLOR="DarkOrchid"]Share Folders[/COLOR]
Thanks so much for the response.  I went to System - Admin - Shared Folders.

I created a SMB(Samba) and NFS to /media/fat32.  I created both because I don't know which one is needed.  I want to install linux on my PDA so both might be the best thing to do.  Maybe I should share something other then my fat32 partition.  Should Ubuntu be the WINS server?

The laptop I am trying to share to is an XP machine made last year.  It has the Korean OS so it is harder then normal for me to get around it.  I don't speak Korean.

How do I get Ubuntu to join the correct, non-default workgroup that Windows is on?  I went to System - Networking - General tab and change the information there, but it either doesn't work or I need to reboot for it to take effect.

How do I get XP to find Ubuntu's shared folders?  <-- yeah common question

[COLOR="DarkOrchid"]
PRINTER[/COLOR]
My printer is an HP Officejet 4255 all-in-one.  I am using 4200 series linux drivers and it works great.

Thanks for the help again.

---

### Post by morequarky on 2006-05-16
[COLOR="Green"]testparm outputs this[/COLOR]

[COLOR="DeepSkyBlue"]
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[fat]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = JUPITER
        server string = %h server (Samba, Ubuntu)
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

[fat]
        comment = fat32
        path = /media/fat32
        read only = No
        guest ok = Yes
[/COLOR]
[COLOR="Green"]
The workgroup name is now correct.  Don't know how it got there.  
After a reboot, Windows now thinks Ubuntu is on the same
workgroup, but Ubuntu isn't sharing anything it seems.  Windows pops-up
a username and password for access to Ubuntu; nothing I enter works.
[/COLOR]

---

### Post by dmizer on 2006-05-16
i was able to get windows to see my ubuntu shared.  it's not a how to, but it might help ya in your quest for a local network: [http://www.ubuntuforums.org/showthread.php?t=169660&highlight=dmizer](http://www.ubuntuforums.org/showthread.php?t=169660&highlight=dmizer)

i have done nothing but fail at getting printing to work so ... all i can do is wish ya the best of luck.

---

### Post by morequarky on 2006-05-17
I found out what I needed to do.  Everything is taken care of.  It works now.
Windows sees and can access the fat32 partition on my ubuntu box.

:)

Thanks for all the great help....

---

### Post by Jose Catre-Vandis on 2006-05-26
[QUOTE=morequarky]I found out what I needed to do.  Everything is taken care of.  It works now.
Windows sees and can access the fat32 partition on my ubuntu box.

:)

Thanks for all the great help....[/QUOTE]


And did you get your printer working over the network too? If so how?

---

### Post by morequarky on 2006-05-26
Still working on that.  I have a printer for each computer and with the rare color image needed, we can transfer the file over and print it from here.  So it isn't super needed, but I would like to get it to work sometime.

---

### Post by Lord Illidan on 2006-05-26
I'd like to know, too.

---

### Post by edafe on 2007-01-08
Maybe this is useful:

[http://www.edafe.org/ubuntu/index.html#cupssamba](http://www.edafe.org/ubuntu/index.html#cupssamba)

Regards,
Edafe

---

