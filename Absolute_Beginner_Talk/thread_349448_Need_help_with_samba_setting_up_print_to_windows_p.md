---
title: "Need help with samba setting up print to windows printer"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Jim Rogers on 2007-01-30
Using the GUI, System/Adrministration/Printing I installed a printer on Ubuntu. This printer is an Epso Stylus Color 2200 and is located as a shared printer on an HP Laptop.

The GUI printer setup found the host and found the printer. But no amount of coaching will get a single line of print on the windows printer. The firewall on my Windows machine never sees a request for access, and nothing shows up in the Windowws printer's queue. I get a partial message on the Ubuntu print queue after what a ppears to be a timeout. 

I opened up the Samba .conf file and made sure the Workgroup is the same.
a few additonal settings I either examined and left, or changed(*)
    win support = no
   *wins server = 192.168.1.100            this is the hp laptop the printer is attached to.
    dns proxy = no
   *name resolve order lmhost host wins bcast
   NETWORKING
  * interfaces = 192.168.1.101 ra0        This machine that I wish to print from
   PRINTING
   *load printers = yes

In a howto book "Ubuntu Unleashed" a statement is made that the Windows printer must have a username and password for Samba to work. As near as I can tell, attempting to follow the books instructions, I do not have that option for a Windows shared printer.

Any help or suggestions would be appreciated

---

### Post by Jim Rogers on 2007-01-30
Added note.

         smbclient -L HP-LAPTOP does not list any printer.

Wow, the only person replaying is me. No Samba gurus out there?

---

### Post by jkeyes0 on 2007-01-30
What happens if you disable your windows firewall and try again? I know the built-in XP firewall is a bit tricky when it comes to... well... anything trying to connect.

---

### Post by Jim Rogers on 2007-01-30
No change really. Actually I am using McAfee which alerts me to any request for "service" and then you allow the request or not. I long ago tired of Windows' firewall problems and have not used it for some time.

There is a great deal of information out there to do exactly what I am wishing to do. I am just too new to the environment to understand/implement what some suggest. 

I am seriously considering a print server on my network. For $69.95 it could not be any cheaper, but when I was having problems with my Linksys Wireless network, I was advised to buy something else, but toughed it out and now it works great, so sorta would like to master this task as well because you learn so much.

Retired Sr. Systems Analysts can be dangerous you know. unfortunately my experience was not on Linux/Unix.

Thank you so much for you response.

---

### Post by Jim Rogers on 2007-01-30
SOLVED ----- painlessly..

Googled the solution:
    FORGET SAMBA!!!!
    On the Windows machine:
          Open Control Panel/Add Remove Programs
          Click on Add Windows Components
              Select and Add "Other Network Print Services"
    On the Ubuntu Linux machine
          System/Administration/Printin
                Add new printer
                    Choose Network Printer
                         Choose Unix LPD Printer
                             The host name is the ip address of the Windows XP machine
                             the Queue name is the shared printer name (entered on the Window machine)
Thank you gunnyman posted on May 8, 2006.
You sir, have made my day
SOLVED SOLVED SOLVED

---

### Post by mdsmedia on 2007-01-30
Thanks Jim,

I've been going to dive into this myself, but never got around to it. I installed Samba some time back but have reinstalled Dapper since and just haven't got round to network printing or even reinstalling the printer, as yet.

Your step by step should at least get me up and running if I have Windows running on the dektop (printer host machine). Or it will give me some clues on where to look.

I just loved this smilie so much I had to include it :) :guitar:

---

### Post by Alabaster on 2007-01-31
Kick ***

Worked first time.

UBUNTU IS ALL ALL POWERFULL

Mwah hahahaha:twisted:

---

### Post by Alabaster on 2007-03-20
Hmmm.... worked first time then never worked again.....

Doesn´t give me an error message, just doesn´t ever print.....

Anyone?

---

