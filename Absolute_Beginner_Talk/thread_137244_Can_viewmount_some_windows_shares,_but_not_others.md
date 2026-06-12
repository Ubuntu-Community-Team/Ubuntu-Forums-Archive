---
title: "Can view/mount some windows shares, but not others"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by ras on 2006-02-27
Can view/mount some windows shares, but not others.

I am trying to mount my wife's window's xp share and am having trouble.  I have mounted my share and the alluser's share, but cannot mount her's.  I assume the trouble is with windows.

In XP I shared my wife's share (C:\Documents and Settings\valleri\MyDocuments) and set it to "share folders on the network" and "allow network users to change my files".  However, I still cannot connect with smbclient. It shows up as a share, but connection to the internal directories is denied.

The Windows shares are ```

austin@mightywhitey:~$ smbclient -L //toshitop
Password:
Domain=[TOSHITOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        CanonPIX        Printer   Canon PIXMA iP3000
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        valleri-tosh    Disk
        shared-tosh     Disk
        austin-tosh     Disk
        Printer         Printer   Microsoft Office Document Image Writer
Domain=[TOSHITOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
austin@mightywhitey:~$
```

But when I try to log onto 'valleri-tosh' via smbclient using the appropriate username and password, and try to view the directories, I get the following:```

austin@mightywhitey:~$ smbclient //toshitop/valleri-tosh -U valleri
Password:
Domain=[TOSHITOP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> dir
NT_STATUS_ACCESS_DENIED listing \*

                47594 blocks of size 2097152. 27960 blocks available
smb: \>

```

A linux guru friend suggested that the problem is in windows, but I have exhausted myself trying every conceivable way to share it in windows, yet it still doesn't work.

Can a windows/linux user help me?  This wouldn't have anything to do with my /etc/init.d/samba file or anything on the linux side, would it?  Thanks.

ras

---

### Post by ras on 2006-02-27
bump

---

