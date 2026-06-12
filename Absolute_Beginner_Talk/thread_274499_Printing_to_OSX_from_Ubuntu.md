---
title: "Printing to OSX from Ubuntu"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by hovind on 2006-10-09
Hi everyone.
I'm a recent convert to Ubuntu after trying numerous other distros in my quest to rid my life of windows. I love it so far, with the only real challenge up to now being getting wireless up and running (which I finally was able to do).

These forums have been an enormous help, not only for solving problems as they arise, but for exploring Ubuntu generally and seeing what it is capable of.

Here's my new problem, though. I'm trying to set up network printing from my new Ubuntu laptop to my desktop running OSX 10.4.8. I was able to print to the Mac from Windows through SMB simply by browsing for the printer and installing a generic driver, but am unable either to browse for or directly link to the printer's location on the Mac. 

What is the simplest way of doing this? Am I missing an easy solution here?
I am able to access other SMB shares on the Mac, just not the printer.

Any insight from anyone here would be great. Thanks.

---

### Post by Mr Frosti on 2006-10-09
In order to share printers between computers, you will need the Samba packages for printer / file sharing. This can be easily installed by going into the "System -> Administration -> Shared Folders" and installing the packages that Ubuntu will prompt you for. Once this is done, you can add a Samba user by pasting the following code in a terminal and creating a password:

```
smbpasswd -a nobody
```

You can now connect to your machine's IP address by typing in "smb://<IP ADDRESS>". 

Username: nobody
Password: (the one you created above)

Double-click on the printer hosted on the Ubuntu machine and it should automatically install.

---

### Post by lemonsCC on 2006-10-09
Thanks Mr Frosti,

I wasn't trying to setup a printer but your code let me setup file sharing in my network!

Is it possible to access samba from the internet?  or is it a network only thing?

---

### Post by hovind on 2006-10-10
Thanks for your response Mr Frosti.
Correct me if I'm mistaken, but those instructions (I tried it, to no avail) appear to set up smb sharing to a printer if it was hosted on my Ubuntu machine.

What I am looking for is a way to use the printer hosted on my OSX box from the linux machine. 

Am I wrong? Did I do something incorrectly?

---

### Post by Mr Frosti on 2006-10-16
If OSX is hosting the printer, then Ubuntu should be able to map to it, in almost the same manner as Windows. Since printers are shared through the Samba protocol, you can browse to the IP address of the host, and double-click on the printer that should be displayed to add it. 

Alternately, you can go into System -> Printers, and go through the Printer installation manually. 

> Is it possible to access samba from the internet? or is it a network only thing?

Samba is a protocol, the same as HTTP is a protocol. You probably could access a Samba share over the Internet, except for 99.9% of all networks, and ISP will have Samba ports blocked to prevent this. So much for Windows making things easier...

---

