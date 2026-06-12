---
title: "Samba Help"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2008-02-29
Hello :)

I've been trying to access a "test" Samba share that I'm setting up for my home directory on Ubuntu. When in smb.conf I modified the following:
[homes]
[INDENT]comment = Home Directories
browseable = yes
writable = yes[/INDENT]
And in [global]:
[INDENT]smb passwd file = /etc/samba/smbpasswd
encryptpasswords = yes[/INDENT]

Then I try to access my share by:
smbclient  //computername/stuff

But "stuff" i've varied between "home" and "usernames" but I always receive an error. (Stupid question, I know). So then I tried to see what it was doing, so I ran smbclient -L //computername and received the following (partial):
[INDENT]
        homes           Disk      Home Directories
        nonpareilpearl    Disk      Home Directories


        Workgroup            Master
        ---------            -------
        MSHOME               COMPUTERNAME[/INDENT]



Can someone tell if something is wrong with it, or tell me exactly how I should be connecting to my home directory (even though I'm in my user account already, like I said this is more a test run)?

Thanks :)

---

### Post by nonpareilpearl on 2008-02-29
Nevermind, got it. A lot of references I used showed too few '\', so I needed this:
[INDENT]smbclient \\\\PHOENIX\\homes[/INDENT]

Instead of this:
[INDENT]smbclient \\PHOENIX\homes[/INDENT]

Just an FYI for anyone who comes across this .

---

