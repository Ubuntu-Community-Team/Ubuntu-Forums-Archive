---
title: "Printing from Windows"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by cawill on 2007-03-19
Hi

I have a Officejet G85 which prints and scans fine using ubuntu 6.10

I would like to be able use a windows pc to print over my network.

i followed this thread:
[http://www.ubuntuforums.org/showthread.php?p=1561331#post1561331]("http://www.ubuntuforums.org/showthread.php?p=1561331#post1561331")

But only got as far as editing cupsd.conf, how do I find out what my server name is.

Thanks in advance.
Chris

---

### Post by schwascore on 2007-03-19
The easiest way to print to Ubuntu from XP is to do the following:

- In Ubuntu, click on System --> Administration --> Printing

- Click on Global Settings --> Share Printers.  This will give you a warning saying that you are going to open port 631.  Click OK.

- In Windows XP, go to your Control Panel, then to Printers and Faxes.

- Click on Add Printer

- Make sure that the bottom radio button is selected (add a network printer).  Click Next.

- Click the bottom radio button and enter a URL to your printer.  It should look something like this:

[http://IPOFUBUNTUCOMPUTER:631/printers/YOURPRINTERNAME](http://IPOFUBUNTUCOMPUTER:631/printers/YOURPRINTERNAME)

For example, my URL looks like this:

[http://172.16.0.200:631/printers/HL-2060](http://172.16.0.200:631/printers/HL-2060)

- Click Next

- Now you'll need to select the drivers for your printer and you should be all set.

Good luck!

---

