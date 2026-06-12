---
title: "Samba Issues"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by playing_with_matches on 2007-09-05
Ok, I set Samba up ok and all, but I'm having some issues.  The Windows machine can access my shared folders, my RhythmBox playlist (Windows uses Itunes), and my printer.  However the Ubuntu machine cannot connect to anything on the Windows Machine... 

1.  I added a rule under Firestarter (the firewall) to allow incoming connections from the Windows machine.  For some reason though, when I go under Places->Network, it won't show the computers on the samba network unless I completely disable the firewall.

2.  Even when I completely disable Firestarter, I cannot access the Windows machine, although I see it.  I get a popup telling me that "You Must log in to access mike@windowsmachine domain MSHOME"  I put in my username and password, and nothing works.  And under rhythmbox, I can see the connection to the windows Itunes, but it doesn't list any songs!  

Any help would be greatly appreciated!

---

### Post by gautada on 2007-09-06
> I get a popup telling me that "You Must log in to access mike@windowsmachine domain MSHOME" I put in my username and password, and nothing works.

Try turning off authentication on windows.  Some windows credentials need to be written as "\\MACHINE\USER"  which is a pain.  But to start remove all credentials requirements on windows (in samba speak "Allow guests").  This should remove the login request.  Also try smbtree from the command line and make sure you are really seeing all windows shares.  I just type in a random password.  If you still require credentials on the windows box this will not return the shared folders you expect.

---

### Post by playing_with_matches on 2007-09-06
Hey, thanks for the reply.  I ran the smbtree, and this is the output i get:

```

MSHOME
        \\MIKE           
                \\MIKE\PhotoSmart-7150  PhotoSmart-7150
                \\MIKE\IPC$             IPC Service ()
                \\MIKE\MyFiles        
                \\MIKE\print$         
        \\JERK                          i'm a jerk
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine JERK.  Error was NT_STATUS_ACCESS_DENIED


```

The Windows PC (the one named JERK) isn't being noticed, but won't let me do anything with it.  It's running XP.  How do I disable the creditials? I tried to do it by enabling the "Guest" account, but i still get the "Authentication Required" box.  when I try logging in (even if i just type "guest") i get a popup saying:

"Sorry, couldn't display all the contents of "Windows Network: jerk".

---

### Post by playing_with_matches on 2007-09-06
Oh, and here is smb.conf in case that helps at all:

```

[global]
    ; General server settings
    netbios name = mike
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
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

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = mike
    force group = mike

```

---

### Post by gautada on 2007-09-10
I cannot remember exactly.  My windows box is currently down until I get a part in the mail...  On the windows box "JERK" create a shared folder.  It is under the right-click on a folder.  You set the share name and the required credentials.  If you futz with these settings you will get the correct setup.  Sorry I cannot give specific instructions from memory.

Check out:

[http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php]("http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php")
[http://www.reallylinux.com/docs/sambaserver.shtml]("http://www.reallylinux.com/docs/sambaserver.shtml")

Don't forget to turn off the firewall on "JERK" for right now until it is working.

Also for right now in your smb.conf I would make "guest ok = no" equal "yes" for "[MyFiles]" until it is working the way you want.

---

