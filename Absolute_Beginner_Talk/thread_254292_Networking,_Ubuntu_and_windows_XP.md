---
title: "Networking, Ubuntu and windows XP"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by danr on 2006-09-09
I've been working on this and I have it so I can access my windows files from Ubuntu but I can not get into Ubuntu from the windows XP computer.
It does show up in "my network places" in windows as ubuntu500mhz, but when I click on the icon it opens a little box and asks for, user name and password.
I assume it wants the user name and password I use to log into the computer running Ubuntu and I tried it but it does not work.

Can anyone tell me what it wants me to enter there?

Thank you for any help you can offer, Dan

---

### Post by onesojourner on 2006-09-09
I think if you open your smb.cnfg file you can shoose the password there. I am struggling with this crap to so some one should jump in here.

---

### Post by danr on 2006-09-09
Hey thanks, but how do I get to that file?

(I'm very new at this)

---

### Post by jordanmthomas on 2006-09-09
```
gksu gedit /etc/samba/smb.conf
```

Set up your shares at the bottom like this:
```

[music]
force user = jordan
force group = users
case sensitive = no
guest ok = yes
msdfs proxy = no
path = /home/jordan/music

available = yes
browseable = yes
public = yes
writable = no

```

Save it and then restart samba
```
sudo /etc/init.d/samba force-reload
```

The options pretty much speak for themselves.  Try this and see if you can get to a share with Windows

---

### Post by Emmett on 2006-09-09
Look in the How to Forum for a how to on Setup Samba peer to peer with windows from Stormbringer. It is a exellent how to and helped me out.

Hope it helps 

Emmett

---

