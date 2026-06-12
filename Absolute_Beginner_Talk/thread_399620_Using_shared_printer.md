---
title: "Using shared printer"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-04-02
I wonder if there is a way for me to connect to a printer that is on a computer within my network that is running XP.

---

### Post by StarscreamD on 2007-04-02
Sure, run XP. I doubt those networks are going to jive together, and if they do it would be a miracle. Good luck!

---

### Post by rubbsdecvik on 2007-04-02
There sure is.

If you hit System->Administration->Printing.

You can then add a new printer.  Select Network Printer then select Windows Printer.

From there you can enter the host name (network name of your XP Machine) and the name of your printer.

You can also usually surf the network and add it graphically (i think).  you can do this by  hitting Places -> Network.  Then select Windows Network, and find your machine.  On your XP machine your printer should show up.  There should be some way to add it that way.

---

### Post by dstew on 2007-04-02
Yes, you can use the shared printer. You use the Samba program in Linux to communicate with the XP computer network, which can share files, folders and printers. You have to set up the XP computer first the share the printer, then use the Linux printer management software CUPS to create the printer. Since you need to use Samba to communicate with the Windows network, the printer name needs to start with smb. I share a computer that is plugged into my wife's XP desktop, and it has the name smb://MARYS/printer2. MARYS is the name of my wifes computer on the windows network (server name) and the name of the shared printer is printer2.

To install Samba, if it is not already installed, use the Add/Remove programs or Synaptic. CUPS I think is already installed. If you use Ubuntu, I think you have a Print Manager front end that you can use. If you have Xubuntu, you need to use the web-page printer manager for CUPS at [http://localhost:631](http://localhost:631)

EDIT: I see from the other posts that maybe you don't need Samba if you have Edgy.

---

### Post by Liam1964 on 2007-04-02
Funny thing is, I have virually no experience of Ubuntu. I have only one machine running Ubuntu, and five others running XP. My network "jives" really well, share printers no issues, share folders etc. I am amazed at StarscreamD's response.

All I did was add a network printer and it just worked. Maybe I am not the person to tell you how to do it, but I can tell you it can be done.

---

### Post by dstew on 2007-04-02
Liam1964, is your printer a network printer or a Windows shared printer? Do you have Edgy, Dapper, or Feisty?

---

