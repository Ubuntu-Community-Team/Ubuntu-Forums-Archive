---
title: "[SOLVED] Establishign connection between UBUNTU gutsy and XP (wired)"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-12-20
Hello, first let me say i consider myself an advanced user :)
But im close to .... arhhhhhh im trying since 6 hours to establish a WIRED network connection.

So the network looks like this.

Wired connection with a crosscable i belive(i had this running sometime ago with a diffrent release and notebook). 

WORKGROUP = mshome ( in windows and ubuntu-smb)

**UBUNTU SETTINGS**
Samba is installed and i entered a user smb password.
The ubuntu network is either static ip with 192.168.0.2 or roaming mode i tried DHCP too, which had the best results so far as firefox was searching.
Added a shared folder
Ubuntu is patched. 


if i 
```
sudo ifdown eth0
```

or```
 sudo ifup eth0 
```

i get a eth0 not configured, I CAN connect with pppoe direct from my ubuntu notebook but not over XP.

ifconfig gives me, 

eth0:avah i HAD an static ip rightnow its not static ... i try around ...

**XP SETTINGS**
The windows lan connection is configured with ip - 192.168.0.1
I haveedited windows firewall bitdefender to add the ubuntu ip (192.168.0.2) and xp ip (192.168.0.1) to thrusted.
Added a shared folder and activated files and printer sharing.
Broadband connection is activated to Internet shared.

I can see on the ubuntu desktop a connection called "192.168.0.1", but accessing it reports="The folder contents could not be displayed".
Network tool ping is not finding anything.
Under windows i cannot see anything.

What i need to know IS .... How can i access the XP computer AND how can i access Internet over XP computer now. I do not need XP to access ubuntu at all. I just want file transfer and Internet .... 

Please help me im to stupid to find a howto with samba ... i dont know what i can do next .... ahhhhhhh  MAYBE someoen can help me through this .. or point me to an EASY howto, not a howto which just describes toll functions ... and i dont want a complete samba environment i want just access xp ...thanks


Cheers

---

### Post by spiderbatdad on 2007-12-20
```
sudo aa-complain cupsd
``` This command is supposed to address a bug in cups app armour. Hope this helps.

And this: [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by shareMenaPeace on 2007-12-20
Hi spiderbatdad, 
thanks for the link, but i run into the following problem there....

All seems to go well since i try to mount these commands:
```

//DEVMACHINE/shares     /media/winshares        cifs   auto,credentials=/etc/smbcredentials,workgroup=MSHOME,gid=smb,uid=1000,file_mode=770,dir_mode=770,rw       0       0
```

I recive
WARNING file mode not expressed in octal
WARNING dir_mode not expressed in octal

mount error could not find target server TCP name DEVMACHINE/_incoming not found 
No ip address specified and hostname not found.

Hmm

---

### Post by spiderbatdad on 2007-12-20
yep same error here.  I've only been at it about 16 hours though. :)

---

### Post by shareMenaPeace on 2007-12-20
lol, 
i think this tutorial is intresting but really not the right one, because it focus on mounting and not establishing a conenction....and its not noted that its compatible to gutsy ...

---

### Post by spiderbatdad on 2007-12-21
the primary problem for me seems to be cups to allow the connection. I have various refusal messages in the syslog:
E [20/Dec/2007:23:17:38 -0500] cupsdAuthorize: Local authentication certificate not found!

and...screenshot below

I'm reading something now about adding cupsys to the shadow group:[http://www.cups.org/articles.php?L274](http://www.cups.org/articles.php?L274)

---

### Post by shareMenaPeace on 2007-12-21
And did you had progress?

:D

---

### Post by shareMenaPeace on 2007-12-21
Please maybe someone else can point me to a howto access xp from ubuntu via wired cable?
What is importend ... what do i need to check?

Thanks!

---

### Post by shareMenaPeace on 2007-12-21
Ok i got it!


The error WAS because i have 2 network cards ... and i configured them exactly wrong :)

From the howto link above the control network cmd shows the correct LAN connection.


Cheers

---

### Post by shareMenaPeace on 2007-12-21
To connect i need to create a user with password in windows and log with this login into win network from ubuntu OR i can use the way described in above howto. To access Ubuntu i can create also an extra account from the user and groups menu.

Im not quiet sure if this is the correct way and why i need a smb user .. hmm :)


:popcorn:

---

