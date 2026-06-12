---
title: "Print from Ubuntu to printer on Win XP mach"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by 3rdgear on 2006-07-22
I have just installed Ubuntu on one of several machines on my home network. All the other machines run Windows XP. 
My HP Officejet printer is installed on a Windows XP mach. I would like to be able to print to that printer.
I have installed the HPlip driver on my ubuntu machine, and have installed my printer as a network printer.
When I send a print job to my printer, the printer shows "printing" and the job stays stuck in the print queue on the windows machine.](*,) ](*,) 

I have tried to search the forums for info, many I see want to print from windows xp to ubuntu. 

Any help?

---

### Post by OU812 on 2006-07-23
I'm looking at the linux cookbook right now. I'll writed what it says.

1. install printers on win boxes and share them as you would normally.
2. make sure the guest account is enabled, make sure everyone has permission to print from shared printer.
3. install cups from samba server.
4. configure cups for samba.
sudo ln -s 'which smbspool' /usr/lib/cups/backend/smb
5. create a printers share in smb.conf on samba server.
[printers]
 comment = All Printers
 printing = cups
 printcap name = cups

Restart samba afte editing smb.conf

6. install windows printers on samba server with cups. open cups with [http://localhost:631/admin)](http://localhost:631/admin)). log in as root. click add printer, then the printer name. Enter location and description, go to next window, click on drop down menu, scroll to bottom, select windows printer via samba. In next window device uri for [printer name] enter the device rui.(This part I'll directly quote)

"Alps" (printer name) is connected to powerpc on windows 2000, so you must enter the "guest" username and hostname: smb://guest@powerpc/alps. In the next 2 windows, select the printer driver.

7. Print test page from server. go to linux client and open cups web interface. If it worked, the printer will appear. Print test page from linux client.

john

---

### Post by 3rdgear on 2006-07-23
Thank you for the reply and info. I am still new enough to linux that I am not sure what exactly to do with the smb.conf file.  When I pull it up, there are alot of lines that I believe are commented out. (start with #)

The actual lines you have given me under "printers" do not exist, but many more do exist.  Am I to add the lines you show me, and ignore what is there already???

3rdgear
:-k

---

### Post by OU812 on 2006-07-23
Yes. Add the lines.

john

---

