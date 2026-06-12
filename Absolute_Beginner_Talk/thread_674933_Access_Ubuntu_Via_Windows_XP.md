---
title: "Access Ubuntu Via Windows XP?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by mikeylikesit on 2008-01-22
hi all i have been using ubuntu for a while now, but i have found that i need some windows programs (ie. photoshop, dreamweaver, outlook to sync my pda) so i have set up another computer running windows next to my ubuntu box and i share the keyboard and mouse with synergy. All seems to work well execpt when i try and access my ubuntu shares through windows it asks for a password and username. i have tried my creditials that i use to log into ubuntu with with no luck, does anyone have any ideas? thanks

---

### Post by emarkd on 2008-01-22
Unfortunately, accessing Windows shares from Ubuntu is still quite a bit easier than accessing Ubuntu shares from Windows.  There's some really good information here:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by kevin11951 on 2008-01-22
ok, i dont know if this will work, but it worked for me, and it should for you to! 

note: you will still have to enter a user and password, but this will make it so it works!

 How to add/edit/delete network users

```
sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers
```

    * Insert the following line into the new file 

```
system_username = "network username"
```

    * Save the edited file 
    * To edit network user 

```
sudo smbpasswd -a system_username
```

    * To delete network user 

```
sudo smbpasswd -x system_username
```

also im sure that by the time im done writing this, there will be hundreds of replies!

---

### Post by firsttimeubuntero on 2008-01-22
not sure if it will be of much help, but here's a link:

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by beercz on 2008-01-22
Does [this]("http://www.winscp.com/") help?

---

### Post by hyper_ch on 2008-01-22
I'd setup samba

(1) install sambe (it probably already is)

```

sudo apt-get install samba

```

(2) backup your original config
```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.org

```

(3) open the samba config
```

sudo gedit /etc/samba/smb.conf

```

(4) replace the content with this here
```

[global]
workgroup = WORKGROUP
hosts deny = 192.168.0.1

[exchange]
comment = Exchange
path = /home/USER/Exchange
force user = USER
force group = USER
read only = No

[Share]
comment = Share
path = /home/USER/Share

```

USER --> that's your username
WORKGROUP --> that's the name of your windows workgroup (in english it's also just "WORKGROUP")
hosts deny --> enter here the IP of your router

Then you have an example for a read/write folder "Exchange" and a read-only folder "Share"

Change this accordingly. You can have multiple read-only or rw... just use that example...
well, you also have to create those dirs, if they don't exist:

```

mkdir /home/USER/Exchange

```

(5) Then add the system user to the samba user file
```

sudo smbpasswd -a USER

```

(6) finally restart samba
```

sudo /etc/init.d/samba restart

```

---

