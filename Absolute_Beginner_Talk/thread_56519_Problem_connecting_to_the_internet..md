---
title: "Problem connecting to the internet."
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by grizzlefist on 2005-08-12
Hey everybody.

There are a few things I'm having problems with, and just a few general questions (I'll start off with just one, though).  I have a good amount of experience with Windows (nothing too technical, though), but none at all with Linux.

My problem is connecting to the internet.  I've read through various guides and searched through other people's posts in these forums seeking answers, but so far I've not met with success.

The general advice seemed to be 'use scanModem'.  I downloaded it, and used the Archive Manager to unpack it and run the program/script, but I couldn't make sense of the results.  Another post suggested that I look in Windows, in the control panel to find out what kind of modem I have.  This is what I found out.

  Lucent Win Modem
  PCI Slot 3 (PCI bus 0, device 10, function 0)
  Max port speed 11520.

  Driver version 8.28.0.0
    C:\windows\system32\drivers\ltmdmnt.sys
    C:\windows\system32\drivers\Modem.sys

From what I've read Win Modems are tricky to setup, and on top of that my ISP is AOL.  I've seen suggestions of using a program called 'penggy' to connect, so I downloaded a package with a red swirly (I think that means I don't have to compile it?) named "penggy_0.2.1-10_i386.deb", but I don't know what to do with it.

Another user, dfghost, [[link to his post]](http://ubuntuforums.org/showpost.php?p=125932&postcount=1), also had a Lucent Win Modem on COM 3, and it was suggested that he use the command "sudo modprobe lt_modem" to "load the lt_modem modules from linux-restricted-modules".  I did that, and there was no output/error, so I assume it worked fine.  The next step seems to be "put lt_serial and lt_modem in /etc/modules".  I found lt_serial and lt_modem, but there is no /etc/modules, and I cannot create a directory (most of the menu options are grayed out).

So, that's where I'm at right now.  Can someone help me with this?

---

### Post by PeP on 2005-08-12
for .deb files read this:
[http://ubuntuguide.org/#generalnotes](http://ubuntuguide.org/#generalnotes)
and this  
[http://ubuntuguide.org/#installuninstalldebfiles](http://ubuntuguide.org/#installuninstalldebfiles)

you do many task with few privileges (wich is often said to be good for security), to get root powah so that you can mess around in folders that are not in your home use sudo ...
read this again:
[http://ubuntuguide.org/#generalnotes](http://ubuntuguide.org/#generalnotes)

last but not least: /etc/modules is not supposed to be a directory but a file:
create/edit it by
sudo gedit /etc/modules
but give a try to this first:
man modules

---

### Post by grizzlefist on 2005-08-13
First off, thank you for replying so quickly.

The penggy package I had downloaded was apparently a newer package or something, and there was a problem depackaging it (one of the dependent libraries wasn't the latest revision, I guess), so I got a different version from packages.ubuntu.com, which worked fine.

After reading the manual for penggy, I edited penggy.cfg to the best of my knowledge, and also edited the files that contain usernames/passwords and numbers to dial.

Following that, I tried to connect using "sudo penggy", but I recieved an error saying that the modem couldn't be initialized.  Is this some sort of driver issue?  If so, where do I look in the scanModem results to find out which one(s) I need?

---

