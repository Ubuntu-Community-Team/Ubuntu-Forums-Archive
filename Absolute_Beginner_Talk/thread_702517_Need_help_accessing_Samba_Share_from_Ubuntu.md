---
title: "Need help accessing Samba Share from Ubuntu"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-20
I have a Samba Share setup on another machine that is running Xubuntu that I can happily access from my WinXP machines by entering in the username/password credentials, but when I try and access the same share from Ubuntu/Nautilus it doesn't prompt me for the credentials and just fails to access saying:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/err-accessingsambashare.png[/IMG]
But I know the folder wasn't/isn't deleted because it's still accessable from my XP machines...
Why isn't Ubuntu prompting for user/pass? I believe this is why it's failing.

p.s. In Synaptic I have the following installed: 
[list][*]libsmbclient
[*]samba-common
[*]smbclient
[/list]
TIA,
-BassKozz

---

### Post by maybeway36 on 2008-02-20
Try:
```
smbclient -L //nameofserver
```

---

### Post by BassKozz on 2008-02-20
> **maybeway36 said:**
> Try:
```
smbclient -L //nameofserver
```
Ouput:
```
~$ smbclient -L //Remote-Samba
Password: 
Domain=[Remote-Samba] OS=[Unix] Server=[Samba 3.0.26a]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (Remote-Samba server (Samba, Ubuntu))
        Media           Disk      Media Files
        print$          Disk      Printer Drivers
Domain=[Remote-Samba] OS=[Unix] Server=[Samba 3.0.26a]

        Server               CommentRemote-Samba
        ---------            -------

        Workgroup            Master
        ---------            -------
        MSHOME               Host-Computer
        WORKGROUP            Remote-Samba
```

p.s. I probably should've been more explicit, I am trying to access this from Nautilus, or mount it.

---

### Post by BassKozz on 2008-02-20
:BUMP:

How can I get Nautilus to prompt for user/pass credentials when trying to access a Samba share?

---

### Post by spiderbatdad on 2008-02-20
maybe install nautilus-gksu

---

### Post by BassKozz on 2008-02-20
> **spiderbatdad said:**
> maybe install nautilus-gksu
Just installed it, then opened up Nautilus, and still the same problem:(

---

### Post by BassKozz on 2008-02-20
Well I was able to mount the samba share to my home folder using the instructions I found here:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba#head-d0cf07ad854d6a463aa1ba9345600732832d47ef)
The odd thing is the following doesn't work:
```
~$ sudo smbmount //Remote-Samba/media /mnt/smb-media/
Password: 
7121: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```
and this was after I "mkdir /mnt/smb-media"
so I had to:
```
~$ smbmount //remote-samba/media ~/mnt
Password: 
```
Which does work... 
I wounder why you can't samba mount to the /mnt/ directory but you can to the /home/user/mnt/ directory?
...
Anyways, I am still trying to figure out how to access the samba share directly via Nautilus (navigating to Network, and finding the share doesn't prompt for user/pass)?

---

### Post by BassKozz on 2008-02-24
:BUMP: :roll:

---

### Post by Iowan on 2008-02-24
Check the link in my sig.

---

### Post by BassKozz on 2008-02-24
> **Iowan said:**
> Check the link in my sig.

Thanks but this still leaves me questioning why Nautilus won't let you logon to Samba Shares, you still have to use a terminal command to mount it...
Is this by design? Is there a way to get Nautilus to play nice w/ Samba shares?

---

### Post by Iowan on 2008-02-24
I usually use the "Connect to Server" option.  For whatever reason, I end up with an icon on my desktop.  The first time in each session I must enter password (it seems to default to username).  After that, it's usually click and access.

---

### Post by i_m_bobo on 2008-02-24
-BassKozz,

Check the last page **[here]("http://ubuntuforums.org/showthread.php?t=701994&page=4&highlight=samba")**, where windyweather and I work through a very similar problem..

---

### Post by bazzawill on 2008-02-24
You can access samba shares in nautilus from places - network on the panel or go - network in nautilus

---

