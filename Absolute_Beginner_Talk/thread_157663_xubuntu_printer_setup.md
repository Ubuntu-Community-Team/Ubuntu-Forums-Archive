---
title: "xubuntu printer setup"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by threegremlins on 2006-04-09
I've switched over to xubuntu from ubuntu because of my machine and am having problems setting up the my printer epson c40ux on a usb port and/or my even more ancient epson lq1070+ps2. it was easy on ubuntu but can't find anything to set it up in the menu. I'll try setting it up through command line if some one can tell me how or even better tell me which program I can synaptify my xubuntu system into letting me set either of them up.

---

### Post by threegremlins on 2006-04-12
Okee dokee, found a good tool.
if your as linux challenged as I am and need to set up your printer
goto

[http://localhost:631/admin](http://localhost:631/admin)

many many thanks to those who developed the website

---

### Post by jhuff on 2006-04-23
What did you use for a User Name and Password?

---

### Post by 3rdalbum on 2006-04-24
It's not a website, it's just an HTML-based frontend for CUPS. But I agree, it's pretty good :-)

---

### Post by threegremlins on 2006-05-05
removed inaccurate post

---

### Post by threegremlins on 2006-05-14
I recently downloaded the xubuntu fight7 iso and installed it. I thought I had the printer setup figured out, BUZZT Wrong! So I have to apologize to jhuff. When I tried [http://localhost:631/admin](http://localhost:631/admin), I was presented with the a popup asking for account and password, no matter what or how often I tried it refused to accept. I have to wonder what I did before so that it let me use it on previous times. So clicking on links and even joining the group, on the home page of the web interface it says(they must have snuck it in while I wasn't looking).

"Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing). /usr/share/doc/cupsys/README.Debian.gz describes the details and how to reenable it again."

So I gksudoed thunar, iknew I would eventually have to and found myself at /usr/share/cupsys and found this,
---------------------
readme.txt (only showing the important bits here)

    SETTING UP PRINTER QUEUES USING YOUR WEB BROWSER

    CUPS 1.2 includes a web-based administration tool that allows
    you to manage printers, classes, and jobs on your server. 
    Open the following URL in your browser to access the printer
    administration tools:

    [http://localhost:631/admin/](http://localhost:631/admin/)

    DO NOT use the hostname for your machine - it will not work
    with the default CUPS configuration.  To enable
    administration access on other addresses, check the "Allow
    Remote Administration" box and click on the "Change Settings"
    button.

    You will be asked for the administration password (root or
    any other user in the sys/system/root group on your system)
    when performing any administrative function.
-------------------------------------
and this in readme.debian (both these are tarzipped by the way)

 -   Administration over the web interface is disabled by default since it
     requires the CUPS daemon to be able to read /etc/shadow.  If you want to
     enable web administration with shadow passwords (authentication type
     'basic'), put the user cupsys into group shadow by

     adduser cupsys shadow

     as root.

     Only users who are in group 'lpadmin' can administrate printers (using
     gnome-cups-manager, lpadmin or any other frontend but the web
     interface).  To allow printer administration to user joe, put him into
     this group by executing

     adduser joe lpadmin

     (again as root).
----------------------------------------
I tried the commands and discovered my user name was already in lpadmin, going back to the interface I was still denied access by the popup. I didn't know what to do about "type 'basic'" is that setting the shadow passwords to basic, is it a command option? I clicked on the help icon in the menu and found some skimpy explanation about xfprint4 and the went to the XFCE website looking for more and found they hadn't much of anyhting else to offer. So this had to be a debian problem and went to the Ubuntu website and scrounged around there and found something at this address.
"  [https://wiki.ubuntu.com/NetworkPrintingWithUbuntu](https://wiki.ubuntu.com/NetworkPrintingWithUbuntu)  "
I opened /etc/cups/cupsd.conf, the files or structure weren't the same as the sample file at the website so I had no clue what or how to change anything but I gave it a try and headed back the to the web interface with still no luck.
----------------------------------------
This is my /etc/cups/cupsd.conf file
    #   Sample configuration file for the Common UNIX Printing System (CUPS)
    #   scheduler.  See "man cupsd.conf" for a complete description of this
    #   file.
    #

    # Log general information in error_log - change "info" to "debug" for
    # troubleshooting...
    LogLevel warning

    # Administrator user group...
    SystemGroup lpadmin

    # Only listen for connections from the local machine.
    # These settings are configured in /etc/cups/cups.d/ports.conf so that
    # changing them does not require to change this file.
    # Listen localhost:631
    # Listen /var/run/cups/cups.sock

    # Show shared printers on the local network.
    # The 'Browsing' setting is configurhttps://wiki.ubuntu.com/NetworkPrintingWithUbuntued         in /etc/cups/cups.d/browse.conf
    # so that changing it does not require to change this file.
    # Browsing Off
    BrowseOrder allow,deny
    BrowseAllow @LOCAL
    BrowseAddress @LOCAL
    
    # Default authentication type, when authentication is required...
    DefaultAuthType Basic
    
    # Restrict access to the server...
    <Location />
      Order allow,deny
      Allow localhost
    </Location>
    
    # Restrict access to the admin pages...
    <Location /admin>
      Order allow,deny
      Allow localhost
    </Location>
    
    # Restrict access to configuration files...
    <Location /admin/conf>
      AuthType Basic
      Require user @SYSTEM
      Order allow,deny
      Allow localhost
    </Location>
    
    # Set the default printer/job policies...
    <Policy default>
      # Job-related operations must be done by the owner or an adminstrator...
      <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes         Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job         Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
        Require user @OWNER @SYSTEM
        Order deny,allow
      </Limit>
    
      # All administration operations require an adminstrator to authenticate...
      <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer         Pause-    Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer         Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After         CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs             CUPS-Reject-Jobs CUPS-Set-    Default>
        AuthType Basic
        Require user @SYSTEM
        Order deny,allow
      </Limit>

      # Only the owner or an administrator can cancel or authenticate a job...
      <Limit Cancel-Job CUPS-Authenticate-Job>
        Require user @OWNER @SYSTEM
        Order deny,allow
      </Limit>
    
      <Limit All>
        Order deny,allow
      </Limit>
    </Policy>
    
    # Include files in /etc/cups/conf.d
    Include /etc/cups/cups.d/ports.conf
    Include /etc/cups/cups.d/browse.conf
    
    #
    #
-------------------------------------------
To me the above file is gobbledygook but I had tried, I deleted the file I changed and repalced it with the backup file I made. Then not having any success with it before but still determined to fire up the printer, I installed gnome-cups-manager and set up my printer that way. It went fine but when I tried printing a test with abiword nothing. In menu/accessories/print dialogue there was an icon but no text and in the print que there was no job to print. So I think part of the problem is with the xfprint4 program itself, the XFCE website says it should recognize a printer setup with any application. I tried going with the command line and started reading about lpadmin, cupsenable, adduser but those options to me are somewhat vague if you haven't spent alot of time with them, so I wasn't any closer to a solution. I thought if XFCE doesn't recognize it but the gnome cups manager has installed it and can print a test page from the manager, would it run with a different window manager. Back to synaptic, install a window manager, gdm doesn't show it, find xfce.desktop make new *.desktop, logout, log into new window manager session, launch mousepad, type "this is a test" and select file/print and the damn thing printed. logout, log into XFCE session launch abiword type "this is a test" and it printed too in XFCE. Okay it's a solution to my printer problem but a poor one at best, because firing it up the next day into an XFCE session, nothing. Is there anyone who can tell me how to enable web interface, how to change the cupsd.conf file and if I even should, point me to a more easily understandable manual on command lines. If you do I'll make a tutorial a monkey could follow and publish it somewhere, where it will be easy to find.

---

### Post by graemenunn on 2006-05-27
Hi there... this is my first post so hopefully it will be helpful!

I have just jumped through these hoops so hopefully it will work for you.
The documentation is at : file:///usr/share/xubuntu-docs/desktopguide/C/printer-configuration.html

Basically you have to add cupsys to the shadow group and then restart cupsys

If you can't get at the help files then the instructions are:

Printer Configuration with the Browser

First, you will need to enable the web administration interface of CUPS (Common UNIX Printing System).

   1.Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups
   2. Select the group shadow and click Properties.
   3. Add the user cupsys to the group.
   4. Restart CUPS with this command:

      $sudo /etc/init.d/cupsys restart

Next, visit the web interface by entering [http://localhost:631/admin](http://localhost:631/admin) in your browser's location bar. Once there, you will be able to see, install, and configure the detected printers on your system. 

Hope this helps
Graeme

---

### Post by jis on 2006-06-22
Nice posting, Graeme. 

I think the printer setup is way too complicated and confusing for the average absolute beginner in XUbuntu. IMO there should be a way to setup printers through Settings -> Printing System Settings dialog or otherwise through menus. (Maybe the HTML-based frontend for CUPS could be launched from the dialog.)

---

### Post by rokky on 2006-06-22
Great instructions, Graeme!   I had no clue (never had to deal with CUPS quite so directly before in other distros).   jis has it right - this is way too complicated, especially when compared to Edubuntu 5.10's setup (should have been about same as "stock" Ubuntu 5.10).  HUGE step backwards.  

I got the cutesy web GUI working, but test pages just show a few random garbage characters.  Apparently the drivers for a rather common HP LaserJet 5 are not included, and I need to re-discover how to find/install an appropriate PPD file - ugh!

Rokky

---

