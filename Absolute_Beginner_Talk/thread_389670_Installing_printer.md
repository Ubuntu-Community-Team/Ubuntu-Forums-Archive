---
title: "Installing printer"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by theRevMom on 2007-03-21
[FONT=Arial][COLOR=Black]I've been trying to install my printer with no success.  I have a HP PSC 2410 USB, all in one printer, scanner, fax, copier.  

First I tried to add the printer through the Applications>System Tools>Printers Foomatic-gui for Add a printer. But the USB printers are not listed. 

So I went to System>Printing  and it couldn't locate CUPS.
ERROR: The CUPS server could not be contacted.

So I followed the step by step directions [here]("http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation") but CUPS does not open to give me the install options. 

I have the HP tar.gz downloaded. I attempted to install it with the Package Manager, but it came up with errors too:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/home/carly/hplip-1.7.2/ui/setupform.py", line 215, in showPage
    self.updatePPDPage()
  File "/home/carly/hplip-1.7.2/ui/setupform.py", line 477, in updatePPDPage
    ppds = cups.getSystemPPDs()
  File "/home/carly/hplip-1.7.2/prnt/cups.py", line 194, in getSystemPPDs
    major, minor, patch = getVersionTuple()
  File "/home/carly/hplip-1.7.2/prnt/cups.py", line 406, in getVersionTuple
    return cupsext.getVersionTuple()
NameError: global name 'cupsext' is not defined




URGGGG....[/COLOR][/FONT]

---

### Post by h0ax on 2007-03-21
Hey there - 
I have the exact same printer, however -> I had zero problems installing it with the System->Administration-> Printers
+add printer
(then it reads from database)
Then it's self explanatory

Are you having problems getting to this screen?

---

### Post by h0ax on 2007-03-21
Hey there - 
I have the exact same printer, however -> I had zero problems installing it with the System->Administration-> Printers
+add printer
(then it reads from database)
Then it's self explanatory

Are you having problems getting to this screen?

If the problem is cups not running you could run 

```
ps ax | grep cups
```
to see what is listed
here's what I have: (you can start these things up and then try again)
> 
gnome-cups-icon --sm-client-id default3
/usr/sbin/cupsd
gnome-cups-manager


Are you using Gnome?

---

### Post by theRevMom on 2007-03-21
No, I can't get that window.... try as I might.  I do not have a Sytem -> Administration -> Printers option.  I have only a Printing option.  that opens CUPS.  But the printer is not there.

Here's what I get when I enter your suggestion:

root@carly-kitchen:/home/carly# ps ax | grep cups
 5612 ?        Ss     0:00 /usr/sbin/cupsd
 5777 pts/0    S+     0:00 grep cups

---

### Post by h0ax on 2007-03-21
Are you using Ubuntu default GNOME window manager?

Why are you logged in as root?

The CUPS daemon is running, which is good - exit from root and run the ps ax | grep cups again - see if it's different.

---

### Post by h0ax on 2007-03-21
also - what happens if you run 
```
 gnome-cups-manager 
```
? Does it pop up as before?

---

### Post by theRevMom on 2007-03-21
ps ax | grep cups  gives me the same result again. 

[FONT=monospace]gnome-cups-manager pops up the CUPS window with nothing in it.
 Go figure.  

Here's a snag: I can scan into the GIMP.  But I can't find the printer, let alone print to it!
[/FONT]

---

### Post by theRevMom on 2007-03-21
[COLOR=Black]I rebooted and found the printer in System -> Administration -> Printing.  I added it.  I still could not get a print from it.  

So now, could it be I have a permissions problem?  When I installed the drivers, I was logged in as root (the directions at the Linuxprinting.org HowTo).  Could this cause a problem?

And, more important, how do I fix this? 

Edit:  i checked into permissions and followed the steps in [this post]("http://www.ubuntuforums.org/showthread.php?t=385231&highlight=permission+printer")

So now the permission things look right.  But the printer info box now shows this error:

"Ready: /usr/lib/cups/filter/foomatic-rip failed"

Suggestions?


Edit:  12:03 a.m. 22 March:

I uninstalled everything.  I reinstalled Everything.  I went through the linuxfoundation directions again.  the results have me steaming:  it still won't print.  I can scan.  I can fax from the computer.  I cannot print.  

The printer properties say the machine is ready. When I send anything to the printer (hit print or print a test page), the print manager window shows the printer is stopped.  It won't go.  


Somebody, PLEASE help me with this.  I've put in 4 very long nights trying to get this to work and I HAVE to have a printer.

Anyone?


[/COLOR]

---

### Post by theRevMom on 2007-03-22
bump....

and an update.  I changed the permissions of the usb0 file and it no longer hangs on "printer stopped."  

Now it says that the printer is not connected..... 

Hello?

---

### Post by theRevMom on 2007-03-22
bump

Has anyone a clue about this?

---

### Post by 11hjpphty76lkjj on 2007-03-23
Rather than using the gnome printer configuration please use HPLIP.

[http://hplip.sf.net](http://hplip.sf.net)

If you need any other help let me know.  The automatic installer is tested extensively with ubuntu, as well as there is a manual install process for ubuntu if you should have any problems.

---

### Post by theRevMom on 2007-03-23
Kalosaurusrex!! Thank you so very much!  I had the file already on the computer from that very site, but I missed the directions.  I'd downloaded the tar file and attempted a manual install.

Now, with your guidance, IT WORKS!!  Thank you

---

### Post by 11hjpphty76lkjj on 2007-03-23
Awesome. Glad to hear it :)

Happy Ubuntu'ing!

---

