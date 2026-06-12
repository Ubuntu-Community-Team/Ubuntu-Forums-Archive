---
title: "trouble configuring samba"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by vamp4life666 on 2008-01-23
from the the ubuntu documentation page I got:

"Configuring SAMBA

You may configure the SAMBA server by editing the /etc/samba/smb.conf file to change the default settings or add new settings. More information about each setting is available in the comments of the /etc/samba/smb.conf file or by viewing the /etc/samba/smb.conf manual page from the prompt with the following command typed at a terminal prompt: "

I have tried the follwing with no success

/etc/samba/smb.conf          gets me permission denied
sudo /etc/samba/smb.conf        gets me command not found
root /etc/samba/smb.conf         get me command not found
su /etc/samba/smb.conf            gets me unkonwn Id


any ideas?

---

### Post by hyper_ch on 2008-01-23
```

sudo gedit /etc/samba/smb.conf

```

or

```

sudo kate /etc/samba/smb.conf

```

or

```

sudo mousepad /etc/samba/smb.conf

```

or

```

sudo nano /etc/samba/smb.conf

```

or

```

sudo vi /etc/samba/smb.conf

```

or

```

sudo vim /etc/samba/smb.conf

```

or

....

depends on what programs you ahve installed.

---

### Post by drs305 on 2008-01-23
To edit this file:
```
gksu gedit /etc/samba/smb.conf
```

You may want to make a backup first:
```
 sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

---

### Post by Nythain on 2008-01-23
as mentioned before, ceptin ill point something out...
gedit should be opened with gksu and would be used if you are running gnome and want to open it in a graphical editor

kate should be opened with kdesu and would be used if you are running kde and want to open it in a graphical editor

nano, vi, and vim are all console text editors i believe, are opened properly with sudo and probably from either a console or a tty?

hope that clarifies it a little bit

---

### Post by vamp4life666 on 2008-01-23
Sudo nano got me into File: /etc/smaba/smb.conf      

the others did not......   
I installed gedit  but sudo gedit  gives me cannot open display...?    

I think if i stick to nano I'll get it, thanks.

---

### Post by vamp4life666 on 2008-01-23
> **Nythain said:**
> as mentioned before, ceptin ill point something out...
gedit should be opened with gksu and would be used if you are running gnome and want to open it in a graphical editor

kate should be opened with kdesu and would be used if you are running kde and want to open it in a graphical editor

nano, vi, and vim are all console text editors i believe, are opened properly with sudo and probably from either a console or a tty?

hope that clarifies it a little bit



I did not know the difference, thank you for pointing that out.    

I am in text only, so I guess nano will be the way to go.

MG

---

### Post by hyper_ch on 2008-01-23
> **Nythain said:**
> as mentioned before, ceptin ill point something out...
gedit should be opened with gksu and would be used if you are running gnome and want to open it in a graphical editor

kate should be opened with kdesu and would be used if you are running kde and want to open it in a graphical editor

nano, vi, and vim are all console text editors i believe, are opened properly with sudo and probably from either a console or a tty?

hope that clarifies it a little bit

well, you can also just use "sudo".... althou gksu and kdesu would be more appropriate.

---

