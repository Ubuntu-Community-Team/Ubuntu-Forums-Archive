---
title: "How To Network Windows &amp; Ubuntu?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-06-23
Well I've been grunting and poking at Ubuntu with a figurative sharp stick...

New to this whole Linux thing, but I've made some progress.  (I tried it years ago, a friend installed it on a machine for me and I never figured anything out.  It's going much better this time.)


So I've got this nice home network running Windows (when it's running).  The Ubuntu machine was born onto the network fully able to recognize and access the shared resources there.  Color me thrilled.

I just have two problems:  First, I can't figure out how to access anything on the Ubuntu box from XP, and second, the network printer seems to be invisible to Ubuntu.


I made a new folder in my Home folder, labeled it "Test" and stuffed a nondescript txt file into it.  Then I right-clicked it, said I wanted to share it, and when prompted I installed Samba and smb(?).  I was then able to see the Ubuntu machine from my XP machine (though it was in MSHOME instead of the workgroup I have my other machines on), but when I clicked on the Ubuntu machine it demanded a username and password.

All I could think of is the single username and password the Ubuntu computer has, which was refused.


Here's what I want:  I want to be able to put a second (and perhaps third) hard drive into the Ubuntu machine, then use that/those drive(s) for storage for both that machine and other machines on the network.

I searched all through the documentation and saw a bunch of stuff about servers and messing with configuration files and typing things into the terminal...

I'm a Linux infant.  I'm figuring things out, but it's hard to get used to after dealing with more than a decade of Microsloth.  If there's an "Easy Guide to Linux/Windows Networking for Windows Morons" file out there, please point me to it.  If not, please walk me through the steps I need to do.


Also, don't forget the printer.  It's an HP PSC 1410 All-In-One.  I don't care at all about Ubuntu using the scanner or anything of that sort on it, I just want to be able to print from Ubuntu, through the network, and out the printer (which is currently attached to a Windows XP machine).

---

### Post by cwmoser on 2007-06-23
As far as being able to share Ubuntu folders and printers to other Windows computers, use the application called Samba.  Samba allows you to network those folders to windows PC's.

Check this out:

Ref:
[http://www.debuntu.org/guest-file-sharing-with-samba](http://www.debuntu.org/guest-file-sharing-with-samba)

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)


You will have to edit a config file like similar to this:

$ sudo vi /etc/samba/smb.conf


workgoup = CWMOSER 
interfaces = lo eth0 
bind interfaces only = true 
security = share 
guest account = nobody 
load printers = yes 
printing = cups 
printcap name = cups 


[MAXTOR] 
  path = /media/MAXTOR 
  browseable = yes 
  read only = no 
;or writable = yes 
  guest ok = yes 

[HOME] 
  path = /home/carl 
  browseable = yes 
  read only = no 
  guest ok = yes 

[C-DRIVE] 
  path = /media/sda1 
  browseable = yes 
  ;read only = no 
  writable = yes 
  guest ok = yes 



[printers] 
  comment = All Printers 
  browseable = no 
  path = /tmp 
  printable = yes 
  guest ok = yes 
  public = yes 
  writable = no 
  create mode = 0700 
  printer admin = root 



[print$] 
  comment = Printer Drivers 
  path = /var/lib/samba/printers 
  browseable = yes 
  read only = yes 
  guest ok = yes 
  write list = root 


Then restart Samba to reflect the changes:

$ sudo /etc/init.d/samba restart

I use Samba to network Ubuntu folders to Windows PCs and also to my vmware virtual Windows XP.

Carl

---

### Post by Spektyr on 2007-06-24
Fantastic, that's got the computers talking to each other beautifully.  Thanks a lot!

Now... the printer.

I haven't been able to get Global Settings to detect LAN Printers (in the System - Administration - Printing window).  I tried manually entering a New Printer.  I put in the network name of the computer it's attached to (XP machine) and the shared name of the printer.  Then I select the printer from the list.

The printer is an HP PSC 1410, so the closest thing on the list is the HP PSC 1400.  According to HP, the Windows drivers are the same between the two.  But here's where I get confused.

The driver recommended is "hpijs".  There's a button labeled "Install Driver", but I can't tell if that is to install a different driver or the one that's listed as recommended.  Whatever the case, if I click on that button it tells me to pick a PPD file, and I have no clue what it wants.

It will, let me click "Forward" and move on to the next step.  I'm not sure if I even have a driver installed at this point.  Then I can click "Apply" and the printer shows up in the Printers window and says that it's ready.


If I tell the printer to print a test page, the printer powers up, makes some "I'm getting ready to do something" noises, and then flashes the power button repeatedly as though something was wrong.  The document to be printed gets stuck in the queue on my XP machine and won't delete (or let any other printed documents continue on to the printer) until I reboot Windows and delete it.

Ideas?

---

### Post by UltraMathMan on 2007-06-24
To get my Ubuntu laptop to print through my XP machine I needed to install **Print Services for Unix** in Windows. This can be installed by going to Control Panel -> Add/Remove Programs -> Add/Remove Windows Components -> and checking "Other Network File and Print Services". 

-Hope this helps :)

---

### Post by Spektyr on 2007-06-24
> **UltraMathMan said:**
> To get my Ubuntu laptop to print through my XP machine I needed to install **Print Services for Unix** in Windows. This can be installed by going to Control Panel -> Add/Remove Programs -> Add/Remove Windows Components -> and checking "Other Network File and Print Services". 

-Hope this helps :)

I did that and I'm still getting the same thing.  I tried deleting and reinstalling the printer, but every time I send a test page the printer warms up and stalls, leaving the document jammed in the buffer until I reboot the XP box.

I just thought of this... does Linux have a problem with a space in the shared name of a printer?

---

### Post by joeldi on 2008-02-29
I'm having the exact same problem, so BUMP

I'll add that the same printer with the same drivers works if I plug it into my laptop directly

---

### Post by joeldi on 2008-03-06
bump.

---

### Post by Squish on 2008-07-14
Bumppetty bump

---

