---
title: "CUPS hangs my system -- Ubuntu 7.10"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Lorin Ricker on 2007-12-31
Just started doing some serious (non-test-page) printing today, mostly printing some Mozilla Forum pages on moving my Tbird email folder/profiles from W to Ubuntu 7.10 (Compaq desktop PC, AMD Athlon CPU, 64MB, two IDE disks, dual boot Ubuntu & W2K) --

Problem is, printing seems to hang my system at unpredictable and non-repeatable times... I've had Ubuntu up for many many days now, trying things out and getting myself educated.  Only today did I really start printing anything in earnest -- and that marks "the only thing that changed" in my config or use-habits so far.

So -- I'm printing a couple of jobs OK to HP LaserJet 2300d, connected via USB port... a few pages of duplex print OK from Mozilla Forum (in Firefox 2.0.0.11)... then bang!  I've had two describable symptoms so far:

1) My terminal screen went completely black (like something stomped on video memory?).  Nothing I could do seemed to recover the display -- although it "felt like" Ubuntu was still up behind a black screen.

2) Cold restart after 1 above -- went back to web pages to finish grabbing a couple of pages... surfing okay, did a couple more page-prints... and again: bang!  But this time, screen didn't die/blank-black, instead entire system seemed to freeze.  Although I could move my mouse cursor ok, I could not recapture focus or control over anything.  Dead Edgy, from everything I could tell -- and no means of regaining control, other than another cold restart.

Oh, and one other thing -- after each restart, the LaserPrinter queue is "stopped", and I have to re-Enable it from the Printer Admin applet.

OK, looking around on this Forum, I see lots of (older) posts about how CUPS is (apparently) buggy, leads to crashes and hangs, etc. -- But so far, I've found nothing which either helps me understand what to do about this, or how to even start understanding what's really going on. :confused:

This thread [System Hangs (uBuntu 7.04 Server AMD64)]("http://ubuntuforums.org/showthread.php?t=466374") gives a vague hint that Ubuntu can throw hardware errors on AMD CPUs, but this gives no practical guidance or fixes... I thought Linux & Ubuntu were solid on AMD as well as Intel???

I'd appreciate any guidance or ideas, even on what "under the covers" stuff to look for or at.  Is printing really this bad on Ubuntu/Linux?

TIA -- Lorin

---

### Post by spiderbatdad on 2007-12-31
Is printing really this bad on Ubuntu/Linux?  Yes. you can thank the manufacturers for using proprietary drivers.  Although HP is generally compatible. Your issue seems like a configuration problem.  You might post your cupsd.conf so someone can analyse it.

---

### Post by Lorin Ricker on 2008-01-01
> You might post your cupsd.conf so someone can analyse it.

OK, here's my /etc/cups/cupsd.conf --

```

#
#
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
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
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

#
#
```

My original installation of Ubuntu (from the Alternate Desktop CD v7.10) seems to have figured all this out on its own -- found my HP 2300d printer, and did this config as part of the installation.  On the advice from another thread, I did define a PDF-pseudo-printer, although I don't see any of that in the above...

I bet I'll learn something here... TIA.

---

### Post by Lorin Ricker on 2008-01-01
And to save someone the trouble of asking ( :) ), here's my /etc/cups/printers.conf --

```

# Printer configuration file for CUPS v1.3.2
# Written by cupsd on 2007-12-31 13:53
<DefaultPrinter hp_LaserJet_2300_series>
Info Hewlett-Packard hp LaserJet 2300 series
DeviceURI hp:/usb/hp_LaserJet_2300_series?serial=CNBFB11606
State Idle
StateTime 1199134420
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option sides two-sided-long-edge
Option page-right 18
Option scaling 109
</Printer>
<Printer PDF_file_generator>
Info PDFprinter
Location pony
DeviceURI cups-pdf:/
State Idle
StateTime 1199053582
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option sides two-sided-long-edge
</Printer>

```

---

### Post by Lorin Ricker on 2008-01-01
Aha... It's not what I thought.  Some forum searching led me to this very long thread, [feisty fawn freeze ! driving me insane]("http://ubuntuforums.org/showthread.php?t=412125&page=28"), esp. post #822 ( p.28 ) and #544 ( p.19 ), which seem most relevant.

My system-hangs, as originally described above, seem to be a widely-shared and highly frustrating experience -- my symptoms match those described in "ff freeze!..." exactly.  So, I'll conclude this thread by noting that my initial hunch of something being wrong with CUPS itself is *wrong*, a bad guess.  More likely, I'm seeing the same behaviors re: Firefox, kernel boot settings, and/or interrupt processing (the best explanation for "it happens randomly and unpredictably") as what's documented there.

I'll apply the fix-suggestions in #822 first (the easiest, and seems to be most obvious), and then, if that doesn't fully fix the problem, I'll try #544, and I'll post results here.

Problem is, with a problem like this, it's kind'a like the futile attempt to" prove a negative" -- how do we really know that it's resolved, won't happen again (for this build/config)???

And where's the official Ubuntu Support Team (Canonical) on this whole issue???!!! Seems like it's nearly a show-stopper, yet I cannot find any trace of them being aware of this problem in the above-ref'd thread.  Are they working on fixing this system-hang definitively -- and letting us all know that they've done so, and what the problem actually, finally was?  After reading "The Official Ubuntu Book (2nd ed.)", with all it's brave talk about Support and The Community, I'm a little shaken by all of this -- looks to me like the Community works hard (e.g., this Forum), but where in the heck is the Official Support?:confused:

I'm really hoping for Ubuntu to deliver Reliability and Stability to my SOHO PCs, where Windoze never could (or can)... I'm not trying to be negative or critical here -- just trying to get my bearings.  Perhaps some more experienced voices and viewpoints will respond here to help calibrate me? :confused:

TIA -- I'm in Ubuntu for the long-haul, even with this problem! :)

---

