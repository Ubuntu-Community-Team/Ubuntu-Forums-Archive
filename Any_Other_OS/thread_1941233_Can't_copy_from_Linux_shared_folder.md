---
title: "Can't copy from Linux shared folder"
date: 2012-03-15
forum: Any Other OS
---

### Post by maspai on 2012-03-15
Hi
I have Linux Mint 12 LXDE with samba installed. I shared a folder via system-config-samba, with visible and writable options set to on.
But then I couldn't copy files in the shared folder from other computer with Windoz. The error said that I don't have permission to change the files in the folder. Weird, because I even just wanted to copy, not move nor delete.
Any help appreciated. God bless you.
Thanx.

---

### Post by SlugSlug on 2012-03-15
just check the 'workgroup' matches up in both ubuntu and windows

---

### Post by Morbius1 on 2012-03-15
Please post the output of the following command:
```
testparm -s
```

---

### Post by Perfect Storm on 2012-03-15
Moved to Other OS/Distro Talk.

---

### Post by JoJairus on 2012-06-07
Hi, I'm having the same problem between Windows 7 Home on my netbook and my partner's Linux Mint 12 distro, which I installed recently for her.  Anything dropped into Public folder, from either machine, has Permissions that need to be unlocked with sudo nautilus before the other machine can move/edit the files.  This wasn't a problem with Linux Mint 11.

Output of my testparm -s:
[global]
    server string = %h server (Samba, LinuxMint)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

any advice?  Or maybe installing Linux Mint 13 will cure it.  Joseph

---

### Post by Morbius1 on 2012-06-07
You don't have the Public folder defined in smb.conf so I'm guessing that you created the share from Nautilus. If you run the following command it should show you all the shares you created from Nautilus:
```
net usershare info --long
```The easiest way to resolve this issue if I understand your post correctly is to add the following line to the [global] section right under the workgroup line:
```
force user = morbius
```[COLOR=Blue]*Change morbius to the local user's login username - the user that created the share.*[/COLOR]
Then restart samba:
```
sudo service smbd restart
```

---

### Post by JoJairus on 2012-07-25
Morbius, thanks for the excellent instant advice, which worked:

[COLOR=#800000]sudo gedit /etc/samba/smb.conf  [/COLOR]

then inserted these two lines after WORKGROUP:
  # Line advised by Morbius1 to force permissions of files dropped in from another machine:
   force user = cm
   [FONT=Times New Roman, serif][SIZE=3]Then restarted samba as you advised.[/SIZE][/FONT]
 
Good enough for me on the Linux Mint 13 machine I maintain:  
Now I can drop files from one of my Windows computers into a shared folder on the LM13, and user cm has the permission to move them etc.

---

