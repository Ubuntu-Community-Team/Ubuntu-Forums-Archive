---
title: "Copying files across Network with Samba"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-09-17
Hi All 

I have Samba setup on my Ubuntu Server & I can see the shared directory on my  client machine via the GUI.

Problem is that I can't copy all the files since Gnome does not give me Administrator rights; however, when I use the terminal I cannot access the network drive?

I asked a broader question in an earlier thread - [http://www.ubuntuforums.org/showthread.php?t=257213](http://www.ubuntuforums.org/showthread.php?t=257213)

Any ideas?

Thanks in advance

---

### Post by jordanmthomas on 2006-09-17
Have you set up your samba shares correctly?  
In */etc/samba/samba.conf*, here are how my shares are set up so people can get them
The owner of the files is jordan
```
[video]
force user = jordan
force group = users
case sensitive = no
msdfs proxy = no
path = /home/jordan/video

available = yes
guest ok = yes
```

Try making some share following a similar format and then restart samba
```
sudo /etc/init.d/samba force-reload
```

Then, on your client box, you should be able to use smbmount to mount the share via a command line.  Hope this is somewhat helpful!

---

