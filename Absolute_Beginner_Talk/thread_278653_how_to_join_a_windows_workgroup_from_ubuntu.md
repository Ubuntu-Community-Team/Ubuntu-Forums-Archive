---
title: "how to join a windows workgroup from ubuntu ?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by kevinrea on 2006-10-16
hi guys,

a newbie of course..
how do i join a windows workgroup with my ubuntu system ?

thanks,
kevin
[email]ksrea@sbcglobal.net[/email]

---

### Post by daou on 2006-10-16
If you want to do this for sharing files & printers, have a look here:

[URL="http://www.ubuntuforums.org/showthread.php?t=202605"]http://www.ubuntuforums.org/showthread.php?t=202605
[/URL]

---

### Post by kevinrea on 2006-10-16
no, i don't want to use samba.

besides, that is from the pc to the linux box.

i want to go from the linux box to the pc.

in order to do that i need the linux box to join the microsft workgroup that the pc is in.

thanks,
kevin

---

### Post by bodhi.zazen on 2006-10-16
> **kevinrea said:**
> no, i don't want to use samba.

besides, that is from the pc to the linux box.

i want to go from the linux box to the pc.

in order to do that i need the linux box to join the microsft workgroup that the pc is in.

thanks,
kevin

As far as I know you only need to join the windows workgroup if you are using samba.

Ther are several ways to access the windows box. VPN is one, look at [OpenVPN](http://openvpn.net/howto.html).

Another is RDP via tsclient.

---

### Post by Dual Cortex on 2006-10-16
I may be one of the lucky ones... to access any other computers (Surprisingly) I simply go to Places>Computers>Go>Network> ...
If you are one of the lucky ones too, you might be able to see your windows computer.

---

### Post by kevinrea on 2006-10-17
yes, that did work..


thank you !!

kevin

---

### Post by Blood Red Sandman on 2006-10-17
> **bodhi.zazen said:**
> As far as I know you only need to join the windows workgroup if you are using samba. Dumb Question as I am new to ubuntu, but what is Samba?  And why would I want to use it?

Reason why I ask is that I am wanting to migrate over to Ubuntu. However my job requires that I still have a copy of Windows Xp on one of my home computers (Don't complain, they are providing the licenses)

---

### Post by cwaldbieser on 2006-10-17
> **Blood Red Sandman said:**
> Dumb Question as I am new to ubuntu, but what is Samba?  And why would I want to use it?

Reason why I ask is that I am wanting to migrate over to Ubuntu. However my job requires that I still have a copy of Windows Xp on one of my home computers (Don't complain, they are providing the licenses)

Samba is a suite of programs that let UNIX-like systems use Windows file sharing protocols.  In a nutshell, it means you can set up your Ubuntu box to be a file server, read shared folders from your Windows PC, or use a shared Windows printer.

---

### Post by gilesrsmith on 2006-10-22
Hi There

I have tried all of the above to access a windows workgroup from my linux laptop. 

I can see the workgroup through Places>Network Servers and i can see the other computers (winxp and a synology nas) but i can't view the folders in each computer. I get an error saying unable to display contents of this computer every time I try?

any ideas?

thanks

---

### Post by bodhi.zazen on 2006-10-22
Gotta ask, Did you set up your Windows boxes to allow teh connection?

[Windows RDC setup](http://www.microsoft.com/windowsxp/using/mobility/getstarted/remoteintro.mspx)

If so, What protocol are you trying to use?

---

### Post by gilesrsmith on 2006-10-22
I was trying to access shared folders on other xp machines from my dapper laptop, using the file browser. I can see the workgroup, and if i double click on that I can sometimes see all the other computers on the network, I can ftp to my nas fine, also vnc to all other machines, but I can't simply browse shared folders.

---

### Post by bodhi.zazen on 2006-10-22
Sorry, I did not see we went to page 2....

In that case, did you install samba (samba client to be exact)?

If so, open nautilus and type:```
smb://<windows_ip_address_or_share_name>
```

8-)

---

### Post by gilesrsmith on 2006-10-22
AHhhhhhhhh...

Thanks so much got it all working now cheers,

I am pretty new to linux so am always making the mistake of trying to find a windows style way of doing something

---

### Post by gilesrsmith on 2006-10-22
One more question, what happens if i need a username and password to logon?

I have a synology nas connected to a windows workgroup, 

if i use <smb://192.168.1.99> it times out cos i guess it is waiting for authorisation? however that works with all other machines on my network as they don't need authorisation

---

### Post by bodhi.zazen on 2006-10-22
> **gilesrsmith said:**
> One more question, what happens if i need a username and password to logon?

I have a synology nas connected to a windows workgroup, 

if i use <smb://192.168.1.99> it times out cos i guess it is waiting for authorisation? however that works with all other machines on my network as they don't need authorisation

See if this helps: [How to samba](http://www.linuxheadquarters.com/howto/networking/samba.shtml)

---

### Post by gilesrsmith on 2006-10-23
Thanks I got it all sorted now!

---

### Post by newrhyme on 2006-10-25
In addition...
SAMBA will allow Windows to access UNIX computers, as well as, the other way around: letting UNIX access Windows computers.

InMyHumbleOpinion: A Necessity for using any Windows components, on a UNIX-based network.:D 


> **cwaldbieser said:**
> Samba is a suite of programs that let UNIX-like systems use Windows file sharing protocols.  In a nutshell, it means you can set up your Ubuntu box to be a file server, read shared folders from your Windows PC, or use a shared Windows printer.

---

### Post by Ben Sprinkle on 2006-10-25
You don't need to join a workgroup. Linux can view all shared folders from windows without being on thier workgroup. :)

---

