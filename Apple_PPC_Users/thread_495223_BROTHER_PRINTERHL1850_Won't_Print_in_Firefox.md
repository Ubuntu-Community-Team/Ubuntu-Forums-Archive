---
title: "BROTHER PRINTERHL1850 Won't Print in Firefox"
date: 2007-07-07
forum: Apple PPC Users
---

### Post by dtownsend on 2007-07-07
I have Brother Printer HL1850 which will not print in Firefox on my iMac PPC G3.  Am using OS X Version 10.4.9. Cannot change printer designation from "Generic Post Script". Has anyone else had this problem?  How to fix??

---

### Post by Tommy on 2007-07-19
> **dtownsend said:**
> I have Brother Printer HL1850 which will not print in Firefox on my iMac PPC G3.  Am using OS X Version 10.4.9. Cannot change printer designation from "Generic Post Script". Has anyone else had this problem?  How to fix??

That designation just means you don't have the PPD for the printer. You should be able to start the installation from scratch and get the correct PPD. See the entry about your printer at linuxprinting.org:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1850](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1850)

If your problem is with OS X you might get some more assistance at an Apple support forum. While OS X uses CUPS (like Ubuntu), Apple "hides" CUPS's functionality in a different way.

P.S.: I used to have an older PostScript Level 2 printer that wouldn't print in Firefox. It printed a strange little error and nothing else. The solution was to add a little bit of PostScript code when printing to make it work like a Level 1 printer. I found the code by printing to a PS file and opening it in a text editor. The special code was embedded in the file but wasn't being invoked. This theoretically should not apply to yours but if the problem persists you might explore it -- but check the printer settings and reset to defaults first.

---

