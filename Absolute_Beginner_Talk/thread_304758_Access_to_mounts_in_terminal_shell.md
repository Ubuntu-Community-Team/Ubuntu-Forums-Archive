---
title: "Access to mounts in terminal shell"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by stasmash on 2006-11-22
Hello everyone,
    I have mounted a network share through System->Administration->Shared Folders. I now want to have access to said share from terminal shell for the purposes of a Perl script doing some admin work.
     For whatever reason I am completely turned around and can't mount it. I have read more then a few posts on here and need a little walk through. I am using 6.10 and have Samba installed yet no smbmount for some reason.

Sorry for the lack of details, I could provide more if started in the right direction. I would like to think that if I mapped it in X Windows and see the darn shares in Nautilus then I could easily access the shares from terminal.

Thanks and Happy Thanksgiving!
S;

---

### Post by taurus on 2006-11-22
Is your XP already mounted?  What is the output of this command from a terminal then?

```
df -h
```

---

### Post by NESFreak on 2006-11-22
have you tried
```
man samba
```?

and for mounting and stuff you need smbclient
```
man smbclient
```

hope the man file contains something usefully
NESFreak

---

### Post by dbott67 on 2006-11-22
See the [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=280473") in my signature below.

Another useful command is smbtree:
```
dbott@dapper:~$ smbtree
Password:
WORKGROUP
        \\PIII-600
        \\NAS-160GB
                \\NAS-160GB\IPC$
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC
MSHOME
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott-P4
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\PIV3GHZ                       Joyce Laptop
cli_start_connection: failed to connect to PIV3GHZ<20> (0.0.0.0)
        \\DAPPER                        dapper server (Samba, Ubuntu)
                \\DAPPER\print$                 Printer Drivers
                \\DAPPER\ndis
                \\DAPPER\IPC$                   IPC Service (dapper server (Samba, Ubuntu))
                \\DAPPER\ADMIN$                 IPC Service (dapper server (Samba, Ubuntu))
```

-Dave

---

### Post by NESFreak on 2006-11-22
btw smbmount is part of the smbfs package which isn't installed by default.
```
sudo aptitude install smbfs
```

---

