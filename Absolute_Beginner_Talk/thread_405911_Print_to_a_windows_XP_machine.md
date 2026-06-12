---
title: "Print to a windows XP machine"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by reality_hunter on 2007-04-10
I am hoping someone here will assist me because after about 10-15 hours of work..i am ready to give up :

==================================================
printer: KONICA MINOLTA magicolor 2430DL (using USB)
*this is setup as a shared printer and can also print from a 3rd box(laptop)

also using a D-LINK wire/wireless router
==================================================

I recently installed UBUNTU edgy 6.10 on my HP and that is the only operating system on that machine. I have learned a lot from this forum and the starter guide since I am not that much familiar with the commands and all that but I will be hopefully soon.

anyways the problem is printing on my windows XP machine from my UBUNTU. Before I goon further I think its important that I should mention one MAIN problem that I think could be preventing me from printing, but i am not sure if thats what it is. The main problem I think is:
* On UBUNTU, when I click on add printers and go through the steps and click apply, I DONOT see a printer added on the printer dialog box that is open. I have tried many time , rebooting and all that, but nothing and cannot find the answer anywhere why this might be.
* This was not the case when I had first newly installed UBUNTU because that time going thru the process of adding printer, I was able to add a printer and it would show on the printer section. BUT now this does not happen. PLEASE ADVICE as to what to do.

Also, In the process described , I have one more question. setup procedure:
1) add printer
2)choose network printer --> chooose "SMB"
3) *after choosing SMB, there is a popup asking me username and password. Sometimes it asks 2 times and sometimes it asks for three times and sometimes just once. I will mention what it asks for next:
(i) please enter the login for the "192.168.xxx.xx1" (this is the IP for the windows
computer)
(ii) please enter the login for the "CHIMPI" (this is the name of the windows computer)
(iii) please enter the login for the "username-desktop" (name of the UBUNTU desktop)
(I do have a username and password setup on my windows machine)
I have tried with and without the passwords but nothing. It would be informative to know what and why it is asking. PLEASE also advice whether to leave these fields blank or not.
4) at HOST: I put "192.168.xxx.xx1"
5) printer: I put the shared name for the printer "KONlaser"
6) *this username and password feild is automatically filled up by the LAST Username and Password entered from the popup, BUT either way, this should be the username and password for the UBUNTU......is this correct?
7)clicking NEXT, I can choose the manufacturer and next I can see the exact printer MODEL listed from the list and by selecting that ...clicking next and then apply.

this procedure used to add a printer and now it does not. PLEASE kindly help.

Also, I should mention that the firewall on the windows doesnot seem to be the problem because I had just setup a network drive between the 2 computers and I have more than 150GB of HD space on that network drive that is installed on UBUNTU but can be accessed as a network drive from the windows.
Also, just to be sure -- how do i properly find the IP address of my UBUNTU? because I have noticed that from the network config it displays the IPv4 address or somthing, but from my router configuration setting....it is "192.168.xxx.xx0" ("which I am guessing is the correct one")

sorry about making the thread so long (this is my *edit post), I will learn.
thanks for the taking the time to read this and thanks for helping out

---

### Post by thefoolisme on 2007-04-10
Did you try adding a printer by choosing a CUPS network printer, and searching for it that way?  

Incidently, don't know whether you have this yet or not, but the linux drivers for your printer can be found here if not on the list:

[http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#drivers](http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#drivers)

Lucky for you too.  There aren't any linux drivers for my Canon MF4150  :-(

---

### Post by reality_hunter on 2007-04-10
but why isn't SMB be able to add a printer?? I have the exact same model number listed when ask for choosing the driver and yet i dont see a printer added and its far from printing yet....

---

### Post by dstew on 2007-04-10
Just to be clear, the printer is being shared on a Windows network, correct? That is, the printer is not connected to your network directly, but only through the Windows box, right? If so, you would use Samba. Can you access shared folders on the Windows box through Samba?

---

### Post by reality_hunter on 2007-04-10
> **dstew said:**
> Just to be clear, the printer is being shared on a Windows network, correct? That is, the printer is not connected to your network directly, but only through the Windows box, right? If so, you would use Samba. Can you access shared folders on the Windows box through Samba?

hi dstew,
the printer is connected to my windows machine through a USB and is setup as a shared printer, which I can access from my two other windows computer in the home network. Therefore, I guess I would use Samba.
I dont know how to access the shared folders on the windows-printer box from my UBUNTU machine, but I did setup the network drive between these two computer---meaning that the hard drive of my UBUNTU can be seen on my windows box as a network drive and I can shard/access  files back and forth within that drive on my windows and within that shared folder on my UBUNTU.  So access is not a problem.

---

### Post by dstew on 2007-04-10
I have Xubuntu Dapper 6.06, so when I set up my shared printer I used the CUPS administration tool, which is a local web site at [http://localhost:631](http://localhost:631). When I used that to set up my shared printer, I used the printer name smb://MARYS/Printer2 (my wife Mary's computer name, and the shared printer name.) I did not use any IP addresses.

Once the CUPS printer administration tool knew the name of the printer, I was able to install a driver from the list, and it worked after that. I don't know if I will be able to help you further, since you have a different installation, but you might see if the CUPS printer administration tool is there.

You can access Windows shared folders using smbmount //server/share /media/Windows_share. It is just like the regular mount command, but you use smbmount instead. I think it acts just like mount -t smbfs. You can read about it on the Samba man pages (man samba).

---

### Post by reality_hunter on 2007-04-10
> **dstew said:**
> I have Xubuntu Dapper 6.06, so when I set up my shared printer I used the CUPS administration tool, which is a local web site at [http://localhost:631](http://localhost:631). When I used that to set up my shared printer, I used the printer name smb://MARYS/Printer2 (my wife Mary's computer name, and the shared printer name.) I did not use any IP addresses.

Once the CUPS printer administration tool knew the name of the printer, I was able to install a driver from the list, and it worked after that. I don't know if I will be able to help you further, since you have a different installation, but you might see if the CUPS printer administration tool is there.

You can access Windows shared folders using smbmount //server/share /media/Windows_share. It is just like the regular mount command, but you use smbmount instead. I think it acts just like mount -t smbfs. You can read about it on the Samba man pages (man samba).

:guitar:  got it working , thanks for the help man.
What I had to do was run the printing utility (apparently there was 2 of them) and the new printer utility was what i used to create a 
"smb:///COMP_NAME/SHARE_PRINTER_NAME" file and click apply and i am guessing that it added this into the system somewhere and after this I went to cups and add printers and entered "smb:///CHIMPI/KONlaser" as a url and it worked like a charm.
thanks again for helping out

---

