---
title: "Home Networking"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Hygelac on 2006-03-25
I've got four computers hooked-up through a router for internet access.  What is the best way for me to create a network so that I can transfer files between them?  :-k  There are two wireless Kubuntu notebooks (one old, one new), one old Kubuntu desktop, and one fairly new WinXP desktop.  Does someone have some good information on how to do this (for example, should I use FTP; and if so, how)?  It is most important for me to be able to transfer files between the Kubuntu machines; I hope to soon have the WinXP be one of them...  ;)

---

### Post by John.Michael.Kane on 2006-03-25
this is for linux to linux networking
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html) 
[http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)

This is for linux to windows 
[http://www.oreilly.com/catalog/samba/chapter/book/index.html](http://www.oreilly.com/catalog/samba/chapter/book/index.html)
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)


Hope this helps

---

### Post by Hygelac on 2006-03-25
Thanks for those links; I now have a working NFS network between the three Kubuntu computers!  \\:D/  Tommorow I'll try to get Samba running.

---

### Post by Hygelac on 2006-04-01
Now Samba works too!  The hardest thing was figuring out how to get the WinXP machine to respond to a ping from another computer (I had to disable its firewall and antivirus, which means that I also had to switch-off the DSL modem to be safe); after that it was all relatively simple.  If I have lots of time on my hands later I'll try to get a nicer Samba set-up going.  Again, thanks for the links.

---

### Post by localzuk on 2006-04-01
You shouldn't need to turn off your firewall - just make an exception to allow samba (port 445) traffic through -that is unless you are using ZoneAlarm (I have had to deal with this program a lot and it *does not* like windows networking/fileshares for some reason...)

---

### Post by Hygelac on 2006-04-01
Oh dear; I am using ZoneAlarm. :mad:

---

### Post by jamesr on 2006-04-01
I am posting this message from a system that is running ZoneAlarm (free) without any problems. This system is part of a house intranet which includes  a file server running breezy as a server with Samba so that I share files on a common directory (the file server will be replacing a NT fileserver once finished). I am currently not having any problems. So what type of problems did you see.

---

### Post by localzuk on 2006-04-02
The problems I always saw were completely random. Generally, however, no matter what you provided as an 'exception' (port, application etc...) file sharing was just not allowed to work - authentication would fail, sometimes network browsing would fail and others.

---

### Post by BarFly on 2006-04-02
I can't get Samba to work either.  I want to connect to a Windows machine.  Everytime I go to Places-Network Servers, it will not let me log in with the password.  The same thing happens if I try to access the Ubuntu computer from the Windows computer.  I must have set it up wrong (I am very new to Linux).  Can I just uninstall it and try again?  If so, how?  I cannot even figure out where it installed Samba.

---

### Post by localzuk on 2006-04-02
Try running the command (on the linux box) ```
sudo smbpasswd user
``` replacing user with the user you want to be able to log in to samba shares on that box from windows. It will prompt you for a password.

I am not sure about the other way round.

---

### Post by BarFly on 2006-04-02
Thanks a bunch!  The thought did occur to me that I was using the wrong password, but I didn't think I could be that stupid.  One less troublesome item in my list of problems in switching to Linux after using Windows for years.

---

### Post by Hygelac on 2006-04-17
It works now.  I told ZoneAlarm that the Samba server was in the 'Trusted Zone' and set the security of that zone to medium.  I can now ping and share files between the server and client.  Next, to see if these new firewall settings compromised the security of the client... :rolleyes:

---

