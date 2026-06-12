---
title: "Network Printing from Win2000 just &quot;broke&quot;"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-01-14
Up until today I have been able to share my HL-5140 printer (using Ubuntu 6.10 and Network Printing from Win200 guidelines) with two WIN boxes through my network.  Now the WIN boxes refuse to recognize the printer.

Also -- the settings for Printers>Global Settings will now not accept the "Share Printers" designation.  I thought maybe something went wrong here, so I unchecked this setting but now can not re-check it to allow for sharing.  

Any ideas here.

The only changes made to this system have been to increase my screen resolution (don't think this should have effected the printer though).

Help -- this is a major obstacle to my desktop remaining in Linux when the family needs to print through this system.

](*,)

---

### Post by crispy_420 on 2007-01-15
Just a first thought, could this be a samba issue?

---

### Post by chaplanger on 2007-01-15
> **crispy_420 said:**
> Just a first thought, could this be a samba issue?

I don't know.  Samba is installed on my system.  How would I go about checking on Samba?

---

### Post by crispy_420 on 2007-01-15
Check for printers. They are in there somewhere. They are near the end of smb.conf (/etc/samba/smb.conf).

---

### Post by chaplanger on 2007-01-15
> **crispy_420 said:**
> Check for printers. They are in there somewhere. They are near the end of smb.conf (/etc/samba/smb.conf).

Here's what samba.conf shows:
-------------------------------
########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin
--------------------------------------------

Is this correct or should there be changes?

---

