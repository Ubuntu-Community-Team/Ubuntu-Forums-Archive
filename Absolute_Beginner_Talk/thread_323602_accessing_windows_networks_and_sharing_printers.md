---
title: "accessing windows networks and sharing printers"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by klauszlion on 2006-12-22
I have a network with several windows machines and two linux box with edgy eft but I'm not able to see neither the windows boxes in linux nor the opposite and am not able to access the printer I have in one of the linix boxes. Help?????

---

### Post by meng on 2006-12-22
Have you tried to access by IP address rather than hostname?

---

### Post by dbbolton on 2006-12-22
i might suggest samba ...

---

### Post by klauszlion on 2006-12-22
I'v installed samba and swat and when I install the network printer in windows it doesn't connect.

When I try to access the linux machines they ask me for a username and password I try every user I have on the linux machine and none enters...

---

### Post by jvc26 on 2006-12-22
Have you set up samba users and passwords as it may be asking for that rather than your username and password from the login.
Il

---

### Post by mcleaver on 2006-12-23
> **Illuvator said:**
> Have you set up samba users and passwords as it may be asking for that rather than your username and password from the login.
Il

How does one go about doing that? Do I need (to be) a Linux nerd to achieve this?

RGds

Martin

---

### Post by Scorpuk on 2006-12-23
here's a good guide to setting up a samba server:

[http://www.samba.netfirms.com/addusers.htm]("http://www.samba.netfirms.com/addusers.htm")

---

### Post by mcleaver on 2006-12-23
> **Scorpuk said:**
> here's a good guide to setting up a samba server:

[http://www.samba.netfirms.com/addusers.htm]("http://www.samba.netfirms.com/addusers.htm")

Thanks but it's way above my head. I just want to read and write to a windows server... I have no idea how to begin when I see all those lines in Smb.conf.
Another issue is thatm, when installing Xubuntu, I was asked for a user name and password, but not for a root password. Now everything I need to do at the terminal asks for a root password, but there is none. (My own password doesn't work.)
Martin

---

### Post by nsleiman on 2006-12-26
try 'sudo su' than 'passwd' 

it worked for me once!

---

### Post by theoldgit on 2006-12-26
to run stuff that needs root all you have to do is type "sudo" before the comand, when prompted for the password use yor usual password.

To try to get Samba working try webmin. [http://www.webmin.com/](http://www.webmin.com/) I fount it really goos especially with Ubuntu. I believe you can set up users with it too.

Hope this helps

---

### Post by klauszlion on 2006-12-26
I've been trying every book and guide to samba I can find but however am still unable to see either the linux machines from the windows nor the oposite, and I'm in need of using the printer I have installed in one of the linux machines   from the windows ones. I'm presently downloading the webmin tool to see If I'm able to acheive a conclusion to this problem.

---

### Post by klauszlion on 2006-12-26
Guys the light starts to appear at the end of the tunnel after using set of intructions I found on the linux cookbook I'm now able to see the entire network from all machines and access all the shares in it, however my problem with printing remains I can se and detect the printers but when I try to create the connection and it asks for the driver I install it its detects but doesn't  print.](*,)

---

