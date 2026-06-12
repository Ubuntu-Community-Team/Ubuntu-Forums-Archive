---
title: "does anyone know how to &quot;see&quot; windows shares?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-12-23
ok i'm going to try and describe this as clearly as i can.  i am using feisty fawn. i've done this before but for some reason i can't do this now (connect to a windows computer on the network) the other computer is using windows vista.  i've done this before with ubuntu (same distro) and connected to the same windows machine.  everything and i repeat everything is the same as before.  i am trying to connect through: places -  network - windows network - workgroup- and then i get an error message stating that the folder contents could not be displayed.  in fact i don't even see an icon for the windows computer. Now, this is even more interesting.  i downloaded Smb4k.  Right off the bat i can see the vista (windows) machine.  also, i can see everything thats on there.  But wait- when i try to connect through there i can an error message saying that what i have selected could not be mounted. here is the error message

smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1

this error message is from the smb4k application.  Now are there any dependencies that i need or may have overlooked.  if my memory serves me right i could connect right off the bat last time.  Stupid me updated to Gutsy Gibbon and now went back to feisty fawn because gutsy has more holes in it than a piece of swiss cheese.  Thats another story for another time.  One last tidbit of info- i can see my computer on the network from the windows machine yet i can't connect to the ubuntu computer from the windows machine.  so what has to be done? can someone point me to a "how to"? let me know whats up!  thanx and happy holidays!!

---

### Post by jaybombalous on 2007-12-23
you have a permissions problem, but I am not the one to tell u the command to fix it.


> smbmnt must be installed suid root for direct user mounts (1000,1000)

^^^ its telling u exactly what to do, I just don't know how to do that. Maybe u can look further now. In particular smbmnt is installed with the wrong permission suid. change it and it should work just like it did before.

---

### Post by jaybombalous on 2007-12-23
try this, goto where smbmnt is installed, do a right click on the file and check the properties > permissions tab. 

Using 

```
gksudo nautilus
```

gives u root access to the files if in case u choose to modify them.

---

### Post by bradmayne on 2007-12-23
can you go into more detail as to where smbmnt is installed? or what to do after the command you just just posted? after i used the command you posted the only icon i see is "desktop" i added 2 screenshots so that i can give a bit more detail of what my problem is. the error message is the message i receive while going to places- network- etc as i described above.  the other screenshot is from the smb4k app that i mentioned above in my first post.  can someone please help???

---

### Post by HermanAB on 2007-12-23
smbmount is deprecated.  You should use cifs.  Read the Official Howto on the Samba web site for details.

Cheers,

Herman

---

### Post by shareMenaPeace on 2007-12-23
sorry if im off track but what worked for me was using dhcp in network settings on ubuntu and a static ip in windows (192.168.0.1)

---

### Post by HermanAB on 2007-12-23
Don't confuse general TCP/IP issues with SMB issues.  These things are on top of each other.  SMB needs TCP, which needs IP.  So SMB won't work if the routing underneath is broken.  Therefore, first sort out your addresses, netmasks and routing, before playing with SMB, otherwise you are just wasting your own time.

---

