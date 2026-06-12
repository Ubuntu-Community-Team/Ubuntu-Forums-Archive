---
title: "[SOLVED] CUPS Dapper, an HP printer and lots of macs"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by dckirba on 2008-01-31
Hey guys,

A couple of us at office are trying to set up a printer to share. 

We have a bunch of macs at one end of our office and the other end is wondows pcs. We're trying to set up a HP p2015 printer on the mac end using a computer running Dapper.

We've gone through a few threads here. Printer works fine from the Dapper system, but we can't share it. We're having trouble sharing the file sharing folder as well.

This is what we've done so far to try and get the printer to work:

Editted the File: /etc/cups/cups.d/ports.conf to this:

```
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
```

However, no jobs get through both from a mac or a windows machine. We added the printer as an ipp printer, installed the driver... 

We think it might be a problem with permissions, but not sure how to change them. One post said to go to system>administration>printing and enable sharing under global settings, but that's not available on dapper.

Another question,
How do you log into the CUPS interface. It asks for a username and password when adding or removing printers, but the sudo password doesn't work.

Also, Dapper is using an older version of HPLIP There is no specific driver for the p2015, but the printer works well with the HP plus driver. Should I upgrade to a new version of HPLIP?

I think that's it for now. Thanks a ton,

Cheers,
David K

---

### Post by bvmou on 2008-01-31
Does the print server built in to the printer allow you to give it jobs from the network?  A printer of that quality typically does, just by plugging it into the network via its ethernet jack.  There should even be a web interface to it.

One thing I know you can do is something like this:  get root access to the print server, whether via ssh or at the computer's terminal.  Use w3m or a browser to open [https://localhost:631](https://localhost:631) .  I think you may have to give the CUPS username as 'root' rather than another sudoer.  Enable the relevant sharing options, I just enable everything which may not be the securest option ;)  You can print a test page from that interface.

For Macs the main network tool is bonjour; I think it is a dependency of some parts of 'foomatic', which you probably installed already.  In any case do an 'apt-cache search bonjour' and see if there are packages that look relevant.

For windows I once followed this tutorial and it worked fine:  [http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876]("http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876") , though it was a bit overkill for my limited windows needs.

Again, in all likelihood you can just plug the printer into your network and go to the built in web interface.  Check the documentation for something like 'HP Jetdirect Fast Ethernet print server'.

---

### Post by tr333 on 2008-01-31
> **bvmou said:**
> I think you may have to give the CUPS username as 'root' rather than another sudoer.

I have always just used my regular login account username as it has sudo permissions.  Doing this seems to work ok for me.

A quick search of the Ubuntu Wiki found this:  [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
It seems to have information on using Ubuntu as a print server and getting windows/mac computers to print to it.

---

### Post by dckirba on 2008-01-31
Thank you both for the quick replies :)

The old printer we had did have jetdirect, but unfortunately not this one. We looked for one with an ethernet jack, but these are currently not available here, and so admin went with this one. :(

I followed some advice on the wiki and am now able to log onto the CUPS interface. However, I've been sitting here all afternoon trying to download updated HPLIP drivers and I don't know if it has anything to do with the AU summit, but connections are sooooooo slow today :)

But here's my plan for the next few hours, let me know if I'm on the right track.

1. Install new HPLIP so that I actually have Laserjet P2015 on the menu and not just Laserjet Plus.
2. Log into CUPS and add printer
3. Enable sharing in CUPS
4. Add IPP printer on mac

Thanks again and I'll keep you posted on progress :)

Cheers,
David

---

### Post by bvmou on 2008-01-31
That sounds about right.  Also - I think your internet problems may have something to do with this undersea cable failure: [http://www.redherring.com/Home/23633]("http://www.redherring.com/Home/23633")

Good luck and let us know how it turns out

---

### Post by dckirba on 2008-02-01
Thanks a ton guys, it works now :) I kept track of posts that I used along the way so here they are in case someone runs across the same blocks.

```
**to enable CUPS listening on port 631**
[http://ubuntuforums.org/showthread.php?t=268245&highlight=sharing+printers]("http://ubuntuforums.org/showthread.php?t=268245&highlight=sharing+printers")

**to log into cups:**
[https://help.ubuntu.com/community/PrintingCupsWebInterface]("https://help.ubuntu.com/community/PrintingCupsWebInterface")

**for updated HP drivers for linux:**
[http://hplip.sourceforge.net/downloads.html]("http://hplip.sourceforge.net/downloads.html")

**to install HP drivers:**
To use the self-extracting file, follow these steps:
Download the file to a convenient location (e.g., home directory or desktop, etc).
Open a console/terminal and cd to the download directory.
Type in and run this command: 'sh hplip-2.7.12.run'

**for dapper install of hp printers:**
[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper]("https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper")

**help for printers**
[https://help.ubuntu.com/community/Printers]("https://help.ubuntu.com/community/Printers")

**set up on mac**
[https://help.ubuntu.com/community/NetworkPrintingFromMacOSX]("https://help.ubuntu.com/community/NetworkPrintingFromMacOSX")

```

Now to figure out why file sharing isn't working ;)

Cheers!

---

