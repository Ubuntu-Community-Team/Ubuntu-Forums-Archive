---
title: "Samba and  printer sharing"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Blaze1024 on 2006-10-14
Hello Everyone  I hope someone can help with a question I have regarding  Samba and  printer sharing 

Does the line [printers] from my "smb.conf" control printer sharing. Here is that section of my "smb.conf" file
 

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no


for instance when I run 
 smbclient -L localhost -U% 
I get this 


Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        MyFiles         Disk
        IPC$            IPC       IPC Service (Samba 3.0.22)
        ADMIN$          IPC       IPC Service (Samba 3.0.22)
        2430dl          Printer   BW prints on 2430 dl
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        RED                  Samba 3.0.22

        Workgroup            Master
        ---------            -------
        WORKGROUP

the line I am concerned with is 
2430dl          Printer   BW prints on 2430 dl


now if I comment the print section out then run 
sudo /etc/init.d/samba restart
and  
smbclient -L localhost -U% 

I get this

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        MyFiles         Disk
        IPC$            IPC       IPC Service (Samba 3.0.22)
        ADMIN$          IPC       IPC Service (Samba 3.0.22)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        RED                  Samba 3.0.22

        Workgroup            Master
        ---------            -------
        WORKGROUP

Notice that the printer is no longer there! does this mean it is no longer being shared by red (computer name)  >>>Before anyone asks,  I have 5 computers and a network printer connected to my home network The printer is a network printer with its own IP.  All devises on the network are named a color, I then mark the end of each network connector with the corresponding color ie. heat shrink or colored tape, it just makes identifying cables a lot easier. The network is a switched Gigalan utilizing a 6th deticated Linux based laptop as a firewall to the Internet. The laptop is an older pentium running a LiveCD based Linux Firewall.  

Also could safely I comment out the [print$] section

---

### Post by Blaze1024 on 2006-10-15
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Deleted
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

---

