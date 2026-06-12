---
title: "smb4k works but i cant see any computers through nautilus"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-12-27
hi i'm in a bit of a bind.  i don't know why but smb4k works well.  however i can't access or even see any other computers on my network through nautilus(places - network- windows network- workgroup) i then get an error stating that the contents could not be displayed.

when i use findsmb i get this-

IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
10.0.0.4        BRAD-LAPTOP   +[WORKGROUP] [Unix] [Samba 3.0.24]
brad@brad-laptop:~$ 
brad@brad-laptop:~$ 

how do i configure nautilus so i can access my windows pc. (the windows pc is running vista)

does anyone have any ideas as to why smb4k is working fine but nautilus won't?? if its a permission problem how do i reconfigure nautilus?  i had this problem sorted but i had to do a reinstall and i forget what i did to get it to work.  also, i downloaded swat and it won't load.  theres not even an icon for it.

i'm still trying to figure this out.  i used the smbtree command and this is the output:
brad@brad-laptop:~$ smbtree
Password: 
WORKGROUP
        \\VISTA-HP       
Error connecting to 72.51.47.244 (Connection refused)
cli_start_connection: failed to connect to VISTA-HP<20> (72.51.47.244)
MSHOME
        \\BRAD-LAPTOP                   brad-laptop server (Samba, Ubuntu)
                \\BRAD-LAPTOP\DCP-8040          DCP-8040
                \\BRAD-LAPTOP\PSC-2110          PSC-2110
                \\BRAD-LAPTOP\IPC$              IPC Service (brad-laptop server (Samba, Ubuntu))
                \\BRAD-LAPTOP\print$            Printer Drivers
does anyone have any ideas as to why the connection would be refused by the windows machine? i know its a dumb question but i'm grasping at straws at this point

---

### Post by obfusco on 2007-12-28
Have you tried connecting directly (Nautilus->[Ctrl]+L->'smb://72.51.47.244') browsing for shares in samba is often buggy, even windows - windows unless both computers are in a domain.

If that works, you should also be able to use smbfs to mount the shares locally:
[http://ubuntuforums.org/showpost.php?p=1637029&postcount=1](http://ubuntuforums.org/showpost.php?p=1637029&postcount=1)

---

