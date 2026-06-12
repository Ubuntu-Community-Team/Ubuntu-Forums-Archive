---
title: "HPLIP installation"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by indie56 on 2007-04-06
Hello
I have downloaded the Auto Installer to my desktop frrom HPLIP. [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)
The next step is to move this file to /home/username/ directory. How do I do it? What are the terminal commands and thereafter I have to run "sh hplip-1.7.3.run" Again how to do this? 
I have no idea of terminal commands. Pl help
Thanks

---

### Post by SOULRiDER on 2007-04-06
To move a file just type:

```
mv <original file> <where you want ti to be moved>
```

---

### Post by johnc4510 on 2007-04-06
Is there a reason why you need to use a slightly newer version of what is already in the repositories?

---

### Post by indie56 on 2007-04-06
I bought a HP 5610 a few days back and also installed 6.06. I read some where taht full functionality of this all in one can be obtained by installing from HPLIP.
Can you please tell me more. I do not have the faintest idea and am only good for click, drag and drop
Thanks

---

### Post by johnc4510 on 2007-04-06
hplip is in the repository which will install it automatically. First, open Synaptic package mgr.  System>Administration>Synaptic Package Mgr.
Then hunt for hplip. All the apps are listed alphabetically. Right click on it and choose install. Then click on Apply on the tool bar. This will install the version of hplip that is taylored for Ubuntu and will also install any dependencies automatically.

---

### Post by indie56 on 2007-04-06
Done. I have connected the printer to the computer. how do I set up the printer
Thanks

---

### Post by johnc4510 on 2007-04-06
System>Administration>Printing

Click on add new printer and follow instructions

Here is a web site with some basics to help get you started on a few things:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Welcome to the community

---

### Post by indie56 on 2007-04-06
Thanks. Printer and scanner works. What program should I use for faxing from computer?

---

### Post by johnc4510 on 2007-04-06
Don't really know, I've never set up a fax before. Try a forum search for fax or your specific fax printer.

---

### Post by deanjm1963 on 2007-04-06
I'm not sure about this, but I also have an HP printer/scanner and if you use the HPLIP Toolbox there is an option to send a fax.

To install the toolbox, open up synaptic again and search for hplip, right click on hplip and cursor down to Mark Suggested for Installation. HPLIP Toolbox needs python-qt3 to work.

Once installed open up Alacarte, and under Administration there is an entry for HPLIP Toolbox, you just need to "check" it for it to appear in your System>Administration menu.

Hope this helps.

---

### Post by indie56 on 2007-04-06
What is Alacarte?

---

### Post by deanjm1963 on 2007-04-06
Alacarte allows you edit your gnome menus, might be called Menu Editor under Applications>Accessories.

---

### Post by indie56 on 2007-04-07
Hello
I did as indicated in the above posts. I get a message USE CUPS WEB INTERFACE.
Please help
Thanks

---

### Post by 11hjpphty76lkjj on 2007-04-09
If you installed hplip from synaptic that will usually work.  However you may want to remove hplip from your system and install the latest from [http://hplip.sf.net](http://hplip.sf.net).

Then the hp-setup application will run after the install and will configure your system for printer, scanning and faxing.

You could also try running hp-setup from a terminal window.  If you get bad command you may want to consider updating to the lastest from the website above.

Then to fax run hp-toolbox and click the fax icon.

A

---

