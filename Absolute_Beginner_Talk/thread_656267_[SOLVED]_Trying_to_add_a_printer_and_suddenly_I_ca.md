---
title: "[SOLVED] Trying to add a printer and suddenly I can't"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-01-02
I have an HP Photosmart connected to a small office network that I was able to print to just fine a few days ago. This morning I tried to print a few things without success. Because it was so easy to add a printer before I just deleted the printer intending to add it again but now I can't seem to get the system to see the printer. As far as I can tell nothing has been changed with the office network and the other computers (all XP and Vista) all seem to work just fine.

I go to system> Administration> Printing> New Printer> Windows Printer via SAMBA> Browse and nothing comes up. All the computers are connected to the same wired Microtek router and all have internet access working fine.

---

### Post by dburnett77 on 2008-01-02
Yeah, might want to re-install the gdi interface.  Or a complete OS install, again.

These things are known to happen from someone "accidentaly" correcting pre-input.

:)(:<<== wink.

---

### Post by boriquajake on 2008-01-02
> **dburnett77 said:**
> Yeah, might want to re-install the gdi interface.  Or a complete OS install, again.

These things are known to happen from someone "accidentaly" correcting pre-input.

:)(:<<== wink.

Wow, I have no idea what you mean :-)

What is the GDI interface and how do I re-install it? I don't want to even contemplate the other option.

---

### Post by boriquajake on 2008-01-02
> **dburnett77 said:**
> 
These things are known to happen from someone "accidentaly" correcting pre-input.

:)(:<<== wink.

What sort of things could I have messed with pre-input? It would be cool if I didn't make the same mistake again.

---

### Post by boriquajake on 2008-01-02
Wow, I hate to bump this so fast, it is just that this is pretty urgent. If anyone can help me out I will be extremely grateful.

---

### Post by ARhere on 2008-01-02
I have no idea what "dburnett77" was talking about but I will try to help.

Is it connected via USB to one of the PC's on the network?  Or does it have its own RJ-45 connection?  (*that means it plugs into your network switch*)

**IF** it is plugged into a USB, then trying to "find" another printer may not work because the PC already knows about the current USB printer (*it will come up as the same USB device name each time in the hardware list.*).  Check your cups setup file and delete any references to your printer, reboot, and reinstall the printer.

I will step you though it the hard way so you learn.

1. Open your terminal

2. Goto the cups directory
```
cd /etc/cups
```

3. List the files, you should see "cupsd.conf"
```
ls -cl
```

4. backup your current config file, just to be safe!
```
sudo cp cupsd.conf cupsd.conf.old
```

5.  Open "cupsd.conf" with an editor and delete any reference to your current printer.
```
sudo gedit cupsd.conf
```

6.  Save the file, reboot, then reinstall you printer.

Make sure your printer is not plugged in when you do this!

-AR

---

### Post by boriquajake on 2008-01-02
I had already deleted the old printer. Anyway, I am going to show you my results of following these steps as I understand them.

After this:
```
cd /etc/cups
```

I go this:

> /etc/cups$

After this:
```
ls -cl
```

I got this:
> total 76
-rw------- 1 root lp     82 2007-12-18 11:41 classes.conf
-rw-r--r-- 1 root root 1651 2008-01-02 12:13 cupsd.conf
-rw-r--r-- 1 root root 2545 2007-12-15 11:46 cupsd.conf.default
-rw-r--r-- 1 root root 1662 2008-01-02 12:13 cupsd.conf.O
-rw-r--r-- 1 root root 1651 2008-01-02 13:18 cupsd.conf.old
-rw-r--r-- 1 root root 8817 2007-12-15 11:46 cups-pdf.conf
-rw-r--r-- 1 root root 4409 2007-12-15 11:46 mime.convs
-rw-r--r-- 1 root root 6184 2007-12-15 11:46 mime.types
drwxr-xr-x 2 root lp   4096 2008-01-02 12:11 ppd
-rw------- 1 root lp     84 2008-01-02 12:11 printers.conf
-rw------- 1 root lp    375 2008-01-02 12:11 printers.conf.O
-rw-r--r-- 1 root root  242 2007-12-15 11:46 raw.convs
-rw-r--r-- 1 root root  213 2007-12-15 11:46 raw.types
-rw-r--r-- 1 root root  181 2007-12-15 11:46 snmp.conf
drwx------ 2 root lp   4096 2007-12-15 16:04 ssl
jake@jake-crappy-lenovo:/etc/cups$ 

I never saw any reference to my printer and so I didn't bother to back anything up because I didn't see anything to delete but I will paste what came up when I did the next step anyway.


> LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

I know it must be frustrating to try to help someone like me but I do appreciate it.

---

### Post by boriquajake on 2008-01-02
Once again I know that bumping this thread so soon is bad form but I am in a real bind here. :confused

---

### Post by ARhere on 2008-01-02
LMAO... no problem.

Now check your printers config file
```
sudo gedit /etc/cups/printers.conf
```

I also noticed a "[color=blue]printers.conf.O[/color]" file.  It might be the back up the system made before you made changes.

Try that!

-AR

---

### Post by boriquajake on 2008-01-02
> **ARhere said:**
> LMAO... no problem.

Now check your printers config file
```
sudo gedit /etc/cups/printers.conf
```

I also noticed a "[color=blue]printers.conf.O[/color]" file.  It might be the back up the system made before you made changes.

Try that!

-AR

OK, the results of that are:

```
# Printer configuration file for CUPS v1.3.2
# Written by cupsd on 2008-01-02 12:11
```

---

### Post by LowSky on 2008-01-02
if you have cups installed got to your web browser and type ```
http://localhost:631
```

that should let you set up any networked printers

also if its an hp make shure hplip-gui is installed, you can use that as well to manage network printers

---

### Post by boriquajake on 2008-01-02
> **ARhere said:**
> LMAO... no problem.

Now check your printers config file
```
sudo gedit /etc/cups/printers.conf
```

I also noticed a "[color=blue]printers.conf.O[/color]" file.  It might be the back up the system made before you made changes.

Try that!

-AR

Now I am all kinds of paranoid. What changes did I make? Do you mean when I deleted the printer that wasn't working?

---

### Post by boriquajake on 2008-01-02
> **LowSky said:**
> if you have cups installed got to your web browser and type ```
http://localhost:631
```

that should let you set up any networked printers

also if its an hp make shure hplip-gui is installed, you can use that as well to manage network printers

I tried that but I don't seem to have accomplished anything.

Wow, this is really weird. This printer worked for a month at least and then I went away for a few days and suddenly my computer can no longer see it. When I first installed it I didn't do anything with the browser, I just went to administration and followed the steps. What did I do wrong?

---

### Post by LowSky on 2008-01-02
did you loose power or anythin while away. Sometimes when that happens the printer grabs a new IP address.

try using HPLIP - this should work
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by boriquajake on 2008-01-02
> **LowSky said:**
> did you loose power or anythin while away. Sometimes when that happens the printer grabs a new IP address.

try using HPLIP - this should work
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

Installing HPLIP seemed to work just fine but I ran into a problem at the end because the printer is not connected directly to this computer. I need to be able to print to a printer that is connected to one of the other PCs in this office. Originally this was practically effortless. I just went into system>administration> Printing> New Printer> Windows Printer Via SAMBA> browse and the system found the printers connected to computers in the little workgroup. Now when I do that no printers are available.

---

### Post by ARhere on 2008-01-02
> **boriquajake said:**
> I go to system> Administration> Printing> New Printer> Windows Printer via SAMBA> Browse and nothing comes up. All the computers are connected to the same wired Microtek router and all have internet access working fine.

Wait a minute.... are you trying to access a printer connected directly to the PC you are using?  Or are you trying to access a printer shared by another PC through the network?  If you are doing the later, then I think I know what the issue might be, but I need more info.

Please take a moment and describe exactly what you are trying to do, it will make this debugging task easier.

-AR

---

### Post by boriquajake on 2008-01-02
> **ARhere said:**
> Wait a minute.... are you trying to access a printer connected directly to the PC you are using?  Or are you trying to access a printer shared by another PC through the network?  If you are doing the later, then I think I know what the issue might be, but I need more info.

Please take a moment and describe exactly what you are trying to do, it will make this debugging task easier.

-AR

I need to be able to print to a printer that is connected to another PC on in our office. All the other PCs in the office print to a printer that is connected directly to just one of the PCs. Up until today I was able to do the same but for some reason now I can't.

I appreciate your taking the time to work on this. Please let me know what additional info I can provide to make this easier. :-)

---

### Post by ARhere on 2008-01-02
> **boriquajake said:**
> ... I need to be able to print to a printer that is connected to one of the other PCs in this office. Originally this was practically effortless. I just went into system>administration> Printing> New Printer> Windows Printer Via SAMBA> browse and the system found the printers connected to computers in the little workgroup. Now when I do that no printers are available.

AH!!!! I bet I know what is wrong!  When you add a printer attached to another machine across the network, it will use the current IP address.  If you are using a Default Ubuntu install, the default network setup is DHCP.  When the IP is renewed (*changed*) you will not be able to use the printer anymore because the host address changed!  

You need to make the IP of the machine sharing the printer static.  I already went through this pain.  Uninstall the network applet you see on the top right hand of the task bar.  This conflicts with your ifconfig if you try to set your IP to static.

I am at work and don't have my Ubuntu machine in front of me.  Search these forums for steps on setting a static IP (for the machine with the printer) and try what I said.  If you get stuck I will step through it with you tonight.

-AR

---

### Post by boriquajake on 2008-01-02
> **ARhere said:**
> AH!!!! I bet I know what is wrong!  When you add a printer attached to another machine across the network, it will use the current IP address.  If you are using a Default Ubuntu install, the default network setup is DHCP.  When the IP is renewed (*changed*) you will not be able to use the printer anymore because the host address changed!  

You need to make the IP of the machine sharing the printer static.  I already went through this pain.  Uninstall the network applet you see on the top right hand of the task bar.  This conflicts with your ifconfig if you try to set your IP to static.

I am at work and don't have my Ubuntu machine in front of me.  Search these forums for steps on setting a static IP (for the machine with the printer) and try what I said.  If you get stuck I will step through it with you tonight.

-AR

The first time I set up this up I was able to see the entire workgroup in the office. Then I clicked on the PC that I knew had the printer and there is was. Now when I hit browse I don't seem to see the other PCs at all. This makes me wonder if it isn't something more.

---

### Post by ARhere on 2008-01-02
> **boriquajake said:**
> The first time I set up this up I was able to see the entire workgroup in the office. Then I clicked on the PC that I knew had the printer and there is was. Now when I hit browse I don't seem to see the other PCs at all. This makes me wonder if it isn't something more.

Yeah, sounds more like a network issue.

1.  Check to make sure the IP is static on the print server. (*the PC with the printer*)
2.  Check to see if you can ping the PC, or any other.
```
ping <host_ip>
```
3.  If it is a Linksys router or equivalent that you are using as a switch, reset it by unplugging it for 5 seconds.

-AR

---

### Post by ARhere on 2008-01-03
Did you solve your problem?  If so, please mark this as [solved].

Thanks,
-AR

---

