---
title: "HL-1440 Brother Laser Printer hangs"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-04-24
From the Brother webpage:

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html)

comes a series of instructions:

 **   * All print jobs are aborted and nothing is printed.**

      Create a temporary symbolic link to link the file "/etc/init.d/cups" or "/etc/init.d/cupsys" to "/etc/init.d/lpd".

      For Debian Users:
      ln -s /etc/init.d/cupsys /etc/init.d/lpd
      ln -s /etc/init.d/cupsys /etc/init.d/lprng

   **   After the installation, remove the symbolic link.**

      If you created the symbolic link as below:
      ln -s /etc/init.d/cupsys /etc/init.d/lpd
      you can delete it by "rm /etc/init.d/lpd".

What is meant by "after the installation, remove the symbolic link."? 

I'm guessing that I have to uninstall the printer driver. How do I do that? I'm guessing that the printer must be uncabled from the computer first. Then what?

---

### Post by mikeyphi on 2007-04-25
It means type in the command in the Terminal after all is done
sudo rm /etc/init.d/lpd

If you are still having problems or if you haven't started yet...have a look here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1440](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1440)

---

