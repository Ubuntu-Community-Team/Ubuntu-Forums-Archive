---
title: "Networked Printer? &lt;hair pull&gt;"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by khardbored on 2007-06-02
Hi again! Seems I only post here when I have issues. Sniff.

HP PSC 1310 on an XP machine. I can see the XP machine from this machine. I just can't figure  out, for the life of me, how to get the printer setup on my end. When I do menu/system/admin/printer and choose to add a network printer via Windows, it asks me for a password? I enter the password I use for this machine...but then nothing. It doesnt show networked printer or even the network that its on...ideas?

---

### Post by chamberlain2006 on 2007-06-02
I believe that you have to use a username/password on the computer that you're connecting to.  Also, you must make sure that you have a driver for the printer.  I'm not sure if your printer is supported or not, guess you'll know soon enough.

---

### Post by khardbored on 2007-06-02
> **chamberlain2006 said:**
> I believe that you have to use a username/password on the computer that you're connecting to.  Also, you must make sure that you have a driver for the printer.  I'm not sure if your printer is supported or not, guess you'll know soon enough.

The XP machine that I'm connecting to never required a username/password before? Should I create a new user on the XP machine and use that info?

---

### Post by zek725 on 2007-06-02
> **khardbored said:**
> Hi again! Seems I only post here when I have issues. Sniff.

HP PSC 1310 on an XP machine. I can see the XP machine from this machine. I just can't figure  out, for the life of me, how to get the printer setup on my end. When I do menu/system/admin/printer and choose to add a network printer via Windows, it asks me for a password? I enter the password I use for this machine...but then nothing. It doesnt show networked printer or even the network that its on...ideas?

have you properly configured your Samba network?

---

### Post by khardbored on 2007-06-02
Aw man, I need samba setup for this? If thats the case, I'll just give up now. Samba scares khardbored :(
khardbored has no idea what to do...

---

### Post by zek725 on 2007-06-02
> **chamberlain2006 said:**
> Also, you must make sure that you have a driver for the printer.  I'm not sure if your printer is supported or not, guess you'll know soon enough.

the printer is supported. i have the same printer (hp psc 1315) hosted in a XP machine. first of all, i configured Samba to access (read,write) Windows computers then added the printer. 

To print successfully, biderectional support must be disabled in the XP printer *server*.

---

### Post by zek725 on 2007-06-02
> **khardbored said:**
> Samba scares khardbored :(
khardbored has no idea what to do...

do not be. it will be easy to [configure samba.]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by khardbored on 2007-06-02
I disabled bidirectional on the XP machine. Now, configuring Samba to see this machine...thoughts?

---

### Post by zek725 on 2007-06-02
> **khardbored said:**
> I disabled bidirectional on the XP machine. Now, configuring Samba to see this machine...thoughts?

carry on. you're going in the right direction. 

here's a helpful link for installing hp printers. 
[http://ubuntuforums.org/showthread.php?t=184838&highlight=howto+network+printer](http://ubuntuforums.org/showthread.php?t=184838&highlight=howto+network+printer)
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_via_samba](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_print_on_remote_Ubuntu_machine_via_samba)

---

### Post by khardbored on 2007-06-02
I tried running that installer and that didn't work out too well. I'm going to see what I can do with samba, more greek though...erg.

---

### Post by pappapump on 2007-06-02
First, you need to enable sharing on the XP printer.
You do this from the printer settings folder in XP, Right click and choose share.
Then It asks you for a name for the share, so name it.
Now when you go to your Ubuntu PC and try to access the printer the default is usually no password, just hit enter.
If that don't work THEN you can make a password for windows from the administration icon in control panel, or use the users icon which looks like 2 people close together.
By default a windows PC with this same setup will want you to either install files from the host machine or you will be prompted to download the files from the internet.
In the Case of ubuntu setups you can simply find the printer in your shares and click it then do the basic configure from there.
Mine showed up as a HP 3740, I clicked the add printer icon in Ubuntu and found it listed then just used the suggested drivers.
Bear in mind though, that I'm hardwired, not wireless.

---

### Post by khardbored on 2007-06-03
I got it working. I thought it wasn't listed in add printer but I looked harder and there it was. Printed a test page and viola. Im the smartest man alive!!!!!!!!!!!!

---

