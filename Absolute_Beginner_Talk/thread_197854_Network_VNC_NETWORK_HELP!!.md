---
title: "Network /VNC/ NETWORK HELP!!"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by cowley on 2006-06-16
Hi, i am running a laptop and desktop with dapper.  i will be losing the monitor/keyboard off the desktop soon, so want to use it as a mass storage type device as the laptop only has a 40gb hard disk.   what i want to do is be able to access the disks on the desktop  from the laptop when i need to - sometimes i will leave the desktop off.  i also will want to be able to control the desktop via vnc (or whatever is easiest) so i can run updates etc.  any help/advice would be gretaly appreciated!

thanks

simon

---

### Post by pt4117 on 2006-06-16
You can just turn on Remote Desktop.  
System> Preferences >Remote Desktop
Also, since you won't have a keyboard/monitor you will probably want to have it auto login, or enable remote login.  With remote desktop turned on you can VNC into the computer through pretty much any vnc viewer.  

Just one warning, I have seen some computers that have a bios setting that stop it from booting without a keyboard attached.

---

### Post by cowley on 2006-06-16
Hi, thanks

i have had no luck with that - maybe someone can guide me in the right direction.  i have set the remote up and where it says the user has to type this command it says this:
vncviewer localhost:0
this is for the desktop computer

when i type that command into terminal on the laptop it opens up multiple windows of the desktop of the laptop - not the desktop from the desktop pc!!  (did u get that!?)

when i try viewing the laptop on the desktop i have to type:
vncviewer cowley-laptop:0

this is the output

cowley@cowley-desktop:~$ vncviewer cowley-laptop:0
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Couldn't convert 'cowley-laptop' to host address
Unable to connect to VNC server
cowley@cowley-desktop:~$


help please!!

thanks

simon

---

### Post by cowley on 2006-06-16
Right - the firewall firestarter was causing probs so hav removed it, but to use remote desktop i have to use the phsical ip address to connect - not the commands as given in the remote menu - ie:

vncviewer 192.168.1.123:0 instead of vncviewer cowley-laptop:0

any views?

thanks

simon

---

### Post by uteck on 2006-06-16
Make sure the desktop has a static IP, otherwise if it changes you can't login.
You can add the IP and name to /etc/hosts then you can use the name to connect.

You can configure firestarter to let vnc through or just open port 5900.

---

### Post by rccharles on 2006-06-16
[QUOTE=cowley]to use remote desktop i have to use the phsical ip address to connect - not the commands as given in the remote menu - ie:

vncviewer 192.168.1.123:0 instead of vncviewer cowley-laptop:0

[/QUOTE]
Your system needs to know the what ip address cowley-laptop translates to. Normally, a DNS server does the translation. 

You can setup your own translations by adding definitions to the file:
/etc/hosts

Here is an example hosts file:
127.0.0.1	  localhost
192.168.1.10	foo.mydomain.org  foo
192.168.1.13	bar.mydomain.org  bar
216.234.231.5	master.debian.org      master
205.230.163.103 [www.opensource.org](www.opensource.org)

Here is the format of the file:
IP_address canonical_hostname aliases

In your case, it would be:
192.168.1.123    cowley-laptop.mylan.org  cowley

I am not sure a dash - is allowed.  I am confused by your choice of alias names.  Wouldn't you want cowley-desktop instead of cowley-laptop?

for more details:
man hosts

Robert
:)

---

### Post by cowley on 2006-06-16
how do i make the computers have a static ip address within my lan?  i have an inventel wanadoo livebox.

thanks

simon

---

